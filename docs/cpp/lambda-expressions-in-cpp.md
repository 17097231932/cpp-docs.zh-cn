---
description: 了解更多： c + + 中的 Lambda 表达式
title: C++ 中的 Lambda 表达式
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: 5e65279fa8740876ad8824803ec459ced154f952
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321036"
---
# <a name="lambda-expressions-in-c"></a>C++ 中的 Lambda 表达式

在 c + + 11 及更高版本中，lambda 表达式（通常称为 " *lambda*"）是一种定义匿名函数对象的简便方法， (*关闭*) 在调用的位置或作为参数传递给函数的位置。 Lambda 通常用于封装传递给算法或异步方法的少量代码行。 本文将提供 lambda 的定义、将它与其他编程技术做比较、介绍各自的优点并提供一个基本示例。

## <a name="related-topics"></a>相关主题

- [Lambda 表达式与 function 对象](lambda-expression-syntax.md)
- [使用 lambda 表达式](examples-of-lambda-expressions.md)
- [constexpr Lambda 表达式](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Lambda 表达式的各部分

ISO C++ 标准展示了作为第三个参数传递给 `std::sort()` 函数的简单 lambda：

```cpp
#include <algorithm>
#include <cmath>

void abssort(float* x, unsigned n) {
    std::sort(x, x + n,
        // Lambda expression begins
        [](float a, float b) {
            return (std::abs(a) < std::abs(b));
        } // end of lambda expression
    );
}
```

此图显示了 lambda 的组成部分：

![lambda 表达式的结构化元素](../cpp/media/lambdaexpsyntax.png "lambda 表达式的结构化元素")

1. *捕获子句* (也称为 c + + 规范中的 *引导* 。 ) 

1. *参数列表* 可有可无.  (也称为 *lambda 声明符*) 

1. *可变规范* 可有可无.

1. *异常规范* 可有可无.

1. *尾随-返回类型* 可有可无.

1. *lambda 体*。

### <a name="capture-clause"></a>Capture 子句

Lambda 可以在其主体 (在 **c + + 14**) 中引入新变量，还可以从周围范围访问或 *捕获* 变量。 Lambda 在标准语法) 中 (*lambda-引导* 开始，后者指定捕获的变量以及捕获是通过值还是通过引用捕获。 有与号 (`&`) 前缀的变量通过引用访问，没有该前缀的变量通过值访问。

空 capture 子句 `[ ]` 指示 lambda 表达式的主体不访问封闭范围中的变量。

在标准语法) 中，可以使用默认捕获模式 (*捕获-默认* 值来指示如何捕获 lambda 中引用的任何外部变量：表示引用的 `[&]` 所有变量都按引用捕获， `[=]` 这意味着它们按值捕获。 可以使用默认捕获模式，然后为特定变量显式指定相反的模式。 例如，如果 lambda 体通过引用访问外部变量 `total` 并通过值访问外部变量 `factor`，则以下 capture 子句等效：

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

使用捕获默认值时只捕获 lambda 中提到的变量。

如果捕获子句包含捕获-默认值 `&` ，则 `identifier` 该 capture 子句的中的不 `capture` 能有格式 `& identifier` 。 同样，如果捕获子句包括捕获默认值 `=` ，则该捕获子句中的任何一个 `capture` 都不能具有格式 `= identifier` 。 标识符或 **`this`** 在捕获子句中不能出现多次。 以下代码片段给出了一些示例。

```cpp
struct S { void f(int i); };

void S::f(int i) {
    [&, i]{};      // OK
    [&, &i]{};     // ERROR: i preceded by & when & is the default
    [=, this]{};   // ERROR: this when = is the default
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated
}
```

后跟省略号的捕获是包扩展，如以下 [可变参数模板](../cpp/ellipses-and-variadic-templates.md) 示例所示：

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

若要在类方法的主体中使用 lambda 表达式，请将 **`this`** 指针传递给捕获子句，以提供对封闭类的方法和数据成员的访问。

**Visual Studio 2017 版本15.3 及更高版本** (随 [/std 提供： c + + 17](../build/reference/std-specify-language-standard-version.md)) ： **`this`** 可以通过 **`*this`** 在捕获子句中指定来按值捕获指针。 按值捕获意味着整个 *闭包*（即 encapulates lambda 表达式的匿名函数对象）将复制到调用 lambda 的每个调用站点。 当 lambda 将在并行或异步操作中执行时，按值捕获非常有用，尤其是在某些硬件体系结构（如 NUMA）上。

有关演示如何将 lambda 表达式与类方法一起使用的示例，请参阅 [Lambda 表达式的示例中的](../cpp/examples-of-lambda-expressions.md)"示例：在方法中使用 lambda 表达式"。

在使用 capture 子句时，建议你记住以下几点（尤其是使用采取多线程的 lambda 时）：

- 引用捕获可用于修改外部变量，而值捕获却不能实现此操作。  (**`mutable`** 允许修改副本，而不是原始副本。 ) 

- 引用捕获会反映外部变量的更新，而值捕获却不会反映。

- 引用捕获引入生存期依赖项，而值捕获却没有生存期依赖项。 当 lambda 以异步方式运行时，这一点尤其重要。 如果在异步 lambda 中通过引用捕获本地变量，该本地变量将很可能在 lambda 运行时消失，从而导致运行时访问冲突。

### <a name="generalized-capture-c-14"></a>通用捕获 (C++14)

在 C++14 中，可在 Capture 子句中引入并初始化新的变量，而无需使这些变量存在于 lambda 函数的封闭范围内。 初始化可以任何任意表达式表示；且将从该表达式生成的类型推导新变量的类型。 此功能的一个好处是，在 C++14 中，可从周边范围捕获只移动的变量（例如 std::unique_ptr）并在 lambda 中使用它们。

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>参数列表

除了捕获变量，lambda 还可接受输入参数。 标准语法)  (*lambda 声明符* 的参数列表是可选的，在大多数情况中，与函数的参数列表类似。

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

在 **c + + 14** 中，如果参数类型为泛型，则可以使用 **`auto`** 关键字作为类型说明符。 这将告知编译器将函数调用运算符创建为模板。 参数列表中的每个实例 **`auto`** 都等效于不同的类型参数。

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

Lambda 表达式可以将另一个 Lambda 表达式作为其自变量。 有关详细信息，请参阅 [Lambda 表达式的示例](../cpp/examples-of-lambda-expressions.md)主题中的 "高阶 Lambda 表达式"。

由于参数列表是可选的，因此，如果不将参数传递给 lambda 表达式，并且其 lambda 声明符不包含 *异常规范*、 *尾随返回类型* 或，则可以省略空括号 **`mutable`** 。

### <a name="mutable-specification"></a>可变规范

通常，lambda 的函数调用运算符是按值常数值，但使用 **`mutable`** 关键字会取消此操作。它不会生成可变的数据成员。 利用可变规范，lambda 表达式的主体可以修改通过值捕获的变量。 本文后面的一些示例演示如何使用 **`mutable`** 。

### <a name="exception-specification"></a>异常规范

您可以使用 **`noexcept`** 异常规范来指示 lambda 表达式不会引发任何异常。 与普通函数一样，如果 lambda 表达式声明 [](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) **`noexcept`** 异常规范且 lambda 体引发异常，Microsoft c + + 编译器将生成警告 C4297，如下所示：

```cpp
// throw_lambda_expression.cpp
// compile with: /W4 /EHsc
int main() // C4297 expected
{
   []() noexcept { throw 5; }();
}
```

有关详细信息，请参阅 [异常规范 (throw) ](../cpp/exception-specifications-throw-cpp.md)。

### <a name="return-type"></a>返回类型

将自动推导 Lambda 表达式的返回类型。 [`auto`](../cpp/auto-cpp.md)除非指定 *尾随返回类型*，否则不需要使用关键字。 *尾随返回类型* 类似于普通方法或函数的返回类型部分。 但是，返回类型必须跟在参数列表的后面，并且必须在返回类型前面包含尾随返回类型关键字 **`->`** 。

如果 lambda 体仅包含一个返回语句或其表达式不返回值，则可以省略 lambda 表达式的返回类型部分。 如果 lambda 体包含单个返回语句，编译器将从返回表达式的类型推导返回类型。 否则，编译器会将返回类型推导为 **`void`** 。 下面的代码示例片段说明了这一原则。

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

lambda 表达式可以生成另一个 lambda 表达式作为其返回值。 有关详细信息，请参阅 [Lambda 表达式的示例中的](../cpp/examples-of-lambda-expressions.md)"高阶 Lambda 表达式"。

### <a name="lambda-body"></a>Lambda 体

Lambda 表达式的标准语法) 中的 lambda 体 (*复合语句* 可包含普通方法或函数的主体可包含的任何内容。 普通函数和 lambda 表达式的主体均可访问以下变量类型：

- 从封闭范围捕获变量，如前所述。

- parameters

- 本地声明变量

- 类数据成员（在类中声明时 **`this`** 被捕获）

- 具有静态存储持续时间的任何变量（例如，全局变量）

以下示例包含通过值显式捕获变量 `n` 并通过引用隐式捕获变量 `m` 的 lambda 表达式：

```cpp
// captures_lambda_expression.cpp
// compile with: /W4 /EHsc
#include <iostream>
using namespace std;

int main()
{
   int m = 0;
   int n = 0;
   [&, n] (int a) mutable { m = ++n + a; }(4);
   cout << m << endl << n << endl;
}
```

```Output
5
0
```

由于变量 `n` 是通过值捕获的，因此在调用 lambda 表达式后，变量的值仍保持 `0` 不变。 该 **`mutable`** 规范允许在 `n` lambda 中修改。

尽管 lambda 表达式只能捕获具有自动存储持续时间的变量，但你可以在 lambda 表达式的主体中使用具有静态存储持续时间的变量。 以下示例使用 `generate` 函数和 lambda 表达式为 `vector` 对象中的每个元素赋值。 lambda 表达式将修改静态变量以生成下一个元素的值。

```cpp
void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}
```

有关详细信息，请参阅 [生成](../standard-library/algorithm-functions.md#generate)。

下面的代码示例使用上一示例中的函数，并添加了使用 c + + 标准库算法的 lambda 表达式的示例 `generate_n` 。 该 lambda 表达式将 `vector` 对象的元素指派给前两个元素之和。 **`mutable`** 使用关键字，以便 lambda 表达式的主体可以修改其外部变量的副本 `x` 和 `y` lambda 表达式通过值捕获的副本。 由于 lambda 表达式通过值捕获原始变量 `x` 和 `y`，因此它们的值在 lambda 执行后仍为 `1`。

```cpp
// compile with: /W4 /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}

int main()
{
    // The number of elements in the vector.
    const int elementCount = 9;

    // Create a vector object with each element set to 1.
    vector<int> v(elementCount, 1);

    // These variables hold the previous two elements of the vector.
    int x = 1;
    int y = 1;

    // Sets each element in the vector to the sum of the
    // previous two elements.
    generate_n(v.begin() + 2,
        elementCount - 2,
        [=]() mutable throw() -> int { // lambda is the 3rd parameter
        // Generate current value.
        int n = x + y;
        // Update previous two values.
        x = y;
        y = n;
        return n;
    });
    print("vector v after call to generate_n() with lambda: ", v);

    // Print the local variables x and y.
    // The values of x and y hold their initial values because
    // they are captured by value.
    cout << "x: " << x << " y: " << y << endl;

    // Fill the vector with a sequence of numbers
    fillVector(v);
    print("vector v after 1st call to fillVector(): ", v);
    // Fill the vector with the next sequence of numbers
    fillVector(v);
    print("vector v after 2nd call to fillVector(): ", v);
}
```

```Output
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34
x: 1 y: 1
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18
```

有关详细信息，请参阅 [generate_n](../standard-library/algorithm-functions.md#generate_n)。

## <a name="constexpr-lambda-expressions"></a>`constexpr` lambda 表达式

**Visual Studio 2017 版本15.3 及更高版本** (随 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md)) 提供：在常量表达式中允许使用 lambda 表达式，该表达式可以声明为 **`constexpr`** 或在常量表达式中使用。

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

如果 lambda 的 **`constexpr`** 结果满足函数的要求，则隐式 **`constexpr`** ：

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

如果隐式或显式 lambda **`constexpr`** ，则转换为函数指针将产生一个 **`constexpr`** 函数：

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>Microsoft 专用

以下公共语言运行时中不支持 lambda) 托管实体 (CLR： **`ref class`** 、 **`ref struct`** 、 **`value class`** 或 **`value struct`** 。

如果使用的是 Microsoft 特定的修饰符（例如 [`__declspec`](../cpp/declspec.md) ），则可以将其插入到紧随之后的 lambda 表达式中， `parameter-declaration-clause` 例如：

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

若要确定 lambda 是否支持修饰符，请参阅文档的 [Microsoft 特定修饰符](../cpp/microsoft-specific-modifiers.md) 部分中的相关文章。

除了 c + + 11 标准 lambda 功能，Visual Studio 还支持无状态 lambda，它们可全转换为使用任意调用约定的函数指针。

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C + + 标准库中的函数对象](../standard-library/function-objects-in-the-stl.md)<br/>
[函数调用](../cpp/function-call-cpp.md)<br/>
[`for_each`](../standard-library/algorithm-functions.md#for_each)

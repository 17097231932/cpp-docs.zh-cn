---
description: 了解更多：非标准行为
title: 非标准行为
ms.date: 05/06/2019
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
ms.openlocfilehash: 9f696582b23dfd4a22e6d48b9294a79787518b50
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330849"
---
# <a name="nonstandard-behavior"></a>非标准行为

以下部分列出了 c + + 的 Microsoft 实现不符合 c + + 标准的一些地方。 下面给出的节号引用了 C++ 11 标准 (ISO/IEC 14882:2011(E)) 中的节号。

编译器 [限制](../cpp/compiler-limits.md)中提供了不同于 c + + 标准中定义的编译器限制的列表。

## <a name="covariant-return-types"></a>协变返回类型

当虚函数具有可变数量的自变量时，不支持虚拟基类作为协变返回类型。 这不符合 C++ ISO 规范第 10.3 节第 7 段。 下面的示例不编译，从而提供编译器错误 [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)

```cpp
// CovariantReturn.cpp
class A
{
   virtual A* f(int c, ...);   // remove ...
};

class B : virtual A
{
   B* f(int c, ...);   // C2688 remove ...
};
```

## <a name="binding-nondependent-names-in-templates"></a>绑定模板中的非依赖性名称

最初分析模板时，Microsoft c + + 编译器当前不支持绑定非依赖性名称。 这不符合 C++ ISO 规范的第 14.6.3 节。 这可能导致在模板之后（但在模板实例化之前）声明的重载出现。

```cpp
#include <iostream>
using namespace std;

namespace N {
   void f(int) { cout << "f(int)" << endl;}
}

template <class T> void g(T) {
    N::f('a');   // calls f(char), should call f(int)
}

namespace N {
    void f(char) { cout << "f(char)" << endl;}
}

int main() {
    g('c');
}
// Output: f(char)
```

## <a name="function-exception-specifiers"></a>函数异常说明符

分析但不使用除 `throw()` 以外的函数异常说明符。 这不符合 ISO C++ 规范的第 15.4 节。 例如：

```cpp
void f() throw(int); // parsed but not used
void g() throw();    // parsed and used
```

有关异常规范的详细信息，请参阅 [异常规范](../cpp/exception-specifications-throw-cpp.md)。

## <a name="char_traitseof"></a>char_traits::eof()

C + + 标准状态 [char_traits：： eof](../standard-library/char-traits-struct.md#eof) 不能对应于有效的 `char_type` 值。 Microsoft c + + 编译器对类型 **`char`** （而不是类型）强制此约束 **`wchar_t`** 。 这不符合 C++ ISO 规范的第 12.1.1 节中表 62 的要求。 下面的示例将说明这一点。

```cpp
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

## <a name="storage-location-of-objects"></a>对象的存储位置

C++ 标准（第 1.8 节第 6 段）要求完整的 C++ 对象具有唯一的存储位置。 但是，在 Microsoft c + + 中，某些情况下，没有数据成员的类型将与对象的生存期内的其他类型共享存储位置。

---
description: 了解详细信息： typeid 运算符
title: typeid 运算符
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: 8e036cbdcc540eca224b97b09d174362c454da6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145855"
---
# <a name="typeid-operator"></a>typeid 运算符

## <a name="syntax"></a>语法

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>备注

**`typeid`** 运算符允许在运行时确定对象的类型。

的结果 **`typeid`** 为 `const type_info&` 。 值是对对象的引用， `type_info` 该对象表示 *表达式* 的 *类型 id* 或类型，具体取决于 **`typeid`** 所使用的格式。 有关详细信息，请参阅 [Type_info 类](../cpp/type-info-class.md)。

**`typeid`** 运算符不能与)  (抽象声明符或实例的托管类型一起使用。 有关获取 <xref:System.Type> 指定类型的的信息，请参阅 [typeid](../extensions/typeid-cpp-component-extensions.md)。

**`typeid`** 当应用于多态类类型的左值时，运算符执行运行时检查，其中对象的 true 类型无法由提供的静态信息确定。 此类情况是：

- 对类的引用

- 已取消引用的指针 `*`

- 下标指针 (`[ ]`) 。  (使用带有指向多态类型的指针的下标是不安全的。 ) 

如果 *表达式* 指向基类类型，而对象实际上是派生自该基类的类型，则 `type_info` 结果是派生类的引用。 *表达式* 必须指向具有虚函数)  (类的多态类型。 否则，结果为 `type_info` *表达式* 中引用的静态类的。 此外，必须取消引用指针，以便使用的对象是它所指向的对象。 如果没有取消引用指针，结果将是指针的，而不是指向的 `type_info` 指针。 例如：

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

如果 *表达式* 取消引用指针，并且该指针的值为零，则会 **`typeid`** 引发 [bad_typeid 异常](../cpp/bad-typeid-exception.md)。 如果指针不指向有效的对象，则 `__non_rtti_object` 会引发异常。 它指示尝试分析因对象无效而触发了错误的 RTTI。  (例如，它是错误指针，或者代码未使用 [/GR](../build/reference/gr-enable-run-time-type-information.md)) 编译。

如果该 *表达式* 不是指针，而不是对该对象的基类的引用，则结果是 `type_info` 表示该 *表达式* 的静态类型的引用。 表达式的 *静态类型* 引用表达式的类型，因为它在编译时是已知的。 在计算表达式的静态类型时，将忽略执行语义。 此外，在确定表达式的静态类型时，将忽略引用（如果可能）：

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**`typeid`** 还可在模板中用于确定模板参数的类型：

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>请参阅

[运行时类型信息](../cpp/run-time-type-information.md)\
[关键字](../cpp/keywords-cpp.md)

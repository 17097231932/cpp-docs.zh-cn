---
description: 详细了解：关系运算符： &lt; 、 &gt; 、 &lt; = 和 &gt;=
title: 关系运算符： &lt; 、 &gt; 、 &lt; = 和 &gt;=
ms.date: 11/04/2016
f1_keywords:
- <
- '>'
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
ms.openlocfilehash: dee784c5d93610b27a01ba4ecc36638b84a66885
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252410"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>关系运算符： &lt; 、 &gt; 、 &lt; = 和 &gt;=

## <a name="syntax"></a>语法

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>备注

二进制关系运算符确定下列关系：

- 小于 (**\<**) 

- 大于 (**>**) 

- 小于或等于 (**\<=**) 

- 大于或等于 (**>=**) 

关系运算符具有从左到右的关联性。 关系运算符的两个操作数必须是算术或指针类型。 它们将生成类型的值 **`bool`** 。 **`false`** 如果表达式中的关系为 false，则返回的值为 (0) ; 否则返回的值为 **`true`** (1) 。

## <a name="example"></a>示例

```cpp
// expre_Relational_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << "The true expression 3 > 2 yields: "
         << (3 > 2) << endl
         << "The false expression 20 < 10 yields: "
         << (20 < 10) << endl;
}
```

前面的示例中的表达式必须括在括号中，因为 () 的流插入运算符的 **<<** 优先级高于关系运算符。 因此，未括在括号中的第一个表达式的计算结果将为：

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

[标准转换](standard-conversions.md)中涵盖的常用算术转换将应用于算术类型的操作数。

## <a name="comparing-pointers"></a>比较指针

在比较两个指向同一类型的对象的指针时，结果由程序的地址空间中所指向的对象的位置决定。 也可以将指针与计算结果为0的常量表达式或类型为的指针进行比较 `void *` 。 如果对类型的指针进行了指针比较，则 `void *` 另一个指针将隐式转换为类型 `void *` 。 然后进行比较。

不能比较两个类型不同的指针，除非：

- 一个类型是派生自另一个类型的类类型。

- 至少一个指针会显式转换 (将) 转换为类型 `void *` 。  (其他指针将隐式转换为转换的类型 `void *` 。 ) 

两个指向同一对象的相同类型的指针一定是相等的。 如果比较两个指向对象的非静态成员的指针，则以下规则将适用：

- 如果类类型不为 **`union`** ，并且两个成员未由 *访问说明符*（如 **`public`** 、或）分隔，则 **`protected`** **`private`** 指向最后声明的成员的指针将比指向前面声明的成员的指针比较。

- 如果两个成员由 *访问说明符* 隔开，则结果是不确定的。

- 如果类类型为，则指向 **`union`** 该比较中不同数据成员的指针 **`union`** 相等。

如果两个指针指向同一数组的元素或指向超出数组末尾 1 的元素，则指向带较高下标的对象的指针会更高。 仅当指针引用同一数组中的对象或超出数组末尾 1 的位置时，才能保证指针比较有效。

## <a name="see-also"></a>请参阅

[带有二元运算符的表达式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 关系运算符和相等运算符](../c-language/c-relational-and-equality-operators.md)

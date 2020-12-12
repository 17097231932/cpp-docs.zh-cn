---
description: 详细了解：成员访问运算符：。 与&gt;
title: 成员访问运算符：。 与&gt;
ms.date: 11/04/2016
f1_keywords:
- .
- ->
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators [C++]
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
ms.openlocfilehash: 242ded47c22e0cacfc09659fca275c9e412c004e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276811"
---
# <a name="member-access-operators--and--gt"></a>成员访问运算符：。 与&gt;

## <a name="syntax"></a>语法

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>备注

成员访问运算符 **。** 和 **->** 用于引用结构、联合和类的成员。 成员访问表达式具有选定成员的值和类型。

有两种形式的成员访问表达式：

1. 在第一种形式中， *后缀表达式* 表示结构、类或联合类型的值， *名称* 命名为指定的结构、联合或类的成员。 运算的值是 *名称* 为的值，如果 *后缀表达式* 是左值，则它是左值。

1. 在第二种形式中， *后缀表达式* 表示指向结构、联合或类的指针， *名称* 命名为指定的结构、联合或类的成员。 该值是 *名称* 为的，是左值。 **->** 运算符取消引用指针。 因此，表达式 `e->member` 和 `(*e).member` (，其中 *e* 表示指针) 生成相同的结果 (除了运算符 **->** 或 <strong>\*</strong> 重载) 时除外。

## <a name="example"></a>示例

以下示例演示成员访问运算符的两种形式。

```cpp
// expre_Selection_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Date {
   Date(int i, int j, int k) : day(i), month(j), year(k){}
   int month;
   int day;
   int year;
};

int main() {
   Date mydate(1,1,1900);
   mydate.month = 2;
   cout  << mydate.month << "/" << mydate.day
         << "/" << mydate.year << endl;

   Date *mydate2 = new Date(1,1,2000);
   mydate2->month = 2;
   cout  << mydate2->month << "/" << mydate2->day
         << "/" << mydate2->year << endl;
   delete mydate2;
}
```

```Output
2/1/1900
2/1/2000
```

## <a name="see-also"></a>请参阅

[后缀表达式](../cpp/postfix-expressions.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[类和结构](../cpp/classes-and-structs-cpp.md)<br/>
[结构和联合成员](../c-language/structure-and-union-members.md)

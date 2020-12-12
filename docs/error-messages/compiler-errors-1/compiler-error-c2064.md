---
description: 了解更多：编译器错误 C2064
title: 编译器错误 C2064
ms.date: 11/04/2016
f1_keywords:
- C2064
helpviewer_keywords:
- C2064
ms.assetid: 6cda05da-f437-4f50-9813-ae69538713a3
ms.openlocfilehash: dd9f0386267a81d4f92d6dd0474cd9a3292e7345
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328571"
---
# <a name="compiler-error-c2064"></a>编译器错误 C2064

项不会计算为接受 N 个自变量的函数

通过一个表达式对函数进行调用。 表达式不会计算为指向接受指定数量的参数的函数的指针。

在此示例中，代码尝试调用非函数作为函数。 以下示例生成 C2064：

```cpp
// C2064.cpp
int i, j;
char* p;
void func() {
   j = i();    // C2064, i is not a function
   p();        // C2064, p doesn't point to a function
}
```

必须从对象实例的上下文调用指向非静态成员函数的指针。 以下示例生成 C2064，并演示如何修复此错误：

```cpp
// C2064b.cpp
struct C {
   void func1(){}
   void func2(){}
};

typedef void (C::*pFunc)();

int main() {
   C c;
   pFunc funcArray[2] = {&C::func1, &C::func2};
   (funcArray[0])();    // C2064
   (c.*funcArray[0])(); // OK - function called in instance context
}
```

在类中，成员函数指针必须也指示调用对象上下文。 以下示例生成 C2064，并演示如何修复此错误：

```cpp
// C2064d.cpp
// Compile by using: cl /c /W4 C2064d.cpp
struct C {
   typedef void (C::*pFunc)();
   pFunc funcArray[2];
   void func1(){}
   void func2(){}
   C() {
      funcArray[0] = &C::func1;
      funcArray[1] = &C::func2;
   }
   void func3() {
      (funcArray[0])();   // C2064
      (this->*funcArray[0])(); // OK - called in this instance context
   }
};
```

---
description: 了解更多：编译器错误 C2678
title: 编译器错误 C2678
ms.date: 11/04/2016
f1_keywords:
- C2678
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
ms.openlocfilehash: 9314d3d0201e38c2ce13b48f59356e04e0925a3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220859"
---
# <a name="compiler-error-c2678"></a>编译器错误 C2678

二进制“operator”：未定义接受“type”类型的左操作数的运算符（或者没有可接受的转换）

要使用该运算符，必须针对指定类型将其重载，或者定义一个到某个类型（该运算符已针对此类型进行了定义）的转换。

如果左操作数限定为常量，但运算符定义为采用非常量自变量，则会发生 C2678。

## <a name="examples"></a>示例

下面的示例生成 C2678，并演示如何修复此错误：

```cpp
// C2678a.cpp
// Compile by using: cl /EHsc /W4 C2678a.cpp
struct Combo {
   int number;
   char letter;
};

inline Combo& operator+=(Combo& lhs, int rhs) {
   lhs.number += rhs;
   return lhs;
}

int main() {
   Combo const combo1{ 42, 'X' };
   Combo combo2{ 13, 'Z' };

   combo1 += 6; // C2678
   combo2 += 9; // OK - operator+= matches non-const Combo
}
```

如果没有锁住本机成员就对其调用成员函数，也会发生 C2678。

下面的示例生成 C2678，并演示如何修复此错误。

```cpp
// C2678.cpp
// compile with: /clr /c
struct S { int _a; };

ref class C {
public:
   void M( S param ) {
      test = param;   // C2678

      // OK
      pin_ptr<S> ptest = &test;
      *ptest = param;
   }
   S test;
};
```

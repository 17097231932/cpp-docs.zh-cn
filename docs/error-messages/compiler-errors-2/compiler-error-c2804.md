---
description: 了解更多：编译器错误 C2804
title: 编译器错误 C2804
ms.date: 11/04/2016
f1_keywords:
- C2804
helpviewer_keywords:
- C2804
ms.assetid: b066e563-cca4-450c-8ba7-3b0d7a89f3ea
ms.openlocfilehash: c9281b93a67260e079b72ea70e7febc6a73faff3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339259"
---
# <a name="compiler-error-c2804"></a>编译器错误 C2804

二进制“operator operator”的参数太多

重载的二进制运算符成员函数被声明为带有多个参数。 暗含了二元运算符成员函数的第一个操作数参数，其类型为该运算符的封闭类型。

## <a name="examples"></a>示例

下面的示例生成 C2804，并演示如何修复此错误。

```cpp
// C2804.cpp
// compile by using: cl /c /W4 C2804.cpp
class X {
public:
   X& operator+= (const X &left, const X &right);   // C2804
   X& operator+= (const X &right);   // OK - left operand implicitly *this
};

int main() {
   X x, y;
   x += y;   // equivalent to x.operator+=(y)
}
```

下面的示例生成 C2804，并演示如何修复此错误。

```cpp
// C2804_2.cpp
// compile with: /clr /c
ref struct Y {
   Y^ operator +(Y^ hY, int i);   // C2804
   static Y^ operator +(Y^ hY, int i);   // OK
   Y^ operator +(int i);   // OK
};
```

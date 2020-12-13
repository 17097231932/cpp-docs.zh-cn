---
description: 了解详细信息：编译器警告 (等级 1) C4383
title: 编译器警告（等级 1）C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: f6ece51ed497919cf444952f42130cc3a4bfb4a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339925"
---
# <a name="compiler-warning-level-1-c4383"></a>编译器警告（等级 1）C4383

"instance_dereference_operator"：当存在用户定义的 "operator" 运算符时，取消引用句柄的含义可能会更改;将运算符编写为静态函数，以显式了解操作数

当你在托管类型中添加取消引用运算符的用户定义的实例重写时，可能会重写该类型的取消引用运算符的功能以返回该句柄的对象。 请考虑编写静态的、用户定义的取消引用运算符。

有关详细信息，请参阅 [对象运算符控点 (^) ](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) 和 [跟踪引用运算符](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

此外，实例运算符不适用于其他语言编译器通过引用元数据。 有关详细信息，请参阅 [用户定义的运算符 (c + +/cli) ](../../dotnet/user-defined-operators-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C4383。

```cpp
// C4383.cpp
// compile with: /clr /W1

ref struct S {
   int operator*() { return 0; }   // C4383
};

ref struct T {
   static int operator*(T%) { return 0; }
};

int main() {
   S s;
   S^ pS = %s;

   T t;
   T^ pT = %t;
   T% rT = *pT;
}
```

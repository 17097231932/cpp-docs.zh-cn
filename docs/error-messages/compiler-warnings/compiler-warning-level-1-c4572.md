---
description: 了解详细信息：编译器警告 (等级 1) C4572
title: 编译器警告（等级 1）C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: ab447bc7ef5d702599b1583ae94ac0fa94d29a14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332226"
---
# <a name="compiler-warning-level-1-c4572"></a>编译器警告（等级 1）C4572

[ParamArray] 特性已在/clr 下弃用，请使用 "..."是

使用了指定变量参数列表的过时样式。 为 CLR 进行编译时，请使用省略号语法而不是 <xref:System.ParamArrayAttribute> 。 有关详细信息，请参阅 [变量参数列表 ( (c + +/cli) ) ](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C4572。

```cpp
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```

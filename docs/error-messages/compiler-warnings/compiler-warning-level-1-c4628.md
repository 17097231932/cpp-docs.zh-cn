---
description: 了解详细信息：编译器警告 (等级 1) C4628
title: 编译器警告（等级 1）C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: b5dd017afb5b8bb0d882700cb047643d6d118685
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112370"
---
# <a name="compiler-warning-level-1-c4628"></a>编译器警告（等级 1）C4628

-Ze 不支持二合字母。 字符序列“digraph”未解释为“char”的替换标记

在 [/ze](../../build/reference/za-ze-disable-language-extensions.md)下，不支持二合字母。 此警告后会出现错误。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

下面的示例生成 C4628：

```cpp
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```

---
description: 了解更多：编译器错误 C3872
title: 编译器错误 C3872
ms.date: 11/04/2016
f1_keywords:
- C3872
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
ms.openlocfilehash: 860db2f94fa198246290a0e491b1a647dbc91c20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222731"
---
# <a name="compiler-error-c3872"></a>编译器错误 C3872

“char”：此字符不允许在标识符中使用

C++ 编译器对于标识符中允许的字符遵循 C++ 11 标准。 仅允许在标识符中使用某些范围的字符和通用字符名称。 其他限制适用于标识符的初始字符。 有关允许的字符和通用字符名称范围的详细信息和列表，请参阅 [Identifiers](../../cpp/identifiers-cpp.md)。

编译 C++/CLI 代码时，标识符中允许的字符范围限制更少。 使用 /clr 编译的代码中的标识符应遵循  [标准 ECMA-335：公共语言基础结构 (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm)。

下面的示例生成 C3872：

```cpp
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```

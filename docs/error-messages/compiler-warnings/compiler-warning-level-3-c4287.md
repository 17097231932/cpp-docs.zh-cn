---
description: 详细了解：编译器警告 (等级 3) C4287
title: 编译器警告（等级 3）C4287
ms.date: 11/04/2016
f1_keywords:
- C4287
helpviewer_keywords:
- C4287
ms.assetid: 1bf3bff8-6402-4d06-95ba-431678a790a7
ms.openlocfilehash: a82ad437a4ba6e7e374e7eb8f50359e7bf667e9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344076"
---
# <a name="compiler-warning-level-3-c4287"></a>编译器警告（等级 3）C4287

"operator"：无符号/负常量不匹配

在带有负数的操作中使用了一个无符号的变量。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

## <a name="example"></a>示例

下面的示例生成 C4287：

```cpp
// C4287.cpp
// compile with: /W3
#pragma warning(default : 4287)
#include <stdio.h>

int main()
{
    unsigned int u = 1;
    if (u < -1)   // C4287
        printf_s("u LT -1");
    else
        printf_s("u !LT -1");
    return 0;
}
```

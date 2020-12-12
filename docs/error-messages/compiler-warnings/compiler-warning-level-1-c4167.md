---
description: 了解详细信息：编译器警告 (等级 1) C4167
title: 编译器警告（等级 1）C4167
ms.date: 11/04/2016
f1_keywords:
- C4167
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
ms.openlocfilehash: 8d0b08ea4d97c6e85f5e07ce4844abdae7afafbd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266983"
---
# <a name="compiler-warning-level-1-c4167"></a>编译器警告（等级 1）C4167

函数：仅可用作内部函数

**#pragma 函数** 尝试强制编译器对必须以内部形式使用的函数使用常规调用。 将忽略杂注。

若要避免此警告，请删除 **#pragma 函数**。

## <a name="example"></a>示例

```cpp
// C4167.cpp
// compile with: /W1
#include <malloc.h>
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only
int main(){}
```

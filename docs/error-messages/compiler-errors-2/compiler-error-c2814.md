---
description: 了解更多：编译器错误 C2814
title: 编译器错误 C2814
ms.date: 11/04/2016
f1_keywords:
- C2814
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
ms.openlocfilehash: 3da888c70356abee8ae18990d521d5589a5c5069
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278384"
---
# <a name="compiler-error-c2814"></a>编译器错误 C2814

“member”：本机类型不能嵌套在托管类型或 WinRT 类型“type”内

## <a name="example"></a>示例

本机类型不能嵌套在 CLR 或 WinRT 类型中。 下面的示例生成 C2814，并演示如何修复此错误。

```cpp
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```

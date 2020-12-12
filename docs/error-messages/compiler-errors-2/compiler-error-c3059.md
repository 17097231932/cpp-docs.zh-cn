---
description: 了解更多：编译器错误 C3059
title: 编译器错误 C3059
ms.date: 11/04/2016
f1_keywords:
- C3059
helpviewer_keywords:
- C3059
ms.assetid: 57220324-8286-4cab-a1ab-45385eb1eae0
ms.openlocfilehash: 82629fb77a0cf589f4e311d951fcf1540e0b7c8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281751"
---
# <a name="compiler-error-c3059"></a>编译器错误 C3059

“var”：“threadprivate”符号不能用于“clause”子句中

子句中使用了一个 [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) 符号。

下面的示例生成 C3059：

```cpp
// C3059.cpp
// compile with: /openmp
#include "omp.h"
int x, y;
#pragma omp threadprivate(x, y)

int main() {
   #pragma omp parallel private(x, y)   // C3059
   {
      x = y;
   }
}
```

可能的解决方法：

```cpp
// C3059b.cpp
// compile with: /openmp
#include "omp.h"
int x = 0, y = 0;

int main() {
   #pragma omp parallel firstprivate(y) private(x)
   {
      x = y;
   }
}
```

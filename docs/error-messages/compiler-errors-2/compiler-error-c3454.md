---
description: 了解更多：编译器错误 C3454
title: 编译器错误 C3454
ms.date: 11/04/2016
f1_keywords:
- C3454
helpviewer_keywords:
- C3454
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
ms.openlocfilehash: 3d7905600a5d9502315689f9d25bd6d39dd80763
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315928"
---
# <a name="compiler-error-c3454"></a>编译器错误 C3454

类声明中不允许出现 [attribute]

必须为它定义一个类，使其成为特性。

有关更多信息，请参见 [attribute](../../windows/attributes/attribute.md)。

## <a name="example"></a>示例

下面的示例生成 C3454。

```cpp
// C3454.cpp
// compile with: /clr /c
using namespace System;

[attribute]   // C3454
ref class Attr1;

[attribute]   // OK
ref class Attr2 {};
```

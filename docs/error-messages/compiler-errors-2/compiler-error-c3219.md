---
description: 了解更多：编译器错误 C3219
title: 编译器错误 C3219
ms.date: 11/04/2016
f1_keywords:
- C3219
helpviewer_keywords:
- C3219
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
ms.openlocfilehash: 0210d8c65972a6adc7d5c2dbe51088f3c3766106
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267737"
---
# <a name="compiler-error-c3219"></a>编译器错误 C3219

“param”: 泛型参数不能由多个非接口“class”进行约束

由两个或更多托管类约束泛型参数是无效的。

下面的示例生成 C3219：

```cpp
// C3219.cpp
// compile with: /clr
ref class A {};
ref class B {};

generic <class T>
where T : A, B
ref class E {};   // C3219
```

以下示例演示了可能的解决方法：

```cpp
// C3219b.cpp
// compile with: /clr /c
ref class A {};

interface struct C {};

generic <class T>
where T : A
ref class E {};
```

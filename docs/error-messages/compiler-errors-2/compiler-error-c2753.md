---
description: 了解更多：编译器错误 C2753
title: 编译器错误 C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: d7888086f81f26092d41be440f75ef60400229ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174398"
---
# <a name="compiler-error-c2753"></a>编译器错误 C2753

"*template*"：部分专用化无法与主模板的参数列表匹配

如果模板参数列表与参数列表匹配，则编译器会将其视为相同的模板。 不允许两次定义同一模板。

## <a name="example"></a>示例

下面的示例生成 C2753，并演示如何修复此问题：

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```

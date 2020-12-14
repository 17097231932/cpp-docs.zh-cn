---
description: 了解更多：编译器错误 C2243
title: 编译器错误 C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: 48947ee39e61b2db1a64023f730b89d8be8d1907
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302187"
---
# <a name="compiler-error-c2243"></a>编译器错误 C2243

存在从“类型 1”到“类型 2”的“转换类型”转换，但不可访问

访问保护 (**`protected`** 或 **`private`**) 阻止了从指向派生类的指针到指向基类的指针的转换。

下面的示例生成 C2243：

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

**`protected`** **`private`** 派生类的客户端不能访问具有或访问权限的基类。 这些级别的访问控制用于指示基类是对客户端不可见的实现细节。 如果你希望派生类的客户端有权访问派生类指针到基类指针的隐式转换，请使用公共派生。

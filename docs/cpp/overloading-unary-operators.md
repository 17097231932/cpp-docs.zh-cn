---
description: 了解详细信息：重载一元运算符
title: 重载一元运算符
ms.date: 11/04/2016
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
ms.openlocfilehash: 2e0a2d2b902403ee5ed34a95b6d282d7c2199795
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146050"
---
# <a name="overloading-unary-operators"></a>重载一元运算符

可重载的一元运算符如下：

1. `!` ([逻辑非](../cpp/logical-negation-operator-exclpt.md)) 

1. `&`) [的 (地址](../cpp/address-of-operator-amp.md)

1. `~` ([1 的补数](../cpp/one-s-complement-operator-tilde.md)) 

1. `*` ([指针取消引用](../cpp/indirection-operator-star.md)) 

1. `+` ([一元加](../cpp/additive-operators-plus-and.md)) 

1. `-` ([一元求反](../cpp/additive-operators-plus-and.md)) 

1. `++` ([递增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)) 

1. `--` ([减量](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)) 

1. 转换运算符

后缀递增和递减运算符 (`++` 和 `--`) 在 [递增和递减](../cpp/increment-and-decrement-operator-overloading-cpp.md)中单独处理。

转换运算符也将在单独的主题中进行讨论;请参阅 [用户定义的类型转换](../cpp/user-defined-type-conversions-cpp.md)。

以下规则适用于所有其他一元运算符。 若要将一元运算符函数声明为非静态成员，则必须用以下形式声明它：

> *ret 类型* **`operator`***op* **( # B1**

其中 *ret 类型* 是返回类型， *op* 是上表中列出的运算符之一。

若要将一元运算符函数声明为全局函数，则必须用以下形式声明它：

> *ret 类型* **`operator`***op* **(** *arg* **)**

其中， *ret 类型* 和 *op* 为成员运算符函数所述， *arg* 是要在其上操作的类类型的参数。

> [!NOTE]
> 一元运算符的返回类型没有限制。 例如，逻辑“非”(`!`) 返回整数值是合理的，但并非强制性的。

## <a name="see-also"></a>请参阅

[运算符重载](../cpp/operator-overloading.md)

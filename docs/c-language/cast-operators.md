---
description: 详细了解：强制转换运算符
title: 强制转换运算符
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
ms.openlocfilehash: 181d402e260cf4bf0970881226bf558282297333
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214111"
---
# <a name="cast-operators"></a>强制转换运算符

在特定情况下，类型强制转换提供了用于显式转换对象类型的方法。

## <a name="syntax"></a>语法

*cast-expression*: *unary-expression*

**(**  *type-name*  **)**  *cast-expression*

在进行类型强制转换后，编译器将 cast-expression  视为类型 type-name  。 强制转换可用于在任意标量类型的对象与任何其他标量类型之间进行来回转换。 显式类型强制转换受到确定隐式转换效果的相同规则的约束，如[赋值转换](../c-language/assignment-conversions.md)中所述。 有关强制转换的其他约束可能来源于特定类型的实际大小或表示形式。 有关整型类型的实际大小的信息，请参阅[基本类型的存储](../c-language/storage-of-basic-types.md) 。 有关类型强制转换的详细信息，请参阅[类型强制转换](../c-language/type-cast-conversions.md)。

## <a name="see-also"></a>请参阅

[强制转换运算符：()](../cpp/cast-operator-parens.md)

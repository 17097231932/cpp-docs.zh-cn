---
description: 详细了解：减法 (–)
title: 减法 (–)
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
ms.openlocfilehash: 8e0daf4e1bfdbb844df99e3f79dc2baf5a30e6e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114554"
---
# <a name="subtraction--"></a>减法 (–)

减法运算符 ( **-** ) 从第一个操作数中减去第二个操作数。 两个操作数可同时为整型或浮点型，或者一个操作数为指针，另一个操作数为整数。

在将两个指针相减时，会通过将差值除以指针寻址的类型值的大小来将该差值转换为带符号的整数值。 整数值的大小由标准包含文件 STDDEF.H 中的类型 **ptrdiff_t** 定义。 结果表示两个地址间的类型的内存位置数。 只能保证结果对于同一数组的两个元素有意义，如[指针算法](../c-language/pointer-arithmetic.md)中讨论的那样。

在用指针值减去整数值时，减法运算符会通过将整数值乘以指针寻址的值的大小来转换整数值 (*i*)。 转换后，整数值表示 *i* 个内存位置，其中每个位置均具有指针类型所指定的长度。 当用指针值减去转换后的整数值时，结果将为原始地址前的内存地址 *i* 位置数。 新指针指向通过原始指针值寻址的类型的值。

## <a name="see-also"></a>请参阅

[C 加法运算符](../c-language/c-additive-operators.md)

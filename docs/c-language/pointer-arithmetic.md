---
description: 详细了解：指针算术
title: 指针算术
ms.date: 11/04/2016
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
ms.openlocfilehash: 37ee9fd696f874d1faa84b5d656317cf67f75a6c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243115"
---
# <a name="pointer-arithmetic"></a>指针算术

仅当指针操作数寻址数组成员且整数值在同一数组的边界中产生偏移时，涉及指针和整数的加法运算才会提供有意义的结果。 当整数值转换为地址偏移量时，编译器将假定只有大小相同的内存位置位于原始地址和该地址加上偏移量之间。

此假设对数组成员有效。 按照定义，数组是一系列相同类型的值；数组元素位于连续内存位置。 但是，任何类型（数组元素除外）的存储不一定由相同类型的标识符填充。 即，在内存位置（即使是相同类型的位置）之间可能会出现空白。 因此，对任何值（数组元素除外）的地址进行加法或减法的结果是不确定的。

同样，当两个指针值相减时，转换将假定只有相同类型的值（没有空白）位于操作数给定的地址之间。

## <a name="see-also"></a>请参阅

[C 加法运算符](../c-language/c-additive-operators.md)

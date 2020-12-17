---
description: 详细了解：Naked (C)
title: Naked (C)
ms.date: 11/04/2016
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
ms.openlocfilehash: 8d45371f71ccffda2c7505587f0942671d24b047
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257012"
---
# <a name="naked-c"></a>Naked (C)

**Microsoft 专用**

裸存储类特性是特定于 Microsoft 的 C 语言扩展。 编译器生成代码，而没有使用裸存储类特性声明的函数的 prolog 和 epilog 代码。 当您需要使用内联汇编代码编写自己的 prolog/epilog 代码序列时，裸函数很有用。 裸函数对于编写虚拟设备驱动程序很有用。

有关使用 naked 特性的特定信息，请参阅 [Naked 函数](../c-language/naked-functions.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)

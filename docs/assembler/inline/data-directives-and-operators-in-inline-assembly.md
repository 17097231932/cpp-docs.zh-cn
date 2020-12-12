---
description: 详细了解：内联程序集中的数据指令和运算符
title: 内联程序集中的数据指令和运算符
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: a2b11aa95723245fc977f97f42b1de2f6c7306ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117947"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>内联程序集中的数据指令和运算符

**Microsoft 专用**

尽管 **`__asm`** 块可以引用 c 或 c + + 数据类型和对象，但它不能使用 MASM 指令或运算符来定义数据对象。 具体而言，不能使用定义指令 **DB**， `DW` ， **DD**，，，， `DQ` `DT` `DF` 或运算符 `DUP` 或 **THIS**。 MASM 结构和记录也不可用。 内联汇编程序不接受指令 `STRUC` 、 `RECORD` 、 **宽度** 或 **掩码**。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>

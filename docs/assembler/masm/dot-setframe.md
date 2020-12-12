---
description: 了解详细信息：。.SETFRAME
title: .SETFRAME
ms.date: 12/17/2019
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: b3554da14344293f00c499bc3084e6ddfd93c2ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131074"
---
# <a name="setframe"></a>.SETFRAME

使用指定的寄存器 (*reg*) 并 (*offset*) 偏移量来填充展开信息中的帧寄存器字段和偏移量。 偏移必须是 16 的倍数，并且小于或等于 240。 此指令还 `UWOP_SET_FPREG` 使用当前的序言偏移量为指定的寄存器生成展开代码项。

## <a name="syntax"></a>语法

> **..SETFRAME** *reg*， *offset*

## <a name="remarks"></a>备注

**..SETFRAME** 允许 ml64.exe 用户指定框架函数的展开方式，并且仅在序言内允许，该函数从 [过程](proc.md) 框架声明扩展到 [。ENDPROLOG](dot-endprolog.md) 指令。 这些指令不生成代码;它们仅生成 `.xdata` 和 `.pdata` 。 **..SETFRAME** 后面应是实际实现要展开的操作的说明。 最好将展开指令和它们要展开的代码封装在一个宏中，以确保协议。

有关详细信息，请参阅 [MASM ( # A0) ](masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>示例

### <a name="description"></a>说明

下面的示例演示如何使用帧指针：

### <a name="code"></a>代码

```asm
; ml64 frmex2.asm /link /entry:frmex2 /SUBSYSTEM:CONSOLE
_text SEGMENT
frmex2 PROC FRAME
   push rbp
.pushreg rbp
   sub rsp, 010h
.allocstack 010h
   mov rbp, rsp
.setframe rbp, 0
.endprolog
   ; modify the stack pointer outside of the prologue (similar to alloca)
   sub rsp, 060h

   ; we can unwind from the following AV because of the frame pointer
   mov rax, 0
   mov rax, [rax] ; AV!

   add rsp, 060h
   add rsp, 010h
   pop rbp
   ret
frmex2 ENDP
_text ENDS
END
```

## <a name="see-also"></a>请参阅

[指令参考](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)

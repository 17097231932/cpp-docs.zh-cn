---
description: 了解详细信息：。 (32 位 MASM) 模型
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: a4324b89f1194227edd7f1d5b7bd70560eca16be
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951415"
---
# <a name="model-32-bit-masm"></a>. (32 位 MASM) 模型

初始化程序内存模型。 仅 (32 位 MASM。 ) 

## <a name="syntax"></a>语法

> **.模型***内存-模型*⟦__，__ *语言类型*⟧⟦__，__ *堆栈选项*⟧

### <a name="parameters"></a>参数

*内存模型*\
必需参数，确定代码和数据指针的大小。

*语言类型*\
可选参数，设置过程和公共符号的调用和命名约定。

*stack 选项*\
可选参数。

如果 *内存模式* 为 **平面**，则不使用 *堆栈选项*。

指定 **NEARSTACK** 将堆栈段组合成单个物理段 (**DGROUP**) 以及数据。 堆栈段寄存器 (**SS**) 假定为与数据段注册 (**DS**) 相同的地址。 **FARSTACK** 不会将堆栈分组到 **DGROUP**;因此， **SS** 不等于 **DS**。

## <a name="remarks"></a>注解

**.**[对于 x64 ( # A0)](masm-for-x64-ml64-exe.md)，不使用模型。

下表列出了在面向 16 位和 32 位平台时每个参数的可能的值：

|参数|32 位值|16 位值（支持早期的 16 位开发）|
|---------------|--------------------|----------------------------------------------------------------|
|*内存模型*|**降**|小型、**小型、小型**、**中型**、**大型、大规模**、**平面**  |
|*语言类型*|**C**， **STDCALL**|**C**， **BASIC**， **FORTRAN**， **PASCAL**， **SYSCALL**， **STDCALL**|
|*stack 选项*|未使用|**NEARSTACK**、 **FARSTACK**|

## <a name="code"></a>代码

对于 MASM 的相关示例，可从 [Visual Studio 2010 的 Visual C++ 示例和相关文档](https://github.com/Microsoft/vcsamples)下载编译器示例。

下面的示例演示 `.MODEL` 指令的用法。

## <a name="example"></a>示例

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

ifndef X64
.686p
.XMM
.model flat, C
endif

.data
; user data

.code
; user code

fxn PROC public
  xor eax, eax ; zero function return value
  ret
fxn ENDP

end
```

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)

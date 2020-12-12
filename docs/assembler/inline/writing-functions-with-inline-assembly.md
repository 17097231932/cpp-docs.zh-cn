---
description: 了解详细信息：用内联程序集编写函数
title: 使用内联程序集编写函数
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
ms.openlocfilehash: 94a1e03842620982e74818dbf2f1bd492a2a4738
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121798"
---
# <a name="writing-functions-with-inline-assembly"></a>使用内联程序集编写函数

**Microsoft 专用**

如果使用内联程序集代码编写函数，则可轻松将自变量传递给函数并从中返回一个值。 下面的示例先比较为单独的汇编程序编写的函数，然后为内联汇编程序重新编写函数。 称为 `power2` 的函数接收两个参数，将第一个参数乘以 2 得到第二个参数的幂。 为单独的汇编程序编写的函数如下所示：

```asm
; POWER.ASM
; Compute the power of an integer
;
       PUBLIC _power2
_TEXT SEGMENT WORD PUBLIC 'CODE'
_power2 PROC

        push ebp        ; Save EBP
        mov ebp, esp    ; Move ESP into EBP so we can refer
                        ;   to arguments on the stack
        mov eax, [ebp+4] ; Get first argument
        mov ecx, [ebp+6] ; Get second argument
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )
        pop ebp         ; Restore EBP
        ret             ; Return with sum in EAX

_power2 ENDP
_TEXT   ENDS
        END
```

由于此函数是为单独汇编程序编写的，因此它需要单独的源文件、程序集和链接步骤。 C 和 C++ 函数参数通常在堆栈上传递，因此该版本的 `power2` 函数通过其在堆栈上的位置访问其参数。  (请注意，在 MASM 和某些其他组装器中提供的 **MODEL** 指令还允许按名称访问堆栈参数和局部堆栈变量。 ) 

## <a name="example"></a>示例

此程序利用内联程序集代码编写 `power2` 函数：

```cpp
// Power2_inline_asm.c
// compile with: /EHsc
// processor: x86

#include <stdio.h>

int power2( int num, int power );

int main( void )
{
    printf_s( "3 times 2 to the power of 5 is %d\n", \
              power2( 3, 5) );
}
int power2( int num, int power )
{
   __asm
   {
      mov eax, num    ; Get first argument
      mov ecx, power  ; Get second argument
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )
   }
   // Return with result in EAX
}
```

`power2` 函数的内联版本按名称引用其自变量并显示在程序的其余部分所在的同一源文件中。 此外，该版本需要的程序集指令更少。

由于内联版本的 `power2` 不执行 C **`return`** 语句，因此如果您在警告级别2或更高版本中进行编译，则会导致出现无害警告。 函数会返回一个值，但编译器无法在没有语句的情况下告诉该函数 **`return`** 。 您可以使用 [#pragma 警告](../../preprocessor/warning.md) 来禁用此警告的生成。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用 C 或 c + +](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>

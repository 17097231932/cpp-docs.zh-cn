---
description: 了解更多：在内联程序集中调用 c + + 函数
title: 在内联汇编程序内调用 C++ 函数
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
ms.openlocfilehash: 3efd4f00eae5810b287a27546bba3160f479b8f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117960"
---
# <a name="calling-c-functions-in-inline-assembly"></a>在内联汇编程序内调用 C++ 函数

**Microsoft 专用**

**`__asm`** 块只能调用不会重载的全局 c + + 函数。 如果调用重载的全局 C++ 函数或 C++ 成员函数，则编译器会发出错误。

还可以调用用 **extern "C"** 链接声明的任何函数。 这允许 **`__asm`** c + + 程序中的块调用 C 库函数，因为所有标准标头文件都将库函数声明为具有 **Extern "C"** 链接。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>

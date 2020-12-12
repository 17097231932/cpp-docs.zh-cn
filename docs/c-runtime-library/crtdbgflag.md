---
description: 了解详细信息： _crtDbgFlag
title: _CRTDBG_CHECK_CRT_DF
ms.date: 11/04/2016
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
ms.openlocfilehash: ef3c72b89ea9e5e557a567af9a9c52c8e85370ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246739"
---
# <a name="_crtdbgflag"></a>_CRTDBG_CHECK_CRT_DF

**_crtDbgFlag** 标志由五个位域组成，这些字段可控制如何在堆的调试版本上跟踪、验证、报告和转储内存分配。 使用 [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 函数设置该标志的位域。 将在 Crtdbg.h 中声明此标志及其位域。 此标志仅当已在应用程序中定义 [_DEBUG](../c-runtime-library/debug.md) 标志时才可用。

有关将此标志与其他调试函数结合使用的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="see-also"></a>请参阅

[控件标志](../c-runtime-library/control-flags.md)

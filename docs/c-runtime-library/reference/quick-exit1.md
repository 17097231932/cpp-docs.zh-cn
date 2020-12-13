---
description: 了解详细信息： quick_exit
title: quick_exit1
ms.date: 11/04/2016
api_name:
- quick_exit
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 85640af902092d5cc60a1c718dfd8999c41406b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137093"
---
# <a name="quick_exit"></a>quick_exit

导致产生正常程序终止。

## <a name="syntax"></a>语法

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>parameters

*status*<br/>
要返回给主机环境的状态代码。

## <a name="return-value"></a>返回值

**Quick_exit** 函数无法返回到其调用方。

## <a name="remarks"></a>备注

**Quick_exit** 函数导致正常程序终止。 它不调用由 **atexit**、 **_onexit** 或 **信号功能注册的信号** 处理程序注册的任何函数。 如果多次调用 **quick_exit** 或者也调用了 **exit** 函数，则行为是不确定的。

**Quick_exit** 函数在后进先出 (后进先出，) order，通过 **at_quick_exit** 注册的函数，但在注册该函数时已调用的函数除外。  如果在已注册函数的调用过程中进行会终止该函数调用的 [longjmp](longjmp.md) 调用，则行为不确定。

调用已注册的函数后， **quick_exit** 通过使用 *status* 值返回对主机环境的控制来调用 **_Exit** 。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**quick_exit**|\<process.h> 或 \<stdlib.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[中止](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec，_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn，_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>

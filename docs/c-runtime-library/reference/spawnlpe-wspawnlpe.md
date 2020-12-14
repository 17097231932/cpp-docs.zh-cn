---
description: 了解详细信息： _spawnlpe、_wspawnlpe
title: _spawnlpe、_wspawnlpe
ms.date: 11/04/2016
api_name:
- _spawnlpe
- _wspawnlpe
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
- api-ms-win-crt-process-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wspawnlpe
- _spawnlpe
- wspawnlpe
helpviewer_keywords:
- _wspawnlpe function
- wspawnlpe function
- processes, creating
- spawnlpe function
- _spawnlpe function
- processes, executing new
- process creation
ms.assetid: e171ebfa-70e7-4c44-8331-2a291fc17bd6
ms.openlocfilehash: ebe51a8268bb8b641492ef40bd37e55e19bef0c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262953"
---
# <a name="_spawnlpe-_wspawnlpe"></a>_spawnlpe、_wspawnlpe

创建并执行更新过程。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
intptr_t _spawnlpe(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wspawnlpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>参数

*mode*<br/>
调用进程的执行模式。

*cmdname*<br/>
要执行的文件的路径。

*arg0*， *arg1*，.。。 *argn*<br/>
指向参数的指针的列表。 *Arg0* 参数通常是指向 *cmdname* 的指针。 参数 *arg1* 到 *argn* 是指向构成新参数列表的字符串的指针。 在 *argn* 之后，必须有一个 **NULL** 指针，用于标记参数列表的末尾。

*envp*<br/>
指向环境设置的指针的数组。

## <a name="return-value"></a>返回值

同步 **_spawnlpe** 或 **_wspawnlpe** 为 *模式*) 指定 (**_P_WAIT** 的返回值是新进程的退出状态。 **_Spawnlpe** 为 *mode* **_P_NOWAITO 指定的** 异步或 **_wspawnlpe** **_P_NOWAIT** (的返回值是进程句柄。 如果进程正常终止，则退出状态为 0。 如果生成进程专门使用非零参数调用 **退出** 例程，则可以将退出状态设置为一个非零值。 如果更新过程未显式设置正退出状态，则正退出状态指示因中止或中断而造成的异常退出。 返回值-1 表示一个错误， (未) 启动新进程。 在这种情况下， **errno** 设置为以下值之一。

| 值 | 描述 |
|-|-|
| **E2BIG** | 参数列表超过 1024 个字节。 |
| **EINVAL** | *mode* 参数无效。 |
| **ENOENT** | 未找到文件或路径。 |
| **ENOEXEC** | 指定的文件不是可执行文件或者有无效的可执行文件格式。 |
| **ENOMEM** | 没有足够的内存可用于执行新进程。 |

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

其中每个函数都创建并执行一个新进程，将每个命令行自变量作为单独的参数进行传递，并将一个数组指针传递给环境设置。 这些函数使用 **PATH** 环境变量查找要执行的文件。

这些函数验证其参数。 如果 *cmdname* 或 *arg0* 为空字符串或 null 指针，则将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将 **errno** 设置为 **EINVAL**，并返回-1。 不生成任何新进程。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_spawnlpe**|\<process.h>|
|**_wspawnlpe**|\<stdio.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

在参见 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)中的示例。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn，_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[中止](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec，_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>

---
title: system、_wsystem
ms.date: 4/2/2020
api_name:
- system
- _wsystem
- _o__wsystem
- _o_system
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tsystem
- _wsystem
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
ms.openlocfilehash: 15e4637d709fdf4600ecb4c66c7d4a75c4fa07eb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844972"
---
# <a name="system-_wsystem"></a>system、_wsystem

执行命令。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int system(
   const char *command
);
int _wsystem(
   const wchar_t *command
);
```

### <a name="parameters"></a>参数

*command*<br/>
要执行的命令。

## <a name="return-value"></a>返回值

如果 *命令* 为 **NULL** ，并且找到命令解释器，则返回一个非零值。 如果未找到命令解释器，则返回0，并将 **errno** 设置为 **ENOENT**。 如果 *命令* 不为 **NULL**，则 **系统** 返回由命令解释器返回的值。 仅当命令解释器返回值 0 时，它才会返回值 0。 返回值-1 表示错误， **errno** 设置为以下值之一：

| 值 | 说明 |
|-|-|
| **E2BIG** | 自变量列表（与系统相关）太大。 |
| **ENOENT** | 无法找到命令解释器。 |
| **ENOEXEC** | 由于格式无效，无法执行命令解释器文件。 |
| **ENOMEM** | 没有足够的内存可用于执行命令；或可用内存已损坏；或存在无效块，这表明进行调用的进程未正确进行分配。 |

有关这些返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlis 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>注解

**系统**函数将*命令*传递到命令解释器，后者将字符串作为操作系统命令执行。 **系统** 使用 **COMSPEC** 和 **PATH** 环境变量查找 CMD.exe 的命令解释器文件。 如果 *command* 为 **NULL**，则该函数只检查命令解释器是否存在。

你必须通过使用 [fflush](fflush.md) 或 [_flushall](flushall.md)显式刷新，或在调用 **system**之前关闭任何流。

**_wsystem**是**系统**的宽字符版本;**_wsystem**的*命令*参数是宽字符字符串。 否则这些函数具有相同行为。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**系统**|**系统**|**_wsystem**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**系统**|\<process.h> 或 \<stdlib.h>|
|**_wsystem**|\<process.h> 或 \<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此示例使用 **SYSTEM** 键入一个文本文件。

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crt_systemtxt"></a>输入：crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
Line two.
```

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec，_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn，_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>

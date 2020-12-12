---
description: 了解详细信息： perror、_wperror
title: perror、_wperror
ms.date: 4/2/2020
api_name:
- _wperror
- perror
- _o__wperror
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
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: e63108ac90170d460ee8a2c86e1db773343c1911
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304683"
---
# <a name="perror-_wperror"></a>perror、_wperror

打印错误消息。

## <a name="syntax"></a>语法

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>parameters

*message*<br/>
要打印的字符串消息。

## <a name="remarks"></a>备注

**Perror** 函数将错误消息打印到 **stderr**。 **_wperror** 是 **_perror** 的宽字符版本;**_wperror** 的 *message* 参数是宽字符字符串。 否则 **_wperror** 和 **_perror** 的行为相同。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

首先打印一 *条消息*，后跟一个冒号，最后是产生错误的最后一个库调用的系统错误消息，最后是一个换行符。 如果 *message* 为 null 指针或指向空字符串的指针，则 **perror** 仅打印系统错误消息。

错误数字存储在变量 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 中（在 ERRNO.H 中定义）。 通过变量 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 访问系统错误消息，该变量是按错误编号排序的消息数组。 **perror** 使用 **errno** 值作为要 **_sys_errlist** 的索引来打印相应的错误消息。 变量 [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 的值定义为 **_sys_errlist** 数组中的最大元素数。

为获得准确的结果，请在库例程返回错误后立即调用 **perror** 。 否则，后续调用会覆盖 **errno** 值。

在 Windows 操作系统中，某些 **errno** 值列在 errno 中。H 未使用。 这些值将保留以供 UNIX 操作系统使用。 有关 Windows 操作系统使用的 **errno** 值的列表，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。 **perror** 为这些平台未使用的任何 **errno** 值打印一个空字符串。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**perror**|\<stdio.h> 或 \<stdlib.h>|
|**_wperror**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror、_strerror、_wcserror \_ _wcserror](strerror-strerror-wcserror-wcserror.md)<br/>

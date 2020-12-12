---
description: 了解详细信息： _access_s、_waccess_s
title: _access_s、_waccess_s
ms.date: 4/2/2020
api_name:
- _access_s
- _waccess_s
- _o__access_s
- _o__waccess_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- waccess_s
- access_s
- _waccess_s
- _access_s
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
ms.openlocfilehash: cf46f3996005584a8f17b25baac60b9c5683ed19
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303838"
---
# <a name="_access_s-_waccess_s"></a>_access_s、_waccess_s

确定文件的读取/写入权限。 这是 [_access、_waccess](access-waccess.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t _access_s(
   const char *path,
   int mode
);
errno_t _waccess_s(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>parameters

*路径*<br/>
文件或目录路径。

*mode*<br/>
权限设置。

## <a name="return-value"></a>返回值

如果该文件具有给定的模式，则每个函数将返回 0。 如果命名文件不存在或无法以指定模式进行访问，则该函数将返回错误代码。 在这种情况下，该函数从如下集合中返回错误代码，并同时将 `errno` 设置为相同的值。

|errno 值|条件|
|-|-|
`EACCES`|访问被拒绝。 文件的权限设置不允许指定的访问权限。
`ENOENT`|未找到文件名或路径。
`EINVAL`|参数无效。

有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

与文件一起使用时， **_access_s** 函数确定指定的文件是否存在，并可按 *mode* 值的指定进行访问。 与目录一起使用时 **_access_s** 仅确定指定的目录是否存在。 在 Windows 2000 和更高版本的操作系统中，所有目录都具有读取和写入访问权限。

|模式值|文件检查内容|
|----------------|---------------------|
|00|仅检查是否存在。|
|02|写入权限。|
|04|读取权限。|
|06|读取和写入权限。|

读取或写入文件的权限不足以确保文件的打开功能。 例如，如果某个文件被另一个进程锁定，则它可能无法访问，即使 **_access_s** 返回0。

**_waccess_s** 是 **_access_s** 的宽字符版本，其中 **_waccess_s** 的 *path* 参数是宽字符字符串。 否则， **_waccess_s** 和 **_access_s** 的行为相同。

这些函数验证其参数。 如果 *path* 为 NULL 或 *模式* 未指定有效模式，则将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<wchar.h> 或 \<io.h>|\<errno.h>|

## <a name="example"></a>示例

此示例使用 **_access_s** 来检查名为 crt_access_s 的文件，以查看其是否存在以及是否允许写入。

```C
// crt_access_s.c

#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    errno_t err = 0;

    // Check for existence.
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )
    {
        printf_s( "File crt_access_s.c exists.\n" );

        // Check for write permission.
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )
        {
            printf_s( "File crt_access_s.c does have "
                      "write permission.\n" );
        }
        else
        {
            printf_s( "File crt_access_s.c does not have "
                      "write permission.\n" );
        }
    }
    else
    {
        printf_s( "File crt_access_s.c does not exist.\n" );
    }
}
```

```Output
File crt_access_s.c exists.
File crt_access_s.c does not have write permission.
```

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_access、_waccess](access-waccess.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_stat、_wstat 函数](stat-functions.md)

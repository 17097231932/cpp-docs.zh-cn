---
description: 了解详细信息： _getcwd_dbg、_wgetcwd_dbg
title: _getcwd_dbg、_wgetcwd_dbg
ms.date: 11/04/2016
api_name:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
ms.openlocfilehash: e470402cc258bf0fa0512136229eeace5bac466e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256596"
---
# <a name="_getcwd_dbg-_wgetcwd_dbg"></a>_getcwd_dbg、_wgetcwd_dbg

[_getcwd、_wgetcwd](getcwd-wgetcwd.md) 函数的调试版本（仅在调试过程中可用）。

## <a name="syntax"></a>语法

```C
char *_getcwd_dbg(
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetcwd_dbg(
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>parameters

*宽限*<br/>
路径的存储位置。

*maxlen*<br/>
路径的最大长度（字符）： **`char`** 适用于 **_getcwd_dbg** 和 **`wchar_t`** **_wgetcwd_dbg**。

*blockType*<br/>
内存块的请求类型： **_CLIENT_BLOCK** 或 **_NORMAL_BLOCK**。

*filename*<br/>
指向请求分配操作的源文件名的指针或 **NULL**。

*linenumber*<br/>
请求分配操作所在的源文件中的行号或 **NULL**。

## <a name="return-value"></a>返回值

返回一个指向 *缓冲区* 的指针。 **空** 返回值指示一个错误，并且 **Errno** 设置为 **ENOMEM**，指示 (在将 **NULL** 参数指定为 *缓冲区*) 时内存不足，无法分配 *maxlen* **字节，指示** 该路径长于 *maxlen* 个字符。

有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Getcwd_dbg** 和 **_wgetcwd_dbg** 函数与 **_getcwd** 和 **_wgetcwd** 相同，不同之处在于，定义 **_DEBUG** 时，如果将 **NULL** 作为第一个参数传递，则这些函数将使用 **malloc** 和 **_malloc_dbg** 的调试版本来分配内存。 有关详细信息，请参阅 [_malloc_dbg](malloc-dbg.md)。

在大多数情况下，无需显式调用这些函数。 您可以改为定义 **_CRTDBG_MAP_ALLOC** 标志。 定义 **_CRTDBG_MAP_ALLOC** 时，对 **_getcwd** 和 **_wgetcwd** 的调用将分别重新映射到 **_getcwd_dbg** 和 **_wgetcwd_dbg**，并将 *blockType* 设置为 **_NORMAL_BLOCK**。 因此，无需显式调用这些函数，除非你希望将堆块标记为 **_CLIENT_BLOCK**。 有关详细信息，请参阅 [调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[目录控件](../../c-runtime-library/directory-control.md)<br/>
[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>

---
description: 了解详细信息： _write
title: _write
ms.date: 4/2/2020
api_name:
- _write
- _o__write
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: 15988f803b37f9ce128a49662c2311a4aa6ca8fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117154"
---
# <a name="_write"></a>_write

将数据写入文件。

## <a name="syntax"></a>语法

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>parameters

*fd*<br/>
可向其中写入数据的文件的文件描述符。

*宽限*<br/>
要写入的数据。

*计数*<br/>
字节数。

## <a name="return-value"></a>返回值

如果成功， **_write** 返回写入的字节数。 如果磁盘上剩余的实际空间小于函数尝试写入磁盘的缓冲区的大小， **_write** 将失败，并且不会将任何缓冲区内容刷新到磁盘。 返回值-1 表示错误。 如果传递的参数无效，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回-1，并将 **errno** 设置为以下三个值之一： **ebadf (**，这意味着文件描述符无效或文件未打开以进行写入; **ENOSPC**，这意味着设备上没有足够的空间用于操作;或 **EINVAL**，这意味着 *缓冲区* 为空指针，或在 Unicode 模式下传递到文件的奇数字节 *数* 。

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果在文本模式下打开该文件，则会在输出中将每个换行符替换为回车换行符。 此替换不会影响返回值。

在 Unicode 转换模式下打开该文件时（例如，如果使用 **_open** 或 **_sopen** 使用包含 **_O_WTEXT** 的模式参数打开 *fd* ， **_O_U16TEXT** 或 **_O_U8TEXT**，或者，如果它通过使用 **fopen** 和包含 **ccs = Unicode**、 **ccs = utf-utf-16le** 或 **ccs = utf-8** 的模式参数打开，或者通过使用 **_setmode** 将模式更改为 Unicode 转换模式，则将 *缓冲区* 解释为指向 **`wchar_t`** 包含 **utf-16** 数据的数组的指针。 尝试在此模式下写入奇数个字节会导致参数验证错误。

## <a name="remarks"></a>备注

**_Write** 函数将 *缓冲区* 中的 *计数* 字节写入与 *fd* 关联的文件中。 写入操作从与给定文件相关联的文件指针（如果有）的当前位置开始执行。 如果文件处于打开状态以供追加，则该操作从该文件的当前末尾位置开始执行。 写入操作完成后，文件指针将按写入的字节数增加。

写入在文本模式下打开的文件时， **_write** 会将 CTRL + Z 字符视为文件的逻辑端。 写入设备时， **_write** 会将缓冲区中的 CTRL + Z 字符视为输出终止符。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_write**|\<io.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occurred
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>请参阅

[低级别 i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>

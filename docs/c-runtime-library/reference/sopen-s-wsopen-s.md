---
description: 了解详细信息： _sopen_s、_wsopen_s
title: _sopen_s、_wsopen_s
ms.date: 4/2/2020
api_name:
- _sopen_s
- _wsopen_s
- _o__sopen_s
- _o__wsopen_s
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
- _sopen_s
- wsopen_s
- _wsopen_s
- sopen_s
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
ms.openlocfilehash: 14a15f78ad452873813f9a6eb4f65de93cd055b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136989"
---
# <a name="_sopen_s-_wsopen_s"></a>_sopen_s、_wsopen_s

打开文件以供共享。 这些版本的 [_sopen 和 _wsopen](sopen-wsopen.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
errno_t _sopen_s(
   int* pfh,
   const char *filename,
   int oflag,
   int shflag,
   int pmode
);
errno_t _wsopen_s(
   int* pfh,
   const wchar_t *filename,
   int oflag,
   int shflag,
   int pmode,
);
```

### <a name="parameters"></a>parameters

*pfh*<br/>
文件句柄或 -1（如果出现错误）。

*filename*<br/>
文件名。

*oflag*<br/>
允许的操作类型。

*shflag*<br/>
允许的共享类型。

*pmode*<br/>
权限设置。

## <a name="return-value"></a>返回值

非零返回值指示错误;在这种情况下， **errno** 设置为以下值之一。

|errno 值|条件|
|-|-|
| **EACCES** |  给定路径是目录，或者文件是只读的，但是已尝试打开以供写入操作。 |
| **EEXIST** |  指定了 **_O_CREAT** 和 **_O_EXCL** 标志，但 *filename* 已经存在。 |
| **EINVAL** |  *Oflag*、 *shflag* 或 *pmode* 参数无效，或者 *pfh* 或 *filename* 为 null 指针。 |
| **EMFILE** | 没有更多可用的文件描述符。 |
| **ENOENT** | 未找到文件或路径。 |

如果将无效参数传递到该函数，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 **errno** 设置为 **EINVAL** ，并返回 **EINVAL** 。

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果出现错误，则通过 *pfh* (返回-1，除非 *pfh* 为 null 指针) 。

## <a name="remarks"></a>备注

**_Sopen_s** 函数将打开 *文件名* 指定的文件，并准备文件以供 *oflag* 和 *shflag* 定义的共享读取或写入。 **_wsopen_s** 是 **_sopen_s** 的宽字符版本;**_wsopen_s** 的 *filename* 参数是宽字符字符串。 否则 **_wsopen_s** 和 **_sopen_s** 的行为相同。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

整数表达式 *oflag* 是通过合并在中定义的一个或多个清单常量而形成的 \<fcntl.h> 。 当两个或多个常量构成参数 *oflag* 时，它们将与按位 "或" 运算符组合 ( **&#124;** ) 。

|*oflag* 常量|行为|
|-|-|
| **_O_APPEND** | 在执行每个写入操作之前，将文件指针移动到文件末尾。 |
| **_O_BINARY** | 在二进制（未转换）模式下打开该文件。 （有关二进制模式的说明，请参阅 [fopen](fopen-wfopen.md)。） |
| **_O_CREAT** | 创建文件并打开它以供写入。 如果 *文件名* 指定的文件存在，则不起作用。 指定 **_O_CREAT** 时， *pmode* 参数是必需的。 |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | 创建一个文件作为临时文件，如果可能，请不要将它刷新到磁盘中。 指定 **_O_CREAT** 时， *pmode* 参数是必需的。 |
| **_O_CREAT** &#124; **_O_TEMPORARY** | 创建一个文件作为临时文件；在关闭最后一个文件描述符时，删除该文件。 指定 **_O_CREAT** 时， *pmode* 参数是必需的。 |
| **_O_CREAT** &#124; `_O_EXCL` | 如果 *文件名* 指定的文件存在，则返回一个错误值。 仅当与 **_O_CREAT** 一起使用时才适用。 |
| **_O_NOINHERIT** | 阻止创建共享文件描述符。 |
| **_O_RANDOM** | 指定缓存针对（但不限于）从磁盘的随机访问进行优化。 |
| **_O_RDONLY** | 打开文件以供只读。 不能与 **_O_RDWR** 或 **_O_WRONLY** 一起指定。 |
| **_O_RDWR** | 打开文件以供读取和写入。 不能与 **_O_RDONLY** 或 **_O_WRONLY** 一起指定。 |
| **_O_SEQUENTIAL** | 指定缓存针对（但不限于）从磁盘的顺序访问进行优化。 |
| **_O_TEXT** | 在文本（转换）模式下打开文件。 （有关详细信息，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](fopen-wfopen.md)。） |
| **_O_TRUNC** | 打开文件并将其长度截断为零；该文件必须具有写入权限。 不能与 **_O_RDONLY** 一起指定。 与 **_O_CREAT** 一起使用 **_O_TRUNC** 会打开现有文件或创建文件。 **注意：****_O_TRUNC** 标志会销毁指定文件的内容。 |
| **_O_WRONLY** | 打开文件以供只写。 不能与 **_O_RDONLY** 或 **_O_RDWR** 一起指定。 |
| **_O_U16TEXT** | 在 Unicode UTF-16 模式下打开文件。 |
| **_O_U8TEXT** | 在 Unicode UTF-8 模式下打开文件。 |
| **_O_WTEXT** | 在 Unicode 模式下打开文件。 |

若要指定文件访问模式，必须指定 **_O_RDONLY**、 **_O_RDWR** 或 **_O_WRONLY**。 对于访问模式，不存在默认值。

当使用 **_O_WTEXT**、 **_O_U8TEXT** 或 **_O_U16TEXT** 在 Unicode 模式下打开文件时，输入函数会将从文件读取的数据转换为存储为类型的 utf-16 数据 **`wchar_t`** 。 写入在 Unicode 模式下打开的文件的函数需要包含存储为类型的 UTF-16 数据的缓冲区 **`wchar_t`** 。 如果将文件编码为 UTF-8，则在写入它时，UTF-16 数据会转换为 UTF-8；在读取它时，该文件的 UTF-8 编码的内容会转换为 UTF-16。 尝试在 Unicode 模式下读取或写入奇数个字节会导致参数验证错误。 若要读取或写入在你的程序中存储为 UTF-8 的数据，请使用文本或二进制文件模式，而不是 Unicode 模式。 你应负责所有必需的编码转换。

如果 **_O_WRONLY**  |  **_O_APPEND** (追加模式) 和 **_O_WTEXT**、_O_U16TEXT 或 **_O_U8TEXT** 调用_sopen_s，则它首先会尝试打开文件进行读取和写入、读取 BOM，然后将其重新打开以进行写入。 如果无法打开该文件以供读取和写入，则它将打开该文件以供只写，并使用 Unicode 模式设置的默认值。

自变量 *shflag* 是一个常量表达式，它包含在中定义的以下清单常量之一 \<share.h> 。

|*shflag* 常量|行为|
|-|-|
| **_SH_DENYRW** | 拒绝对文件的读取和写入访问。 |
| **_SH_DENYWR** | 拒绝对文件的写入访问。 |
| **_SH_DENYRD** | 拒绝对文件的读取访问。 |
| **_SH_DENYNO** | 允许读取和写入访问。 |

*Pmode* 参数始终是必需的，与 **_sopen** 中的不同。 指定 **_O_CREAT** 时，如果该文件不存在， *pmode* 将指定文件的权限设置，该设置将在首次关闭新文件时设置。 否则，将忽略 *pmode* 。 *pmode* 是一个整数表达式，它包含中定义的一个或两个清单常量 **_S_IWRITE** 和 **_S_IREAD** \<sys\stat.h> 。 当给定这两个常量时，将使用按位“或”运算符合并它们。 *Pmode* 的含义如下所示。

|*pmode*|含义|
|-|-|
| **_S_IREAD** | 只允许读取。 |
| **_S_IWRITE** | 允许写入。 （实际上，允许读取和写入。） |
| **_S_IREAD** &#124; **_S_IWRITE** | 允许读取和写入。 |

如果未授予写入权限，则该文件为只读。 在 Windows 操作系统中，所有文件均可读；不可能提供只写权限。 因此， **_S_IWRITE** 和 **_S_IREAD**  |  **_S_IWRITE** 的模式是等效的。

**_sopen_s** 在设置权限之前将当前文件权限掩码应用到 *pmode* 。 （请参阅 [_umask](umask.md)。）

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen_s**|\<io.h> 或 \<wchar.h>|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|

**_sopen_s** 和 **_wsopen_s** 是 Microsoft 扩展。 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_locking](locking.md) 的示例。

## <a name="see-also"></a>请参阅

[低级别 i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_fsopen、_wfsopen](fsopen-wfsopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>

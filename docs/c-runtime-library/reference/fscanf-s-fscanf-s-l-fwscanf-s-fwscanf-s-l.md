---
description: 了解详细信息： fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l
title: fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l
ms.date: 11/04/2016
api_name:
- fwscanf_s
- _fscanf_s_l
- _fwscanf_s_l
- fscanf_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fwscanf_s_l
- _fscanf_s_l
- fscanf_s
- _ftscanf_s_l
- _ftscanf_s
- fwscanf_s
helpviewer_keywords:
- formatted data [C++], reading from streams
- _ftscanf_s_l function
- _fscanf_s_l function
- ftscanf_s function
- fwscanf_s function
- _ftscanf_s function
- data [CRT], reading from streams
- _fwscanf_s_l function
- fscanf_s function
- fwscanf_s_l function
- ftscanf_s_l function
- streams [C++], reading formatted data from
- fscanf_s_l function
ms.assetid: b6e88194-714b-4322-be82-1cc0b343fe01
ms.openlocfilehash: ae5d0c953cb46850cf56a4ce4113e5831518ae5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124912"
---
# <a name="fscanf_s-_fscanf_s_l-fwscanf_s-_fwscanf_s_l"></a>fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l

从流中读取格式化数据。 这些版本的 [fscanf、_fscanf_l、fwscanf、_fwscanf_l_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md) 具有安全增强功能，如 [CRT 中的安全增强功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
int fscanf_s(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fscanf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwscanf_s(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwscanf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>parameters

*流*<br/>
指向 **文件** 结构的指针。

*format*<br/>
窗体控件字符串。

argument <br/>
可选参数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

每个函数都将返回成功转换并分配的字段数；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 如果发生错误，或者在第一次转换之前到达文件流的末尾，则返回值为 **EOF** （对于 **fscanf_s** 和 **fwscanf_s**）。

这些函数验证其参数。 如果 *stream* 是无效的文件指针，或者 *格式* 为 null 指针，则这些函数将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 **EOF** ，并将 **Errno** 设置为 **EINVAL**。

## <a name="remarks"></a>备注

**Fscanf_s** 函数将数据从 *流* 的当前位置读取到由 *参数* (的位置（如果有任何) ）。 每个 *参数* 都必须是指向类型的变量的指针，该类型与 *格式* 中的类型说明符对应。 *format* 控制输入字段的解释，其形式和函数与 **scanf_s** 的 *格式* 参数相同;有关 *格式* 的说明，请参阅 [格式规范字段： Scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  **fwscanf_s** 是 **fscanf_s** 的宽字符版本; **fwscanf_s** 的格式参数是宽字符字符串。 如果在 ANSI 模式下打开流，则这些函数行为相同。 **fscanf_s** 当前不支持 UNICODE 流的输入。

**_S** 后缀) 更安全的函数 (与其他版本之间的主要区别在于，更安全的函数要求每个 **c**、 **c**、 **s**、 **s** 和 **[** type 字段的大小以字符的形式传递给紧跟在变量后的参数。 有关详细信息，请参阅 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)。

> [!NOTE]
> 大小参数的类型为 **`unsigned`** ，而不是 **size_t**。

这些具有 **_l** 后缀的函数的版本相同，只不过它们使用传入的区域设置参数而不是当前线程区域设置。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftscanf_s**|**fscanf_s**|**fscanf_s**|**fwscanf_s**|
|**_ftscanf_s_l**|**_fscanf_s_l**|**_fscanf_s_l**|**_fwscanf_s_l**|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fscanf_s**， **_fscanf_s_l**|\<stdio.h>|
|**fwscanf_s**， **_fwscanf_s_l**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fscanf_s.c
// This program writes formatted
// data to a file. It then uses fscanf to
// read the various data back from the file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   long l;
   float fp;
   char s[81];
   char c;

   errno_t err = fopen_s( &stream, "fscanf.out", "w+" );
   if( err )
      printf_s( "The file fscanf.out was not opened\n" );
   else
   {
      fprintf_s( stream, "%s %ld %f%c", "a-string",
               65000, 3.14159, 'x' );
      // Set pointer to beginning of file:
      fseek( stream, 0L, SEEK_SET );

      // Read data back from file:
      fscanf_s( stream, "%s", s, _countof(s) );
      fscanf_s( stream, "%ld", &l );

      fscanf_s( stream, "%f", &fp );
      fscanf_s( stream, "%c", &c, 1 );

      // Output data read:
      printf( "%s\n", s );
      printf( "%ld\n", l );
      printf( "%f\n", fp );
      printf( "%c\n", c );

      fclose( stream );
   }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>

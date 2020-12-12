---
description: 了解详细信息： sscanf、_sscanf_l、swscanf、_swscanf_l
title: sscanf、_sscanf_l、swscanf、_swscanf_l
ms.date: 08/29/2019
api_name:
- swscanf
- sscanf
- _sscanf_l
- _swscanf_l
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
- _sscanf_l
- _stscanf
- swscanf
- _stscanf_l
- sscanf
- _swscanf_l
helpviewer_keywords:
- swscanf function
- _stscanf function
- sscanf function
- _stscanf_l function
- _sscanf_l function
- _swscanf_l function
- swscanf_l function
- strings [C++], reading data from
- stscanf function
- reading data, strings
- strings [C++], reading
- sscanf_l function
- stscanf_l function
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
ms.openlocfilehash: f5681e1f8e122c6f24151ae5e8d37186d8bd066e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171265"
---
# <a name="sscanf-_sscanf_l-swscanf-_swscanf_l"></a>sscanf、_sscanf_l、swscanf、_swscanf_l

从字符串中读取格式化数据。 这些函数的更安全版本已发布；请参阅 [sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。

## <a name="syntax"></a>语法

```C
int sscanf(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>parameters

*宽限*<br/>
存储的数据

*format*<br/>
窗体控件字符串。 有关更多信息，请参见 [格式规范](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

argument <br/>
可选自变量

*locale*<br/>
要使用的区域设置

## <a name="return-value"></a>返回值

每个函数都将返回成功转换并分配的字段数；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 如果发生错误，则返回值为 **EOF** ; 或者，如果在第一次转换之前到达字符串的末尾，则为。

如果 *缓冲区* 或 *格式* 为 **NULL** 指针，则将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回-1，并将 **errno** 设置为 **EINVAL**。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Sscanf** 函数将 *缓冲区* 中的数据读入每个 *参数* 给定的位置。 每个 *参数* 都必须是指向类型的变量的指针，该类型与 *格式* 的类型说明符对应。 *Format* 参数控制输入字段的解释，其形式和函数与 **scanf** 函数的 *format* 参数相同。 如果复制出现在重叠的字符串之间，则该行为不确定。

有关 scanf 类型字段字符的信息，请参阅 [Scanf 类型字段字符](../scanf-type-field-characters.md)。 有关 scanf 格式规范字段的信息，请参阅 [格式规范字段](../format-specification-fields-scanf-and-wscanf-functions.md)。

> [!IMPORTANT]
> 使用 **sscanf** 读取字符串时，请始终指定 **% s** 格式的宽度 (例如， **"% 32s"** 而不是 **"% s"**) ;否则，输入格式不正确可能会导致缓冲区溢出。

**swscanf** 是 **sscanf** 的宽字符版本; **swscanf** 的参数是宽字符字符串。 **sscanf** 不处理多字节十六进制字符。 **swscanf** 不处理 Unicode 全角十六进制或 "兼容区域" 字符。 否则， **swscanf** 和 **sscanf** 的行为方式相同。

这些具有 **_l** 后缀的函数的版本相同，只不过它们使用传入的区域设置参数而不是当前线程区域设置。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf**|**sscanf**|**sscanf**|**swscanf**|
|**_stscanf_l**|**_sscanf_l**|**_sscanf_l**|**_swscanf_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**sscanf**、 **_sscanf_l**|\<stdio.h>|
|**swscanf**、 **_swscanf_l**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_sscanf.c
// compile with: /W3
// This program uses sscanf to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string:
   sscanf( tokenstring, "%80s", s ); // C4996
   sscanf( tokenstring, "%c", &c );  // C4996
   sscanf( tokenstring, "%d", &i );  // C4996
   sscanf( tokenstring, "%f", &fp ); // C4996
   // Note: sscanf is deprecated; consider using sscanf_s instead

   // Output the data read
   printf( "String    = %s\n", s );
   printf( "Character = %c\n", c );
   printf( "Integer:  = %d\n", i );
   printf( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、 \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf、_snprintf、_snprintf_l、_snwprintf、_snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>

---
description: 了解详细信息： _mbsnbset、_mbsnbset_l
title: _mbsnbset、_mbsnbset_l
ms.date: 4/2/2020
api_name:
- _mbsnbset
- _mbsnbset_l
- _o__mbsnbset
- _o__mbsnbset_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbset
- mbsnbset_l
- _mbsnbset
- _mbsnbset_l
helpviewer_keywords:
- tcsnset function
- _tcsnset_l function
- _mbsnbset function
- _tcsnset function
- _mbsnbset_l function
- mbsnbset_l function
- tcsnset_l function
- mbsnbset function
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
ms.openlocfilehash: a99e92cec8b15c9534cec981652ce7c78fa31923
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240255"
---
# <a name="_mbsnbset-_mbsnbset_l"></a>_mbsnbset、_mbsnbset_l

将多字节字符字符串的前 **n** 个字节设置为指定字符。 提供这些函数的更多安全版本；请参阅 [_mbsnbset_s、_mbsnbset_s_l](mbsnbset-s-mbsnbset-s-l.md)。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
unsigned char *_mbsnbset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnbset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>parameters

*str*<br/>
要修改的字符串。

*c*<br/>
单字节或多字节字符设置。

*计数*<br/>
要设置的字节数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbsnbset** 返回指向已更改的字符串的指针。

## <a name="remarks"></a>备注

**_Mbsnbset** 和 **_mbsnbset_l** 函数最多将 *str* 的第一个 *计数* 字节设置为 *c*。 如果 *count* 大于 *str* 的长度，则使用 *str* 的长度而不是 *count*。 如果 *c* 是多字节字符，且不能完全设置到 *count* 指定的最后一个字节中，则用空白字符填充最后一个字节。 **_mbsnbset** 和 **_mbsnbset_l** 不会在 *str* 末尾放置终止 null。

**_mbsnbset** 和 **_mbsnbset_l** 类似于 **_mbsnset**，只不过它会设置 *计数* 字节而不是 *count* 个字符的 *c*。

如果 *str* 为 **NULL** 或 *计数* 为零，则此函数将生成无效的参数异常，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 **errno** 设置为 **EINVAL** ，并且该函数将返回 **NULL**。 此外，如果 *c* 不是有效的多字节字符，则将 **Errno** 设置为 **EINVAL** ，并改为使用空格。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 此函数的 **_mbsnbset** 版本对与区域设置相关的行为使用当前区域设置; **_mbsnbset_l** 版本相同，只不过它使用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**安全说明** 此 API 会引发由缓冲区溢出问题带来的潜在威胁。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbsnbset**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_mbsnbset.c
// compile with: /W3
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset( string, '*', 4 ); // C4996
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s
   printf( "After:  %s\n", string );
}
```

### <a name="output"></a>输出

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>

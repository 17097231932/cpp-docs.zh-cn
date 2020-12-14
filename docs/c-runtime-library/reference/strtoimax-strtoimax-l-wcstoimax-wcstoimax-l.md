---
description: 了解详细信息： strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l
title: strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l
ms.date: 11/04/2016
api_name:
- wcstoimax
- _wcstoimax_l
- _strtoimax_l
- strtoimax
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcstoimax
- _tcstoimax
- strtoimax
- _wcstoimax_l
- _strtoimax_l
- _tcstoimax_l
helpviewer_keywords:
- strtoimax funciton
- conversion functions
- _strtoimax_l function
- _wcstoimax_l function
- wcstoimax function
ms.assetid: 4530d3dc-aaac-4a76-b7cf-29ae3c98d0ae
ms.openlocfilehash: 9de1e03ef54b65d321e38f86a6f39bc014df7bf4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288745"
---
# <a name="strtoimax-_strtoimax_l-wcstoimax-_wcstoimax_l"></a>strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l

将字符串转换为受支持的最大带符号整数类型的整数值。

## <a name="syntax"></a>语法

```C
intmax_t strtoimax(
   const char *strSource,
   char **endptr,
   int base
);
intmax_t wcstoimax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
intmax_t _strtoimax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
intmax_t _wcstoimax_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>parameters

*strSource*<br/>
要转换的 null 终止的字符串。

*endptr*<br/>
指向停止扫描的字符的指针。

*base*<br/>
要使用的基数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strtoimax** 返回在字符串 *strSource* 中表示的值，除非表示形式会导致溢出，在这种情况下，它将返回 **INTMAX_MAX** 或 **INTMAX_MIN**， **errno** 设置为 **ERANGE**。 如果无法执行任何转换，则函数返回 0。 **wcstoimax** 将类似值返回到 **strtoimax**。

**INTMAX_MAX** 和 **INTMAX_MIN** 是在 stdint.h> 中定义的。

如果 *strSource* 为 **NULL** 或 *基数* 不为零，并且小于2或大于36，则将 **errno** 设置为 **EINVAL**。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Strtoimax** 函数将 *strSource* 转换为 **intmax_t**。 **Strtoimax** 的宽字符版本为 **wcstoimax**;其 *strSource* 参数是宽字符字符串。 否则，这些函数具有相同行为。 这两个函数在其无法识别为数字一部分的第一个字符处停止读取字符串 *strSource* 。 这可能是终止 null 字符，也可能是大于或等于 *基准* 的第一个数字字符。

区域设置的 **LC_NUMERIC** 类别设置确定 *strSource* 中的基数字符的识别;有关详细信息，请参阅 [setlocale、_wsetlocale](setlocale-wsetlocale.md)。 没有 **_l** 后缀的函数使用当前区域设置; **_strtoimax_l** 和 **_wcstoimax_l** 与没有 **_l** 后缀的相应函数相同，只不过它们改用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果 *endptr* 不为 **NULL**，则指向停止扫描的字符的指针将存储在 *endptr* 指向的位置。 如果无法执行任何转换 () 找不到任何有效的数字或指定了无效的基，则 *strSource* 的值将存储在 *endptr* 指向的位置。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoimax**|**strtoimax**|**strtoimax**|**wcstoimax**|
|**_tcstoimax_l**|**strtoimax_l**|**_strtoimax_l**|**_wcstoimax_l**|

**strtoimax** 要求 *strSource* 指向以下格式的字符串：

> [*空格*][{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*数字*  &#124; *字母*]

*空格* 可能包含被忽略的空格和制表符;*位数* 为一个或多个十进制数字;*字母* 是从 "a" 到 "z" (或 "a" 到 "z" ) 的一个或多个字母。 不符合此形式的第一个字符停止扫描。 如果 *base* 介于2和36之间，则将其用作数字的基数。 如果 *base* 为0，则使用 *strSource* 指向的字符串的初始字符来确定基。 如果第一个字符为“0”，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 *base* 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果 *base* 为0且扫描的第一个字符为 "0"，则假定八进制整数，而 "8" 或 "9" 字符会停止扫描。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtoimax**、 **_strtoimax_l**、 **wcstoimax**、 **_wcstoimax_l**|\<inttypes.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l](strtoumax-strtoumax-l-wcstoumax-wcstoumax-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>

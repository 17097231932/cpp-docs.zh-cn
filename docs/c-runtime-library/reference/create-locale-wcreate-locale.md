---
description: 了解详细信息： _create_locale、_wcreate_locale
title: _create_locale、_wcreate_locale
ms.date: 4/2/2020
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
- _o__create_locale
- _o__wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: feb2fee7befbaf3f798dc36466674eaa4aec55fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341512"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale、_wcreate_locale

创建区域设置对象。

## <a name="syntax"></a>语法

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>parameters

*category*<br/>
类别。

*locale*<br/>
区域设置说明符。

## <a name="return-value"></a>返回值

如果提供了有效的 *区域* 设置和 *类别* ，则会将指定的区域设置作为 **_locale_t** 对象返回。 不更改程序的当前区域设置。

## <a name="remarks"></a>备注

**_Create_locale** 函数允许你创建一个对象，该对象表示特定于区域特定的设置，这些设置可用于多个 CRT 函数的区域设置特定版本 (具有 **_l** 后缀) 的函数。 此行为类似于 **setlocale**，只是将设置保存在返回的 **_locale_t** 结构中，而不是将指定的区域设置应用到当前环境。 当不再需要 **_locale_t** 结构时，应使用 [_free_locale](free-locale.md) 将其释放。

**_wcreate_locale** 是 **_create_locale** 的宽字符版本;**_wcreate_locale** 的 *区域设置* 参数是宽字符字符串。 否则 **_wcreate_locale** 和 **_create_locale** 的行为相同。

*Category* 参数指定受影响的特定于区域设置的行为的部分。 用于 *类别* 的标志和它们影响的程序的部分如下表中所示：

| *类别* 标志 | 影响 |
|-----------------|---------|
| **LC_ALL** |以下列出了所有类别。 |
| LC_COLLATE |**Strcoll**、 **_stricoll**、 **wcscoll**、 **_wcsicoll**、 **strxfrm**、 **_strncoll**、 **_strnicoll**、 **_wcsncoll**、 **_wcsnicoll** 和 **wcsxfrm** 函数。 |
| LC_CTYPE | 除 **isdigit**、 **isxdigit**、 **mbstowcs** 和 **mbtowc** 之外的字符处理函数 (，它们不会影响) 。 |
| **LC_MONETARY** | **Localeconv** 函数返回的货币格式信息。 |
| LC_NUMERIC | 格式化输出例程的小数点字符 (如 **printf**) 、数据转换例程和 **localeconv** 返回的非货币格式设置信息。 除小数点字符外， **LC_NUMERIC** 设置 [localeconv](localeconv.md)返回的千位分隔符和分组控制字符串。 |
| LC_TIME | **Strftime** 和 **wcsftime** 函数。 |

此函数验证 *类别* 和 *区域设置* 参数。 如果 category 参数不是上表中给出的值之一，或者如果 *locale* 为 **null**，则该函数返回 **null**。

*Locale* 参数是指向指定区域设置的字符串的指针。 有关 *区域设置* 参数格式的信息，请参阅 [区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。

*区域设置* 参数可以采用区域设置名称、语言字符串、语言字符串和国家/地区代码、代码页或语言字符串、国家/地区代码和代码页。 可用区域设置名称、语言、国家/地区代码和代码页集包含 Windows NLS API 支持的所有内容。 [区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中描述了 **_create_locale** 支持的区域设置名称集。 [语言字符串](../../c-runtime-library/language-strings.md)和 [国家/地区字符串](../../c-runtime-library/country-region-strings.md)中列出了 **_create_locale** 支持的语言和国家/地区字符串集。

有关区域设置的详细信息，请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md)。

已不推荐使用此函数之前的名称（ **__create_locale** 有两个前导下划线)  (。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>请参阅

[区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[语言字符串](../../c-runtime-library/language-strings.md)<br/>
[国家/地区字符串](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>

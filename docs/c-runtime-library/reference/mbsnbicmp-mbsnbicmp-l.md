---
description: 了解详细信息： _mbsnbicmp、_mbsnbicmp_l
title: _mbsnbicmp、_mbsnbicmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
- _o__mbsnbicmp
- _o__mbsnbicmp_l
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
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 9cc833061ceca899af78da4c50610ed101dcd2d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240268"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp、_mbsnbicmp_l

比较两个多字节字符字符串的 **n** 个字节，忽略大小写。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>parameters

*string1*、 *string2*<br/>
要比较的 null 终止的字符串。

*计数*<br/>
要比较的字节数。

## <a name="return-value"></a>返回值

返回值指示子字符串之间的关系。

|返回值|描述|
|------------------|-----------------|
|< 0|*string1* 子串小于 *string2* 子串。|
|0|*string1* 子字符串与 *string2* 子字符串相同。|
|> 0|大于 *string2* 子字符串的 *string1* 子串。|

出现错误时， **_mbsnbicmp** 返回在 Mbstring.h 和中定义的 **_NLSCMPERROR**。

## <a name="remarks"></a>备注

**_Mbsnbicmp** 函数最多可执行 *string1* 和 *string2* 的第一个 *计数* 字节的序号比较。 通过将每个字符转换为小写来执行比较; [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) 是 **_mbsnbicmp** 区分大小写的版本。 如果在比较 *计数* 字符之前的任一字符串中达到终止 null 字符，则比较结束。 如果在比较 *计数* 字符之前的任一字符串中达到终止 null 字符时字符串相等，则较短的字符串较小。

**_mbsnbicmp** 与 [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)类似，不同之处在于，它将字符串向上比较（而不是按 *字符）。*

两个包含位于 ASCII 表中“Z”和“a”之间的字符（“[”、“\\”、“]”、“^”、“_”和“\`”）的字符串将有不同的比较结果，具体取决于它们的大小写形式。 例如，两个字符串 "ABCDE...Z" 和 "ABCD ^" 比较小写 ( "abcde...z" > "abcd ^" ) ，而另一种方法 ( "ABCDE...Z" < "ABCD ^" ) （如果它是大写字母）。

**_mbsnbicmp** 根据当前使用的 [多字节代码页](../../c-runtime-library/code-pages.md) 识别多字节字符序列。 它不受当前区域设置影响。

如果 *string1* 或 *string2* 是 null 指针， **_mbsnbicmp** 将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则函数返回 **_NLSCMPERROR** ，并将 **Errno** 设置为 **EINVAL**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md) 的示例。

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>

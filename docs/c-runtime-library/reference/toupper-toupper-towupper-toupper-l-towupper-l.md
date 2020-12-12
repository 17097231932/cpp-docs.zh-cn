---
description: 了解详细信息： toupper、_toupper、towupper、_toupper_l、_towupper_l
title: toupper、_toupper、towupper、_toupper_l、_towupper_l
ms.date: 4/2/2020
api_name:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
- _o__toupper
- _o__toupper_l
- _o__towupper_l
- _o_toupper
- _o_towupper
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towupper
- _toupper
- _totupper
- toupper
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
ms.openlocfilehash: cb2a121d1fa96c0149a329520f5c71c1cc4f4d9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318307"
---
# <a name="toupper-_toupper-towupper-_toupper_l-_towupper_l"></a>toupper、_toupper、towupper、_toupper_l、_towupper_l

将字符转换为大写。

## <a name="syntax"></a>语法

```C
int toupper(
   int c
);
int _toupper(
   int c
);
int towupper(
   wint_t c
);
int _toupper_l(
   int c ,
   _locale_t locale
);
int _towupper_l(
   wint_t c ,
   _locale_t locale
);
```

### <a name="parameters"></a>parameters

*c*<br/>
要转换的字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

其中每个例程都转换 *c* 的副本（如果可能），并返回结果。

如果 *c* 是一个宽字符，其中 **iswlower** 为非零，并且有一个对应的宽字符，其中 [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) 为非零值，则 **towupper** 将返回相应的宽字符;否则， **towupper** 将返回 *c* 。

没有保留任何返回值以指示错误。

为了使 **toupper** 能够提供预期的结果， [__isascii](isascii-isascii-iswascii.md) 和 [islower](islower-iswlower-islower-l-iswlower-l.md) 都必须返回非零值。

## <a name="remarks"></a>备注

如果可行且恰当，则其中的各个例程将指定小写字母转换为大写字母。 **Towupper** 的大小写转换是特定于区域设置的。 只改变与当前区域设置相关的字符的大小写。 没有 **_l** 后缀的函数使用当前设置的区域设置。 这些具有 **_l** 后缀的函数的版本将区域设置用作参数，并使用该区域设置，而不是使用当前设置的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

为了使 **toupper** 能够提供预期的结果， [__isascii](isascii-isascii-iswascii.md) 和 [isupper](isupper-isupper-l-iswupper-iswupper-l.md) 都必须返回非零值。

[数据转换例程](../../c-runtime-library/data-conversion.md)

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** 和 **_towupper_l** 没有区域设置依赖关系，因此不应直接调用。 它们由 **_totupper_l** 供内部使用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper**|\<ctype.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [to 函数](../../c-runtime-library/to-functions.md)中的示例。

## <a name="see-also"></a>请参阅

[为，isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[to 函数](../../c-runtime-library/to-functions.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>

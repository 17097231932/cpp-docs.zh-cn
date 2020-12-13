---
description: 了解详细信息： isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l
title: isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l
ms.date: 4/2/2020
api_name:
- _iswxdigit_l
- iswxdigit
- isxdigit
- _isxdigit_l
- _o_iswxdigit
- _o_isxdigit
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
- iswxdigit
- isxdigit
- _istxdigit
helpviewer_keywords:
- isxdigit function
- istxdigit function
- _iswxdigit_l function
- _istxdigit function
- _isxdigit_l function
- iswxdigit_l function
- isxdigit_l function
- hexadecimal characters
- iswxdigit function
ms.assetid: c8bc5146-0b58-4e3f-bee3-f2318dd0f829
ms.openlocfilehash: 87e9e8d07f9a0da38bc6590f27fcb770fc2b789b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344843"
---
# <a name="isxdigit-iswxdigit-_isxdigit_l-_iswxdigit_l"></a>isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l

确定整数是否表示十六进制数字字符。

## <a name="syntax"></a>语法

```C
int isxdigit(
   int c
);
int iswxdigit(
   wint_t c
);
int _isxdigit_l(
   int c,
   _locale_t locale
);
int _iswxdigit_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>parameters

*c*<br/>
要测试的整数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果 *c* 是十六进制数字的特定表示形式，则每个例程将返回非零值。 如果 *c* 是 (a-f、a-f 或 0-9) 的十六进制数字， **isxdigit** 将返回一个非零值。 如果 *c* 是对应于十六进制数字字符的宽字符，则 **iswxdigit** 将返回一个非零值。 如果 *c* 不满足测试条件，则这些例程都将返回0。

对于 "C" 区域设置， **iswxdigit** 函数不支持 Unicode 全角十六进制字符。

这些具有 **_l** 后缀的函数的版本使用传入的区域设置，而不是其与区域设置相关的行为的当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果 *c* 不是 EOF 或介于0到0xff （含0和0xff），则 **isxdigit** 和 **_isxdigit_l** 的行为是不确定的。 当使用调试 CRT 库并且 *c* 不是这些值之一时，函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istxdigit**|**isxdigit**|**isxdigit**|**iswxdigit**|

## <a name="remarks"></a>备注

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**isxdigit**|\<ctype.h>|
|**iswxdigit**|\<ctype.h> 或 \<wchar.h>|
|**_isxdigit_l**|\<ctype.h>|
|**_iswxdigit_l**|\<ctype.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[为，isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>

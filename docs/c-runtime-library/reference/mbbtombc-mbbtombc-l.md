---
description: 了解详细信息： _mbbtombc、_mbbtombc_l
title: _mbbtombc、_mbbtombc_l
ms.date: 4/2/2020
api_name:
- _mbbtombc_l
- _mbbtombc
- _o__mbbtombc
- _o__mbbtombc_l
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
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
ms.openlocfilehash: 20aa3c9abdc9d4dad1f6da50abdb9977f2b22694
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299641"
---
# <a name="_mbbtombc-_mbbtombc_l"></a>_mbbtombc、_mbbtombc_l

将单字节的多字节字符转换为相应的双字节的多字节字符。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
unsigned int _mbbtombc(
   unsigned int c
);
unsigned int _mbbtombc_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>parameters

*c*<br/>
要转换的单字节字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果 **_mbbtombc** 成功转换 *c*，它将返回一个多字节字符;否则，它将返回 *c*。

## <a name="remarks"></a>备注

**_Mbbtombc** 函数将给定的单字节的多字节字符转换为相应的双字节的多字节字符。 字符必须在要转换的0x7E 或0xA1 的范围内。

输出值受区域设置的 **LC_CTYPE** 类别设置的设置的影响;有关详细信息，请参阅 [setlocale、_wsetlocale](setlocale-wsetlocale.md) 。 此函数的版本相同，不同之处在于 **_mbbtombc** 会将当前区域设置用于与区域设置相关的行为，而 **_mbbtombc_l** 使用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在早期版本中， **_mbbtombc** 命名为 **hantozen**。 对于新代码，请使用 **_mbbtombc**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb、_mbctombb_l](mbctombb-mbctombb-l.md)<br/>

---
description: 了解详细信息： btowc
title: btowc
ms.date: 4/2/2020
api_name:
- btowc
- _o_btowc
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: bbd6121499e03c356e80e49cbcbe75929ca96c2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171720"
---
# <a name="btowc"></a>btowc

确定整数是否表示初始位移状态中的有效单字节字符。

## <a name="syntax"></a>语法

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>parameters

*character*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

如果整数表示初始位移状态中的有效单字节字符，则将返回字符的宽字符表示形式。 如果整数是 EOF 或不是初始位移状态中的有效单字节字符，则返回 WEOF。 此函数的输出受当前 **LC_TYPE** 区域设置的影响。

## <a name="remarks"></a>备注

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**btowc**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>

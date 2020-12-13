---
description: 了解详细信息： _get_printf_count_output
title: _get_printf_count_output
ms.date: 11/04/2016
api_name:
- _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: fe5ee728b7bc8400cd93ec4e93131496d59334c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339012"
---
# <a name="_get_printf_count_output"></a>_get_printf_count_output

指示 [printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)系列函数是否支持 **% n** 格式。

## <a name="syntax"></a>语法

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>返回值

如果支持 **% n** ，则为非零值; 如果不支持 **% n** ，则为0。

## <a name="remarks"></a>备注

如果不支持 **% n** (默认) ，则在任何 **printf** 函数的格式字符串中遇到 **% n** 时，将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果启用了 **% n** 支持 (请参阅 [_set_printf_count_output](set-printf-count-output.md)) ， **% n** 将按 [格式规范语法： printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)中所述的方式运行。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_set_printf_count_output](set-printf-count-output.md) 示例。

## <a name="see-also"></a>请参阅

[_set_printf_count_output](set-printf-count-output.md)<br/>

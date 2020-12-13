---
description: 了解详细信息： _get_wpgmptr
title: _get_wpgmptr
ms.date: 4/2/2020
api_name:
- _get_wpgmptr
- _o__get_wpgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: fdc2f17a2c4d43a762f9fbab6629e2524742f0ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338925"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

获取 **_wpgmptr** 全局变量的当前值。

## <a name="syntax"></a>语法

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>parameters

*pValue*<br/>
一个指针，指向要使用 **_wpgmptr** 变量的当前值填充的字符串。

## <a name="return-value"></a>返回值

如果成功，则返回零；如果失败，则返回错误代码。 如果 *pValue* 为 **NULL**，则将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数会将 **errno** 设置为 **EINVAL** 并返回 **EINVAL**。

## <a name="remarks"></a>备注

仅当程序具有丰富的入口点（如 **wmain ( # B1** 或 **WWinMain ( # B3**）时，才调用 **_get_wpgmptr** 。 **_Wpgmptr** 全局变量包含与进程关联的可执行文件的完整路径（以宽字符字符串形式）。 有关详细信息，请参阅 [_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_get_pgmptr](get-pgmptr.md)<br/>

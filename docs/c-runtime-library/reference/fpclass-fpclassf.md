---
description: 了解详细信息： _fpclass、_fpclassf
title: _fpclass、_fpclassf
ms.date: 4/2/2020
api_name:
- _fpclass
- _fpclassf
- _o__fpclass
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: bd7a2aa02a3431ff41c4d9695efca1f959ece24f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164908"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass、_fpclassf

返回一个值，该值指示参数的浮点分类。

## <a name="syntax"></a>语法

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>parameters

*x*<br/>
要测试的浮点值。

## <a name="return-value"></a>返回值

**_Fpclass** 和 **_fpclassf** 函数返回一个整数值，该值指示参数 *x* 的浮点分类。 分类可能具有在中定义的下列值之一 \<float.h> 。

|值|描述|
|-----------|-----------------|
|**_FPCLASS_SNAN**|信令 NaN|
|**_FPCLASS_QNAN**|静默 NaN|
|**_FPCLASS_NINF**|负无穷 (-INF) |
|**_FPCLASS_NN**|标准化的非零负值|
|**_FPCLASS_ND**|非标准化的负值|
|**_FPCLASS_NZ**|负零 (-0) |
|**_FPCLASS_PZ**|正零 (+0)|
|**_FPCLASS_PD**|非标准化的正值|
|**_FPCLASS_PN**|标准化的非零正值|
|**_FPCLASS_PINF**|正无穷大 (+INF)|

## <a name="remarks"></a>备注

**_Fpclass** 和 **_Fpclassf** 函数是 Microsoft 特定的。 它们类似于 [fpclassify](fpclassify.md)，但返回有关参数的更多详情信息。 仅当为 x64 平台编译时， **_fpclassf** 函数才可用。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fpclass**， **_fpclassf**|\<float.h>|

有关兼容性和符合性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>

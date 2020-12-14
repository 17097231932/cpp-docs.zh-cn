---
description: 了解详细信息：标准、normf、norml
title: norm、normf、norml1
ms.date: 04/05/2018
api_name:
- norm
- normf
- norml
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- norm
- normf
- norml
- complex/norm
- complex/normf
- complex/norml
helpviewer_keywords:
- norm function
- normf function
- norml function
ms.assetid: 9786ecfe-0019-4553-b378-0af6c691e15c
ms.openlocfilehash: 175cff5f9c0e31a56a86a96c3262e2c3c546fe4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256297"
---
# <a name="norm-normf-norml"></a>norm、normf、norml1

检索复数的平方量值。

## <a name="syntax"></a>语法

```C
double norm( _Dcomplex z );
float normf( _Fcomplex z );
long double norml( _Lcomplex z );
```

```cpp
float norm( _Fcomplex z );  // C++ only
long double norm( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>parameters

*z*<br/>
一个复数。

## <a name="return-value"></a>返回值

*Z* 的平方量。

## <a name="remarks"></a>备注

由于 c + + 允许重载，因此你可以调用采用 **_Fcomplex** 或 **_Lcomplex** 值的 **标准** 重载，以及返回值 **`float`** 或 **`long double`** 值。 在 C 程序中，" **标准** " 始终采用 **_Dcomplex** 值并返回 **`double`** 值。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**标准**、 **normf**、 **norml**|\<complex.h>|\<complex.h>|

**_Fcomplex**、 **_Dcomplex** 和 **_Lcomplex** 类型是特定于 Microsoft 的等效项，它们分别是未实现的本机 C99 类型 **float _Complex**、 **double _Complex** 和 **long double _Complex**。  有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字母函数引用](crt-alphabetical-function-reference.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>

---
description: 了解详细信息： ccos、ccosf、ccosl
title: ccos、ccosf、ccosl
ms.date: 11/04/2016
api_name:
- ccos
- ccosf
- ccosl
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
- ccos
- ccosf
- ccosl
- complex/ccos
- complex/ccosf
- complex/ccosl
helpviewer_keywords:
- ccos function
- ccosf function
- ccosl function
ms.assetid: 4ab936ac-ff85-49ac-9418-2b69cf5d4696
ms.openlocfilehash: 54036a2ddd3d61bba1d11a4841eaab1bd546c0ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275134"
---
# <a name="ccos-ccosf-ccosl"></a>ccos、ccosf、ccosl

检索复数的余弦值。

## <a name="syntax"></a>语法

```C
_Dcomplex ccos(
   _Dcomplex z
);
_Fcomplex ccos(
   _Fcomplex z
);  // C++ only
_Lcomplex ccos(
   _Lcomplex z
);  // C++ only
_Fcomplex ccosf(
   _Fcomplex z
);
_Lcomplex ccosl(
   _Lcomplex z
);
```

### <a name="parameters"></a>parameters

*z*<br/>
表示角度的复数（以弧度为单位）。

## <a name="return-value"></a>返回值

*Z* 的余弦值（以弧度表示）。

## <a name="remarks"></a>备注

由于 c + + 允许重载，因此可以调用 **ccos** 的重载，该重载采用并返回 **_Fcomplex** 和 **_Lcomplex** 值。 在 C 程序中， **ccos** 始终采用并返回 **_Dcomplex** 值。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**ccos**、               **ccosf**、 **ccosl**|\<complex.h>|\<ccomplex>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字母函数引用](crt-alphabetical-function-reference.md)<br/>
[catanh、catanhf、catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh、ctanhf、ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan、catanf、catanl](catan-catanf-catanl.md)<br/>
[csinh、csinhf、csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh、casinhf、casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh、ccoshf、ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh、cacoshf、cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos、cacosf、cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan、ctanf、ctanl](ctan-ctanf-ctanl.md)<br/>
[csin、csinf、csinl](csin-csinf-csinl.md)<br/>
[casin、casinf、casinl](casin-casinf-casinl.md)<br/>
[csqrt、csqrtf、csqrtl](csqrt-csqrtf-csqrtl.md)<br/>

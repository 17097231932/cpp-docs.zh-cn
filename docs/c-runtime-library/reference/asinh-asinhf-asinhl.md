---
title: asinh、asinhf、asinhl
description: 适用于 asinh、asinhf 和 asinhl 的 API 参考;计算浮点值的反双曲正弦值。
ms.date: 08/31/2020
api_name:
- asinh
- asinhf
- asinhl
- _o_asinh
- _o_asinhf
- _o_asinhl
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
- asinhf
- asinhl
- asinh
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
ms.openlocfilehash: 332e6bfc95bd297d703d879cdd468b450cfdc763
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556783"
---
# <a name="asinh-asinhf-asinhl"></a>asinh、asinhf、asinhl

计算反双曲正弦。

## <a name="syntax"></a>语法

```C
double asinh( double x );
float asinhf( float x );
long double asinhl( long double x );
#define asinh(X) // Requires C11 or higher

float asinh( float x );  // C++ only
long double asinh( long double x );  // C++ only
```

### <a name="parameters"></a>参数

*x*<br/>
浮点值。

## <a name="return-value"></a>返回值

**Asinh**函数返回*x*的反双曲正弦 (圆弧双曲正弦) 值。 此函数在浮点域上有效。 如果 *x* 为静默 NaN、不定或无穷大，则返回相同的值。

|输入|SEH 异常|**_matherr** 异常|
|-----------|-------------------|--------------------------|
|± QNAN、IND、INF|无|无|

## <a name="remarks"></a>备注

使用 c + + 时，可以调用采用并返回或值的 **asinh** 的重载 **`float`** **`long double`** 。 在 C 程序中，除非使用 \<tgmath.h> 宏来调用此函数，否则 **asinh** 始终采用并返回 **`double`** 。

如果使用 \<tgmath.h> `asinh()` 宏，则参数的类型将决定选择哪个版本的函数。 有关详细信息，请参阅 [类型-泛型数学](../../c-runtime-library/tgmath.md) 。


默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的 C 标头|必需的 C++ 标头|
|--------------|--------------|------------------|
|**asinh**、 **asinhf**、 **asinhl**|\<math.h>|\<cmath> 或 \<math.h>|
|**asinh ( # B1 ** 宏 | \<tgmath.h> ||

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_asinh.c
// Compile by using: cl /W4 crt_asinh.c
// This program displays the hyperbolic sine of pi / 4
// and the arc hyperbolic sine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = sinh( pi / 4 );
   y = asinh( x );
   printf( "sinh( %f ) = %f\n", pi/4, x );
   printf( "asinh( %f ) = %f\n", x, y );
}
```

```Output
sinh( 0.785398 ) = 0.868671
asinh( 0.868671 ) = 0.785398
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh、coshf、coshl](cosh-coshf-coshl.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>

---
title: rint, rintf, rintl
description: 适用于 rint、rintf 和 rintl 的 API 参考;这会将浮点值舍入到最接近的整数（采用浮点格式）。
ms.date: 9/1/2020
api_name:
- rintf
- rintl
- rint
- _o_rint
- _o_rintf
- _o_rintl
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
- rintf
- rintl
- rint
helpviewer_keywords:
- rintf function
- rint function
- rintl function
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
ms.openlocfilehash: 1ed1fa279694d3df75db5963e5a571d58299e415
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555340"
---
# <a name="rint-rintf-rintl"></a>rint, rintf, rintl

将浮点值舍入到最接近的整数（采用浮点格式）。

## <a name="syntax"></a>语法

```C
double rint( double x );
float rintf( float x );
long double rintl( long double x );
#define rint(X) // Requires C11 or higher

float rint( float x );  // C++ only
long double rint( long double x );  // C++ only
```

### <a name="parameters"></a>参数

*x-blade*\
要舍入的浮点值。

## <a name="return-value"></a>返回值

**Rint**函数将返回表示最接近*x*的整数的浮点值。 根据浮点舍入模式的当前设置对中间值进行舍入，这与 **nearbyint** 函数相同。 与 **nearbyint** 函数不同，如果结果不同于参数中的值， **rint** 函数可能会引发 **FE_INEXACT** 浮点异常。 无错误返回。

|输入|SEH 异常|**_matherr** 异常|
|-----------|-------------------|--------------------------|
|±∞、QNAN、IND|无|无|
|非规格化数|EXCEPTION_FLT_UNDERFLOW|无|

## <a name="remarks"></a>备注

由于 c + + 允许重载，因此你可以调用 **rint** 的重载，该重载采用和返回 **`float`** 和 **`long double`** 值。 在 C 程序中，除非使用 \<tgmath.h> 宏调用此函数，否则， **rint** 始终采用并返回 **`double`** 。

如果使用 \<tgmath.h> `rint()` 宏，则参数的类型将决定选择哪个版本的函数。 有关详细信息，请参阅 [类型-泛型数学](../../c-runtime-library/tgmath.md) 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**rint**、 **rintf**、 **rintl**|\<math.h>|\<cmath>|
|**rint** 宏 | \<tgmath.h> ||

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_rint.c
// Build with: cl /W3 /Tc crt_rint.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 2.5 and -2.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 2.5;

   printf("rint(%f) is %.0f\n", x, rint (x));
   printf("rint(%f) is %.0f\n", -x, rint (-x));
   printf("rintf(%f) is %.0f\n", y, rintf(y));
   printf("rintf(%f) is %.0f\n", -y, rintf(-y));
   printf("rintl(%Lf) is %.0Lf\n", z, rintl(z));
   printf("rintl(%Lf) is %.0Lf\n", -z, rintl(-z));
}
```

```Output
rint(2.499999) is 2
rint(-2.499999) is -2
rintf(2.800000) is 3
rintf(-2.800000) is -3
rintl(2.500000) is 3
rintl(-2.500000) is -3
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint、lrintf、lrintl、llrint、llrintf、llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[lround、lroundf、lroundl、llround、llroundf、llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)<br/>
[nearbyint、nearbyintf、nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint](rint-rintf-rintl.md)<br/>

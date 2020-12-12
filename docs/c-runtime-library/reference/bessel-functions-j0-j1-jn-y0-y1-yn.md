---
description: 了解有关以下方面的详细信息：贝赛耳函数： _j0、_j1、_jn、_y0、_y1、_yn
title: 贝塞尔函数：_j0、_j1、_jn、_y0、_y1、_yn
ms.date: 4/2/2020
api_name:
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
- _o__j0
- _o__j1
- _o__jn
- _o__y0
- _o__y1
- _o__yn
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
- c.bessel
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
helpviewer_keywords:
- Bessel functions
- _j0 function
- _j1 function
- _jn function
- _y0 function
- _y1 function
- _yn function
ms.assetid: a21a8bf1-df9d-4ba0-a8c2-e7ef71921d96
ms.openlocfilehash: 8ada869b615e26d004e10ccc3355e83c9772888f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171863"
---
# <a name="bessel-functions-_j0-_j1-_jn-_y0-_y1-_yn"></a>贝塞尔函数：_j0、_j1、_jn、_y0、_y1、_yn

计算第一种或第二种贝塞尔函数，顺序为 0、1 或 n。 贝赛耳函数通常用于电磁波理论的数学学科中。

## <a name="syntax"></a>语法

```C
double _j0(
   double x
);
double _j1(
   double x
);
double _jn(
   int n,
   double x
);
double _y0(
   double x
);
double _y1(
   double x
);
double _yn(
   int n,
   double x
);
```

### <a name="parameters"></a>parameters

*x*<br/>
浮点值。

*n*<br/>
Bessel 函数的整数顺序。

## <a name="return-value"></a>返回值

其中每个例程都返回 *x* 的贝赛耳函数。 如果 *x* 在 **_y0**、 **_y1** 或 **_yn** 函数中为负，则例程会将 **errno** 设置为 **EDOM**，将 **_DOMAIN** 错误消息输出到 **stderr**，并返回 **_HUGE_VAL**。 您可以使用 **_matherr** 修改错误处理。

## <a name="remarks"></a>备注

**_J0**、 **_j1** 和 **_jn** 例程分别返回第一种类型的贝赛耳函数： orders 0、1和 n。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|**无效**|**_DOMAIN**|

**_Y0**、 **_y1** 和 **_yn** 例程将返回第二种类型的贝赛耳函数：分别为 "orders 0"、"1" 和 "n"。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|**无效**|**_DOMAIN**|
|±0|**ZERODIVIDE**|**_SING**|
|&#124;x&#124; < 0。0|**无效**|**_DOMAIN**|

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_j0**、 **_j1**、 **_jn**、 **_y0**、 **_y1**、 **_yn**|\<cmath> (c + +) 、 \<math.h> (c、c + +) |

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_bessel1.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.387;
   int n = 3, c;

   printf( "Bessel functions for x = %f:\n", x );
   printf( "   Kind   Order  Function     Result\n\n" );
   printf( "   First  0      _j0( x )     %f\n", _j0( x ) );
   printf( "   First  1      _j1( x )     %f\n", _j1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   First  %d      _jn( %d, x )  %f\n", c, c, _jn( c, x ) );
   printf( "   Second 0      _y0( x )     %f\n", _y0( x ) );
   printf( "   Second 1      _y1( x )     %f\n", _y1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   Second %d      _yn( %d, x )  %f\n", c, c, _yn( c, x ) );
}
```

```Output
Bessel functions for x = 2.387000:
   Kind   Order  Function     Result

   First  0      _j0( x )     0.009288
   First  1      _j1( x )     0.522941
   First  2      _jn( 2, x )  0.428870
   First  3      _jn( 3, x )  0.195734
   First  4      _jn( 4, x )  0.063131
   Second 0      _y0( x )     0.511681
   Second 1      _y1( x )     0.094374
   Second 2      _yn( 2, x )  -0.432608
   Second 3      _yn( 3, x )  -0.819314
   Second 4      _yn( 4, x )  -1.626833
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_matherr](matherr.md)<br/>

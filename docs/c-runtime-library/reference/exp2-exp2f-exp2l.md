---
title: exp2、exp2f、exp2l
description: '适用于 exp2 的 API ref ( # A1、exp2f ( # A3 和 exp2l ( # A5，计算2的计算频率为指定值。'
ms.date: 9/1/2020
api_name:
- exp2
- exp2f
- exp2l
- _o_exp2
- _o_exp2f
- _o_exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
ms.openlocfilehash: 518525a38ef575583fde3b7732561f2fa553dd18
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556614"
---
# <a name="exp2-exp2f-exp2l"></a>exp2、exp2f、exp2l

计算2的指定值。

## <a name="syntax"></a>语法

```C
double exp2(
   double x
);

float exp2(
   float x
);  // C++ only

long double exp2(
   long double x
); // C++ only

float exp2f(
   float x
);

long double exp2l(
   long double x
);
#define exp2(X) // Requires C11 or higher
```

### <a name="parameters"></a>参数

*x-blade*\
指数值。

## <a name="return-value"></a>返回值

如果成功，则返回 *x*的以2为底的指数，即 2<sup>x</sup>。 否则，它将返回以下值之一：

|问题|返回|
|-----------|------------|
|*x* = ±0|1|
|*x* =-无限大|+0|
|*x* = + 无穷|+INFINITY|
|*x* = NaN|NaN|
|溢出范围错误|+ HUGE_VAL、+ HUGE_VALF，或 + HUGE_VALL|
|下溢范围错误|舍入后的正确结果|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

由于 c + + 允许重载，因此你可以调用采用并返回和类型的 **exp2** 的重载 **`float`** **`long double`** 。 在 C 程序中，除非使用 \<tgmath.h> 宏来调用此函数，否则， **exp2** 始终采用并返回 **`double`** ，除非使用 <t h.> 中的宏。

如果使用 \<tgmath.h> `exp2()` 宏，则参数的类型将决定选择哪个版本的函数。 有关详细信息，请参阅 [类型-泛型数学](../../c-runtime-library/tgmath.md) 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**exp2**、 **expf2**、 **expl2**|\<math.h>|\<cmath>|
|**exp2** 宏 | \<tgmath.h> ||

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字母函数引用](crt-alphabetical-function-reference.md)<br/>
[exp、expf、expl](exp-expf.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>

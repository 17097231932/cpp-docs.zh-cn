---
description: 了解详细信息： _swab
title: _swab
ms.date: 4/2/2020
api_name:
- _swab
- stdlib/_swab
- _o__swab
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: 178189ede5330d467e8ec263a4558bb55108f354
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326247"
---
# <a name="_swab"></a>_swab

交换字节。

## <a name="syntax"></a>语法

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>parameters

*src*<br/>
要复制和交换的数据。

*目的*<br/>
已交换数据的存储位置。

*n*<br/>
要复制和交换的字节数。

## <a name="return-value"></a>返回值

**Swab** 函数不返回值。 如果 *src* 或 *dest* 指针为 null 或 *n* 小于零，则函数将 **errno** 设置为 **EINVAL** ，并调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。

有关此代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>备注

如果 *n* 为偶数，则 **_swab** 函数将从 *src* 复制 *n* 个字节，交换每对相邻的字节，并将结果存储在 *dest* 上。 如果 *n* 为奇数， **_swab** 会复制和交换 *src* 的前 *n* 个字节，而不会复制最终字节。 **_Swab** 函数通常用于准备要传输到使用不同的字节顺序的计算机的二进制数据。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_swab**|C： \<stdlib.h> c + +： \<cstdlib> 或 \<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>请参阅

[缓冲区操作](../../c-runtime-library/buffer-manipulation.md)<br/>

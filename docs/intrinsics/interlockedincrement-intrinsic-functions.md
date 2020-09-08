---
title: _InterlockedIncrement 内部函数
description: 用于联锁增量的 Microsoft C/c + + 编译器内部函数。
ms.date: 09/03/2020
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
ms.openlocfilehash: 2148ae31f3eb03e398372db3bf15fc64e4857dd1
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556316"
---
# <a name="_interlockedincrement-intrinsic-functions"></a>`_InterlockedIncrement` 内部函数

为 Win32 Windows SDK [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement) 函数提供编译器内部支持。 `_InterlockedIncrement`内部函数是**Microsoft 特定**的。

## <a name="syntax"></a>语法

```C
long _InterlockedIncrement(
   long volatile * lpAddend
);
long _InterlockedIncrement_acq(
   long volatile * lpAddend
);
long _InterlockedIncrement_rel(
   long volatile * lpAddend
);
long _InterlockedIncrement_nf(
   long volatile * lpAddend
);
short _InterlockedIncrement16(
   short volatile * lpAddend
);
short _InterlockedIncrement16_acq(
   short volatile * lpAddend
);
short _InterlockedIncrement16_rel(
   short volatile * lpAddend
);
short _InterlockedIncrement16_nf (
   short volatile * lpAddend
);
__int64 _InterlockedIncrement64(
   __int64 volatile * lpAddend
);
__int64 _InterlockedIncrement64_acq(
   __int64 volatile * lpAddend
);
__int64 _InterlockedIncrement64_rel(
   __int64 volatile * lpAddend
);
__int64 _InterlockedIncrement64_nf(
   __int64 volatile * lpAddend
);
```

### <a name="parameters"></a>参数

*lpAddend*\
[in，out]指向要递增的变量的指针。

## <a name="return-value"></a>返回值

返回值是生成的递增值。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|标头|
|---------------|------------------|------------|
|`_InterlockedIncrement`, `_InterlockedIncrement16`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_InterlockedIncrement64`|ARM、x64、ARM64|\<intrin.h>|
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM，ARM64|\<intrin.h>|

## <a name="remarks"></a>备注

`_InterlockedIncrement` 存在几种变体，这些变体根据其涉及的数据类型和是否使用特定于处理器获取或发布语义而有所不同。

当 `_InterlockedIncrement` 函数对 32 位整数值操作时，`_InterlockedIncrement16` 对 16 位整数值操作且 `_InterlockedIncrement64` 可以对 64 位整数值操作。

ARM 平台上，如果需要（例如在临界区的起点和终点）获取和发布语义，可以使用带 `_acq` 和 `_rel` 后缀的函数。 `_nf` ( "无防护" ) 后缀的内部函数不能充当内存屏障。

由 `lpAddend` 参数指向的变量必须与 32 位边界对齐；否则，此函数在多处理器 x86 系统和任何非 x86 系统上将失效。 有关详细信息，请参阅 [align](../cpp/align-cpp.md)。

Win32 函数在 `Wdm.h` 或 `Ntddk.h` 中声明。

这些例程只能用作内部函数。

## <a name="example"></a>示例

有关如何使用的示例 `_InterlockedIncrement` ，请参阅 [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。

## <a name="see-also"></a>另请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[字](../cpp/keywords-cpp.md)\
[与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

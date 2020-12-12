---
description: 了解详细信息： _interlockedbittestandset 内部函数
title: _interlockedbittestandset 内部函数
ms.date: 09/02/2019
f1_keywords:
- _interlockedbittestandset_cpp
- _interlockedbittestandset_HLEAcquire
- _interlockedbittestandset64
- _interlockedbittestandset64_acq
- _interlockedbittestandset64_nf
- _interlockedbittestandset64_rel
- _interlockedbittestandset
- _interlockedbittestandset_rel
- _interlockedbittestandset64_HLEAcquire
- _interlockedbittestandset_HLERelease
- _interlockedbittestandset_acq
- _interlockedbittestandset_nf
- _interlockedbittestandset64_cpp
- _interlockedbittestandset64_HLERelease
helpviewer_keywords:
- _interlockedbittestandset intrinsic
- _interlockedbittestandset64 intrinsic
- lock_bts instruction
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
ms.openlocfilehash: bc1ee5e70c5b892b7c98bb9cb03f75b3baeda268
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168197"
---
# <a name="_interlockedbittestandset-intrinsic-functions"></a>_interlockedbittestandset 内部函数

**Microsoft 专用**

生成指令以检查 `b` 地址的位 `a` 并返回其当前值，然后将其设置为1。

## <a name="syntax"></a>语法

```C
unsigned char _interlockedbittestandset(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_acq(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLEAcquire(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLERelease(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_nf(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_rel(
   long *a,
   long b
);
unsigned char _interlockedbittestandset64(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_acq(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_nf(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_rel(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLERelease(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>parameters

*的*\
中指向要检查的内存的指针。

*b*\
中要测试的位位置。

## <a name="return-value"></a>返回值

位在设置之前的位置的值 `b` 。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|标头|
|---------------|------------------|------------|
|`_interlockedbittestandset`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM，ARM64|\<intrin.h>|
|`_interlockedbittestandset64_acq`, `_interlockedbittestandset64_nf`, `_interlockedbittestandset64_rel`|ARM64|\<intrin.h>|
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86、x64|\<immintrin.h>|
|`_interlockedbittestandset64`|x64、ARM64|\<intrin.h>|
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|X64|\<immintrin.h>|

## <a name="remarks"></a>备注

在 x86 和 x64 处理器上，这些内部函数使用 `lock bts` 指令读取指定的位并将其设置为1。 此操作为原子性操作。

在 ARM 和 ARM64 处理器上，将内部函数 `_acq` 和 `_rel` 后缀用于获取和释放语义，如关键部分的开头和结尾。 ARM 内部 `_nf` ( "无防护" ) 后缀不能充当内存屏障。

在支持硬件锁省略 (HLE) 指令的 Intel 处理器上，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一条发送到处理器的提示，可通过消除硬件中的锁写步骤加快速度。 如果在不支持 HLE 的处理器上调用这些内部函数，则忽略该提示。

这些例程只能用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

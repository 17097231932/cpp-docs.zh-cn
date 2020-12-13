---
description: 了解详细信息： _InterlockedAddLargeStatistic
title: _InterlockedAddLargeStatistic
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: 52ca32d0f9b08d638a66923f8f0204eb515b447e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336873"
---
# <a name="_interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Microsoft 专用**

执行联锁加法，其中第一个操作数为64位值。

## <a name="syntax"></a>语法

```C
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

### <a name="parameters"></a>parameters

*加数*\
[in，out]指向添加操作的第一个操作数的指针。 所指向的值将替换为添加的结果。

*“值”* \
中第二个操作数;要添加到第一个操作数的值。

## <a name="return-value"></a>返回值

第二个操作数的值。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**头文件** \<intrin.h>

## <a name="remarks"></a>备注

`_InterlockedAddLargeStatistic`内部函数不是原子的，因为它是作为两个单独的锁定指令实现的。 在执行内部函数时在另一个线程上发生的原子64位读取操作可能导致读取的值不一致。

`_InterlockedAddLargeStatistic` 表现为读写屏障。 有关详细信息，请参阅 [_ReadWriteBarrier](../intrinsics/readwritebarrier.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

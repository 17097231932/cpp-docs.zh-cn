---
description: 了解详细信息： __faststorefence
title: __faststorefence
ms.date: 09/02/2019
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: f12d16232e034c562f564d851da08c62cb59c34f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337036"
---
# <a name="__faststorefence"></a>__faststorefence

**Microsoft 专用**

保证每个以前的内存引用（包括加载和存储内存引用）在任何后续的内存引用之前全局可见。

## <a name="syntax"></a>语法

```C
void __faststorefence();
```

## <a name="requirements"></a>要求

|Intrinsic|体系结构|
|---------------|------------------|
|`__faststorefence`|X64|

**头文件** \<intrin.h>

## <a name="remarks"></a>备注

生成一个完整的内存屏障指令序列，该指令序列保证在应用程序继续执行之前全局可见之前发出的加载和存储操作。 效果相当于所有 x64 平台上的 `_mm_mfence` 内部函数，但是速度更快。

在 AMD64 平台上，此例程会生成一个指令，该指令是比 `sfence` 指令更快的存储隔离。 对于时间关键型代码，仅在 AMD64 平台上使用此内部函数而不是 `_mm_sfence`。 在 Intel x64 平台上，`_mm_sfence` 指令速度更快。

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)

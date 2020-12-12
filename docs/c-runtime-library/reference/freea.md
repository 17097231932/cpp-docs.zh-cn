---
description: 了解详细信息： _freea
title: _freea
ms.date: 11/04/2016
api_name:
- _freea
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: 6d6f57117265e62e7d3c822110b52f69cb65ffac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282960"
---
# <a name="_freea"></a>_freea

解除分配或释放内存块。

## <a name="syntax"></a>语法

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>parameters

*memblock*<br/>
要释放的以前分配的内存块。

## <a name="return-value"></a>返回值

无。

## <a name="remarks"></a>备注

**_Freea** 函数释放以前通过调用 [_malloca](malloca.md)分配的内存块 (*memblock*) 。 **_freea** 检查是否已在堆或堆栈上分配内存。 如果它是在堆栈上分配的， **_freea** 不执行任何操作。 如果被分配到堆上，则已释放的字节数等于分配块时请求的字节数。 如果 *memblock* 为 **NULL**，则将忽略指针并 **_freea** 立即返回。 尝试释放无效指针 (指向内存块的指针（不是由 **_malloca**) 分配）可能会影响后续分配请求并导致错误。

如果发现内存是在堆上分配的， **_freea** 将在内部 **免费** 调用。 内存是在堆上还是在堆栈上由内存中的标记决定，该内存地址紧接所分配的内存。

如果在释放内存时发生错误，则会在出现故障的情况下，使用操作系统中的信息设置 **errno** 。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

释放内存块后， [_heapmin](heapmin.md) 通过合并未使用的区域并将其释放回到操作系统，将堆上的可用内存量降至最低。 未释放给操作系统的已释放内存还原到可用池，并且可用于重新分配。

调用 **_freea** 必须附带对 **_malloca** 的所有调用。 在同一内存上调用 **_freea** 两次也是错误的。 当应用程序与调试版的 C 运行时库链接时，尤其是在定义 **_CRTDBG_MAP_ALLOC** 启用 [_malloc_dbg](malloc-dbg.md)功能的情况下，可以更容易地查找 **_freea** 的丢失或重复调用。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

标记 **_freea** `__declspec(noalias)` ，这意味着保证函数不修改全局变量。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_freea**|\<stdlib.h> 和 \<malloc.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参见 [_malloca](malloca.md) 的示例。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>

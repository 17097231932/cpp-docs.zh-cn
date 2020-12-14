---
description: 了解详细信息： _aligned_offset_realloc
title: _aligned_offset_realloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_realloc
- _o__aligned_offset_realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_offset_realloc
- _aligned_offset_realloc
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
ms.openlocfilehash: 0e61a1425d495b2ab7019eee9f42dbe26989312e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312457"
---
# <a name="_aligned_offset_realloc"></a>_aligned_offset_realloc

更改使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块的大小。

## <a name="syntax"></a>语法

```C
void * _aligned_offset_realloc(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>parameters

*memblock*<br/>
当前的内存块指针。

*大小*<br/>
内存分配的大小。

*关联*<br/>
对齐值，必须是 2 的整数次幂。

*offset*<br/>
用于强制对齐的内存分配中的偏移量。

## <a name="return-value"></a>返回值

**_aligned_offset_realloc** 返回指向重新分配的 (并可能移动) 内存块的 void 指针。 如果大小为零且缓冲区参数不为 **null**，则返回值为 null; 否则，如果没有足够的可用内存来将块扩展到给定大小，则返回值为 **null** 。 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。

**_aligned_offset_realloc** 标记为 `__declspec(noalias)` 和 `__declspec(restrict)` ，这意味着该函数保证不修改全局变量，并且返回的指针没有化名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

## <a name="remarks"></a>备注

与 [_aligned_offset_malloc](aligned-offset-malloc.md)一样， **_aligned_offset_realloc** 允许在结构中将结构对齐。

**_aligned_offset_realloc** 基于 **malloc**。 有关使用 **_aligned_offset_malloc** 的详细信息，请参阅 [malloc](malloc.md)。 如果 *memblock* 为 **NULL**，则函数在内部调用 **_aligned_offset_malloc** 。

如果内存分配失败或请求的大小大于 **_HEAP_MAXREQ**，则此函数会将 **Errno** 设置为 **ENOMEM** 。 有关 **errno** 的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_offset_realloc** 验证其参数。 如果 *对齐* 不是2的幂或如果 *offset* 大于或等于 *大小* 且非零，则此函数将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 **NULL** ，并将 **Errno** 设置为 **EINVAL**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>请参阅

[数据对齐](../../c-runtime-library/data-alignment.md)<br/>

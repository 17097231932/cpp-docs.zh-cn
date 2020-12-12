---
description: 了解详细信息： CWin32Heap 类
title: CWin32Heap 类
ms.date: 11/04/2016
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
ms.openlocfilehash: a19c7f01a572bad46dbbab2925104d4dfcf569be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140200"
---
# <a name="cwin32heap-class"></a>CWin32Heap 类

此类使用 Win32 堆分配函数实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CWin32Heap：： CWin32Heap](#cwin32heap)|构造函数。|
|[CWin32Heap：： ~ CWin32Heap](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CWin32Heap：： Allocate](#allocate)|从堆对象中分配内存块。|
|[CWin32Heap：： Attach](#attach)|将堆对象附加到现有堆。|
|[CWin32Heap：:D etach](#detach)|从现有堆分离堆对象。|
|[CWin32Heap：： Free](#free)|释放以前从堆中分配的内存。|
|[CWin32Heap：： GetSize](#getsize)|返回从堆对象分配的内存块的大小。|
|[CWin32Heap：：重新分配](#reallocate)|从堆对象中重新分配内存块。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CWin32Heap：： m_bOwnHeap](#m_bownheap)|用于确定堆句柄的当前所有权的标志。|
|[CWin32Heap：： m_hHeap](#m_hheap)|堆对象的句柄。|

## <a name="remarks"></a>备注

`CWin32Heap` 使用 Win32 堆分配函数（包括 [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) 和 [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)）来实现内存分配方法。 与其他堆类不同， `CWin32Heap` 需要先提供有效的堆句柄才能分配内存：其他类默认使用进程堆。 可以向构造函数或 [CWin32Heap：： Attach](#attach) 方法提供句柄。 有关更多详细信息，请参阅 [CWin32Heap：： CWin32Heap](#cwin32heap) 方法。

## <a name="example"></a>示例

请参阅 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>要求

**标头：** atlmem

## <a name="cwin32heapallocate"></a><a name="allocate"></a> CWin32Heap：： Allocate

从堆对象中分配内存块。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>parameters

*nBytes*<br/>
新内存块中请求的字节数。

### <a name="return-value"></a>返回值

将指针返回到新分配的内存块。

### <a name="remarks"></a>备注

调用 [CWin32Heap：： Free](#free) 或 [CWin32Heap：：重新分配](#reallocate) 以释放此方法分配的内存。

使用 [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)实现。

## <a name="cwin32heapattach"></a><a name="attach"></a> CWin32Heap：： Attach

将堆对象附加到现有堆。

```cpp
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>parameters

*hHeap*<br/>
现有堆句柄。

*bTakeOwnership*<br/>
一个标志，该标志指示 `CWin32Heap` 对象是否要在堆的资源上取得所有权。

### <a name="remarks"></a>备注

如果 *bTakeOwnership* 为 TRUE，则 `CWin32Heap` 对象负责删除堆句柄。

## <a name="cwin32heapcwin32heap"></a><a name="cwin32heap"></a> CWin32Heap：： CWin32Heap

构造函数。

```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```

### <a name="parameters"></a>parameters

*hHeap*<br/>
一个现有的堆对象。

dwFlags <br/>
在创建堆时使用的标志。

*nInitialSize*<br/>
堆的初始大小。

*nMaxSize*<br/>
堆的最大大小。

### <a name="remarks"></a>备注

在分配内存之前，必须为 `CWin32Heap` 对象提供有效的堆句柄。 实现此目的的最简单的方法是使用进程堆：

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

也可以向构造函数提供现有堆句柄，在这种情况下，新对象不会接管此堆的所有权。 在删除 `CWin32Heap` 对象时，原始堆句柄仍将有效。

使用 [CWin32Heap：： Attach](#attach)，还可以将现有堆附加到新的对象。

如果在单个线程中执行所有操作时需要堆，则最佳方法是创建如下对象：

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

参数 HEAP_NO_SERIALIZE 指定在堆函数分配和释放内存时不会使用互斥，从而使性能得到相应的提升。

第三个参数默认为 0，这使堆能够根据需要增长。 有关内存大小和标志的说明，请参阅 [HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) 。

## <a name="cwin32heapcwin32heap"></a><a name="dtor"></a> CWin32Heap：： ~ CWin32Heap

析构函数。

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>备注

如果对象具有堆的所有权，则销毁堆句柄 `CWin32Heap` 。

## <a name="cwin32heapdetach"></a><a name="detach"></a> CWin32Heap：:D etach

从现有堆分离堆对象。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>返回值

返回对象之前附加到的堆的句柄。

## <a name="cwin32heapfree"></a><a name="free"></a> CWin32Heap：： Free

通过 [CWin32Heap：： Allocate](#allocate) 或 [CWin32Heap：：](#reallocate)Allocate 释放之前从堆中分配的内存。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>parameters

*h-p*<br/>
指向要释放的内存块的指针。 NULL 是有效的值并且不执行任何操作。

## <a name="cwin32heapgetsize"></a><a name="getsize"></a> CWin32Heap：： GetSize

返回从堆对象分配的内存块的大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>parameters

*h-p*<br/>
指向该方法将获取的内存块的指针。 这是 [CWin32Heap：： Allocate](#allocate) 或 [CWin32Heap：：](#reallocate)Allocate 返回的指针。

### <a name="return-value"></a>返回值

返回分配的内存块的大小（以字节为单位）。

## <a name="cwin32heapm_bownheap"></a><a name="m_bownheap"></a> CWin32Heap：： m_bOwnHeap

用于确定 [m_hHeap](#m_hheap)中存储的堆句柄的当前所有权的标志。

```
bool m_bOwnHeap;
```

## <a name="cwin32heapm_hheap"></a><a name="m_hheap"></a> CWin32Heap：： m_hHeap

堆对象的句柄。

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>备注

用于将句柄存储到堆对象的变量。

## <a name="cwin32heapreallocate"></a><a name="reallocate"></a> CWin32Heap：：重新分配

从堆对象中重新分配内存块。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>parameters

*h-p*<br/>
指向要重新分配的内存块的指针。

*nBytes*<br/>
已分配块的新大小（以字节为单位）。 块可放大或缩小。

### <a name="return-value"></a>返回值

将指针返回到新分配的内存块。

### <a name="remarks"></a>备注

如果 *p* 为 NULL，则假定尚未分配内存块，并调用了 [CWin32Heap：： Allocate](#allocate) 的参数 *nBytes*。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)<br/>
[CLocalHeap 类](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 类](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap 类](../../atl/reference/ccomheap-class.md)

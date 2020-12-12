---
description: '了解更多相关信息：自定义字符串管理器的实现 (基本方法) '
title: '自定义字符串管理器的实现 (基本方法) '
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: e532312edff16229b6b91eef1d95ae764b70eb5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166949"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>自定义字符串管理器的实现 (基本方法) 

为字符串数据自定义内存分配方案的最简单方法是使用 ATL 提供的类， `CAtlStringMgr` 但提供自己的内存分配例程。 的构造函数 `CAtlStringMgr` 采用单个参数：指向对象的指针 `IAtlMemMgr` 。 `IAtlMemMgr` 是一个抽象基类，它提供到堆的泛型接口。 使用 `IAtlMemMgr` 接口可以 `CAtlStringMgr` 分配、重新分配和释放用于存储字符串数据的内存。 您可以 `IAtlMemMgr` 自行实现接口，也可以使用五个由 ATL 提供的内存管理器类之一。 ATL 提供的内存管理器只是包装现有的内存分配设施：

- [CCRTHeap](../atl/reference/ccrtheap-class.md) ([malloc](../c-runtime-library/reference/malloc.md)、 [free](../c-runtime-library/reference/free.md)和 [realloc](../c-runtime-library/reference/realloc.md) 包装标准 CRT 堆函数) 

- [CWin32Heap](../atl/reference/cwin32heap-class.md)使用[HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)、 [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)和[HeapRealloc](/windows/win32/api/heapapi/nf-heapapi-heaprealloc)包装 Win32 堆句柄

- [CLocalHeap](../atl/reference/clocalheap-class.md) 包装 Win32 Api： [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)、 [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)和 [LocalRealloc](/windows/win32/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md) 包装 Win32 Api： [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)、 [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)和 [GlobalRealloc](/windows/win32/api/winbase/nf-winbase-globalrealloc)。

- [CComHeap](../atl/reference/ccomheap-class.md) 包装 COM 任务分配器 Api： [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)、 [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)和 [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

出于字符串内存管理的目的，最有用的类是 `CWin32Heap` 因为它允许您创建多个独立的堆。 例如，如果想要对字符串使用单独的堆，则可以执行以下操作：

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

若要使用此专用字符串管理器管理变量的内存 `CString` ，请将指向该管理器的指针作为参数传递给该 `CString` 变量的构造函数：

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>请参阅

[内存管理与 CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

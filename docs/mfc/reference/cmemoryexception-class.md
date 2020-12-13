---
description: 了解详细信息： CMemoryException 类
title: CMemoryException 类
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 694629d65c8b4cffc351873d5da3d8ed3c34cf8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336649"
---
# <a name="cmemoryexception-class"></a>CMemoryException 类

表示内存不足异常条件。

## <a name="syntax"></a>语法

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CMemoryException：： CMemoryException](#cmemoryexception)|构造 `CMemoryException` 对象。|

## <a name="remarks"></a>备注

无需进行进一步的限制。 内存异常由自动引发 **`new`** 。 例如，如果您使用编写自己的内存函数，则 `malloc` 您需要负责引发内存异常。

有关的详细信息 `CMemoryException` ，请参阅文章 [ (MFC) 的异常处理 ](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>要求

**标头：** afx

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a> CMemoryException：： CMemoryException

构造 `CMemoryException` 对象。

```
CMemoryException();
```

### <a name="remarks"></a>备注

不要直接使用此构造函数，而应调用 global 函数 [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)。 此全局函数在内存不足的情况下可能会成功，因为它在以前分配的内存中构造异常对象。 有关异常处理的详细信息，请参阅文章 [异常](../exception-handling-in-mfc.md)。

## <a name="see-also"></a>请参阅

[CException 类](cexception-class.md)<br/>
[层次结构图](../hierarchy-chart.md)

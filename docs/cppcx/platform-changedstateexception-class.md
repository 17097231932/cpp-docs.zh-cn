---
description: 了解详细信息： Platform：： ChangedStateException 类
title: Platform::ChangedStateException 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
ms.openlocfilehash: baabf54cacfc4dd03256b569fb868c402ea98a97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284026"
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException 类

当对象的内部状态发生更改进而导致方法的结果失效时引发。

## <a name="syntax"></a>语法

```cpp
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>备注

例如，如果在父集合更改后调用集合迭代器或集合视图的方法，即会导致方法的结果失效，这时就会引发此异常。

有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md) 类。

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**Metadata：** platform.string

## <a name="see-also"></a>请参阅

[Platform：： COMException 类](../cppcx/platform-comexception-class.md)

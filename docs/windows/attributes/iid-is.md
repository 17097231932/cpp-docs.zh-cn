---
title: 'iid_is (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 6a8fe8c7481cd251baff65293607733573f46ea6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832212"
---
# <a name="iid_is"></a>iid_is

指定接口指针所指向的 COM 接口的 IID。

## <a name="syntax"></a>语法

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>参数

*expression*<br/>
C 语言表达式，指定接口指针所指向的 COM 接口的 IID。

## <a name="remarks"></a>注解

**Iid_is** c + + 特性具有与[iid_is](/windows/win32/Midl/iid-is) MIDL 特性相同的功能。

## <a name="example"></a>示例

下面的代码演示如何使用 **iid_is**：

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|Interface 参数，数据成员|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[参数属性](parameter-attributes.md)

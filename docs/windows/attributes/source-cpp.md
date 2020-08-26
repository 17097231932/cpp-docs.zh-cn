---
title: '源 (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: f9a1f576e26805c5dd84c2d83cdf3615d0661af3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842762"
---
# <a name="source-c"></a>source (C++)

在类上，为连接点指定 COM 对象的源接口。 在属性或方法上，指示成员返回作为事件来源的对象或变体。

## <a name="syntax"></a>语法

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>参数

*interfaces*<br/>
将源属性应用于类时指定的一个或多个接口。 将源应用于属性或方法时，不使用此参数。

## <a name="remarks"></a>注解

**源**c + + 特性与[源](/windows/win32/Midl/source)MIDL 特性具有相同的功能。

您可以使用 [默认](default-cpp.md) 属性来指定对象的默认源接口。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|**`class`**， **`struct`** ， **接口**|
|**且**|否|
|**必需属性**|`coclass` 当应用于类或结构时， () |
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[coclass](coclass.md)

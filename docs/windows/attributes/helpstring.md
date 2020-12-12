---
description: 了解详细信息： helpstring
title: 'helpstring (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 3b3aa2470080f33fd4a9dea4f063e908c0431d5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148806"
---
# <a name="helpstring"></a>helpstring

指定一个字符串，用于描述应用该字符串的元素。

## <a name="syntax"></a>语法

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>parameters

*string*<br/>
帮助字符串的文本。

## <a name="remarks"></a>备注

**Helpstring** c + + 特性具有与 [helpstring](/windows/win32/Midl/helpstring) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用 **helpstring** 的示例，请参阅 [defaultvalue](defaultvalue.md)的示例。

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|**interface**、 **`typedef`** ， **`class`** 、method、property|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)

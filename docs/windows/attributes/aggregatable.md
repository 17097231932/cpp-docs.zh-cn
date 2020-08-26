---
title: '可聚合 (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: 6782b1ca28eb07b3f726bd85cd7fffa9b1f1bad2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836369"
---
# <a name="aggregatable"></a>aggregatable

指示类支持聚合。

## <a name="syntax"></a>语法

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>参数

*value*<br/>
 (可选) 用于指示 COM 对象何时可以聚合的参数：

- `never` 无法聚合 COM 对象。

- `allowed` COM 对象可以直接创建，也可以进行聚合。 这是默认值。

- `always` 不能直接创建 COM 对象，只能对其进行聚合。 调用 `CoCreateInstance` 此对象时，必须指定聚合对象的 `IUnknown` 接口 (控制 `IUnknown`) 。

## <a name="remarks"></a>注解

可 **聚合** c + + 属性具有与可 [聚合](/windows/win32/Midl/aggregatable) MIDL 属性相同的功能。 这意味着编译器会将可 **聚合** 特性传递到生成的 .idl 文件。

此属性要求 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果 `progid` 应用了，则 `vi_progid` `coclass` 还会应用。

### <a name="atl-projects"></a>ATL 项目

如果在使用 ATL 的项目中使用此属性，该属性的行为将会更改。 除了前面所述的行为，该特性还将以下宏之一添加到目标类：

|参数值|插入的宏|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_aggregatable.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyModule")];

[ coclass, aggregatable(allowed),
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]
class CMyClass {};
```

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|**`class`**, **`struct`**|
|**且**|否|
|**必需属性**|以下一项或多项操作： `coclass` 、 `progid` 或 `vi_progid` 。|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[聚合](/windows/win32/com/aggregation)

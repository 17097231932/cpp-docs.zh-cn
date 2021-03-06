---
description: 了解详细信息： satype
title: 'satype (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: dab0f866eba5501a9a83d531d9cbdf50501dcff0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327314"
---
# <a name="satype"></a>satype

指定结构的数据类型 `SAFEARRAY` 。

## <a name="syntax"></a>语法

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>parameters

data_type<br/>
`SAFEARRAY`作为参数传递给接口方法的数据结构的数据类型。

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|Interface 参数，interface 方法|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

## <a name="remarks"></a>备注

**Satype** c + + 特性指定的数据类型 `SAFEARRAY` 。

> [!NOTE]
> 将从生成的 .idl 文件中的指针中删除间接级别， `SAFEARRAY` 方法是从生成的 .idl 文件中的声明。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>请参阅

[编译器特性](compiler-attributes.md)<br/>
[参数属性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[id](id.md)

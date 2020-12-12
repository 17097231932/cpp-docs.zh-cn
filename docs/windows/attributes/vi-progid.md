---
description: 了解详细信息： vi_progid
title: 'vi_progid (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: 766ebcee636b3fb0bcdb1aeabd53ee0e977ca790
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327182"
---
# <a name="vi_progid"></a>vi_progid

指定 ProgID 的与版本无关的形式。

## <a name="syntax"></a>语法

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>参数

*name*<br/>
表示对象的独立于版本的 ProgID。

Progid 提供了一个可读版本的类标识符 (CLSID) 用于标识 COM/ActiveX 对象。

## <a name="remarks"></a>备注

**Vi_progid** c + + 特性使你可以为 COM 对象指定独立于版本的 progid。 ProgID 的格式为 *name1*。 独立于版本的 ProgID 没有 *版本*。 可以同时 `progid` 在上指定和 **vi_progid** 特性 `coclass` 。 如果未指定 **vi_progid**，则独立于版本的 progid 是 [progid](progid.md) 特性指定的值。

**vi_progid** 隐含 `coclass` 特性，即，如果指定 **vi_progid**，则与指定 `coclass` 和 **vi_progid** 特性相同。

**Vi_progid** 特性会使类在指定的名称下自动注册。 生成的 .idl 文件将不会显示 ProgID 值。

在 ATL 项目中，如果也存在 [coclass](coclass.md) 特性，则由 `GetVersionIndependentProgID` 特性)  (插入的函数使用指定的 ProgID `coclass` 。

## <a name="example"></a>示例

有关 **vi_progid** 的示例用法，请参阅 [coclass](coclass.md)示例。

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|**`class`**, **`struct`**|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[ProgID 密钥](/windows/win32/com/-progid--key)

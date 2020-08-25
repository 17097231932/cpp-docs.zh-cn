---
title: 'usesgetlasterror (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: e3d3c292554350d85296971a9bd3620909ef47c7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831627"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

告诉调用方如果在调用该函数时出现错误，则调用方可以调用 `GetLastError` 来检索错误代码。

## <a name="syntax"></a>语法

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>备注

**Usesgetlasterror** c + + 特性具有与[usesgetlasterror](/windows/win32/Midl/usesgetlasterror) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用**usesgetlasterror**的示例，请参阅[idl_module](idl-module.md)示例。

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|**module** 特性|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)

---
description: 了解详细信息： RemoveIUnknown 类
title: RemoveIUnknown 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: 0ef00ee9859a27252550aaeec6fb9b4f9ef2d5b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278722"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>parameters

*T*<br/>
一个类。

## <a name="remarks"></a>备注

使类型等效于 `IUnknown` 基于的类型，但具有非虚拟 `QueryInterface` 的、 `AddRef` 和 `Release` 成员函数。

默认情况下，COM 方法提供虚拟 `QueryInterface` 、 `AddRef` 和 `Release` 方法。 但是， `ComPtr` 不需要虚拟方法的开销。 `RemoveIUnknown` 提供私有、非虚拟的 `QueryInterface` 、和方法，从而消除了开销 `AddRef` `Release` 。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`ReturnType`|与模板参数 *T* 等效但包含非虚拟成员的类型的同义词 `IUnknown` 。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

`RemoveIUnknown`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>请参阅

[Microsoft：： WRL：:D etails 命名空间](microsoft-wrl-details-namespace.md)

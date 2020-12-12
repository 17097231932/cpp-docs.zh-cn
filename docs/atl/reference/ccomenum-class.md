---
description: 了解详细信息： CComEnum 类
title: CComEnum 类
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 0cee4129c0bc5129313b92e144c22de9d161c9cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146687"
---
# <a name="ccomenum-class"></a>CComEnum 类

此类定义基于数组的 COM 枚举器对象。

## <a name="syntax"></a>语法

```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
T,
    Copy>,
public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>parameters

*基座*<br/>
COM 枚举器接口。 有关示例，请参阅 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 。

*piid*<br/>
指向枚举器接口的接口 ID 的指针。

*T*<br/>
枚举器接口公开的项的类型。

*复制*<br/>
同类 [复制策略类](../../atl/atl-copy-policy-classes.md)。

*ThreadModel*<br/>
类的线程模型。 此参数默认为项目中使用的全局对象线程模型。

## <a name="remarks"></a>备注

`CComEnum` 定义基于数组的 COM 枚举器对象。 此类类似于 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) ，后者实现基于 c + + 标准库容器的枚举器。 下面概述了使用此类的典型步骤。 有关详细信息，请参阅 [ATL 集合和枚举](../../atl/atl-collections-and-enumerators.md)器。

## <a name="to-use-this-class"></a>使用此类：

- **`typedef`** 此类的专用化。

- 使用 **`typedef`** 作为专用化中的模板参数 `CComObject` 。

- 创建专用化的实例 `CComObject` 。

- 通过调用 [CComEnumImpl：： Init](../../atl/reference/ccomenumimpl-class.md#init)初始化枚举器对象。

- 将枚举器接口返回到客户端。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>要求

**标头：** atlcom。h

## <a name="example"></a>示例

下面显示的代码提供了一个可重用的函数，用于创建和初始化枚举器对象。

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

此模板函数可用于实现 `_NewEnum` 集合接口的属性，如下所示：

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

此代码 **`typedef`** 为提供 `CComEnum` 通过接口公开变型向量的。 `IEnumVariant` `CVariantArrayCollection`类只是专门 `CreateEnumerator` 用于处理此类型的枚举器对象并传递所需的参数。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl 类](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)

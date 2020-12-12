---
description: 了解详细信息： CComDynamicUnkArray 类
title: CComDynamicUnkArray 类
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: fe817b097bbb75c7d09bffdb6883e5ac4a76f966
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152082"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray 类

此类存储指针的数组 `IUnknown` 。

## <a name="syntax"></a>语法

```
class CComDynamicUnkArray
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|构造函数。 将集合值初始化为 NULL，将集合大小初始化为零。|
|[CComDynamicUnkArray：： ~ CComDynamicUnkArray](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CComDynamicUnkArray：： Add](#add)|调用此方法可添加指向 `IUnknown` 该数组的指针。|
|[CComDynamicUnkArray：： begin](#begin)|返回指向集合中第一个 `IUnknown` 指针的指针。|
|[CComDynamicUnkArray：： clear](#clear)|清空数组。|
|[CComDynamicUnkArray：： end](#end)|返回指向集合中最后一个指针之后的一个指针 `IUnknown` 。|
|[CComDynamicUnkArray：： GetAt](#getat)|检索指定索引处的元素。|
|[CComDynamicUnkArray：： System.windows.application.getcookie](#getcookie)|调用此方法以获取与给定指针关联的 cookie `IUnknown` 。|
|[CComDynamicUnkArray：： GetSize](#getsize)|返回数组的长度。|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|调用此方法以获取 `IUnknown` 与给定 cookie 关联的指针。|
|[CComDynamicUnkArray：： Remove](#remove)|调用此方法可 `IUnknown` 从数组中删除指针。|

## <a name="remarks"></a>备注

`CComDynamicUnkArray` 保存一个动态分配的 `IUnknown` 指针数组，其中每个都是连接点上的接口。 `CComDynamicUnkArray` 可用作 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 模板类的参数。

`CComDynamicUnkArray`方法[开始](#begin)和[结束](#end)可用于循环遍历所有连接点 (例如，在) 引发事件时。

有关自动创建连接点代理的详细信息，请参阅向 [对象添加连接点](../../atl/adding-connection-points-to-an-object.md) 。

> [!NOTE]
> **注意** 类由 `CComDynamicUnkArray` **添加类** 向导在创建具有连接点的控件时使用。 如果要手动指定连接点的数目，请将引用从更改 `CComDynamicUnkArray` 为 `CComUnkArray<` *n* `>` ，其中 *n* 是所需的连接点的数目。

## <a name="requirements"></a>要求

**标头：** atlcom。h

## <a name="ccomdynamicunkarrayadd"></a><a name="add"></a> CComDynamicUnkArray：： Add

调用此方法可添加指向 `IUnknown` 该数组的指针。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>parameters

*pUnk*<br/>
`IUnknown`要添加到数组中的指针。

### <a name="return-value"></a>返回值

返回与新添加的指针关联的 cookie。

## <a name="ccomdynamicunkarraybegin"></a><a name="begin"></a> CComDynamicUnkArray：： begin

返回指向接口指针集合的开头的指针 `IUnknown` 。

```
IUnknown**
    begin();
```

### <a name="return-value"></a>返回值

指向 `IUnknown` 接口指针的指针。

### <a name="remarks"></a>备注

集合包含指向本地存储的接口的指针 `IUnknown` 。 将每个 `IUnknown` 接口强制转换为实际接口类型，然后调用它。 不需要先查询接口。

使用接口之前 `IUnknown` ，应检查其是否不为 NULL。

## <a name="ccomdynamicunkarrayclear"></a><a name="clear"></a> CComDynamicUnkArray：： clear

清空数组。

```cpp
void clear();
```

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="ccomdynamicunkarray"></a> CComDynamicUnkArray::CComDynamicUnkArray

构造函数。

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>备注

将集合大小设置为零，并将值初始化为 NULL。 如果需要，析构函数将释放该集合。

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="dtor"></a> CComDynamicUnkArray：： ~ CComDynamicUnkArray

析构函数。

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>备注

释放由类构造函数分配的资源。

## <a name="ccomdynamicunkarrayend"></a><a name="end"></a> CComDynamicUnkArray：： end

返回指向集合中最后一个指针之后的一个指针 `IUnknown` 。

```
IUnknown**
    end();
```

### <a name="return-value"></a>返回值

指向 `IUnknown` 接口指针的指针。

## <a name="ccomdynamicunkarraygetat"></a><a name="getat"></a> CComDynamicUnkArray：： GetAt

检索指定索引处的元素。

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要检索的元素的索引。

### <a name="return-value"></a>返回值

指向 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 接口的指针。

## <a name="ccomdynamicunkarraygetcookie"></a><a name="getcookie"></a> CComDynamicUnkArray：： System.windows.application.getcookie

调用此方法以获取与给定指针关联的 cookie `IUnknown` 。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>parameters

*ppFind*<br/>
`IUnknown`需要相关 cookie 的指针。

### <a name="return-value"></a>返回值

返回与指针关联的 cookie `IUnknown` ; 如果找不到匹配的指针，则返回零 `IUnknown` 。

### <a name="remarks"></a>备注

如果有多个相同指针的实例，则 `IUnknown` 此函数将返回第一个实例的 cookie。

## <a name="ccomdynamicunkarraygetsize"></a><a name="getsize"></a> CComDynamicUnkArray：： GetSize

返回数组的长度。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

数组的长度。

## <a name="ccomdynamicunkarraygetunknown"></a><a name="getunknown"></a> CComDynamicUnkArray::GetUnknown

调用此方法以获取 `IUnknown` 与给定 cookie 关联的指针。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>parameters

*dwCookie*<br/>
需要关联指针的 cookie `IUnknown` 。

### <a name="return-value"></a>返回值

返回 `IUnknown` 指针，或者如果找不到匹配的 cookie，则为 NULL。

## <a name="ccomdynamicunkarrayremove"></a><a name="remove"></a> CComDynamicUnkArray：： Remove

调用此方法可 `IUnknown` 从数组中删除指针。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>parameters

*dwCookie*<br/>
引用 `IUnknown` 要从数组中移除的指针的 cookie。

### <a name="return-value"></a>返回值

如果指针被移除，则返回 TRUE;否则为 FALSE。

## <a name="see-also"></a>请参阅

[CComUnkArray 类](../../atl/reference/ccomunkarray-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)

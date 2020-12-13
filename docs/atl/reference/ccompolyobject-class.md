---
description: 了解详细信息： CComPolyObject 类
title: CComPolyObject 类
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: 1584fd03882b0eb0618bd20b54134317efd17ba8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142397"
---
# <a name="ccompolyobject-class"></a>CComPolyObject 类

此类实现 `IUnknown` 聚合或非聚合对象。

## <a name="syntax"></a>语法

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>parameters

*独立*<br/>
从 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)派生的类，以及要在对象上支持的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CComPolyObject：： CComPolyObject](#ccompolyobject)|构造函数。|
|[CComPolyObject：： ~ CComPolyObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CComPolyObject：： AddRef](#addref)|递增对象的引用计数。|
|[CComPolyObject：： CreateInstance](#createinstance)| (静态) 使你可以创建新的 **CComPolyObject<** `contained` **>** 对象，而不会产生 [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)开销。|
|[CComPolyObject：： FinalConstruct](#finalconstruct)|执行的最终初始化 `m_contained` 。|
|[CComPolyObject：： FinalRelease](#finalrelease)|执行的最终析构 `m_contained` 。|
|[CComPolyObject：： QueryInterface](#queryinterface)|检索指向所请求的接口的指针。|
|[CComPolyObject：： Release](#release)|递减对象的引用计数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComPolyObject：： m_contained](#m_contained)|如果对象已聚合，则委托 `IUnknown` 对外部未知的调用; 如果对象未聚合，则委托给 `IUnknown` 对象的。|

## <a name="remarks"></a>备注

`CComPolyObject` 实现聚合或非聚合对象的 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。

创建实例时 `CComPolyObject` ，将检查外部未知的值。 如果为 NULL， `IUnknown` 则为非聚合对象实现。 如果外部未知值不为 NULL， `IUnknown` 则为聚合对象实现。

使用的优点 `CComPolyObject` 是，你不必在模块中同时使用 [CComAggObject](../../atl/reference/ccomaggobject-class.md) 和 [CComObject](../../atl/reference/ccomobject-class.md) 来处理聚合和非聚合事例。 单个 `CComPolyObject` 对象处理两种情况。 这意味着在您的模块中只存在一个 vtable 副本和一个函数副本。 如果 vtable 很大，这可能会显著降低模块大小。 但是，如果你的 vtable 很小，则使用 `CComPolyObject` 可能会导致模块大小稍微大一些，因为它未针对聚合或非聚合对象进行优化，如 `CComAggObject` 和 `CComObject` 。

如果在对象的类定义中指定了 DECLARE_POLY_AGGREGATABLE 宏， `CComPolyObject` 将使用来创建对象。 如果使用 ATL 项目向导创建 "完全控制" 或 "Internet Explorer" 控件，则将自动声明 DECLARE_POLY_AGGREGATABLE。

如果聚合，则 `CComPolyObject` 对象具有其自己的 `IUnknown` 、与外部对象的不同， `IUnknown` 并保留其自己的引用计数。 `CComPolyObject` 使用 [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) 委托给外部未知。

有关聚合的详细信息，请参阅 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>要求

**标头：** atlcom。h

## <a name="ccompolyobjectaddref"></a><a name="addref"></a> CComPolyObject：： AddRef

递增对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可能对诊断或测试有用的值。

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a> CComPolyObject：： CComPolyObject

构造函数。

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>parameters

*函数*<br/>
中如果要聚合对象，则为指向外部未知的指针; 如果对象未聚合，则为 NULL。

### <a name="remarks"></a>备注

初始化 `CComContainedObject` 数据成员、 [m_contained](#m_contained)，并递增模块锁计数。

析构函数递减模块锁计数。

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a> CComPolyObject：： ~ CComPolyObject

析构函数。

```
~CComPolyObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源，调用 [FinalRelease](#finalrelease)，并递减模块锁计数。

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a> CComPolyObject：： CreateInstance

允许您创建新的 **CComPolyObject<** `contained` **>** 对象，而不会产生 [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)开销。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>parameters

*pp*<br/>
弄指向 **CComPolyObject<** 指针的指针 `contained` **>** 。 如果 `CreateInstance` 不成功，则 *pp* 设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

返回的对象的引用计数为零，因此立即调用 `AddRef` ，然后在完成后使用 `Release` 释放对象指针上的引用。

如果不需要直接访问对象，但仍想要创建一个不带开销的新对象， `CoCreateInstance` 请改为使用 [CComCoClass：： CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 。

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a> CComPolyObject：： FinalConstruct

在对象构造的最后阶段调用，此方法对 [m_contained](#m_contained) 数据成员执行任何最终初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a> CComPolyObject：： FinalRelease

在对象销毁过程中调用，此方法将释放 [m_contained](#m_contained) 数据成员。

```cpp
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a> CComPolyObject：： m_contained

派生自类的 [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) 对象。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>parameters

*独立*<br/>
中从 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)派生的类，以及要在对象上支持的任何其他接口。

### <a name="remarks"></a>备注

`IUnknown` 如果对象 `m_contained` 已聚合，则会将调用委托给外部未知，如果对象未聚合，则委托给 `IUnknown` 此对象的。

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a> CComPolyObject：： QueryInterface

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>parameters

*Q*<br/>
COM 接口。

*iid*<br/>
中所请求的接口的标识符。

*ppvObject*<br/>
弄指向由 *iid* 标识的接口指针的指针。 如果对象不支持此接口，则将 *ppvObject* 设置为 NULL。

*pp*<br/>
弄指向由标识的接口的指针 `__uuidof(Q)` 。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

对于聚合对象，如果请求的接口为 `IUnknown` ，则 `QueryInterface` 返回一个指向聚合对象自身的指针 `IUnknown` ，并递增引用计数。 否则，此方法将通过 `CComContainedObject` 数据成员（ [m_contained](#m_contained)）来查询接口。

## <a name="ccompolyobjectrelease"></a><a name="release"></a> CComPolyObject：： Release

递减对象的引用计数。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试版本中，将 `Release` 返回一个值，该值对于诊断或测试可能很有用。 在 nondebug 生成中， `Release` 始终返回0。

## <a name="see-also"></a>请参阅

[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[类概述](../../atl/atl-class-overview.md)

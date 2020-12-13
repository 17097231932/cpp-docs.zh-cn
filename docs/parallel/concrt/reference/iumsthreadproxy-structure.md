---
description: 了解详细信息： IUMSThreadProxy 结构
title: IUMSThreadProxy 结构
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: 02eb999b35143e4fc9e0416e02abb60c3c64768d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334323"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy 结构

执行线程的抽象。 如果想要计划程序获得用户模式计划 (UMS) 线程，则将计划程序策略元素 `SchedulerKind` 的值设置为 `UmsThreadDefault`，并实现 `IUMSScheduler` 接口。 UMS 线程仅在具有 Windows 7 或更高版本的 64 位操作系统上受到支持。

## <a name="syntax"></a>语法

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[IUMSThreadProxy：： EnterCriticalRegion](#entercriticalregion)|调用以输入关键区域。 在关键区域内部，计划程序将不会看到在该区域发生的异步阻止操作。 这意味着，计划程序将不会为页错误、线程挂起、内核异步过程调用 (Apc) 等，而对于 UMS 线程，则不会被重新输入。|
|[IUMSThreadProxy：： EnterHyperCriticalRegion](#enterhypercriticalregion)|调用以输入超关键区域。 在超关键区域内时，计划程序将不会观察在该区域发生的任何阻止性操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。|
|[IUMSThreadProxy：： ExitCriticalRegion](#exitcriticalregion)|调用以退出关键区域。|
|[IUMSThreadProxy：： ExitHyperCriticalRegion](#exithypercriticalregion)|调用以退出超关键区域。|
|[IUMSThreadProxy：： GetCriticalRegionType](#getcriticalregiontype)|返回线程代理所在的关键区域类型。 由于超关键区域是关键区域的超集，因此，如果代码已进入关键区域，然后输入了一个超级关键区域，则 `InsideHyperCriticalRegion` 将返回。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a> IUMSThreadProxy：： EnterCriticalRegion 方法

调用以输入关键区域。 在关键区域内部，计划程序将不会看到在该区域发生的异步阻止操作。 这意味着，计划程序将不会为页错误、线程挂起、内核异步过程调用 (Apc) 等，而对于 UMS 线程，则不会被重新输入。

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>返回值

关键区域的新深度。 关键区域是可重入的。

## <a name="iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a> IUMSThreadProxy：： EnterHyperCriticalRegion 方法

调用以输入超关键区域。 在超关键区域内时，计划程序将不会观察在该区域发生的任何阻止性操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>返回值

超关键区域的新深度。 超关键区域是可重入的。

### <a name="remarks"></a>备注

计划程序必须特别注意它所调用的方法以及它在此类区域中获取的锁定。 如果此类区域中的代码在由计划程序负责计划的内容所持有的锁上停滞，则会不幸死锁。

## <a name="iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a> IUMSThreadProxy：： ExitCriticalRegion 方法

调用以退出关键区域。

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>返回值

关键区域的新深度。 关键区域是可重入的。

## <a name="iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a> IUMSThreadProxy：： ExitHyperCriticalRegion 方法

调用以退出超关键区域。

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>返回值

超关键区域的新深度。 超关键区域是可重入的。

## <a name="iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a> IUMSThreadProxy：： GetCriticalRegionType 方法

返回线程代理所在的关键区域类型。 由于超关键区域是关键区域的超集，因此，如果代码已进入关键区域，然后输入了一个超级关键区域，则 `InsideHyperCriticalRegion` 将返回。

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>返回值

线程代理所在的关键区域的类型。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[IUMSScheduler 结构](iumsscheduler-structure.md)

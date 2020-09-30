---
title: ICommandImpl 类
ms.date: 11/04/2016
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
ms.openlocfilehash: 2f2d3938d63e5e67fc501d52d269c06f6b144ac8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501823"
---
# <a name="icommandimpl-class"></a>ICommandImpl 类

提供 [ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85)) 接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>参数

*T*<br/>
派生自的类 `ICommandImpl` 。

*CommandBase*<br/>
命令接口。 默认值为 `ICommand`。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

| 名称 | 说明 |
|-|-|
|[取消](#cancel)|取消当前命令执行。|
|[CancelExecution](#cancelexecution)|取消当前命令执行。|
|[CreateRowset](#createrowset)|创建行集对象。|
|[执行](#execute)|执行命令。|
|[GetDBSession](#getdbsession)|返回一个接口指针，该指针指向创建该命令的会话。|
|[ICommandImpl](#icommandimpl)|构造函数。|

### <a name="data-members"></a>数据成员

| 名称 | 说明 |
|-|-|
|[m_bCancel](#bcancel)|指示是否要取消该命令。|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|指示是否要在执行时取消该命令。|
|[m_bIsExecuting](#bisexecuting)|指示命令当前是否正在执行。|

## <a name="remarks"></a>注解

命令对象的必需接口。

## <a name="icommandimplcancel"></a><a name="cancel"></a> ICommandImpl：： Cancel

取消当前命令执行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>备注

请参阅*OLE DB 程序员参考*中的[ICommand：： Cancel](/previous-versions/windows/desktop/ms714402(v=vs.85)) 。

## <a name="icommandimplcancelexecution"></a><a name="cancelexecution"></a> ICommandImpl：： CancelExecution

取消当前命令执行。

### <a name="syntax"></a>语法

```cpp
HRESULT CancelExecution();
```

## <a name="icommandimplcreaterowset"></a><a name="createrowset"></a> ICommandImpl：： CreateRowset

由 [Execute](#execute) 调用以创建单个行集。

### <a name="syntax"></a>语法

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>参数

*RowsetClass*<br/>
表示用户的行集类的模板类成员。 通常由向导生成。

*pUnkOuter*<br/>
中 `IUnknown` 如果行集作为聚合的一部分创建，则为指向控制接口的指针; 否则为 null。

*riid*<br/>
中对应于中的 *riid* `ICommand::Execute` 。

*pParams*<br/>
[in/out]对应于中的 *pParams* `ICommand::Execute` 。

*pcRowsAffected*<br/>
对应于中的 *pcRowsAffected* `ICommand::Execute` 。

*ppRowset*<br/>
[in/out]对应于中的 *ppRowset* `ICommand::Execute` 。

*pRowsetObj*<br/>
弄指向行集对象的指针。 通常不使用此参数，但如果必须在将其传递给 COM 对象之前对行集执行更多工作，则可以使用此参数。 *PRowsetObj*的生存期由*ppRowset*绑定。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。 `ICommand::Execute`有关典型值的列表，请参阅。

### <a name="remarks"></a>注解

若要创建多个行集，或提供自己的条件来创建不同的行集，请在中对进行不同 `CreateRowset` 的调用 `Execute` 。

请参阅*OLE DB 程序员参考*中的[ICommand：： Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 。

## <a name="icommandimplexecute"></a><a name="execute"></a> ICommandImpl：： Execute

执行命令。

### <a name="syntax"></a>语法

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[ICommand：： Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 。

### <a name="remarks"></a>注解

请求的传出接口将是从该函数创建的行集对象获取的接口。

`Execute` 调用 [CreateRowset](#createrowset)。 重写默认实现以创建多个行集，或提供自己的条件来创建不同的行集。

## <a name="icommandimplgetdbsession"></a><a name="getdbsession"></a> ICommandImpl：： GetDBSession

返回一个接口指针，该指针指向创建该命令的会话。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[ICommand：： GetDBSession](/previous-versions/windows/desktop/ms719622(v=vs.85)) 。

### <a name="remarks"></a>注解

对于从会话中检索属性很有用。

## <a name="icommandimplicommandimpl"></a><a name="icommandimpl"></a> ICommandImpl：： ICommandImpl

构造函数。

### <a name="syntax"></a>语法

```cpp
ICommandImpl();
```

## <a name="icommandimplm_bcancel"></a><a name="bcancel"></a> ICommandImpl：： m_bCancel

指示是否取消该命令。

### <a name="syntax"></a>语法

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>备注

可以在 command 类的方法中检索此变量 `Execute` ，并根据需要取消。

## <a name="icommandimplm_bcancelwhenexecuting"></a><a name="bcancelwhenexecuting"></a> ICommandImpl：： m_bCancelWhenExecuting

指示在执行时是否可以取消该命令。

### <a name="syntax"></a>语法

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>备注

默认值为 **`true`** 可) 取消 (。

## <a name="icommandimplm_bisexecuting"></a><a name="bisexecuting"></a> ICommandImpl：： m_bIsExecuting

指示命令当前是否正在执行。

### <a name="syntax"></a>语法

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>备注

`Execute`Command 类的方法可以将此变量设置为 **`true`** 。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)

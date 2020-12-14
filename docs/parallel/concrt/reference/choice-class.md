---
description: 了解详细信息： choice 类
title: choice 类
ms.date: 11/04/2016
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
ms.openlocfilehash: a7597a3bd530185e316cdc42ebbc4696162d498f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254464"
---
# <a name="choice-class"></a>choice 类

`choice` 消息块是多源、单目标的块，表示与一组源进行的控制流交互。 choice 块将等待多个源中的任何一个源以生成消息，并将传播生成该消息的源的索引。

## <a name="syntax"></a>语法

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>parameters

*T*<br/>
一个 `tuple` 基于的类型，表示输入源的负载。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`type`|的类型别名 `T` 。|

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[choice](#ctor)|已重载。 构造 `choice` 消息块。|
|[~ choice 析构函数](#dtor)|销毁 `choice` 消息块。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[接受](#accept)|接受此块提供的消息 `choice` ，并将所有权转移到调用方。|
|[acquire_ref](#acquire_ref)|获取此消息块上的引用计数 `choice` ，以防止删除。|
|[接受](#consume)|使用以前由此消息块提供的消息 `choice` ，并通过目标成功保留该消息，并将所有权转移给调用方。|
|[has_value](#has_value)|检查是否已 `choice` 使用值初始化此消息块。|
|[索引](#index)|返回 `tuple` 表示消息块所选元素的索引 `choice` 。|
|[link_target](#link_target)|将目标块链接到此 `choice` 消息块。|
|[拆卸](#release)|释放以前成功的消息保留。|
|[release_ref](#release_ref)|释放此消息块上的引用计数 `choice` 。|
|[保留](#reserve)|保留此消息块先前提供的消息 `choice` 。|
|[unlink_target](#unlink_target)|将目标块与此 `choice` 消息块断开。|
|[unlink_targets](#unlink_targets)|从此消息块取消所有目标的 `choice` 锁定。  (重写 [ISource：： unlink_targets](isource-class.md#unlink_targets)。 ) |
|[value](#value)|获取消息块已选择其索引的消息 `choice` 。|

## <a name="remarks"></a>备注

选择块可确保仅使用其中一个传入消息。

有关详细信息，请参阅 [异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept"></a><a name="accept"></a> 接受

接受此块提供的消息 `choice` ，并将所有权转移到调用方。

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>parameters

*_MsgId*<br/>
`runtime_object_identity`所提供的 `message` 对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `accept` 。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的消息的指针。

## <a name="acquire_ref"></a><a name="acquire_ref"></a> acquire_ref

获取此消息块上的引用计数 `choice` ，以防止删除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>parameters

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由在 `ITarget` 方法中链接到此源的对象调用 `link_target` 。

## <a name="choice"></a><a name="ctor"></a> 选择

构造 `choice` 消息块。

```cpp
explicit choice(
    T _Tuple);

choice(
    Scheduler& _PScheduler,
    T _Tuple);

choice(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

choice(
    choice&& _Choice);
```

### <a name="parameters"></a>parameters

*_Tuple*<br/>
choice 的源的 `tuple` 。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `choice` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `choice` 对象。 所用 `Scheduler` 对象由该计划组提示。

*_Choice*<br/>
要从中进行复制的 `choice` 消息块。 请注意原始对象是孤立的，使之成为一个移动构造函数。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

在锁定状态下不执行移动构造，这意味着应由用户确保在移动期间没有轻量任务处于飞行状态。 否则可能会发生大量争用，从而导致异常或不一致的状态。

## <a name="choice"></a><a name="dtor"></a> ~ choice

销毁 `choice` 消息块。

```cpp
~choice();
```

## <a name="consume"></a><a name="consume"></a> 接受

使用以前由此消息块提供的消息 `choice` ，并通过目标成功保留该消息，并将所有权转移给调用方。

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>parameters

*_MsgId*<br/>
`runtime_object_identity`保留 `message` 对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `consume` 。

### <a name="return-value"></a>返回值

指向 `message` 调用方现在具有所有权的对象的指针。

### <a name="remarks"></a>备注

此 `consume` 方法类似于 `accept` ，但必须始终在之前调用 `reserve` 返回的 **`true`** 。

## <a name="has_value"></a><a name="has_value"></a> has_value

检查是否已 `choice` 使用值初始化此消息块。

```cpp
bool has_value() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果块接收了值，则 **`false`** 为; 否则为。

## <a name="index"></a><a name="index"></a> 编入

返回 `tuple` 表示消息块所选元素的索引 `choice` 。

```cpp
size_t index();
```

### <a name="return-value"></a>返回值

消息索引。

### <a name="remarks"></a>备注

可以使用方法提取消息有效负载 `get` 。

## <a name="link_target"></a><a name="link_target"></a> link_target

将目标块链接到此 `choice` 消息块。

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>parameters

*_PTarget*<br/>
指向 `ITarget` 链接到此消息块的块的指针 `choice` 。

## <a name="release"></a><a name="release"></a> 拆卸

释放以前成功的消息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>parameters

*_MsgId*<br/>
`runtime_object_identity` `message` 要释放的对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `release` 。

## <a name="release_ref"></a><a name="release_ref"></a> release_ref

释放此消息块上的引用计数 `choice` 。

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>parameters

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由 `ITarget` 正在从此源取消链接的对象调用。 允许源块释放为目标块保留的任何资源。

## <a name="reserve"></a><a name="reserve"></a> 保留

保留此消息块先前提供的消息 `choice` 。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>parameters

*_MsgId*<br/>
`runtime_object_identity` `message` 保留的对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `reserve` 。

### <a name="return-value"></a>返回值

**`true`** 如果消息已成功保留，则 **`false`** 为; 否则为。 预留可能因为众多原因失败，包括：消息已预留或已由另一目标接受，源可能拒绝预留等。

### <a name="remarks"></a>备注

调用后 `reserve` ，如果成功，则必须调用或，才能 `consume` `release` 分别获取或放弃消息的所有权。

## <a name="unlink_target"></a><a name="unlink_target"></a> unlink_target

将目标块与此 `choice` 消息块断开。

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>parameters

*_PTarget*<br/>
指向 `ITarget` 要从此消息块断开链接的块的指针 `choice` 。

## <a name="unlink_targets"></a><a name="unlink_targets"></a> unlink_targets

从此消息块取消所有目标的 `choice` 锁定。

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>备注

不需要从析构函数中调用此方法，因为内部块的析构函数 `single_assignment` 会正确取消链接。

## <a name="value"></a><a name="value"></a> 值

获取消息块已选择其索引的消息 `choice` 。

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>parameters

*_Payload_type*<br/>
消息负载的类型。

### <a name="return-value"></a>返回值

消息的负载。

### <a name="remarks"></a>备注

因为 `choice` 消息块可以采用不同负载类型的输入，您必须指定检索时的负载类型。 您可以根据方法的结果确定类型 `index` 。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[联接类](join-class.md)<br/>
[single_assignment 类](single-assignment-class.md)

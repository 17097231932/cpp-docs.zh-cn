---
description: 了解详细信息： message_processor 类
title: message_processor 类
ms.date: 11/04/2016
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
ms.openlocfilehash: f74314bde6e12ea8b00bfc7bfd2567ca15864f75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202192"
---
# <a name="message_processor-class"></a>message_processor 类

`message_processor` 类是用于处理 `message` 对象的抽象基类。 不能保证消息的排序。

## <a name="syntax"></a>语法

```cpp
template<class T>
class message_processor;
```

### <a name="parameters"></a>parameters

*T*<br/>
此对象处理的消息内有效负载的数据类型 `message_processor` 。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`type`|的类型别名 `T` 。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[async_send](#async_send)|当在派生类中重写时，以异步方式将消息放置到块中。|
|[sync_send](#sync_send)|当在派生类中重写时，以同步方式将消息放入块。|
|[wait](#wait)|当在派生类中重写时，等待所有异步操作完成。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|当在派生类中被重写时，执行将消息转发到块的过程。 每次添加新消息并发现队列为空时调用一次。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`message_processor`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="async_send"></a><a name="async_send"></a> async_send

当在派生类中重写时，以异步方式将消息放置到块中。

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>parameters

*_Msg*<br/>
`message`要异步发送的对象。

### <a name="remarks"></a>备注

处理器实现应重写此方法。

## <a name="process_incoming_message"></a><a name="process_incoming_message"></a> process_incoming_message

当在派生类中被重写时，执行将消息转发到块的过程。 每次添加新消息并发现队列为空时调用一次。

```cpp
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>备注

消息块实现应重写此方法。

## <a name="sync_send"></a><a name="sync_send"></a> sync_send

当在派生类中重写时，以同步方式将消息放入块。

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>parameters

*_Msg*<br/>
`message`要同步发送的对象。

### <a name="remarks"></a>备注

处理器实现应重写此方法。

## <a name="wait"></a><a name="wait"></a> 再

当在派生类中重写时，等待所有异步操作完成。

```cpp
virtual void wait() = 0;
```

### <a name="remarks"></a>备注

处理器实现应重写此方法。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ordered_message_processor 类](ordered-message-processor-class.md)

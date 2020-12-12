---
description: 了解详细信息： message_not_found 类
title: message_not_found 类
ms.date: 11/04/2016
f1_keywords:
- message_not_found
- CONCRT/concurrency::message_not_found
- CONCRT/concurrency::message_not_found::message_not_found
helpviewer_keywords:
- message_not_found class
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
ms.openlocfilehash: c0b098a530768617b2fa2cf52dfe374dc44a2c12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169380"
---
# <a name="message_not_found-class"></a>message_not_found 类

此类描述消息块找不到请求的消息时引发的异常。

## <a name="syntax"></a>语法

```cpp
class message_not_found : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[message_not_found](#ctor)|已重载。 构造 `message_not_found` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`message_not_found`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="message_not_found"></a><a name="ctor"></a> message_not_found

构造 `message_not_found` 对象。

```cpp
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>parameters

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)

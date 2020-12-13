---
description: 了解详细信息： invalid_scheduler_policy_key 类
title: invalid_scheduler_policy_key 类
ms.date: 11/04/2016
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
ms.openlocfilehash: d352246cf0fe94f0ba5ee567f353680c89efcddc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334515"
---
# <a name="invalid_scheduler_policy_key-class"></a>invalid_scheduler_policy_key 类

此类描述无效或未知键传递给 `SchedulerPolicy` 对象构造函数，或 `SchedulerPolicy` 对象的 `SetPolicyValue` 方法被传递了必须使用其他方式（例如 `SetConcurrencyLimits` 方法）进行更改的键时引发的异常。

## <a name="syntax"></a>语法

```cpp
class invalid_scheduler_policy_key : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[invalid_scheduler_policy_key](#ctor)|已重载。 构造 `invalid_scheduler_policy_key` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_scheduler_policy_key`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="invalid_scheduler_policy_key"></a><a name="ctor"></a> invalid_scheduler_policy_key

构造 `invalid_scheduler_policy_key` 对象。

```cpp
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```

### <a name="parameters"></a>parameters

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[SchedulerPolicy 类](schedulerpolicy-class.md)

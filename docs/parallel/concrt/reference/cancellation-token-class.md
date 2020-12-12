---
description: 了解详细信息： cancellation_token 类
title: cancellation_token 类
ms.date: 11/04/2016
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
ms.openlocfilehash: 3f97d0f6e55f06b4b75b22cc1ae6eefa05b50f85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172188"
---
# <a name="cancellation_token-class"></a>cancellation_token 类

`cancellation_token` 类表示确定某项操作是否已请求取消的功能。 给定的标记可与 `task_group`、`structured_task_group` 或 `task` 关联以实现隐式取消。 它还可为了取消而进行轮询，或可在取消关联的 `cancellation_token_source` 时注册回调。

## <a name="syntax"></a>语法

```cpp
class cancellation_token;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[cancellation_token](#ctor)||
|[~ cancellation_token 析构函数](#dtor)||

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|通过 `register` 方法基于注册时返回的 `cancellation_token_registration` 对象移除之前注册的回调。|
|[is_cancelable](#is_cancelable)|返回有关此标记是否可取消的指示。|
|[is_canceled](#is_canceled)|**`true`** 如果标记已取消，则返回。|
|[无](#none)|返回一个取消标记，此标记绝不会受到取消。|
|[register_callback](#register_callback)|使用标记注册一个回调函数。 取消该标记时，将进行回调。 请注意，如果在调用此方法时已删除此标记，则将立即同步进行回调。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator！ =](#operator_neq)||
|[operator =](#operator_eq)||
|[operator = =](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`cancellation_token`

## <a name="requirements"></a>要求

**标头：** pplcancellation_token。h

**命名空间：** 并发

## <a name="cancellation_token"></a><a name="dtor"></a> ~ cancellation_token

```cpp
~cancellation_token();
```

## <a name="cancellation_token"></a><a name="ctor"></a> cancellation_token

```cpp
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>parameters

*_Src*<br/>
要复制或移动的 cancellation_token。

## <a name="deregister_callback"></a><a name="deregister_callback"></a> deregister_callback

通过 `register` 方法基于注册时返回的 `cancellation_token_registration` 对象移除之前注册的回调。

```cpp
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>parameters

*_Registration*<br/>
与将取消注册的回调对应的 `cancellation_token_registration` 对象。 此标记必须先前已从对 `register` 的调用中返回。

## <a name="is_cancelable"></a><a name="is_cancelable"></a> is_cancelable

返回有关此标记是否可取消的指示。

```cpp
bool is_cancelable() const;
```

### <a name="return-value"></a>返回值

有关此标记是否可以取消的指示。

## <a name="is_canceled"></a><a name="is_canceled"></a> is_canceled

**`true`** 如果标记已取消，则返回。

```cpp
bool is_canceled() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果标记已取消，则为值; 否则为值 **`false`** 。

## <a name="none"></a><a name="none"></a> 内容

返回一个取消标记，此标记绝不会受到取消。

```cpp
static cancellation_token none();
```

### <a name="return-value"></a>返回值

无法取消的取消标记。

## <a name="operator"></a><a name="operator_neq"></a> operator！ =

```cpp
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>parameters

*_Src*<br/>
要比较的 `cancellation_token`。

### <a name="return-value"></a>返回值

## <a name="operator"></a><a name="operator_eq"></a> operator =

```cpp
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>parameters

*_Src*<br/>
`cancellation_token`要分配的。

### <a name="return-value"></a>返回值

## <a name="operator"></a><a name="operator_eq_eq"></a> operator = =

```cpp
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>parameters

*_Src*<br/>
要比较的 `cancellation_token`。

### <a name="return-value"></a>返回值

## <a name="register_callback"></a><a name="register_callback"></a> register_callback

使用标记注册一个回调函数。 取消该标记时，将进行回调。 请注意，如果在调用此方法时已删除此标记，则将立即同步进行回调。

```cpp
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>parameters

*_Function*<br/>
取消此 `cancellation_token` 时将回调的函数对象的类型。

*_Func*<br/>
取消此 `cancellation_token` 时将回调的函数对象。

### <a name="return-value"></a>返回值

可在 `cancellation_token_registration` 方法中用于取消注册之前注册的回调并防止进行该回调的 `deregister` 对象。 如果在[](invalid-operation-class.md) `cancellation_token` 使用[cancellation_token：： none](#none)方法创建的对象上调用，则该方法将引发 invalid_operation 异常。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)

---
description: 了解详细信息： concurrent_priority_queue 类
title: concurrent_priority_queue 类
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 6097e8f3bdb56ed792509460349bba8f9aef25a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329870"
---
# <a name="concurrent_priority_queue-class"></a>concurrent_priority_queue 类

`concurrent_priority_queue` 类是允许多个线程并发推送和弹出项的容器。 项按优先级顺序弹出，其中优先级由作为模板参数提供的涵子确定。

## <a name="syntax"></a>语法

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>parameters

*T*<br/>
要存储在优先级队列中的元素的数据类型。

*_Compare*<br/>
可将两个元素的值作为排序键进行比较以确定其在优先级队列中相对顺序的函数对象的类型。 此参数为可选自变量，默认值是二元谓词 `less<T>`。

*_Ax*<br/>
一种表示存储的分配器对象的类型，该分配器对象封装有关并发优先级队列的内存分配和解除分配的详细信息。 此参数为可选参数，默认值为 `allocator<T>`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`allocator_type`|一种表示适用于并发优先级队列的分配器类的类型。|
|`const_reference`|一种表示存储在并发优先级队列中类型的一个元素的常量引用的类型。|
|`reference`|一种表示存储在并发优先级队列中类型的一个元素的引用的类型。|
|`size_type`|一种计算并发优先级队列中元素数量的类型。|
|`value_type`|一种表示存储在并发优先级队列中的数据类型的类型。|

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|已重载。 构造并发优先级队列。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[clear](#clear)|清除并发优先级中的所有元素。 此方法不是并发安全方法。|
|[empty](#empty)|测试在调用此方法时并发优先级队列是否为空。 此方法是并发安全方法。|
|[get_allocator](#get_allocator)|返回用于构造并发优先级队列的分配器的副本。 此方法是并发安全方法。|
|[push](#push)|已重载。 在并发优先级队列中添加一个元素。 此方法是并发安全方法。|
|[大小](#size)|返回并发优先级队列中元素的数量。 此方法是并发安全方法。|
|[swap](#swap)|交换两个并发优先级队列中的内容。 此方法不是并发安全方法。|
|[try_pop](#try_pop)|如果队列非空，移除并返回队列中优先级最高的元素。 此方法是并发安全方法。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator =](#operator_eq)|已重载。 将另一个对象的内容分配 `concurrent_priority_queue` 给此对象。 此方法不是并发安全方法。|

## <a name="remarks"></a>备注

有关类的详细信息 `concurrent_priority_queue` ，请参阅 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`concurrent_priority_queue`

## <a name="requirements"></a>要求

**标头：** concurrent_priority_queue。h

**命名空间：** 并发

## <a name="clear"></a><a name="clear"></a> 清除

清除并发优先级中的所有元素。 此方法不是并发安全方法。

```cpp
void clear();
```

### <a name="remarks"></a>备注

`clear` 不是并发安全的。 调用此方法时，必须确保没有其他线程在并发优先级队列中调用方法。 `clear` 不释放内存。

## <a name="concurrent_priority_queue"></a><a name="ctor"></a> concurrent_priority_queue

构造并发优先级队列。

```cpp
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```

### <a name="parameters"></a>parameters

*_InputIterator*<br/>
输入迭代器的类型。

*_Al*<br/>
要用于此对象的分配器类。

*_Init_capacity*<br/>
`concurrent_priority_queue` 对象的初始容量。

*_Begin*<br/>
要复制的范围元素中的第一个元素的位置。

*_End*<br/>
要复制的元素范围以外的第一个元素的位置。

*_Src*<br/>
要从中复制或移动元素的源 `concurrent_priority_queue` 对象。

### <a name="remarks"></a>备注

所有构造函数都存储分配器对象 `_Al` 并初始化优先级队列。

第一个构造函数指定一个空的初始优先级队列，并根据需要指定分配器。

第二个构造函数指定具有初始容量的优先级队列 `_Init_capacity` ，并根据需要指定分配器。

第三个构造函数指定迭代器范围 [，) 提供的值 `_Begin` `_End` ，并根据需要指定分配器。

第四个和第五个构造函数指定优先级队列的副本 `_Src` 。

第六个和第七个构造函数指定优先级队列的移动 `_Src` 。

## <a name="empty"></a><a name="empty"></a> 空白处

测试在调用此方法时并发优先级队列是否为空。 此方法是并发安全方法。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果在调用函数时优先级队列为空，则 **`false`** 为; 否则为。

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

返回用于构造并发优先级队列的分配器的副本。 此方法是并发安全方法。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

用于构造对象的分配器副本 `concurrent_priority_queue` 。

## <a name="operator"></a><a name="operator_eq"></a> operator =

将另一个对象的内容分配 `concurrent_priority_queue` 给此对象。 此方法不是并发安全方法。

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>parameters

*_Src*<br/>
源 `concurrent_priority_queue` 对象。

### <a name="return-value"></a>返回值

对此对象的引用 `concurrent_priority_queue` 。

## <a name="push"></a><a name="push"></a> 请求

在并发优先级队列中添加一个元素。 此方法是并发安全方法。

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>parameters

*_Elem*<br/>
要添加到并发优先级队列中的元素。

## <a name="size"></a><a name="size"></a> 规格

返回并发优先级队列中元素的数量。 此方法是并发安全方法。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

此对象中的元素数 `concurrent_priority_queue` 。

### <a name="remarks"></a>备注

返回的大小保证包含通过调用函数添加的所有元素 `push` 。 但是，它可能不会反映挂起的并发操作的结果。

## <a name="swap"></a><a name="swap"></a> 购

交换两个并发优先级队列中的内容。 此方法不是并发安全方法。

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>parameters

*_Queue*<br/>
要与其交换内容的 `concurrent_priority_queue` 对象。

## <a name="try_pop"></a><a name="try_pop"></a> try_pop

如果队列非空，移除并返回队列中优先级最高的元素。 此方法是并发安全方法。

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>parameters

*_Elem*<br/>
如果队列非空，则为将使用最高优先级元素填充的变量的引用。

### <a name="return-value"></a>返回值

**`true`** 如果弹出了某个值，则 **`false`** 为; 否则为。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)

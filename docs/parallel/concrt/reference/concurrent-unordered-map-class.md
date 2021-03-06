---
description: 了解详细信息： concurrent_unordered_map 类
title: concurrent_unordered_map 类
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::at
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
ms.openlocfilehash: fb1c5c6dd35a1f1a79ea2988bbc2a33f1fb40058
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284883"
---
# <a name="concurrent_unordered_map-class"></a>concurrent_unordered_map 类

`concurrent_unordered_map` 类是控制 `std::pair<const K, _Element_type>` 类型元素的长短不一序列的并发安全容器。 序列以支持并发安全追加、元素访问、迭代器访问和迭代器遍历操作的方式表示。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。

## <a name="syntax"></a>语法

```cpp
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
details::_Hash_compare<K,
    _Hasher,
key_equality>,
    _Allocator_type,
false>>;
```

### <a name="parameters"></a>parameters

*K*<br/>
键类型。

*_Element_type*<br/>
映射类型。

*_Hasher*<br/>
哈希函数对象类型。 此参数为可选参数，默认值为 `std::hash<K>`。

*key_equality*<br/>
相等比较函数对象类型。 此参数为可选参数，默认值为 `std::equal_to<K>`。

*_Allocator_type*<br/>
表示存储分配器对象的类型，该对象封装有关并发无序映射的内存分配和解除分配的详细信息。 此参数是可选的，默认值为 `std::allocator<std::pair<K` ， `_Element_type>>` 。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`allocator_type`|用于管理存储的分配器的类型。|
|`const_iterator`|受控序列的常量迭代器的类型。|
|`const_local_iterator`|受控序列的常量存储桶迭代器的类型。|
|`const_pointer`|元素的常量指针的类型。|
|`const_reference`|元素的常量引用的类型。|
|`difference_type`|两个元素间的带符号距离的类型。|
|`hasher`|哈希函数的类型。|
|`iterator`|受控序列的迭代器的类型。|
|`key_equal`|比较函数的类型。|
|`key_type`|排序键的类型。|
|`local_iterator`|受控序列的存储桶迭代器的类型。|
|`mapped_type`|与每个键关联的映射值的类型。|
|`pointer`|指向元素的指针的类型。|
|`reference`|元素的引用的类型。|
|`size_type`|两个元素间的无符号距离的类型。|
|`value_type`|元素的类型。|

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[concurrent_unordered_map](#ctor)|已重载。 构造并发的无序映射。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[at](#at)|已重载。 在中查找 `concurrent_unordered_map` 具有指定键值的元素。 此方法是并发安全方法。|
|[hash_function](#hash_function)|获取存储的哈希函数对象。|
|[insert](#insert)|已重载。 向对象中添加元素 `concurrent_unordered_map` 。|
|[key_eq](#key_eq)|获取存储的相等比较函数对象。|
|[swap](#swap)|交换两个 `concurrent_unordered_map` 对象的内容。 此方法不是并发安全方法。|
|[unsafe_erase](#unsafe_erase)|已重载。 从中移除 `concurrent_unordered_map` 位于指定位置的元素。 此方法不是并发安全方法。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[操作员\[\]](#operator_at)|已重载。 查找或插入具有指定键的元素。 此方法是并发安全方法。|
|[operator =](#operator_eq)|已重载。 将另一个对象的内容分配 `concurrent_unordered_map` 给此对象。 此方法不是并发安全方法。|

## <a name="remarks"></a>备注

有关类的详细信息 `concurrent_unordered_map` ，请参阅 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_map`

## <a name="requirements"></a>要求

**标头：** concurrent_unordered_map。h

**命名空间：** 并发

## <a name="at"></a><a name="at"></a> 最

在中查找 `concurrent_unordered_map` 具有指定键值的元素。 此方法是并发安全方法。

```cpp
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```

### <a name="parameters"></a>parameters

*KVal*<br/>
要查找的键值。

### <a name="return-value"></a>返回值

对找到的元素数据值的引用。

### <a name="remarks"></a>备注

如果未找到自变量键值，函数将引发类 `out_of_range` 的对象。

## <a name="begin"></a><a name="begin"></a> begin

返回一个迭代器，该迭代器指向并发容器中的第一个元素。 此方法是并发安全方法。

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>返回值

指向并发容器中第一个元素的迭代器。

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

返回一个常量迭代器，该迭代器指向并发容器中的第一个元素。 此方法是并发安全方法。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

并发容器中第一个元素的常量迭代器。

## <a name="cend"></a><a name="cend"></a> cend

返回一个常量迭代器，该迭代器指向并发容器中最后一个元素之后的位置。 此方法是并发安全方法。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

指向并发容器中最后一个元素之后的位置的常量迭代器。

## <a name="clear"></a><a name="clear"></a> 清除

清除并发容器中的所有元素。 此函数不是并发安全函数。

```cpp
void clear();
```

## <a name="concurrent_unordered_map"></a><a name="ctor"></a> concurrent_unordered_map

构造并发的无序映射。

```cpp
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>parameters

*_Iterator*<br/>
输入迭代器的类型。

*_Number_of_buckets*<br/>
此无序映射的初始存储桶数。

*_Hasher*<br/>
此无序映射的哈希函数。

*key_equality*<br/>
此无序映射的相等性比较函数。

*_Allocator*<br/>
此无序映射的分配器。

*_Begin*<br/>
要复制的范围元素中的第一个元素的位置。

*_End*<br/>
要复制的元素范围以外的第一个元素的位置。

*_Umap*<br/>
要从中复制或移动元素的源 `concurrent_unordered_map` 对象。

### <a name="remarks"></a>备注

所有构造函数都会存储一个分配器对象 `_Allocator` 并初始化无序映射。

第一个构造函数指定一个空的初始映射，并显式指定要使用的存储桶的数量、哈希函数、相等性比较函数和分配器类型。

第二个构造函数指定无序映射的分配器。

第三个构造函数指定迭代器范围 [，) 提供的值 `_Begin` `_End` 。

第四个和第五个构造函数指定并发无序映射 `_Umap` 的副本。

最后一个构造函数指定并发无序映射 `_Umap`的移动。

## <a name="count"></a><a name="count"></a> 计

计算与指定键匹配的元素的数目。 此函数是并发安全函数。

```cpp
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>parameters

*KVal*<br/>
要搜索的键。

### <a name="return-value"></a>返回值

键在容器中出现的次数。

## <a name="empty"></a><a name="empty"></a> 空白处

测试元素是否存在。 此方法是并发安全方法。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果并发容器为空，则为 **`false`** ; 否则为。

### <a name="remarks"></a>备注

在出现并发插入时，无论并发容器是否为空，在调用此函数后，甚至在读取返回值之前都可能会立即更改。

## <a name="end"></a><a name="end"></a> end

返回一个迭代器，该迭代器指向并发容器中最后一个元素之后的位置。 此方法是并发安全方法。

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>返回值

指向并发容器中最后一个元素之后的位置的迭代器。

## <a name="equal_range"></a><a name="equal_range"></a> equal_range

查找与指定键匹配的范围。 此函数是并发安全函数。

```cpp
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>parameters

*KVal*<br/>
要搜索的键值。

### <a name="return-value"></a>返回值

一 [对](../../../standard-library/pair-structure.md) ，其中第一个元素是开始迭代器，第二个元素是指向范围末尾的迭代器。

### <a name="remarks"></a>备注

并发插入可能会导致在开始迭代器之后以及结束迭代器之前插入额外的键。

## <a name="find"></a><a name="find"></a> 查找

查找与指定键匹配的元素。 此函数是并发安全函数。

```cpp
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>parameters

*KVal*<br/>
要搜索的键值。

### <a name="return-value"></a>返回值

一个迭代器，该迭代器指向与所提供的键相匹配的第一个元素的位置， `end()` 如果此类元素不存在，则为迭代器。

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

返回此并发容器的存储分配器对象。 此方法是并发安全方法。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

此并发容器的存储分配器对象。

## <a name="hash_function"></a><a name="hash_function"></a> hash_function

获取存储的哈希函数对象。

```cpp
hasher hash_function() const;
```

### <a name="return-value"></a>返回值

存储的哈希函数对象。

## <a name="insert"></a><a name="insert"></a> &

向对象中添加元素 `concurrent_unordered_map` 。

```cpp
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>parameters

*_Iterator*<br/>
用于插入的迭代器类型。

*V*<br/>
插入到映射中的值的类型。

*value*<br/>
要插入的值。

*_Where*<br/>
搜索插入点的起始位置。

*first*<br/>
要插入的范围的开始处。

*last*<br/>
要插入的范围的结尾处。

### <a name="return-value"></a>返回值

一个包含迭代器和一个布尔值的对。 有关更多详细信息，请参阅“备注”部分。

### <a name="remarks"></a>备注

第一个成员函数确定元素 X 是否存在于其键具有等效顺序的序列中 `value` 。 否则，它将创建此类元素 X，并使用对其进行初始化 `value` 。 然后，该函数确定指定 X 的迭代器 `where` 。如果发生插入，则函数返回 `std::pair(where, true)` 。 否则，它将返回 `std::pair(where, false)`。

第二个成员函数返回 insert ( `value`) ，使用 `_Where` 作为受控序列中的开始位置来搜索插入点。

第三个成员函数从 [，) 范围内插入元素值 `first` 序列 `last` 。

最后两个成员函数与前两个成员函数的行为相同，除了 `value` 用于构造插入值外。

## <a name="key_eq"></a><a name="key_eq"></a> key_eq

获取存储的相等比较函数对象。

```cpp
key_equal key_eq() const;
```

### <a name="return-value"></a>返回值

存储的相等比较函数对象。

## <a name="load_factor"></a><a name="load_factor"></a> load_factor

计算并返回容器的当前加载因子。 加载因子是容器中的元素数除以 bucket 数。

```cpp
float load_factor() const;
```

### <a name="return-value"></a>返回值

容器的加载因子。

## <a name="max_load_factor"></a><a name="max_load_factor"></a> max_load_factor

获取或设置容器的最大加载因子。 最大加载因子是在容器增长其内部表之前，在任何存储桶中都可以有的元素的最大数目。

```cpp
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>parameters

`_Newmax`

### <a name="return-value"></a>返回值

第一个成员函数将返回存储的最大加载因子。 第二个成员函数不返回值，但如果提供的加载因子无效，则会引发 [out_of_range](../../../standard-library/out-of-range-class.md) 异常。

## <a name="max_size"></a><a name="max_size"></a> max_size

返回由分配器确定的并发容器的最大大小。 此方法是并发安全方法。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>返回值

可插入此并发容器中的元素的最大数目。

### <a name="remarks"></a>备注

此上限值实际上可能比容器实际保存的值高。

## <a name="operator"></a><a name="operator_at"></a> operator[]

查找或插入具有指定键的元素。 此方法是并发安全方法。

```cpp
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```

### <a name="parameters"></a>parameters

*KVal*<br/>
要

查找或插入的键值。

### <a name="return-value"></a>返回值

对找到或插入的元素数据值的引用。

### <a name="remarks"></a>备注

如果未找到自变量键值，则它将与数据类型的默认值一起插入。

`operator[]` 可用于将元素插入使用 `m`（其中 `m[key] = DataValue;` 是具有键值 `DataValue` 的元素 `mapped_type` 的值）的映射 `key`。

使用 `operator[]` 插入元素时，返回的引用不指示插入是更改预先存在的元素还是创建一个新元素。 成员函数 `find` 和 [insert](#insert) 可用于确定具有指定键的元素在插入前是否已存在。

## <a name="operator"></a><a name="operator_eq"></a> operator =

将另一个对象的内容分配 `concurrent_unordered_map` 给此对象。 此方法不是并发安全方法。

```cpp
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>parameters

*_Umap*<br/>
源 `concurrent_unordered_map` 对象。

### <a name="return-value"></a>返回值

对此对象的引用 `concurrent_unordered_map` 。

### <a name="remarks"></a>备注

在清除并发向量中的所有现有元素后，`operator=` 会将 `_Umap` 的内容复制或移动到此并发向量中。

## <a name="rehash"></a><a name="rehash"></a> rehash

重新生成哈希表。

```cpp
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>parameters

*_Buckets*<br/>
所需的存储桶数。

### <a name="remarks"></a>备注

成员函数将存储桶数更改为至少 `_Buckets` 并根据需要重新生成哈希表。 存储桶的数目必须是2的幂。 如果不是2的幂，则它将向上舍入到2的下一个最大的幂。

如果存储桶的数量无效 (0 或大于 bucket) 的最大数目，则会引发 [out_of_range](../../../standard-library/out-of-range-class.md) 异常。

## <a name="size"></a><a name="size"></a> 规格

返回此并发容器中的元素数量。 此方法是并发安全方法。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

容器中的项数。

### <a name="remarks"></a>备注

在存在并发插入时，并发容器中的元素数量可能会在调用此函数后立即更改，甚至会在读取返回值之前。

## <a name="swap"></a><a name="swap"></a> 购

交换两个 `concurrent_unordered_map` 对象的内容。 此方法不是并发安全方法。

```cpp
void swap(concurrent_unordered_map& _Umap);
```

### <a name="parameters"></a>parameters

*_Umap*<br/>
要交换的 `concurrent_unordered_map` 对象。

## <a name="unsafe_begin"></a><a name="unsafe_begin"></a> unsafe_begin

返回一个迭代器，该迭代器指向特定 bucket 的此容器中的第一个元素。

```cpp
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>parameters

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>返回值

指向 bucket 开头的迭代器。

## <a name="unsafe_bucket"></a><a name="unsafe_bucket"></a> unsafe_bucket

返回特定键在此容器中映射到的 bucket 索引。

```cpp
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>parameters

*KVal*<br/>
要搜索的元素键。

### <a name="return-value"></a>返回值

此容器中的密钥的 bucket 索引。

## <a name="unsafe_bucket_count"></a><a name="unsafe_bucket_count"></a> unsafe_bucket_count

返回此容器中的当前 bucket 数。

```cpp
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>返回值

此容器中的当前 bucket 数。

## <a name="unsafe_bucket_size"></a><a name="unsafe_bucket_size"></a> unsafe_bucket_size

返回此容器的特定存储桶中的项数。

```cpp
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>parameters

*_Bucket*<br/>
要搜索的存储桶。

### <a name="return-value"></a>返回值

此容器中的当前 bucket 数。

## <a name="unsafe_cbegin"></a><a name="unsafe_cbegin"></a> unsafe_cbegin

返回一个迭代器，该迭代器指向特定 bucket 的此容器中的第一个元素。

```cpp
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>parameters

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>返回值

指向 bucket 开头的迭代器。

## <a name="unsafe_cend"></a><a name="unsafe_cend"></a> unsafe_cend

返回一个迭代器，该迭代器指向特定存储桶中最后一个元素之后的位置。

```cpp
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>parameters

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>返回值

指向 bucket 开头的迭代器。

## <a name="unsafe_end"></a><a name="unsafe_end"></a> unsafe_end

返回一个迭代器，该迭代器指向特定 bucket 的此容器中的最后一个元素。

```cpp
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>parameters

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>返回值

指向 bucket 末尾的迭代器。

## <a name="unsafe_erase"></a><a name="unsafe_erase"></a> unsafe_erase

从中移除 `concurrent_unordered_map` 位于指定位置的元素。 此方法不是并发安全方法。

```cpp
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```

### <a name="parameters"></a>parameters

*_Where*<br/>
要从中拭除的迭代器位置。

*_Begin*<br/>
要消除的元素范围中第一个元素的位置。

*_End*<br/>
要消除的元素范围之外的第一个元素的位置。

*KVal*<br/>
要清除的键值。

### <a name="return-value"></a>返回值

前两个成员函数返回一个迭代器，该迭代器指定已移除的任何元素之外保留的第一个元素; `concurrent_unordered_map::end` 如果此类元素不存在，则为 ( # A1。 第三个成员函数返回它删除的元素的数目。

### <a name="remarks"></a>备注

第一个成员函数将移除 `_Where` 所指向的受控序列的元素。 第二个成员函数删除范围 [，) 中的元素 `_Begin` `_End` 。

第三个成员函数删除范围 `concurrent_unordered_map::equal_range` (KVal) 分隔的元素。

## <a name="unsafe_max_bucket_count"></a><a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

返回此容器中的最大存储桶数。

```cpp
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>返回值

此容器中的最大存储桶数。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)

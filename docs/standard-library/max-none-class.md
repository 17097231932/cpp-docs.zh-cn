---
description: 了解详细信息： max_none 类
title: max_none 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
ms.openlocfilehash: 9d3f6bf2d7dda114ed7541b91da8081d501ddec5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149248"
---
# <a name="max_none-class"></a>max_none 类

描述 [max 类](../standard-library/allocators-header.md) 对象，该对象将 [freelist](../standard-library/freelist-class.md) 对象的最大长度限制为零。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>parameters

*数量*\
max 类，用于决定要存储于 `freelist` 中的最大元素数目。

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[分配](#allocated)|逐量增加已分配的内存块的计数。|
|[分配](#deallocated)|逐量减小已分配的内存块的计数。|
|[full](#full)|返回一个值，该值指定是否应将更多的内存块添加到空闲列表。|
|[取出](#released)|逐量减小空闲列表上内存块的计数。|
|[saved](#saved)|逐量增加空闲列表上内存块的计数。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="max_noneallocated"></a><a name="allocated"></a> max_none：：已分配

逐量增加已分配的内存块的计数。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>parameters

*_Nx*\
增量值。

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 它在每次成功调用后调用 `cache_freelist::allocate` 到运算符 **`new`** 。 参数 *_Nx* 是由运算符分配的块区中的内存块数 **`new`** 。

## <a name="max_nonedeallocated"></a><a name="deallocated"></a> max_none：:d eallocated

逐量减小已分配的内存块的计数。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>parameters

*_Nx*\
增量值。

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 此成员函数在每次调用后调用 `cache_freelist::deallocate` 到运算符 **`delete`** 。 参数 *_Nx* 是由运算符释放的块区中的内存块数 **`delete`** 。

## <a name="max_nonefull"></a><a name="full"></a> max_none：： full

返回一个值，该值指定是否应将更多的内存块添加到空闲列表。

```cpp
bool full();
```

### <a name="return-value"></a>返回值

此成员函数总是返回 **`true`** 。

### <a name="remarks"></a>备注

此成员函数由 `cache_freelist::deallocate` 调用。 如果调用返回，则将 **`true`** `deallocate` 内存块置于可用列表中; 如果返回，则 **`false`** `deallocate` 调用运算符 **`delete`** 来解除分配块。

## <a name="max_nonereleased"></a><a name="released"></a> max_none：：已发布

逐量减小空闲列表上内存块的计数。

```cpp
void released();
```

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 每当当前 max 类的 `released` 成员函数从空闲列表中删除内存块时，`cache_freelist::allocate` 将对其进行调用。

## <a name="max_nonesaved"></a><a name="saved"></a> max_none：：已保存

逐量增加空闲列表上内存块的计数。

```cpp
void saved();
```

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 每当此成员函数向空闲列表放入内存块时，`cache_freelist::deallocate` 将对其进行调用。

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)

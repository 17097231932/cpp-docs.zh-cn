---
description: 了解详细信息： remove_extent 类
title: remove_extent 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_extent
helpviewer_keywords:
- remove_extent class
- remove_extent
ms.assetid: b9320862-3891-49fc-80bc-571eb2c035cf
ms.openlocfilehash: 6f088d58cafdafd9c6ebe4c1fcbbbd8db4dff69c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159669"
---
# <a name="remove_extent-class"></a>remove_extent 类

从数组类型设置元素类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct remove_extent;

template <class T>
using remove_extent_t = typename remove_extent<T>::type;
```

### <a name="parameters"></a>parameters

*关心*\
要修改的类型。

## <a name="remarks"></a>备注

的实例 `remove_extent<T>` 保留修改后的类型， `T1` 当 *t* 为形式时，则为 `T1[N]` ，否则为 *t*。

## <a name="example"></a>示例

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "remove_extent_t<int> == "
        << typeid(std::remove_extent_t<int>).name()
        << std::endl;T
    std::cout << "remove_extent_t<int[5]> == "
        << typeid(std::remove_extent_t<int[5]>).name()
        << std::endl;T
    std::cout << "remove_extent_t<int[5][10]> == "
        << typeid(std::remove_extent_t<int[5][10]>).name()
        << std::endl;
    return (0);
    }
```

```Output
remove_extent_t<int> == int
remove_extent_t<int[5]> == int
remove_extent_t<int[5][10]> == int [10]
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[remove_all_extents 类](../standard-library/remove-all-extents-class.md)

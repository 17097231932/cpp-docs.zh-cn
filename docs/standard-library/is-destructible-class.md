---
description: 了解详细信息： is_destructible 类
title: is_destructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_destructible
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
ms.openlocfilehash: fcd41c292c0054553b165529a85e7b23312d3c2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231155"
---
# <a name="is_destructible-class"></a>is_destructible 类

测试该类型是否易损坏。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>parameters

*关心*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型 *T* 是易损坏类型，则类型谓词的实例为 true; 否则为 false。 易损坏类型是引用类型、对象类型以及那些在其中对于等于 `U` 的某些类型 `remove_all_extents_t<T>` 而言未计算操作数 `std::declval<U&>.~U()` 格式正确的类型。 其他类型（包括不完整类型、 **`void`** 和函数类型）不是易损坏类型。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)

---
description: 了解详细信息： is_nothrow_copy_constructible 类
title: is_nothrow_copy_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_constructible
helpviewer_keywords:
- is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
ms.openlocfilehash: b238b86a5780d12dd6c1e62e0b2d79b9fbc139dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323591"
---
# <a name="is_nothrow_copy_constructible-class"></a>is_nothrow_copy_constructible 类

测试类型是否具有 **`nothrow`** 复制构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_nothrow_copy_constructible;
```

### <a name="parameters"></a>parameters

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型 *Ty* 具有 nothrow 复制构造函数，则类型谓词的实例为 true; 否则为 false。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)

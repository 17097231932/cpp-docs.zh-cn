---
description: 了解详细信息： is_move_constructible 类
title: is_move_constructible 类
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 05ef640b2841eb3ab66f6d5a6d3b8ede7acf2754
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323628"
---
# <a name="is_move_constructible-class"></a>is_move_constructible 类

测试是否可以使用移动操作构造该类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>parameters

*关心*\
要计算的类型。

## <a name="remarks"></a>备注

**`true`** 如果可以使用移动操作构造类型 *T* ，则为的类型谓词的计算结果为。 此谓词等效于 `is_constructible<T, T&&>`。 不具有移动构造函数但有接受参数的复制构造函数的类型 *T* `const T&` `std::is_move_constructible` 。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)

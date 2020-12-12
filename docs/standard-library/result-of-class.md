---
description: 了解详细信息： result_of 类
title: result_of 类
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: 2aba6b073309be064b9ff0edc7bffa4d8d0098e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273899"
---
# <a name="result_of-class"></a>result_of 类

确定可调用类型的返回类型，该可调用类型采用指定参数类型。 在 c + + 14 中添加，在 c + + 17 中已弃用。

## <a name="syntax"></a>语法

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>parameters

*Fn*\
要查询的可调用类型。

*ArgTypes*\
供可调用类型查询的参数列表的类型。

## <a name="remarks"></a>备注

使用此模板在编译时确定 () 的结果类型 `Fn` `ArgTypes` ，其中 *Fn* 是可调用类型、对函数的引用或对可调用类型的引用，该类型是使用 *ArgTypes* 中的类型的参数列表调用的。 `type` `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 如果未计算的表达式的格式正确，则类模板的成员会将的结果类型命名为 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 。 否则，类模板不具有成员 `type` 。 类型 *Fn* 和参数包 *ArgTypes* 中的所有类型都必须是完整类型、 **`void`** 或未知绑定的数组。 弃用，以支持 c + + 17 中的 [invoke_result](invoke-result-class.md) 。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[invoke_result 类](invoke-result-class.md)

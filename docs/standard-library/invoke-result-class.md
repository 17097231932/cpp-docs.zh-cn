---
description: 了解详细信息： invoke_result 类
title: invoke_result 类
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: 4204ff1b0b8d38eab4b7d8c0de4709b90e12f5d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231490"
---
# <a name="invoke_result-class"></a>invoke_result 类

确定在编译时采用指定参数类型的可调用类型的返回类型。 在 c + + 17 中添加。

## <a name="syntax"></a>语法

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<class Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>parameters

*多次*\
要查询的可调用类型。

*Args*\
供可调用类型查询的参数列表的类型。

## <a name="remarks"></a>备注

使用此模板可在编译时确定可 *调用* (*Args*... ) 的结果类型，其中，可 *调用* 的和 *参数* 中的所有类型都是任何完整的类型、未知绑定的数组或可能的 cv 限定的 **`void`** 。 `type`类模板的成员在使用 arguments 参数 ... 调用时命名可 *调用* 的返回类型 *。*`type`仅当使用参数 *Args*... 调用时可以调用可调用时，才定义成员在未计算的上下文中。 否则，类模板没有成员 `type` ，这允许在编译时对特定参数类型集进行 SFINAE 测试。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)

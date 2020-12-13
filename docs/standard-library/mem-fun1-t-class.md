---
description: 了解详细信息： mem_fun1_t 类
title: mem_fun1_t 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: a0fd8f060757c7dc5004ad753fd168c9e644e1b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149079"
---
# <a name="mem_fun1_t-class"></a>mem_fun1_t 类

一种适配器类， `non_const` 在使用指针参数进行初始化时，此类允许使用单个自变量的成员函数作为二元函数对象调用。 在 c + + 11 中已弃用，在 c + + 17 中删除。

## <a name="syntax"></a>语法

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;
};
```

### <a name="parameters"></a>parameters

*_Pm*\
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*_Pleft*\
在其上调用 *_Pm* 成员函数的对象。

*然后*\
要提供给 *_Pm* 的参数。

## <a name="return-value"></a>返回值

一个自适应二元函数。

## <a name="remarks"></a>备注

类模板 `Type` 在私有成员对象中存储 _Pm 的副本，该副本必须是指向类的成员函数的指针。 它将其成员函数定义 `operator()` 为返回 (**_Pleft** -> \* `_Pm`) # B2 **右**) 。

## <a name="example"></a>示例

通常不直接使用 `mem_fun1_t` 的构造函数；helper 函数 `mem_fun` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun](../standard-library/functional-functions.md#mem_fun)。

---
description: 了解详细信息： pointer_to_binary_function 类
title: pointer_to_binary_function 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 5cdecc297ff5c55c9b6c57b5b6ab029636f3958c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340705"
---
# <a name="pointer_to_binary_function-class"></a>pointer_to_binary_function 类

将二元函数指针转换为自适应二元函数。 在 c + + 11 中已弃用，在 c + + 17 中删除。

## <a name="syntax"></a>语法

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>parameters

*pfunc*\
要转换的二元函数。

*左中*\
调用 *\* pfunc* 的左对象。

*然后*\
要对其调用 *\* pfunc* 的适当对象。

## <a name="return-value"></a>返回值

类模板存储的副本 `pfunc` 。 它将其成员函数定义 `operator()` 为返回 `(* pfunc)(Left, right)` 。

## <a name="remarks"></a>备注

二元函数指针是一个函数对象，且可能会被传递到期望将二元函数作为参数的任何 C++ 标准库算法，但这不适用。 若要将其与适配器一起使用（如向其绑定值或将值与配合一起使用），则必须为其提供嵌套类型 `first_argument_type` 、 `second_argument_type` 和，这样才能 `result_type` 实现此类调整。 `pointer_to_binary_function` 执行的转换允许函数适配器与二元函数指针配合使用。

## <a name="example"></a>示例

很少直接使用 `pointer_to_binary_function` 的构造函数。 有关如何声明和使用 `pointer_to_binary_function` 适配器谓词的示例，请参阅帮助程序函数 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)。

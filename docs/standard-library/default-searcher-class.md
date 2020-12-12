---
description: 了解详细信息： default_searcher 类
title: default_searcher 类
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 0eb47d3f4c49c9bb6c9c4e68ab2164b87ea9834d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324583"
---
# <a name="default_searcher-class"></a>default_searcher 类

`default_searcher`是用于搜索在对象的构造函数中指定的序列的操作的函数对象类型。 搜索是在提供给对象的函数调用运算符的另一序列中完成的。 `default_searcher`调用[std：： search](algorithm-functions.md#search)来执行搜索。

## <a name="syntax"></a>语法

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>成员

| 成员 | 描述 |
| - | - |
| **构造函数** | |
| [default_searcher](#default-searcher-constructor) | 构造一个搜索者实例。 |
| **运算符** | |
| [运算符 ( # B1 ](#operator-call) | 对序列调用操作。 |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a> default_searcher 构造函数

`default_searcher`使用序列搜索和相等谓词来构造函数对象。

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>parameters

*pat_first*\
要搜索的序列的初始元素。

*pat_last*\
要搜索的序列的末尾。

*pred*\
序列元素的可选相等比较谓词。 如果未指定相等比较类型，则默认值为 `std::equal_to` 。

### <a name="remarks"></a>备注

引发 *BinaryPredicate* 或 *ForwardIterator* 类型的复制构造函数引发的任何异常。

此类是 c + + 17 中新增的。 C + + 20 生成构造函数 **`constexpr`** 。

## <a name="operator"></a><a name="operator-call"></a> 运算符 ( # A1

函数运算符的调用运算符。 在参数序列内搜索 `[first, last)` 指定给构造函数的序列。

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>parameters

*1*\
要在其中进行搜索的序列的初始元素。

*时间*\
要在其中进行搜索的序列的末尾。

### <a name="remarks"></a>备注

返回一对迭代器。 初始迭代器 *i* 是的有效结果：

`std::search( first, last, pat_first, pat_last, pred )`.

如果 *i** 是 *最后* 一个，则对的第二个迭代器是 *最后一个*。 否则，结果为：

`std::next( i, std::distance( pat_first, pat_last ))`.

此类是 c + + 17 中新增的。 C + + 20 已成为调用运算符 **`constexpr`** 。

## <a name="see-also"></a>请参阅

[\<functional>](functional.md)\
[算法函数](algorithm-functions.md)\
[std：： search](algorithm-functions.md#search)

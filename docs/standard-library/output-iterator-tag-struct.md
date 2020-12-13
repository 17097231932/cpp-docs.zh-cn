---
description: 了解详细信息： output_iterator_tag 结构
title: output_iterator_tag 结构
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: 1bd97f88dc7ae68976920cf006cd10115b16b2f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340900"
---
# <a name="output_iterator_tag-struct"></a>output_iterator_tag 结构

一个类，该类提供 `iterator_category` 表示输出迭代器的函数的返回类型。

## <a name="syntax"></a>语法

struct output_iterator_tag {} ;

## <a name="remarks"></a>备注

分类标记类用作算法选择的编译标记。 模板函数需要查找其迭代器参数的最特定的类别，以便可以在编译时使用最高效的算法。 对于每个 `Iterator` 类型的迭代器，`iterator_traits`< `Iterator`> **::iterator_category** 必须定义为最特定的类别标记，用于描述迭代器的行为。

此类型与 **iterator** \< **Iter**> **：： iterator_category** 在 `Iter` 描述可用作输出迭代器的对象时相同。

和其他迭代器标记一样，此标记不在迭代器的 `value_type` 或 `difference_type` 上进行参数化，因为输出迭代器没有 `value_type` 或 `difference_type`。

## <a name="example"></a>示例

有关如何使用的示例，请参阅 [iterator_traits](../standard-library/iterator-traits-struct.md) 或 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) `iterator_tag` 。

## <a name="requirements"></a>要求

**标头：**\<iterator>

**命名空间:** std

## <a name="see-also"></a>请参阅

[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 标准库参考](../standard-library/cpp-standard-library-reference.md)

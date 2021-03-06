---
description: 了解详细信息： iterator Struct
title: iterator 结构
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 81a35fd749b3393a0235fdac8c4bf13a1ef5af79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254321"
---
# <a name="iterator-struct"></a>iterator 结构

一个空基结构，用于确保用户定义迭代器类能够正常使用 `iterator_trait` 。

## <a name="syntax"></a>语法

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>备注

模板结构充当所有迭代器的一个基类型。 它定义成员类型

- `iterator_category`（模板参数 `Category` 的同义词）。

- `value_type`（模板参数 `Type` 的同义词）。

- `difference_type`（模板参数 `Distance` 的同义词）。

- `distance_type`（模板参数 `Distance` 的同义词）。

- `pointer`（模板参数 `Pointer` 的同义词）。

- `reference`（模板参数 `Reference` 的同义词）。

请注意， `value_type` 即使的 `pointer` 对象上的点 **`const`** `Type` 和引用指定了的对象， **`const`** `Type` 也不应为常量类型。

## <a name="example"></a>示例

有关如何在迭代器基类中声明和使用这些类型的示例，请参阅 [iterator_traits](../standard-library/iterator-traits-struct.md)。

## <a name="requirements"></a>要求

**标头：**\<iterator>

**命名空间:** std

## <a name="see-also"></a>请参阅

[\<iterator>](../standard-library/iterator.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 标准库参考](../standard-library/cpp-standard-library-reference.md)

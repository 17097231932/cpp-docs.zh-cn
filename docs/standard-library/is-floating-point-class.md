---
description: 了解详细信息： is_floating_point 类
title: is_floating_point 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_floating_point
helpviewer_keywords:
- is_floating_point class
- is_floating_point
ms.assetid: 070679c1-115b-4ee4-8ab7-f52e5d9e157f
ms.openlocfilehash: e1ace01a88c103646e9daa6ece82b9c3c3c2978a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230973"
---
# <a name="is_floating_point-class"></a>is_floating_point 类

测试类型是否为浮点。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_floating_point;
```

### <a name="parameters"></a>parameters

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型 *Ty* 为浮点类型或浮点类型的形式，则类型谓词的实例为 true `cv-qualified` ; 否则为 false。

浮点类型为 **`float`** 、 **`double`** 或之一 **`long double`** 。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_floating_point.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_floating_point<trivial> == " << std::boolalpha
        << std::is_floating_point<trivial>::value << std::endl;
    std::cout << "is_floating_point<int> == " << std::boolalpha
        << std::is_floating_point<int>::value << std::endl;
    std::cout << "is_floating_point<float> == " << std::boolalpha
        << std::is_floating_point<float>::value << std::endl;

    return (0);
    }
```

```Output
is_floating_point<trivial> == false
is_floating_point<int> == false
is_floating_point<float> == true
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[is_integral 类](../standard-library/is-integral-class.md)

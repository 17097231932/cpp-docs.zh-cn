---
description: 了解详细信息： is_enum 类
title: is_enum 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_enum
helpviewer_keywords:
- is_enum class
- is_enum
ms.assetid: df3b00b7-4f98-4b3a-96ce-10ad958ee69c
ms.openlocfilehash: 6eaffc4258dd7741e177718ed39a3d8c3f75f96f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231142"
---
# <a name="is_enum-class"></a>is_enum 类

测试类型是否为枚举。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_enum;
```

### <a name="parameters"></a>parameters

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型 *Ty* 是枚举类型或枚举类型的形式，则类型谓词的实例为 true `cv-qualified` ; 否则为 false。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_enum.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

enum color {
    red, greed, blue};

int main()
    {
    std::cout << "is_enum<trivial> == " << std::boolalpha
        << std::is_enum<trivial>::value << std::endl;
    std::cout << "is_enum<color> == " << std::boolalpha
        << std::is_enum<color>::value << std::endl;
    std::cout << "is_enum<int> == " << std::boolalpha
        << std::is_enum<int>::value << std::endl;

    return (0);
    }
```

```Output
is_enum<trivial> == false
is_enum<color> == true
is_enum<int> == false
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[is_integral 类](../standard-library/is-integral-class.md)

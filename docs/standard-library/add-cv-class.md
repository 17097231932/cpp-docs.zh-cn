---
description: 了解详细信息： add_cv 类
title: add_cv 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: bc25efd879a27b3d3af2e5f4db8dd74fafa3fb45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319926"
---
# <a name="add_cv-class"></a>add_cv 类

**`const volatile`** 从类型中创建类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>parameters

*关心*\
要修改的类型。

## <a name="remarks"></a>备注

修改后的类型的实例 `add_cv<T>` 具有 `type` **`typedef`** 等效于 [add_volatile](add-volatile-class.md)和 [add_const](add-const-class.md)修改的成员，除非已经有 cv 限定符、是引用或函数。

`add_cv_t<T>` 帮组程序类型是访问 `add_cv<T>` 成员 typedef `type` 的快捷方式。

## <a name="example"></a>示例

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](type-traits.md)\
[remove_const 类](remove-const-class.md)\
[remove_volatile 类](remove-volatile-class.md)

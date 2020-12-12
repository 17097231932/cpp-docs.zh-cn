---
description: 了解详细信息： is_trivially_copy_assignable 类
title: is_trivially_copy_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: 010e820db570f594568cb60f4edae83b91a997c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271234"
---
# <a name="is_trivially_copy_assignable-class"></a>is_trivially_copy_assignable 类

测试类型是否具有普通复制赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>parameters

*关心*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型 *T* 是具有普通复制赋值运算符的类，则类型谓词的实例为 true; 否则为 false。

如果类 *t* 的赋值构造函数是隐式提供的，则该类没有虚函数， *类 t 没有* 虚函数，类 *t* 没有虚拟基，类类型的所有非静态数据成员的类具有普通赋值运算符，并且类的类型数组的所有非静态数据成员的类具有普通赋值运算符。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)

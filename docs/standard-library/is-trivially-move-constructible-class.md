---
description: 了解详细信息： is_trivially_move_constructible 类
title: is_trivially_move_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: 30e8be25e74aeed1eafc8fcafbece5c62e4ad999
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154313"
---
# <a name="is_trivially_move_constructible-class"></a>is_trivially_move_constructible 类

测试类型是否具有普通移动构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>parameters

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型 *Ty* 是一个具有普通移动构造函数的类，则类型谓词的实例为 true; 否则为 false。

如果以下情况， *Ty* 类的移动构造函数是普通的：

它被隐式声明

其参数类型等效于那些隐式声明的参数类型

类 *Ty* 没有虚函数

类 *Ty* 没有虚拟基

类没有任何不稳定的非静态数据成员

类 *Ty* 的所有直接基都具有普通的移动构造函数

类类型的所有非静态数据成员的类具有普通构造函数

类的类型数组的所有非静态数据成员的类具有普通构造函数

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)

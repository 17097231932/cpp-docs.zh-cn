---
description: 了解详细信息： IsSame 结构
title: IsSame 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
ms.openlocfilehash: b00e85f55fc80af2dd00dc20f090a7b18678f579
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298924"
---
# <a name="issame-structure"></a>IsSame 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>parameters

*T1*<br/>
一种类型。

*T2*<br/>
另一种类型。

## <a name="remarks"></a>备注

测试指定的类型是否与另一个指定的类型相同。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

名称                    | 描述
----------------------- | --------------------------------------------------
[IsSame：： value](#value) | 指示一个类型与另一个类型是否相同。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IsSame`

## <a name="requirements"></a>要求

**标头：** internal。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="issamevalue"></a><a name="value"></a> IsSame：： value

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

### <a name="remarks"></a>备注

指示一个类型与另一个类型是否相同。

`value`**`true`** 如果模板参数相同，则为; **`false`** 如果模板参数不同，则为。

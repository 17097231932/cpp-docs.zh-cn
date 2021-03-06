---
description: 了解详细信息： norm_2 类
title: norm_2 类
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::norm_2::set_x
- amp_short_vectors/Concurrency::graphics::norm_2::set_xy
- amp_short_vectors/Concurrency::graphics::norm_2::g
- amp_short_vectors/Concurrency::graphics::norm_2::get_yx
- amp_short_vectors/Concurrency::graphics::norm_2::set_yx
- amp_short_vectors/Concurrency::graphics::norm_2::operator-=
- amp_short_vectors/Concurrency::graphics::norm_2::operator/=
- amp_short_vectors/Concurrency::graphics::norm_2::operator*=
- amp_short_vectors/Concurrency::graphics::norm_2::yx
- amp_short_vectors/Concurrency::graphics::norm_2::y
- amp_short_vectors/Concurrency::graphics::norm_2::xy
- amp_short_vectors/Concurrency::graphics::norm_2::operator++
- amp_short_vectors/Concurrency::graphics::norm_2::operator-
- amp_short_vectors/Concurrency::graphics::norm_2::rg
- amp_short_vectors/Concurrency::graphics::norm_2::operator=
- amp_short_vectors/Concurrency::graphics::norm_2::get_y
- amp_short_vectors/Concurrency::graphics::norm_2::r
- amp_short_vectors/Concurrency::graphics::norm_2::get_x
- amp_short_vectors/Concurrency::graphics::norm_2::get_xy
- amp_short_vectors/Concurrency::graphics::norm_2::gr
- amp_short_vectors/Concurrency::graphics::norm_2::set_y
- amp_short_vectors/Concurrency::graphics::norm_2::x
- amp_short_vectors/Concurrency::graphics::norm_2::operator+=
- amp_short_vectors/Concurrency::graphics::norm_2
- amp_short_vectors/Concurrency::graphics::norm_2::operator--
ms.assetid: 80703f9b-61f4-414a-93fd-bc774f7d3393
ms.openlocfilehash: 5b4b19d83672a88828d3cad8be7f22a2f54a431e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329985"
---
# <a name="norm_2-class"></a>norm_2 类

表示两个普通数字的短矢量。

## <a name="syntax"></a>语法

```cpp
class norm_2;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[norm_2 构造函数](#ctor)|已重载。 默认构造函数，用0初始化所有元素。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|norm_2：： get_x||
|norm_2：： get_xy||
|norm_2：： get_y||
|norm_2：： get_yx||
|norm_2：： ref_g||
|norm_2：： ref_r||
|norm_2：： ref_x||
|norm_2：： ref_y||
|norm_2：： set_x||
|norm_2：： set_xy||
|norm_2：： set_y||
|norm_2：： set_yx||

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|norm_2：： operator-||
|norm_2：： operator--||
|norm_2：： operator * =||
|norm_2：： operator/=||
|norm_2：： operator + +||
|norm_2：： operator + =||
|norm_2：： operator =||
|norm_2：： operator-=||

### <a name="public-constants"></a>公共常量

|名称|描述|
|----------|-----------------|
|[大小常量](#norm_2__size)||

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|norm_2：： g||
|norm_2：： gr||
|norm_2：： r||
|norm_2：： rg||
|norm_2：： x||
|norm_2：： xy||
|norm_2：： y||
|norm_2：： yx||

## <a name="inheritance-hierarchy"></a>继承层次结构

`norm_2`

## <a name="requirements"></a>要求

**标头：** amp_short_vectors。h

**命名空间：** Concurrency：： graphics

## <a name="norm_2"></a><a name="ctor"></a> norm_2

默认构造函数，用0初始化所有元素。

```cpp
norm_2() restrict(amp,
    cpu);

norm_2(
    norm _V0,
    norm _V1) restrict(amp,
    cpu);

norm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

norm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

norm_2(
    norm _V) restrict(amp,
    cpu);

explicit norm_2(
    float _V) restrict(amp,
    cpu);

norm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>parameters

*_V0*<br/>
要初始化元素0的值。

*_V1*<br/>
要初始化元素1的值。

*_V*<br/>
用于初始化的值。

*_Other*<br/>
用于初始化的对象。

## <a name="size"></a><a name="norm_2__size"></a> 规格

```cpp
static const int size = 2;
```

## <a name="see-also"></a>请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)

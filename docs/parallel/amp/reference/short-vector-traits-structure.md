---
description: 了解详细信息： short_vector_traits 结构
title: short_vector_traits 结构
ms.date: 11/04/2016
f1_keywords:
- short_vector_traits
- AMP_SHORT_VECTORS/short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::size Constant
ms.assetid: cd9492da-9e02-4a6e-9d50-b61252cdb460
ms.openlocfilehash: dc211c8e66cbd31c57655afce22376909cf77530
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329891"
---
# <a name="short_vector_traits-structure"></a>short_vector_traits 结构

short_vector_traits 允许检索 short 矢量类型或标量类型的基础向量长度和标量类型

## <a name="syntax"></a>语法

```cpp
template<
    typename T
>
struct short_vector_traits;
template<>
struct short_vector_traits<unsigned int>;
template<>
struct short_vector_traits<uint_2>;
template<>
struct short_vector_traits<uint_3>;
template<>
struct short_vector_traits<uint_4>;
template<>
struct short_vector_traits<int>;
template<>
struct short_vector_traits<int_2>;
template<>
struct short_vector_traits<int_3>;
template<>
struct short_vector_traits<int_4>;
template<>
struct short_vector_traits<float>;
template<>
struct short_vector_traits<float_2>;
template<>
struct short_vector_traits<float_3>;
template<>
struct short_vector_traits<float_4>;
template<>
struct short_vector_traits<unorm>;
template<>
struct short_vector_traits<unorm_2>;
template<>
struct short_vector_traits<unorm_3>;
template<>
struct short_vector_traits<unorm_4>;
template<>
struct short_vector_traits<norm>;
template<>
struct short_vector_traits<norm_2>;
template<>
struct short_vector_traits<norm_3>;
template<>
struct short_vector_traits<norm_4>;
template<>
struct short_vector_traits<double>;
template<>
struct short_vector_traits<double_2>;
template<>
struct short_vector_traits<double_3>;
template<>
struct short_vector_traits<double_4>;
```

### <a name="parameters"></a>parameters

`T`

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[short_vector_traits::short_vector_traits 构造函数](#ctor)||

### <a name="public-constants"></a>公共常量

|名称|描述|
|----------|-----------------|
|[short_vector_traits::size 常量](#size)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`short_vector_traits`

## <a name="requirements"></a>要求

**标头：** amp_short_vectors。h

**命名空间：** Concurrency：： graphics

## <a name="short_vector_traitsshort_vector_traits-constructor"></a><a name="ctor"></a> short_vector_traits：： short_vector_traits 构造函数

```cpp
short_vector_traits();
```

## <a name="short_vector_traitssize-constant"></a><a name="size"></a> short_vector_traits：： size 常量

```cpp
static int const size = 1;
```

## <a name="see-also"></a>请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)

---
title: Platform::Agile 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
ms.openlocfilehash: d39270b7bf05e820ea376a40310abeb8add2c5ad
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742952"
---
# <a name="platformagile-class"></a>Platform::Agile 类

表示将 MashalingBehavior=Standard 作为敏捷对象（这可以大大降低出现运行时线程处理异常的机率）的对象。 `Agile<T>` 使非敏捷对象可以调用相同或不同线程调用，或是从相同或不同线程进行调用。 有关详细信息，请参阅 [线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)。

## <a name="syntax"></a>语法

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>参数

*T*<br/>
非敏捷类的类型名称。

### <a name="remarks"></a>备注

Windows 运行时中的大多数类都是敏捷类。 敏捷对象可以调用相同或不同线程中的进程内或进程外对象，或是由该对象进行调用。 如果对象不是敏捷对象，请在 `Agile<T>` 对象（这是敏捷对象）中包装非敏捷对象。 随后可以封送 `Agile<T>` 对象，并且可以使用基础非敏捷对象。

`Agile<T>` 类是本机标准 C++ 类，需要 `agile.h`。 它表示非敏捷对象和敏捷对象的 *上下文*。 上下文指定敏捷对象的线程处理模型和封送处理行为。 操作系统使用上下文来确定如何封送对象。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[Agile：： Agile](#ctor)|初始化 Agile 类的新实例。|
|[Agile::~Agile 析构函数](#dtor)|销毁敏捷类的当前实例。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[Agile::Get](#get)|返回用当前敏捷对象表示的对象的句柄。|
|[Agile::GetAddressOf](#getaddressof)|重新初始化当前敏捷对象，然后返回类型为 `T`的对象的句柄地址。|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|将句柄的地址返回到用当前敏捷对象表示的对象。|
|[Agile::Release](#release)|放弃当前敏捷对象的基础对象和上下文。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[Agile：： operator->](#operator-arrow)|检索用当前敏捷对象表示的对象的句柄。|
|[Agile::operator=](#operator-assign)|将指定值分配给当前敏捷对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Object`

`Agile`

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**标头：** agile.h

## <a name="agileagile-constructor"></a><a name="ctor"></a> Agile：： Agile 构造函数

初始化 Agile 类的新实例。

### <a name="syntax"></a>语法

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>参数

*T*<br/>
模板类型名称参数指定的类型。

*object*<br/>
在此构造函数的第二个版本中，用于初始化新的 Agile 实例的对象。 在第三个版本中，复制到新的 Agile 实例的对象。 在第四个版本中，移动到新的 Agile 实例的对象。

### <a name="remarks"></a>备注

此构造函数的第一个版本是默认构造函数。 第二个版本从 `object` 参数指定的对象初始化新实例 Agile 类。 第三个版本是复制构造函数。 第四个版本是移动构造函数。 此构造函数不能引发异常。

## <a name="agileagile-destructor"></a><a name="dtor"></a> Agile：： ~ Agile 析构函数

销毁敏捷类的当前实例。

### <a name="syntax"></a>语法

```cpp
~Agile();
```

### <a name="remarks"></a>备注

此析构函数也会释放当前敏捷对象表示的对象。

## <a name="agileget-method"></a><a name="get"></a> Agile：： Get 方法

返回用当前敏捷对象表示的对象的句柄。

### <a name="syntax"></a>语法

```cpp
T^ Get() const;
```

### <a name="return-value"></a>返回值

用当前敏捷对象表示的对象的句柄。

返回值的类型实际是未公开的内部类型。 保存返回值的一种简便方法是将其分配给使用类型推导关键字声明的变量 **`auto`** 。 例如，`auto x = myAgileTvariable->Get();`。

## <a name="agilegetaddressof-method"></a><a name="getaddressof"></a> Agile：： GetAddressOf 方法

重新初始化当前敏捷对象，然后返回类型为 `T`的对象的句柄地址。

### <a name="syntax"></a>语法

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>参数

*T*<br/>
模板类型名称参数指定的类型。

### <a name="return-value"></a>返回值

`T` 类型的对象的句柄地址。

### <a name="remarks"></a>备注

此操作释放类型为 `T` 的对象的当前表示形式（如果有）；重新初始化敏捷对象的数据成员；获取当前线程处理上下文；然后返回可以表示非敏捷对象的对象句柄变量的地址。 若要使 Agile 类实例表示对象，请使用赋值运算符 ([agile：： operator =](#operator-assign)) 将对象分配给 Agile 类实例。

## <a name="agilegetaddressofforinout-method"></a><a name="getaddressofforinout"></a> Agile：： GetAddressOfForInOut 方法

将句柄的地址返回到用当前敏捷对象表示的对象。

### <a name="syntax"></a>语法

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>参数

*T*<br/>
模板类型名称参数指定的类型。

### <a name="return-value"></a>返回值

返回到用当前敏捷对象表示的对象的句柄的地址。

### <a name="remarks"></a>备注

此操作获取当前线程上下文，然后将句柄的地址返回到基础对象。

## <a name="agilerelease-method"></a><a name="release"></a> Agile：： Release 方法

放弃当前敏捷对象的基础对象和上下文。

### <a name="syntax"></a>语法

```cpp
void Release() throw();
```

### <a name="remarks"></a>备注

放弃当前敏捷对象的基础对象和上下文（如果存在），然后将敏捷对象的值设置为 null。

## <a name="agileoperator-gt-operator"></a><a name="operator-arrow"></a> Agile：： operator- &gt; 运算符

检索用当前敏捷对象表示的对象的句柄。

### <a name="syntax"></a>语法

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>返回值

用当前敏捷对象表示的对象的句柄。

此运算符实际返回未公开的内部类型。 保存返回值的一种简便方法是将其分配给使用类型推导关键字声明的变量 **`auto`** 。

## <a name="agileoperator-operator"></a><a name="operator-assign"></a> Agile：： operator = 运算符

将指定对象分配给当前敏捷对象。

### <a name="syntax"></a>语法

```cpp
Agile<T> operator=( T^ object ) throw();
Agile<T> operator=( const Agile<T>& object ) throw();
Agile<T> operator=( Agile<T>&& object ) throw();
T^ operator=( IUnknown* lp ) throw();
```

#### <a name="parameters"></a>参数

*T*<br/>
模板类型名称指定的类型。

*object*<br/>
复制或移动到当前敏捷对象的对象或对象句柄。

*lp*<br/>
对象的 IUnknown 接口指针。

### <a name="return-value"></a>返回值

`T` 类型的对象的句柄

### <a name="remarks"></a>备注

赋值运算符的第一个版本将引用类型的句柄复制到当前敏捷对象。 第二个版本将对敏捷类型的引用复制到当前敏捷对象。 第三个版本将一个敏捷类型移到当前敏捷对象。 第四个版本将 COM 对象的指针移到当前敏捷对象。

赋值操作自动保存当前敏捷对象的上下文。

## <a name="see-also"></a>请参阅

[平台命名空间](platform-namespace-c-cx.md)

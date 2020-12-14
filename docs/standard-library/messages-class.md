---
description: 了解详细信息：消息类
title: messages 类
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: fe8dcc9cd580f967a3d07a4744598dff72360d44
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230505"
---
# <a name="messages-class"></a>messages 类

类模板描述可用作区域设置 facet 的对象，以便从给定区域设置的国际化消息目录中检索本地化消息。

目前，虽然已实现消息类，但没有任何消息。

## <a name="syntax"></a>语法

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>parameters

*CharType*\
在程序中用于对区域设置中的字符进行编码的类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。

大致来说，此 facet 会打开基类 messages_base 中定义的消息目录，检索所需要的信息，然后关闭目录。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[messages](#messages)|消息 facet 构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|一种用于显示消息的字符类型。|
|[string_type](#string_type)|一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[close](#close)|关闭消息目录。|
|[do_close](#do_close)|一种为失去消息目录而调用的虚拟函数。|
|[do_get](#do_get)|一种为检索消息目录而调用的虚拟函数。|
|[do_open](#do_open)|一种为打开消息目录而调用的虚拟函数。|
|[get](#get)|检索消息目录。|
|[open](#open)|打开消息目录。|

## <a name="requirements"></a>要求

**标头：**\<locale>

**命名空间:** std

## <a name="messageschar_type"></a><a name="char_type"></a> messages：： char_type

一种用于显示消息的字符类型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **CharType** 的同义词。

## <a name="messagesclose"></a><a name="close"></a> 消息：： close

关闭消息目录。

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>parameters

*_Catval*\
要关闭的目录。

### <a name="remarks"></a>备注

此成员函数调用 [do_close](#do_close)(_ *Catval*)。

## <a name="messagesdo_close"></a><a name="do_close"></a> 消息：:d o_close

一种为失去消息目录而调用的虚拟函数。

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>parameters

*_Catval*\
要关闭的目录。

### <a name="remarks"></a>备注

受保护的成员函数关闭 *_Catval* 的消息目录，该目录必须已由之前对 [do_open](#do_open)的调用打开。

必须从以前打开的且未关闭的目录获取 *_Catval*。

### <a name="example"></a>示例

请参阅 [close](#close) 的示例，它调用 `do_close`。

## <a name="messagesdo_get"></a><a name="do_get"></a> 消息：:d o_get

一种为检索消息目录而调用的虚拟函数。

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>parameters

*_Catval*\
指定要搜索的消息目录的标识值。

*_Set*\
用于在消息目录中查找消息的第一个标识。

*_Message*\
用于在消息目录中查找消息的第二个标识。

*_Dfault*\
失败时返回的字符串。

### <a name="return-value"></a>返回值

它在失败时返回 *_Dfault* 的副本。 否则，它返回指定的消息序列的副本。

### <a name="remarks"></a>备注

受保护的成员函数尝试从消息目录 *_Catval* 获取消息序列。 在此过程中，它可以使用 *_Set*、 *_Message* 和 *_Dfault* 。

### <a name="example"></a>示例

请参阅 [get](#get) 的示例，它调用 `do_get`。

## <a name="messagesdo_open"></a><a name="do_open"></a> 消息：:d o_open

一种为打开消息目录而调用的虚拟函数。

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>parameters

*_Catname*\
要搜索的目录的名称。

*_Loc*\
目录中要搜索的区域设置。

### <a name="return-value"></a>返回值

失败时返回一个小于零的值。 否则，返回的值可以用作稍后对 [get](#get) 调用时的第一个自变量。

### <a name="remarks"></a>备注

受保护的成员函数尝试打开名称为 *_Catname* 的消息目录。 在此过程中，它可能会使用区域设置 *_Loc*

返回值应用作稍后对 [close](#close) 调用时的自变量。

### <a name="example"></a>示例

请参阅 [open](#open) 的示例，它调用 `do_open`。

## <a name="messagesget"></a><a name="get"></a> 消息：： get

检索消息目录。

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>parameters

*_Catval*\
指定要搜索的消息目录的标识值。

*_Set*\
用于在消息目录中查找消息的第一个标识。

*_Message*\
用于在消息目录中查找消息的第二个标识。

*_Dfault*\
失败时返回的字符串。

### <a name="return-value"></a>返回值

它在失败时返回 *_Dfault* 的副本。 否则，它返回指定的消息序列的副本。

### <a name="remarks"></a>备注

此成员函数返回 [do_get](#do_get) ( `_Catval` ，，， `_Set` `_Message` `_Dfault`) 。

## <a name="messagesmessages"></a><a name="messages"></a> messages：：消息

消息 facet 构造函数。

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>parameters

*_Refs*\
用于指定对象的内存管理类型的整数值。

*_Locname*\
区域设置的名称。

### <a name="remarks"></a>备注

*_Refs* 参数的可能值及其重要性为：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \> 1：未定义这些值。

由于该析构函数受到保护，可能没有直接的示例。

构造函数通过 **locale：：**[facet](../standard-library/locale-class.md#facet_class) () 初始化其基对象 `_Refs` 。

## <a name="messagesopen"></a><a name="open"></a> messages：： open

打开消息目录。

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>parameters

*_Catname*\
要搜索的目录的名称。

*_Loc*\
目录中要搜索的区域设置。

### <a name="return-value"></a>返回值

失败时返回一个小于零的值。 否则，返回的值可以用作稍后对 [get](#get) 调用时的第一个自变量。

### <a name="remarks"></a>备注

该成员函数将返回 [do_open](#do_open) ( `_Catname` ， `_Loc`) 。

## <a name="messagesstring_type"></a><a name="string_type"></a> messages：： string_type

一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>备注

该类型描述类模板 [basic_string](../standard-library/basic-string-class.md) 的专用化，其对象可以存储消息序列的副本。

## <a name="see-also"></a>请参阅

[\<locale>](../standard-library/locale.md)\
[messages_base 类](../standard-library/messages-base-class.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

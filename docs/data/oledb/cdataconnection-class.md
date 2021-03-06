---
description: 了解详细信息： CDataConnection 类
title: CDataConnection 类
ms.date: 03/27/2019
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: 7cdcb681c40d1ef4e93baee5dc4e4395e6ea9c5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328811"
---
# <a name="cdataconnection-class"></a>CDataConnection 类

管理与数据源的连接。

## <a name="syntax"></a>语法

```cpp
class CDataConnection
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

| 名称 | 描述 |
|-|-|
|[CDataConnection](#cdataconnection)|构造函数。 实例化并初始化一个 `CDataConnection` 对象。|
|[复制](#copy)|创建现有数据连接的副本。|
|[打开](#open)|使用初始化字符串打开与数据源的连接。|
|[OpenNewSession](#opennewsession)|打开当前连接上的新会话。|

### <a name="operators"></a>运算符

| 名称 | 描述 |
|-|-|
|[operator BOOL](#op_bool)|确定当前会话是否已打开。|
|[operator bool](#op_bool_ole)|确定当前会话是否已打开。|
|[operator CDataSource&](#op_cdata_amp)|返回对包含的对象的引用 `CDataSource` 。|
|[operator CDataSource *](#op_cdata_star)|返回指向包含的 `CDataSource` 对象的指针。|
|[operator CSession&](#op_csession_amp)|返回对包含的对象的引用 `CSession` 。|
|[运算符 CSession*](#op_csession_star)|返回指向包含的 `CSession` 对象的指针。|

## <a name="remarks"></a>备注

`CDataConnection` 用于创建客户端的有用类，因为它封装了必需的对象 (数据源和会话) 以及连接到数据源时需要执行的一些工作

`CDataConnection`如果没有，必须创建 `CDataSource` 对象，调用其[OpenFromInitializationString](./cdatasource-class.md#openfrominitializationstring)方法，然后创建[CSession](../../data/oledb/csession-class.md)对象的实例，调用其[Open](./csession-class.md#open)方法，然后创建[CCommand](../../data/oledb/ccommand-class.md)对象并调用其 `Open` * 方法。

对于 `CDataConnection` ，你只需创建一个连接对象，向其传递一个初始化字符串，然后使用该连接打开命令。 如果你计划重复使用与数据库的连接，最好保持连接处于打开状态，并 `CDataConnection` 提供一种简便的方法来实现此目的。

> [!NOTE]
> 如果要创建的数据库应用程序需要处理多个会话，则需要使用 [OpenNewSession](#opennewsession)。

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a> CDataConnection：： CDataConnection

实例化并初始化一个 `CDataConnection` 对象。

### <a name="syntax"></a>语法

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>parameters

*ds*<br/>
中对现有数据连接的引用。

### <a name="remarks"></a>备注

第一个重写使用默认设置创建一个新的 `CDataConnection` 对象。

第二个替代会创建一个新的 `CDataConnection` 对象，其设置等效于指定的数据连接对象。

## <a name="cdataconnectioncopy"></a><a name="copy"></a> CDataConnection：： Copy

创建现有数据连接的副本。

### <a name="syntax"></a>语法

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>parameters

*ds*<br/>
中对要复制的现有数据连接的引用。

## <a name="cdataconnectionopen"></a><a name="open"></a> CDataConnection：： Open

使用初始化字符串打开与数据源的连接。

### <a name="syntax"></a>语法

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>parameters

*szInitString*<br/>
中数据源的初始化字符串。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a> CDataConnection：： OpenNewSession

使用当前连接对象的数据源打开一个新的会话。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>parameters

*会议*<br/>
[in/out]对新会话对象的引用。

### <a name="remarks"></a>备注

新会话使用当前连接对象的包含数据源对象作为其父对象，并可访问与数据源相同的所有信息。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a> CDataConnection：： operator BOOL

确定当前会话是否已打开。

### <a name="syntax"></a>语法

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>备注

返回 (MFC typedef) 值的 **布尔** 值。 **如果为 TRUE** ，则表示当前会话已打开; **FALSE** 表示当前会话已关闭。

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a> CDataConnection：： operator bool (OLE DB) 

确定当前会话是否已打开。

### <a name="syntax"></a>语法

```cpp
operator bool() throw();
```

### <a name="remarks"></a>备注

**`bool`**) 值返回 (c + + 数据类型。 **`true`** 表示当前会话已打开; **`false`** 表示当前会话已关闭。

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a> CDataConnection：： operator CDataSource&amp;

返回对包含的对象的引用 `CDataSource` 。

### <a name="syntax"></a>语法

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>备注

此运算符将返回对所包含的 `CDataSource` 对象的引用，从而使你能够传递 `CDataConnection` `CDataSource` 应有引用的对象。

### <a name="example"></a>示例

如果你的函数 (如下所示 `func`) `CDataSource` 使用引用，则可以改用 `CDataSource&` 传递 `CDataConnection` 对象。

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a> CDataConnection：： operator CDataSource *

返回指向包含的 `CDataSource` 对象的指针。

### <a name="syntax"></a>语法

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>备注

此运算符将返回指向包含的 `CDataSource` 对象的指针，允许您传递 `CDataConnection` 对象（其中需要 `CDataSource` 指针）。

有关使用示例，请参阅 [Operator CDataSource&](#op_cdata_amp) 。

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a> CDataConnection：： operator CSession&amp;

返回对包含的对象的引用 `CSession` 。

### <a name="syntax"></a>语法

```cpp
operator const CSession&();
```

### <a name="remarks"></a>备注

此运算符将返回对所包含的 `CSession` 对象的引用，从而使你能够传递 `CDataConnection` `CSession` 应有引用的对象。

### <a name="example"></a>示例

如果你的函数 (如下所示 `func`) `CSession` 使用引用，则可以改用 `CSession&` 传递 `CDataConnection` 对象。

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a> CDataConnection：： operator CSession *

返回指向包含的 `CSession` 对象的指针。

### <a name="syntax"></a>语法

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>备注

此运算符将返回指向包含的 `CSession` 对象的指针，允许您传递 `CDataConnection` 对象（其中需要 `CSession` 指针）。

### <a name="example"></a>示例

有关使用示例，请参阅 [Operator CSession&](#op_csession_amp) 。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)

---
description: 了解详细信息：访问 XML 数据
title: 访问 XML 数据
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: f229dc4567247ea95ebf00a5dbc9316be8aeac1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246079"
---
# <a name="accessing-xml-data"></a>访问 XML 数据

可以通过两种不同的方法从数据源中检索 XML 数据：一个使用 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) ，另一个使用 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。

|功能|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|传输的数据量|同时检索所有列和行中的数据。|检索所有列中的数据，但一次只能检索一行。 必须使用等方法来浏览行 `MoveNext` 。|
|设置字符串格式|SQL Server 格式化 XML 字符串并将其发送给使用者。|检索以本机格式表示的行集数据 (请求提供程序将其作为 Unicode 字符串发送) 然后生成保存 XML 格式的数据的字符串。|
|控制格式设置|通过设置某些 SQL Server 2000 特定的属性，可以对 XML 字符串的格式设置进行一定程度的控制。|你无法控制生成的 XML 字符串的格式。|

尽管 `CStreamRowset` 提供了以 XML 格式检索数据的一种更有效的方式，但它仅受 SQL Server 2000 的支持。

## <a name="retrieving-xml-data-using-cstreamrowset"></a>使用 CStreamRowset 检索 XML 数据

将 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 指定为或声明中的行集类型 `CCommand` `CTable` 。 你可以将其与你自己的访问器或无访问器一起使用，例如：

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

-或-

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

通常，当您调用 `CCommand::Open` (指定（例如 `CRowset` `TRowset`) 类）时，它将获取一个 `IRowset` 指针。 `ICommand::Execute` 返回一个 `IRowset` 指针，该指针存储在 `m_spRowset` 对象的成员中 `CRowset` 。 方法（如 `MoveFirst` 、 `MoveNext` 和） `GetData` 使用该指针检索数据。

与此相反，当您调用 `CCommand::Open` (但指定 `CStreamRowset` 作为 `TRowset` 类) 时， `ICommand::Execute` 将返回一个 `ISequentialStream` 指针，该指针存储在 `m_spStream` [CStreamRowset](../../data/oledb/cstreamrowset-class.md)的数据成员中。 然后，使用 `Read` 方法检索 XML 格式的 (Unicode 字符串) 数据。 例如：

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 执行 XML 格式设置，并返回行集的所有列和所有行作为一个 XML 字符串。

有关使用方法的示例 `Read` ，请参阅 [实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)中 **的向使用者添加 XML 支持**。

> [!NOTE]
> XML 支持 `CStreamRowset` 仅使用与 SQL Server 2000 一起使用，并要求使用 MDAC) 安装 SQL Server 2000 (的 OLE DB 提供程序。

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>使用 CXMLAccessor 检索 XML 数据

当你不知道数据存储的架构时， [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)允许你以字符串数据的形式访问数据源中的数据。 `CXMLAccessor` 类似于 `CDynamicStringAccessorW` ，但前者会将从数据存储访问的所有数据都转换为 XML 格式的数据 (标记) 的数据。 XML 标记名称与数据存储区的列名尽可能匹配。

`CXMLAccessor`像使用任何其他访问器类一样，将其作为模板参数传递到 `CCommand` 或 `CTable` ：

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

使用 [GetXMLRowData](./cxmlaccessor-class.md#getxmlrowdata) 从表中一次检索一次数据，并使用等方法浏览行， `MoveNext` 例如：

```cpp
// Open data source, session, and rowset
hr = rs.MoveFirst();

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
{
    CStringW strRowData;
    myCmd.GetXMLRowData(strRowData);

    printf_s( "%S\n", strRowData );

    hr = rs.MoveNext();
}
```

可以使用 [GetXMLColumnData](./cxmlaccessor-class.md#getxmlcolumndata) 以 XML 格式的字符串数据形式 (数据类型) 信息检索列。

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)

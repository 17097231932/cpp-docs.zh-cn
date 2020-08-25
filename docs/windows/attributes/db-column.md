---
title: 'db_column (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: 98f546a243016fa85f6d71159ab2fc0a7963bae3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833110"
---
# <a name="db_column"></a>db_column

将指定的列绑定到行集中的某个变量。

## <a name="syntax"></a>语法

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>参数

*序号*<br/>
序号列号 (`DBCOLUMNINFO` 序号) 或列名 (ANSI 或 Unicode 字符串) 与行集中要将数据绑定到的字段相对应。 如果使用数字，则可以跳过连续序号 (例如：1、2、3、5) 。 如果你使用的 OLE DB 提供程序支持，则该名称可以包含空格。 例如，可以使用以下格式之一：

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*dbtype*<br/>
 (可选) 列项 OLE DB [类型指示符](/previous-versions/windows/desktop/ms711251(v=vs.85)) 。

*精度*<br/>
 (可选) 要用于列项的精度。 有关详细信息，请参阅 `bPrecision` [DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85))元素的说明

*scale*<br/>
 (可选) 要用于列项的刻度。 有关详细信息，请参阅 `bScale` [DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85))的元素说明

*status*<br/>
 (可选) 用于保存此列的状态的成员变量。 状态指示列值是否为数据值或其他值（如 NULL）。 有关可能的值，请参阅*OLE DB 程序员参考*中的[状态](/previous-versions/windows/desktop/ms722617(v=vs.85))。

*length*<br/>
 (可选) 用于保存列大小的成员变量（以字节为单位）。

## <a name="remarks"></a>注解

**db_column** 将指定表列绑定到行集中的某个变量。 它分隔可参与基于 OLE DB 的绑定的成员数据 `IAccessor` 。 此属性设置通常使用 OLE DB 使用者宏 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)、 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)和 [COLUMN_ENTRY](../../data/oledb/column-entry.md)来定义的列映射。 这些操作将操作 OLE DB [DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85)) 以绑定指定的列。 使用 **db_column** 特性标记的每个成员都将在列映射中以列项的形式占用一个条目。 因此，您可以调用此特性，以便在命令或表类中放置列映射。

将 **db_column** 与 [db_table](db-table.md) 或 [db_command](db-command.md) 特性结合使用。

当使用者特性提供程序将此特性应用于类时，编译器会将类重命名为 \_ *YourClassName*访问器，其中*YourClassName*是您赋予类的名称，并且编译器还将创建一个名为*YourClassName*的类，该类派生自 \_ *YourClassName*访问器。  将在类视图中看到这两个类。

有关应用程序中使用的此属性的示例，请参阅 [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)。

## <a name="example"></a>示例

此示例将表中的列绑定到 **`long`** 数据成员，并指定 "状态" 和 "长度" 字段。

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

## <a name="example"></a>示例

此示例按顺序将四列绑定到 **`long`** 、字符串、时间戳和 `DB_NUMERIC` 整数。

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|**`class`**、 **`struct`** 、成员、方法|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者属性](ole-db-consumer-attributes.md)<br/>
[类特性](class-attributes.md)

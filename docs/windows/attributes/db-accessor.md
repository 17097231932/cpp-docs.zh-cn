---
title: 'db_accessor (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: 2a4c5475007cbc516f1a06c6bf858089ba24311f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503552"
---
# <a name="db_accessor"></a>db_accessor

将 `db_column` 参与基于的绑定的属性分组 `IAccessor` 。

## <a name="syntax"></a>语法

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>参数

*num*<br/>
指定访问器编号 (从零开始的整数索引) 。 必须使用整数或定义的值按递增顺序指定取值函数。

*auto*<br/>
一个布尔值，指定是否自动检索访问器 (TRUE) 或检索 (FALSE) 。

## <a name="remarks"></a>注解

**db_accessor** 为 `db_column` `db_param` 同一类或函数中的后续和属性定义基础 OLE DB 访问器。 **db_accessor** 可用于成员级别并用于对 `db_column` 参与基于 OLE DB 的绑定的属性进行分组 `IAccessor` 。 它与 `db_table` 或特性结合使用 `db_command` 。 调用此属性与调用 [BEGIN_ACCESSOR](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) 和 [END_ACCESSOR](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md#end_accessor) 宏类似。

**db_accessor** 生成行集，并将其绑定到相应的访问器映射。 如果未调用 **db_accessor**，则将自动生成访问器0，并且所有列绑定将映射到此访问器块。

**db_accessor** 将数据库列绑定分组到一个或多个访问器中。 有关需要使用多个访问器的方案的讨论，请参阅 [在行集上使用多个访问器](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。 另请参阅 [用户记录](../../data/oledb/user-records.md)中的 "用户记录支持多个访问器"。

当使用者特性提供程序将此特性应用于类时，编译器会将类重命名为 \_ *YourClassName*访问器，其中*YourClassName*是您赋予类的名称，并且编译器还将创建一个名为*YourClassName*的类，该类派生自 \_ *YourClassName*访问器。  将在类视图中看到这两个类。

## <a name="example"></a>示例

下面的示例使用 **db_accessor** 将 Orders 表中 Orders 表中的列分组为两个访问器。 访问器0是自动访问器，而访问器1不是。

```cpp
// cpp_attr_ref_db_accessor.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>

[ db_command(L"SELECT LastName, FirstName FROM Orders") ]
class CEmployees {
public:
   [ db_accessor(0, TRUE) ];
   [ db_column("1") ] LONG m_OrderID;
   [ db_column("2") ] TCHAR m_CustomerID[6];
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;

   [ db_accessor(1, FALSE) ];
   [ db_column("8") ] CURRENCY m_Freight;
};
```

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|属性块|
|**且**|否|
|**必需属性**|None|
|**无效的特性**|None|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者属性](ole-db-consumer-attributes.md)

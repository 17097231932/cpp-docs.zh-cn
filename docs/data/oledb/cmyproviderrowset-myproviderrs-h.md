---
description: '了解详细信息： CCustomRowset (CustomRS) '
title: CCustomRowset (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- ccustomrowset
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 87025be2a34f8c850bde2be53ab01519968654d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170459"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

向导将生成行集对象的条目。 在这种情况下，将调用此方法 `CCustomRowset` 。 `CCustomRowset`类继承自名为的 OLE DB 提供程序类 `CRowsetImpl` ，该类实现行集对象的所有必需接口。 下面的代码演示了用于的继承链 `CRowsetImpl` ：

```cpp
template <class T, class Storage, class CreatorClass,
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` 还使用 `IAccessor` 和 `IColumnsInfo` 接口。 它将这些接口用于表中的输出字段。 类还提供了的实现 `IRowsetIdentity` ，该实现允许使用者确定两行是否相同。 `IRowsetInfo`接口实现行集对象的属性。 `IConvertType`接口允许提供程序解析使用者请求的数据类型与提供程序使用的数据类型之间的差异。

`IRowset`接口实际处理数据检索。 使用者首先调用一个方法，该方法 `GetNextRows` 可将句柄返回到称为的行 `HROW` 。 然后，使用者调用 `IRowset::GetData` `HROW` 来检索所请求的数据。

`CRowsetImpl` 还使用几个模板参数。 这些参数可用于确定 `CRowsetImpl` 类处理数据的方式。 `ArrayType`参数允许您确定用于存储行数据的存储机制。 *RowClass* 参数指定包含哪个类 `HROW` 。

使用 *RowsetInterface* 参数，还可以使用 `IRowsetLocate` 或 `IRowsetScroll` 接口。 `IRowsetLocate`和 `IRowsetScroll` 接口都从继承 `IRowset` 。 因此，OLE DB 提供程序模板必须为这些接口提供特殊处理。 如果要使用这两个接口中的任何一个，则需要使用此参数。

## <a name="see-also"></a>请参阅

[提供程序 Wizard-Generated 文件](../../data/oledb/provider-wizard-generated-files.md)<br/>

---
description: '了解详细信息： ATL Database 类 (OLE DB 模板) '
title: ATL 数据库类（OLE DB 模板）
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: a9cc532a0b49f591cd08c70c398f8a37c08071ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213216"
---
# <a name="atl-database-classes-ole-db-templates"></a>ATL 数据库类（OLE DB 模板）

Microsoft 提供了多个 OLE DB 的实现，这是一组 COM 接口，提供对各种信息源和格式的数据的统一访问。

OLE DB 模板是 ATL 中的 c + + 模板，通过提供实现许多常用 OLE DB 接口的类，使 OLE DB 的数据库技术更易于使用。

此模板库包含以下两个部分：

- [OLE DB 使用者模板](../data/oledb/ole-db-consumer-templates-cpp.md) 用于实现 (使用者) 应用程序的 OLE DB 客户端。

- [OLE DB 提供程序模板](../data/oledb/ole-db-provider-templates-cpp.md) 用于实现 OLE DB server (提供程序) 应用程序。

此外， [OLE DB 使用者属性](../windows/attributes/ole-db-consumer-attributes.md) 提供了一种简便的方法来创建 OLE DB 使用者。 OLE DB 属性基于 OLE DB 使用者模板插入代码，以创建工作 OLE DB 使用者。

请注意，MFC 库包含一个类 [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)，用于在控件中显示数据库记录。 视图是直接连接到对象的窗体视图 `CRowset` ，并 `CRowset` 在对话框模板的控件中显示对象的字段。

有关详细信息，请参阅 [OLE DB 编程](../data/oledb/ole-db-programming.md) 和 [OLE DB 程序员指南](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)。

## <a name="see-also"></a>请参阅

[创建 OLE DB 使用者](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[创建 OLE DB 提供程序](../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 使用者模板参考](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 提供程序模板参考](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 模板示例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)

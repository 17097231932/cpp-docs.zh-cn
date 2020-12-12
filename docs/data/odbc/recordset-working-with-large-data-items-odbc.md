---
description: '了解详细信息：记录集：使用大型数据项 (ODBC) '
title: 记录集：处理大数据项 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 7a4ca6de9c0b5be32626c8ca3c7c66cc516057e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204363"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>记录集：处理大数据项 (ODBC)

本主题适用于 MFC ODBC 类和 MFC DAO 类。

> [!NOTE]
> 如果使用的是 MFC DAO 类，请使用类 [CByteArray](../../mfc/reference/cbytearray-class.md) （而不是类 [CLongBinary](../../mfc/reference/clongbinary-class.md)）管理大型数据项。 如果使用的是具有批量取行的 MFC ODBC 类，请使用 `CLongBinary` 而不是 `CByteArray` 。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

假设您的数据库可存储大量数据，如位图 (员工照片、地图、产品的图片、OLE 对象等) 。 此类数据通常称为二进制大型对象 (或 BLOB) ，因为：

- 每个字段值都很大。

- 不同于数字和其他简单数据类型，它没有可预测的大小。

- 从程序的角度来看，数据是 formless 的。

本主题介绍数据库类为处理此类对象提供的支持。

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a> 管理大型对象

记录集有两种方法可解决管理二进制大型对象的特别困难。 您可以使用类 [CByteArray](../../mfc/reference/cbytearray-class.md) ，也可以使用 [CLongBinary](../../mfc/reference/clongbinary-class.md)类。 通常， `CByteArray` 是管理大型二进制数据的首选方法。

`CByteArray` 需要更多的开销 `CLongBinary` ，但其功能更强，如 [CByteArray 类](#_core_the_cbytearray_class)中所述。 `CLongBinary` 在 [CLongBinary 类](#_core_the_clongbinary_class)中进行了简要说明。

有关使用 `CByteArray` 来处理大数据项的详细信息，请参阅 [技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a> CByteArray 类

`CByteArray` 是 MFC 集合类之一。 `CByteArray`对象存储动态字节数组，如有必要，数组可能会增长。 类通过索引提供快速访问，就像内置 c + + 数组一样。 `CByteArray` 出于诊断目的，可以序列化和转储对象。 类提供成员函数，用于获取和设置指定的字节、插入和追加字节以及删除一个字节或所有字节。 这些功能可以更轻松地分析二进制数据。 例如，如果二进制对象是 OLE 对象，则可能必须通过一些标头字节来访问实际对象。

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a> 在记录集中使用 CByteArray

通过向记录集的字段数据成员 `CByteArray` 提供类型，您可以提供一个固定的基， [RFX](../../data/odbc/record-field-exchange-rfx.md) 可以在记录集和数据源之间管理此类对象的传输，还可以通过这些对象处理对象中的数据。 RFX 需要特定站点来检索数据，并且您需要一种方法来访问基础数据。

有关使用 `CByteArray` 来处理大数据项的详细信息，请参阅 [技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a> CLongBinary 类

[CLongBinary](../../mfc/reference/clongbinary-class.md)对象是围绕 `HGLOBAL` 堆上分配的存储块的句柄的简单 shell。 当它绑定包含二进制大型对象的表列时，RFX `HGLOBAL` 会在需要将数据传输到记录集并将该句柄存储在记录集的字段中时分配该句柄 `CLongBinary` 。

反过来，您可以使用 `HGLOBAL` 句柄 `m_hData` 来处理数据本身，就像对任何句柄数据执行操作一样。 这是 [CByteArray](../../mfc/reference/cbytearray-class.md) 添加功能的地方。

> [!CAUTION]
> CLongBinary 对象不能用作函数调用中的参数。 此外，它们的实现（其调用 `::SQLGetData` ）一定会降低滚动快照的滚动性能。 当你 `::SQLGetData` 自行使用调用来检索动态架构列时，这也可能为 true。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集： (ODBC) 获取 Sum 和其他聚合结果 ](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[记录字段交换 (RFX) ](../../data/odbc/record-field-exchange-rfx.md)

---
description: '详细了解：用于记录滚动的命令处理程序 (MFC 数据访问) '
title: 用于记录滚动的命令处理程序（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 03fce51e7b045df0ae5ad1ceb0fa99eb98d0b7c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181379"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>用于记录滚动的命令处理程序（MFC 数据访问）

[CRecordView](../mfc/reference/crecordview-class.md)类提供了以下标准命令的默认命令处理：

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

`OnMove`成员函数为从记录到记录的所有四个命令提供默认命令处理。 发布这些命令后，RFX（或 DFX）将加载新记录到记录集字段，DDX 将移动值到记录窗体控件。 有关 RFX 的信息，请参阅 [记录字段交换 (RFX) ](../data/odbc/record-field-exchange-rfx.md)。

> [!NOTE]
> 确保将这些标准的命令 ID 用于任何与标准记录导航命令关联的用户界面对象。

## <a name="see-also"></a>请参阅

[支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)

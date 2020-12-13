---
description: '了解有关详细信息，请参阅应用程序向导创建的记录视图代码 (MFC 数据访问) '
title: 应用程序向导创建的记录视图代码（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: b0fa7a4960096f11ab66194fa6e41be60b45d4c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332441"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>应用程序向导创建的记录视图代码（MFC 数据访问）

[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)将重写视图的 `OnInitialUpdate` 和 `OnGetRecordset` 成员函数。 在框架创建框架窗口、文档和视图之后，将调用 `OnInitialUpdate` 以便初始化视图。 `OnInitialUpdate` 从文档获取指向记录集的指针。 对基类 [CView：： OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) 函数的调用会打开该记录集。 以下代码显示了的此过程 `CRecordView` ：

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

记录集打开时会选择记录。 [CRecordset：： Open](../mfc/reference/crecordset-class.md#open) 使第一条记录成为当前记录，并将数据从记录集的字段数据成员移到视图中的相应窗体控件。 有关 RFX 的详细信息，请参阅 [记录字段交换 (RFX) ](../data/odbc/record-field-exchange-rfx.md)。 有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。 有关文档/视图创建过程的信息，请参阅 [使用类编写适用于 Windows 的应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)。

> [!NOTE]
> 你应使你的最终用户有能力刷新记录集的记录视图控件。 若没有此能力，当用户将控件的值更改为非法值时，用户可能会永远停滞在当前的记录。 若要刷新控件，请 `CWnd` 使用参数 FALSE 调用成员函数 [UpdateData](../mfc/reference/cwnd-class.md#updatedata) 。

## <a name="see-also"></a>请参阅

[使用记录视图](../data/using-a-record-view-mfc-data-access.md)

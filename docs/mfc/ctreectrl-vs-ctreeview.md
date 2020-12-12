---
description: 了解详细信息： CTreeCtrl 和 CTreeView
title: CTreeCtrl 与CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: edaf2662d483a23c7618a143ee4aabe7910cf121
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309415"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl 与CTreeView

MFC 提供了两个用于封装树控件的类： [CTreeCtrl](reference/ctreectrl-class.md) 和 [CTreeView](reference/ctreeview-class.md)。 每个类在不同情况下都很有用。

`CTreeCtrl`需要普通的子窗口控件时使用; 例如，在对话框中。 `CTreeCtrl`如果窗口中存在其他子控件（如典型对话框），则特别需要使用。

`CTreeView`当你希望树控件在文档/视图体系结构和树控件中充当视图窗口时使用。 `CTreeView`将占用框架窗口或拆分器窗口的整个工作区。 它将在其父窗口调整大小时自动调整大小，并可处理菜单、快捷键和工具栏上的命令消息。 由于树控件包含显示树所需的数据，因此对应的文档对象不必太复杂，甚至可以使用 [CDocument](reference/cdocument-class.md) 作为文档模板中的文档类型。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](using-ctreectrl.md)<br/>
[控件](controls-mfc.md)

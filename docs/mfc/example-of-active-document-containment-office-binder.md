---
description: 了解详细信息：活动文档包含示例： Office 活页夹
title: 活动文档包含示例：Office 活页夹
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
ms.openlocfilehash: 075922f3a50df77f83aab90dc380e33f703737fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290825"
---
# <a name="example-of-active-document-containment-office-binder"></a>活动文档包含示例：Office 活页夹

Microsoft Office 活页夹是活动文档容器的示例。 Office 活页夹包含两个主窗格，就像容器通常一样。 左窗格包含与将活页夹中的活动文档对应的图标。 每个文档都被称为活页夹中的一个 *部分* 。 例如，活页夹可能包含 Word 文档、PowerPoint 文件、Excel 电子表格等。

单击左窗格中的图标可激活对应的活动文档。 活页夹的右窗格随后会显示当前选择的活动文档的内容。

如果您在活页夹中打开并激活 Word 文档，Word 菜单栏和工具栏将出现在视图框架的顶部，您可以使用任何 Word 命令或工具编辑文档的内容。 但是，该菜单栏是活页夹的菜单栏和 Word 的菜单栏的组合。 由于活页夹和 Word 都有 " **帮助** " 菜单，因此会合并相应菜单的内容。 Office 活页夹等活动文档容器自动提供 " **帮助** " 菜单合并;有关详细信息，请参阅 " [帮助" 菜单合并](help-menu-merging.md)。

当您选择另一个应用程序类型的活动文档时，活页夹的界面将会更改以适应活动文档的应用程序类型的界面。 例如，如果活页夹包含 Excel 电子表格，您将发现活页夹中的菜单在您选择 Excel 电子表格部分时发生了更改。

当然，除活页夹外还可能有其他类型的容器。 文件资源管理器使用典型的双窗格界面，其中，左窗格使用树控件来显示驱动器或网络中的目录的分层列表，右窗格显示当前选择的目录中包含的文件。 Internet 浏览器类型的容器 (例如 Microsoft Internet Explorer) ，而不是使用双窗格界面，通常具有一个框架，并提供使用超链接的导航。

## <a name="see-also"></a>请参阅

[活动文档包容](active-document-containment.md)

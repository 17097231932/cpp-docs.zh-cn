---
description: 了解有关以下内容的详细信息：容器：实现容器
title: 容器：实现容器
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 24e3c7f7d4546ebe9b103af0e9ca0d9694b25d2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310316"
---
# <a name="containers-implementing-a-container"></a>容器：实现容器

本文总结了实现容器的过程，向您指出了提供有关实现容器的更多详细介绍的其他文章。 它还列出了您可能需要实现的一些可选 OLE 功能以及描述这些功能的文章。

#### <a name="to-prepare-your-cwinapp-derived-class"></a>准备 CWinApp 派生类

1. 通过 `AfxOleInit` 在成员函数中调用来初始化 OLE 库 `InitInstance` 。

1. 调用 `CDocTemplate::SetContainerInfo` 中的 `InitInstance` 分配在就地激活嵌入项时使用的菜单和快捷键资源。 有关此主题的详细信息，请参阅 [激活](activation-cpp.md)。

当您使用 MFC 应用程序向导创建容器应用程序时，将为您自动提供这些功能。 请参阅 [创建 MFC EXE 程序](reference/mfc-application-wizard.md)。

#### <a name="to-prepare-your-view-class"></a>准备视图类

1. 如果您支持多个选择成为选定项，则通过维护指针或指针列表来跟踪选定项。 您的 `OnDraw` 函数必须绘制所有 OLE 项。

1. 重写 `IsSelected` 来检查当前是否选择了传递到它的项。

1. 实现 `OnInsertObject` 消息处理程序以显示 " **插入对象** " 对话框。

1. 实现 `OnSetFocus` 消息处理程序以将焦点从视图转移到就地活动 OLE 嵌入项。

1. 实现 `OnSize` 消息处理程序以通知 OLE 嵌入项，它需要更改其矩形才能反映其包含视图的大小更改。

由于这些功能的实现在各应用程序之间差异巨大，因此应用程序向导仅提供基本实现。 您可能必须自定义这些函数才能让应用程序正常工作。 有关此示例的示例，请参阅 [容器](../overview/visual-cpp-samples.md) 示例。

#### <a name="to-handle-embedded-and-linked-items"></a>处理嵌入项和链接项

1. 从 [COleClientItem](reference/coleclientitem-class.md)派生类。 此类的对象表示已嵌入或已链接到 OLE 文档的项。

1. 重写 `OnChange` 、 `OnChangeItemPosition` 和 `OnGetItemPosition` 。 这些函数处理嵌入项和链接项的大小调整、定位和修改。

应用程序向导将为你派生类，但你可能需要在 `OnChange` 前面的过程中的步骤2中重写并列出此类函数。 需要为大部分应用程序自定义主干实现，因为这些函数在各应用程序之间的实现是不同的。 有关这种情况的示例，请参阅 MFC 示例 [DRAWCLI](../overview/visual-cpp-samples.md) 和 [CONTAINER](../overview/visual-cpp-samples.md)。

您必须将大量项添加到容器应用程序的菜单结构才能支持 OLE。 有关这些功能的详细信息，请参阅 [菜单和资源：添加容器](menus-and-resources-container-additions.md)。

您可能还想在容器应用程序中支持下列某些功能：

- 在编辑嵌入项时就地激活。

   有关详细信息，请参阅 [激活](activation-cpp.md)。

- 通过从服务器应用程序拖放选择来创建 OLE 项。

   有关详细信息，请参阅 [OLE 拖放](drag-and-drop-ole.md)。

- 链接到嵌入对象或组合容器/服务器应用程序。

   有关详细信息，请参阅 [容器：高级功能](containers-advanced-features.md)。

## <a name="see-also"></a>请参阅

[容器](containers.md)<br/>
[容器：客户端项](containers-client-items.md)

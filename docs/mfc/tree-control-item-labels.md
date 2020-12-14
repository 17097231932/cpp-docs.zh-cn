---
description: 了解详细信息：树控件项标签
title: 树控件项标签
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
ms.openlocfilehash: 62113a7534bf234ac8dde1154d5732bc29df8387
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264059"
---
# <a name="tree-control-item-labels"></a>树控件项标签

在将项添加到树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 时，通常指定项的标签文本。 `InsertItem`成员函数可以传递定义项的属性的[TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw)结构，包括包含标签文本的字符串。 `InsertItem` 具有多个重载，可通过参数的各种组合进行调用。

树形控件分配存储每个项的内存;项标签的文本占据了此内存的重要部分。 如果你的应用程序在树控件中维护字符串的副本，则可以通过在或 LpszItem 参数的 *pszText* 成员中指定 **LPSTR_TEXTCALLBACK** 值， `TV_ITEM` 而不是将实际字符串传递到树控件，来降低控件的内存需求。 使用 **LPSTR_TEXTCALLBACK** 会使树控件在每次需要重绘项时从应用程序检索项的标签文本。 为检索文本，树控件将发送 [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) 通知消息，其中包括 [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) 结构的地址。 您必须通过设置所包含结构的相应成员来做出响应。

树控件使用从创建树控件的进程的堆分配的内存。 树控件中的最大项数取决于堆中的可用内存量。 每个项都采用64字节。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

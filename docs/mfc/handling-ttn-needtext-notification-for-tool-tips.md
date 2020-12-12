---
description: 了解详细信息：处理工具提示的 TTN_NEEDTEXT 通知
title: 处理工具提示的 TTN_NEEDTEXT 通知
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: 793f6c42e0e43c341884b999e5e1aed0be448b00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326413"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>处理工具提示的 TTN_NEEDTEXT 通知

作为 [启用工具提示](enabling-tool-tips.md)的一部分，你可以通过将以下条目添加到所有者窗口的消息映射来处理 **TTN_NEEDTEXT** 消息：

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
此按钮需要文本时调用的成员函数。

请注意，工具提示的 ID 始终为0。

在类定义中声明处理函数，如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#53](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

斜体参数如下：

*id*<br/>
发送通知的控件的标识符。 未使用。 控件 id 取自 **NMHDR** 结构。

*pNMHDR*<br/>
指向 [NMTTDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow) 结构的指针。 [TOOLTIPTEXT 结构](tooltiptext-structure.md)中还进一步讨论了此结构。

*pResult*<br/>
指向可在返回之前设置的结果代码的指针。 **TTN_NEEDTEXT** 处理程序可以忽略 *pResult* 参数。

作为窗体视图通知处理程序的示例：

[!code-cpp[NVC_MFCControlLadenDialog#54](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

`EnableToolTips`从) 中调用 (此片段 `OnInitDialog` ：

[!code-cpp[NVC_MFCControlLadenDialog#55](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>请参阅

[Windows 中不是从 CFrameWnd 派生的工具提示](tool-tips-in-windows-not-derived-from-cframewnd.md)

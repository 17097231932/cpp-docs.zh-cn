---
description: 了解详细信息： WM_ 消息处理程序： N-O
title: WM_ 消息处理程序：N - O
ms.date: 11/04/2016
f1_keywords:
- ON_WM_NCHITTEST
- ON_WM_NCLBUTTONDOWN
- ON_WM_NCCALCSIZE
- ON_WM_NCLBUTTONUP
- ON_WM_NCPAINT
- ON_WM_NCMBUTTONUP
- ON_WM_NCCREATE
- ON_WM_NCACTIVATE
- ON_WM_NCMOUSEMOVE
- ON_WM_NCRBUTTONDBLCLK
- ON_WM_NCLBUTTONDBLCLK
- ON_WM_NCDESTROY
- ON_WM_NCMBUTTONDBLCLK
- ON_WM_NCRBUTTONDOWN
- ON_WM_NCRBUTTONUP
- ON_WM_NCMBUTTONDOWN
helpviewer_keywords:
- ON_WM_NCCALCSIZE [MFC]
- ON_WM_NCMBUTTONDOWN [MFC]
- ON_WM_NCRBUTTONDBLCLK [MFC]
- ON_WM_NCMBUTTONDBLCLK [MFC]
- ON_WM_NCLBUTTONDBLCLK [MFC]
- ON_WM_NCDESTROY [MFC]
- ON_WM_NCRBUTTONDOWN [MFC]
- ON_WM_NCLBUTTONDOWN [MFC]
- ON_WM_NCCREATE [MFC]
- ON_WM_NCRBUTTONUP [MFC]
- ON_WM_NCLBUTTONUP [MFC]
- ON_WM_NCPAINT [MFC]
- ON_WM_NCACTIVATE [MFC]
- ON_WM_NCHITTEST [MFC]
- ON_WM_NCMOUSEMOVE [MFC]
- ON_WM_NCMBUTTONUP [MFC]
- WM_ messages
ms.assetid: 4efd1cda-b642-4e8b-89e8-73255fa70d77
ms.openlocfilehash: 2f70bd0d019b4cdc9557c87c3ae0bb51e330723f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218311"
---
# <a name="wm_-message-handlers-n---o"></a>WM_ 消息处理程序：N - O

下面左侧的映射条目对应于右侧的函数原型：

|映射条目|函数原型|
|---------------|------------------------|
|ON_WM_NCACTIVATE ( # A1|afx_msg BOOL [OnNcActivate](../../mfc/reference/cwnd-class.md#onncactivate) (bool) ;|
|ON_WM_NCCALCSIZE ( # A1|afx_msg void [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize) (BOOL，NCCALCSIZE_PARAMS FAR * ) ;|
|ON_WM_NCCREATE ( # A1|afx_msg BOOL [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate) (LPCREATESTRUCT) ;|
|ON_WM_NCDESTROY ( # A1|afx_msg void [OnNcDestroy](../../mfc/reference/cwnd-class.md#onncdestroy) ( # A1;|
|ON_WM_NCHITTEST ( # A1|afx_msg LRESULT [OnNcHitTest](../../mfc/reference/cwnd-class.md#onnchittest) (CPoint) ;|
|ON_WM_NCLBUTTONDBLCLK ( # A1|afx_msg void [OnNcLButtonDblClk](../../mfc/reference/cwnd-class.md#onnclbuttondblclk) (UINT，CPoint) ;|
|ON_WM_NCLBUTTONDOWN ( # A1|afx_msg void [OnNcLButtonDown](../../mfc/reference/cwnd-class.md#onnclbuttondown) (UINT，CPoint) ;|
|ON_WM_NCLBUTTONUP ( # A1|afx_msg void [OnNcLButtonUp](../../mfc/reference/cwnd-class.md#onnclbuttonup) (UINT，CPoint) ;|
|ON_WM_NCMBUTTONDBLCLK ( # A1|afx_msg void [OnNcMButtonDblClk](../../mfc/reference/cwnd-class.md#onncmbuttondblclk) (UINT，CPoint) ;|
|ON_WM_NCMBUTTONDOWN ( # A1|afx_msg void [OnNcMButtonDown](../../mfc/reference/cwnd-class.md#onncmbuttondown) (UINT，CPoint) ;|
|ON_WM_NCMBUTTONUP ( # A1|afx_msg void [OnNcMButtonUp](../../mfc/reference/cwnd-class.md#onncmbuttonup) (UINT，CPoint) ;|
|ON_WM_NCMOUSEHOVER ( # A1|afx_msg void [OnNcMouseHover](../../mfc/reference/cwnd-class.md#onncmousehover) (UINT，CPoint) ;|
|ON_WM_NCMOUSELEAVE ( # A1|afx_msg void [OnNcMouseLeave](../../mfc/reference/cwnd-class.md#onncmouseleave) ( # A1;|
|ON_WM_NCMOUSEMOVE ( # A1|afx_msg void [OnNcMouseMove](../../mfc/reference/cwnd-class.md#onncmousemove) (UINT，CPoint) ;|
|ON_WM_NCPAINT ( # A1|afx_msg void [OnNcPaint](../../mfc/reference/cwnd-class.md#onncpaint) ( # A1;|
|ON_WM_NCRBUTTONDBLCLK ( # A1|afx_msg void [OnNcRButtonDblClk](../../mfc/reference/cwnd-class.md#onncrbuttondblclk) (UINT，CPoint) ;|
|ON_WM_NCRBUTTONDOWN ( # A1|afx_msg void [OnNcRButtonDown](../../mfc/reference/cwnd-class.md#onncrbuttondown) (UINT，CPoint) ;|
|ON_WM_NCRBUTTONUP ( # A1|afx_msg void [OnNcRButtonUp](../../mfc/reference/cwnd-class.md#onncrbuttonup) (UINT，CPoint) ;|
|ON_WM_NCXBUTTONDBLCLK ( # A1|void [OnNcXButtonDblClk](../../mfc/reference/cwnd-class.md#onncxbuttondblclk) (SHORT，UINT，CPoint) ;|
|ON_WM_NCXBUTTONDOWN ( # A1|afx_msg void [OnNcXButtonDown](../../mfc/reference/cwnd-class.md#onncxbuttondown) (SHORT，UINT，CPoint) ;|
|ON_WM_NCXBUTTONUP ( # A1|afx_msg void [OnNcXButtonUp](../../mfc/reference/cwnd-class.md#onncxbuttonup) (SHORT，UINT，CPoint) ;|
|ON_WM_NEXTMENU ( # A1|afx_msg void [OnNextMenu](../../mfc/reference/cwnd-class.md#onnextmenu) (UINT，LPMDINEXTMENU) ;|
|ON_WM_NOTIFYFORMAT ( # A1|afx_msg UINT [OnNotifyFormat](../../mfc/reference/cwnd-class.md#onnotifyformat) (CWnd *，UINT) ;|

## <a name="see-also"></a>请参阅

[消息映射](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ 消息的处理程序](../../mfc/reference/handlers-for-wm-messages.md)

---
description: 了解详细信息：管理当前视图
title: 管理当前视图
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
ms.openlocfilehash: 9c9acd315636ea33c52fbe63374b5afacef95247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283337"
---
# <a name="managing-the-current-view"></a>管理当前视图

作为框架窗口默认实现的一部分，框架窗口将记录当前活动视图。 如果框架窗口包含多个视图，例如在拆分器窗口中，则当前视图是正在使用中的最新视图。 活动视图独立于 Windows 中的活动窗口或当前输入焦点。

当活动视图发生更改时，框架会通过调用其 [OnActivateView](reference/cview-class.md#onactivateview) 成员函数来通知当前视图。 您可以通过检查 `OnActivateView` 的 *bActivate* 参数来判断视图是否正在激活或停用。 默认情况下，`OnActivateView` 会将焦点设置为处于激活状态的当前视图。 您可以重写 `OnActivateView`，以在停用或重新激活视图时执行任何特殊处理。 例如，您可能需要提供特殊可视提示来区分活动视图与其他非活动视图。

框架窗口将命令转发到其当前 (active) 视图中，如 [命令路由](command-routing.md)中所述，作为标准命令路由的一部分。

## <a name="see-also"></a>请参阅

[使用框架窗口](using-frame-windows.md)

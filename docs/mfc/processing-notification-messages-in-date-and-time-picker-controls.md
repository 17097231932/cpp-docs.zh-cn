---
description: 了解详细信息：处理日期和时间选取器控件中的通知消息
title: 处理日期和时间选取器控件中的通知消息
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: 07ac9c4c8ba58c833591409b1f5ab405cd05ebc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154820"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>处理日期和时间选取器控件中的通知消息

当用户与日期和时间选取器控件交互时，控件 (`CDateTimeCtrl`) 将通知消息发送到其父窗口，通常是视图或对话框对象。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户打开日期和时间选择器以显示嵌入的月历控件时，将发送 DTN_DROPDOWN 通知。

使用 [类向导](reference/mfc-class-wizard.md) 将通知处理程序添加到要实现的那些消息的父类。

以下列表描述了日期和时间选择器控件发送的各种通知。

- DTN_DROPDOWN 通知父级将要显示嵌入的月日历控件。 此通知仅在未设置 DTS_UPDOWN 样式的情况下发送。 有关此通知的详细信息，请参阅 [访问嵌入月历控件](accessing-the-embedded-month-calendar-control.md)。

- DTN_CLOSEUP 向父项通知嵌入的 "月份日历" 控件即将关闭。 此通知仅在未设置 DTS_UPDOWN 样式的情况下发送。

- DTN_DATETIMECHANGE 通知父控件中发生了更改。

- DTN_FORMAT 通知父项需要在回调字段中显示文本。 有关此通知和回调字段的详细信息，请参阅 [在日期和时间选取器控件中使用回调字段](using-callback-fields-in-a-date-and-time-picker-control.md)。

- DTN_FORMATQUERY 请求父对象以提供将在回调字段中显示的字符串的最大允许大小。 处理此通知后，控件可以随时正确显示输出，从而减少控件显示内的闪烁。 有关此通知的详细信息，请参阅 [在日期和时间选取器控件中使用回调字段](using-callback-fields-in-a-date-and-time-picker-control.md)。

- DTN_USERSTRING 通知父级用户已完成日期和时间选择器控件的内容编辑。 仅当设置了 DTS_APPCANPARSE 样式时才会发送此通知。

- 当用户键入回调字段时，DTN_WMKEYDOWN 通知父级。 处理此通知，以在日期和时间选取器控件中模拟非回调字段所支持的相同键盘响应。 有关此通知的详细信息，请参阅在 Windows SDK 中的 [DTP 控件中支持回拨字段](/windows/win32/Controls/date-and-time-picker-controls) 。

## <a name="see-also"></a>请参阅

[使用 CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[控件](controls-mfc.md)

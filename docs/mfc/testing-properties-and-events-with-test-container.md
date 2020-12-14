---
description: 了解详细信息：用测试容器测试属性和事件
title: 使用测试容器测试属性和事件
ms.date: 11/04/2016
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
ms.openlocfilehash: 61cccbda723fb1cfac0ca3fc696639849bde9dd1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216218"
---
# <a name="testing-properties-and-events-with-test-container"></a>使用测试容器测试属性和事件

Visual C++ 中附带的测试容器应用程序是用于测试和调试 ActiveX 控件的 ActiveX 控件容器。 利用测试容器，控件开发人员可以通过更改控件的属性、调用控件的方法和激发其控件的事件来测试控件的功能。 测试容器可以显示数据绑定通知记录，还可以提供用于测试 ActiveX 控件的持久性功能的工具：您可以将属性保存到流或子存储，重载它们，然后检查存储的流数据。 本节介绍如何使用测试容器的基本功能。 有关其他信息，请在运行测试容器时选择 " **帮助** " 菜单。

### <a name="to-access-the-activex-control-test-container"></a>访问 ActiveX 控件测试容器

1. 生成 [TSTCON 示例： ActiveX 控件测试容器](../overview/visual-cpp-samples.md)。

### <a name="to-test-your-activex-control"></a>测试 ActiveX 控件

1. 在测试容器的 " **编辑** " 菜单上，单击 " **插入新控件**"。

1. 在 " **插入控件** " 框中，选择所需控件并单击 **"确定"**。 控件将出现在控件容器中。

    > [!NOTE]
    >  如果控件未列在 "**插入控件**" 对话框中，请确保已使用测试容器的 "**文件**" 菜单中的 "**注册控件**" 命令注册了控件。

此时，你可以测试控件的属性或事件。

#### <a name="to-test-properties"></a>测试属性

1. 在 " **控件** " 菜单上，单击 " **调用方法**"。

1. 在 " **方法名称** " 下拉列表中，选择要测试的属性的 PropPut 方法。

1. 修改 **参数值** 或 **参数类型** ，然后单击 " **设置值** " 按钮。

1. 单击 " **调用** " 将新值应用到对象。

   属性现在包含新值。

#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>测试事件并指定事件信息的目标。

1. 在 " **选项** " 菜单上，单击 " **日志记录**"。

1. 指定事件信息的目标。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[如何：调试 ActiveX 控件](/visualstudio/debugger/how-to-debug-an-activex-control)

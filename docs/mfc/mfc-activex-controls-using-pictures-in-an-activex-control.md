---
description: 了解更多相关信息： MFC ActiveX 控件：在 ActiveX 控件中使用图片
title: MFC ActiveX 控件：在 ActiveX 控件中使用图片
ms.date: 11/04/2016
f1_keywords:
- LPPICTUREDISP
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
ms.openlocfilehash: 9c9989be7503eb449b969fbbf37d92f26c165131
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133076"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>MFC ActiveX 控件：在 ActiveX 控件中使用图片

本文介绍常见的图片类型以及如何在 ActiveX 控件中实现该图片类型。 主题包括：

- [自定义图片属性的概述](#_core_overview_of_custom_picture_properties)

- [在 ActiveX 控件中实现自定义图片属性](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [向控件项目添加内容](#_core_additions_to_your_control_project)

## <a name="overview-of-custom-picture-properties"></a><a name="_core_overview_of_custom_picture_properties"></a> 自定义图片属性的概述

图片类型是部分 ActiveX 控件常见的一组类型中的一种。 图片类型处理元文件、位图或图标，并允许用户指定要在 ActiveX 控件中显示的图片。 自定义图片属性使用图片对象以及允许控制用户访问图片属性的 Get/Set 函数实现。 控制用户可通过常用图片属性页访问自定义图片属性。

除标准图片类型外，还提供字体和颜色类型。 有关如何在 ActiveX 控件中使用标准字体类型的详细信息，请参阅 [MFC ActiveX 控件：使用字体](mfc-activex-controls-using-fonts.md)一文。

ActiveX 控件类提供了若干组件，可用于在控件内实现图片属性。 这些组件包括：

- [CPictureHolder](reference/cpictureholder-class.md) 类。

   通过该类，可轻松访问自定义图片属性所显示项的图片对象和功能。

- 支持 **LPPICTUREDISP** 类型的属性，并通过 Get/Set 函数实现。

   通过“类视图”，可以快速添加一个或多个支持图片类型的自定义属性。 有关如何通过“类视图”添加 ActiveX 控件属性的详细信息，请参阅 [MFC ActiveX 控件：属性](mfc-activex-controls-properties.md)一文。

- 属性页用于操作控件的一个或多个图片属性。

   此属性页是 ActiveX 控件可以使用的一组常用属性页的一部分。 有关 ActiveX 控件属性页的详细信息，请参阅 [MFC ActiveX 控件：使用常用属性页](mfc-activex-controls-using-stock-property-pages.md)一文

## <a name="implementing-a-custom-picture-property-in-your-activex-control"></a><a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a> 在 ActiveX 控件中实现自定义图片属性

完成本部分中概述的步骤后，该控件将可以显示用户选定的图片。 用户可以通过属性页更改显示的图片，该属性页显示当前图片并具有“浏览”按钮，可让用户选择其他图片。

自定义图片属性的实现过程与其他属性类似，主要区别在于自定义属性必须支持图片类型。 由于图片属性的项必须由 ActiveX 控件绘制，因此在完全实现该属性之前，必须对其进行大量的添加和修改。

若要实现自定义图片属性，必须执行以下操作：

- [向控件项目添加代码](#_core_additions_to_your_control_project)。

   必须添加标准图片属性页 ID、 `CPictureHolder`类型的数据成员，以及包含 Get/Set 实现的 **LPPICTUREDISP** 类型的自定义属性。

- [修改控件类中的若干函数](#_core_modifications_to_your_control_project)。

   对用于绘制 ActiveX 控件的若干函数进行修改。

## <a name="additions-to-your-control-project"></a><a name="_core_additions_to_your_control_project"></a> 向控件项目添加内容

若要添加标准图片属性页的属性页 ID，请将以下行插入到控件实现文件 ( 中的 BEGIN_PROPPAGEIDS 宏之后。CPP) ：

[!code-cpp[NVC_MFC_AxPic#1](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

还必须将 BEGIN_PROPPAGEIDS 宏的计数参数递增1。 下面一行阐释了这一点：

[!code-cpp[NVC_MFC_AxPic#2](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

若要将 `CPictureHolder` 数据成员添加到控件类，请在控件头文件 (.H) 中的控件类声明的受保护部分下插入下面一行：

[!code-cpp[NVC_MFC_AxPic#3](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

不需要将数据成员命名 *m_pic*;任何名称都足够了。

接下来，添加支持图片类型的自定义属性：

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>使用“添加属性向导”添加自定义图片属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 从快捷菜单中选择“添加”  ，然后选择“添加属性” 。

1. 在“属性名称”  框中，键入属性名称。 本过程中使用 `ControlPicture` 作为示例。

1. 在 "**属性类型**" 框中，选择 " **IPictureDisp** <strong>\*</strong> " 作为属性类型。

1. 对于“实现类型” ，请单击“Get/Set 方法” 。

1. 为 Get 和 Set 函数键入唯一名称或接受默认名称。 （在本例中，使用默认名称 `GetControlPicture` 和 `SetControlPicture` 。）

1. 单击“完成”。

“添加属性向导”在控件头文件 (.H) 的调度映射注释之间添加了以下代码：

[!code-cpp[NVC_MFC_AxPic#4](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

此外，还在控件实现文件 (.CPP) 的调度映射中插入了以下代码：

[!code-cpp[NVC_MFC_AxPic#5](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

“添加属性向导”还在控件实现文件中添加了以下两个存根函数：

[!code-cpp[NVC_MFC_AxPic#6](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
> 你的控件类和函数名称可能与上面的示例不同。

### <a name="modifications-to-your-control-project"></a><a name="_core_modifications_to_your_control_project"></a> 修改控件项目的内容

对控件项目进行必要的添加后，需要修改几个影响 ActiveX 控件的呈现的函数。 这些函数、 `OnResetState`、 `OnDraw`以及自定义属性的 Get/Set 函数位于控件实现文件中。  (请注意，在此示例中，调用了 control 类 `CSampleCtrl` ， `CPictureHolder` 数据成员 *m_pic*，而自定义图片属性名称为 `ControlPicture` 。 ) 

在控件的 `OnResetState` 函数中，在 `COleControl::OnResetState`的调用后添加以下可选行：

[!code-cpp[NVC_MFC_AxPic#7](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

这会将控件的图片设置为空白图片。

若要正确绘制图片，请确保在控件的 [函数中调用](reference/cpictureholder-class.md#render) CPictureHolder::Render `OnDraw` 。 按下面的示例修改函数：

[!code-cpp[NVC_MFC_AxPic#8](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

在控件的自定义图片属性的 Get 函数中，添加下面一行：

[!code-cpp[NVC_MFC_AxPic#9](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

在控件的自定义图片属性的 Set 函数中，添加下面一行：

[!code-cpp[NVC_MFC_AxPic#10](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

图片属性必须设置为永久属性，以确保设计时添加的信息将在运行时显示。 将下面一行添加到 `COleControl`派生类的 `DoPropExchange` 函数：

[!code-cpp[NVC_MFC_AxPic#11](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
> 你的类和函数名称可能与上面的示例不同。

完成修改后，重新生成项目以整合自定义图片属性的新功能并使用测试容器对新属性进行测试。 请参阅 [使用测试容器测试属性和事件](testing-properties-and-events-with-test-container.md) 了解有关如何访问测试容器的信息。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：使用字体](mfc-activex-controls-using-fonts.md)<br/>
[MFC ActiveX 控件：属性页](mfc-activex-controls-property-pages.md)

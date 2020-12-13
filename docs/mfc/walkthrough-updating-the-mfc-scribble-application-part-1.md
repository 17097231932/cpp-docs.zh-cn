---
description: '了解详细信息：演练：更新 MFC 自由曲线应用程序 (第1部分) '
title: '演练：更新 MFC 自由曲线应用程序 (第1部分) '
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: bb60e535031670eddc84e7170431ad6622d434b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142969"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>演练：更新 MFC 自由曲线应用程序 (第1部分) 

本演练演示如何修改现有 MFC 应用程序以使用功能区用户界面。 Visual Studio 支持 Office 2007 功能区和 Windows 7 Scenic 功能区。 有关功能区用户界面的详细信息，请参阅 [功能区](/windows/win32/uxguide/cmd-ribbons)。

本演练将修改经典自由曲线 1.0 MFC 示例，该示例使你可以使用鼠标创建线条绘图。 本部分演练演示如何修改随意画图示例，使其显示功能区栏。 [第2部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) 将更多按钮添加到功能区栏。

## <a name="prerequisites"></a>先决条件

[自由曲线 1.0 MFC 示例](https://github.com/microsoft/VCSamples/tree/master/VC2010Samples/MFC/general/Scribble)。 有关转换为 Visual Studio 2017 或更高版本的帮助，请参阅 [移植指南： MFC 自由曲线](../porting/porting-guide-mfc-scribble.md)。

## <a name="sections"></a><a name="top"></a> 个

本部分演练包含以下各节：

- [替换基类](#replaceclass)

- [向项目中添加位图](#addbitmap)

- [向项目添加功能区资源](#addribbon)

- [创建功能区栏的实例](#createinstance)

- [添加功能区类别](#addcategory)

- [设置应用程序的外观](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a> 替换基类

若要将支持菜单的应用程序转换为支持功能区的应用程序，则必须从更新的基类派生应用程序、框架窗口和工具栏类。  (建议您不要修改原始自由曲线示例。 相反，请清除自由曲线项目，将其复制到另一个目录，然后修改复制。 ) 

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>替换自由曲线应用程序中的基类

1. 在 "随意"，验证是否 `CScribbleApp::InitInstance` 包含对 [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)的调用。

1. 将以下代码添加到 (Visual Studio 2017 和更早) 版本中的 *stdafx.h* *文件：*

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. 在 "随意画图" 中，修改类的定义， `CScribbleApp` 使其派生自 [CWinAppEx 类](../mfc/reference/cwinappex-class.md)。

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. 当 Windows 应用程序使用初始化 ( .ini) 文件保存用户首选项数据时，将编写自由曲线1.0。 在注册表中修改 "自由曲线" 以存储用户首选项，而不是初始化文件。 若要设置注册表项和基，请在 `CScribbleApp::InitInstance` 语句后面键入以下代码 `LoadStdProfileSettings()` 。

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. 多文档界面 (MDI) 应用程序的主框架不再派生自 `CMDIFrameWnd` 类。 而是派生自 [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) 类。

    在 mainfrm.cpp 和 mainfrm.cpp 文件中，将对的所有引用替换为 `CMDIFrameWnd` `CMDIFrameWndEx` 。

1. 在 childfrm 和 childfrm 文件中，将替换 `CMDIChildWnd` 为 `CMDIChildWndEx` 。

    在 childfrm 中。 h 文件，将替换 `CSplitterWnd` 为 `CSplitterWndEx` 。

1. 修改工具栏和状态栏以使用新的 MFC 类。

    在 mainfrm.cpp 文件中：

    1. 将 `CToolBar` 替换为 `CMFCToolBar`。

    1. 将 `CStatusBar` 替换为 `CMFCStatusBar`。

1. 在 mainfrm.cpp 文件中：

    1. 将 `m_wndToolBar.SetBarStyle` 替换为 `m_wndToolBar.SetPaneStyle`

    1. 将 `m_wndToolBar.GetBarStyle` 替换为 `m_wndToolBar.GetPaneStyle`

    1. 将 `DockControlBar(&m_wndToolBar)` 替换为 `DockPane(&m_wndToolBar)`

1. 在 ipframe 文件中，注释掉以下三行代码。

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. 保存更改，然后生成并运行应用程序。

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a> 向项目中添加位图

本演练的后续四个步骤需要位图资源。 可以通过多种方式获取适当的位图：

- 使用 [资源编辑器](../windows/resource-editors.md) 来创造自己的位图。 或者使用资源编辑器，通过可移植网络图形组装位图， ( .png) 包含在 Visual Studio 中的映像，并且可以从 [Visual studio 图像库](/visualstudio/designers/the-visual-studio-image-library)下载。

    但 **功能区** 用户界面需要某些位图支持透明图像。 透明位图使用32位像素，其中24位指定颜色的红色、绿色和蓝色分量，8位定义指定颜色透明度的 *alpha 通道* 。 当前资源编辑器可以查看，但不能修改包含32位像素的位图。 因此，请使用外部图像编辑器而不是资源编辑器来操作透明位图。

- 将相应的资源文件从另一个应用程序复制到项目，然后从该文件导入位图。

本演练将从在 [演练：使用 MFC 创建功能区应用程序](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)中创建的示例中复制资源文件。

### <a name="to-add-bitmaps-to-the-project"></a>向项目中添加位图

1. 使用文件资源管理器将以下 .bmp 文件从 "资源目录" (`res`) 功能区示例的 "资源目录" 复制到 " `res` 自由曲线项目 () 的资源目录：

   1. 将 main.bmp 复制到随意绘制的项目。

   1. 将 filesmall.bmp 和 filelarge.bmp 复制到随意绘制的项目。

   1. filelarge.bmp 和 filesmall.bmp 文件创建新副本，但将副本保存在功能区示例中。 重命名 homesmall.bmp 和 homelarge.bmp 的副本，然后将副本移到随意绘制的项目。

   1. 创建 toolbar.bmp 文件的副本，但将副本保存在功能区示例中。 重命名 panelicons.bmp 的副本，然后将该副本移到你的自由曲线项目。

1. 导入 MFC 应用程序的位图。 在 **资源视图** 中，双击 " **自由曲线** " 节点，双击该 **位图** 节点，然后单击 " **添加资源**"。 在出现的对话框中，单击 " **导入**"。 浏览到 `res` 目录，选择 main.bmp 文件，然后单击 " **打开**"。

   main.bmp 位图包含26x26 图像。 将位图的 ID 更改为 `IDB_RIBBON_MAIN` 。

1. 导入附加到 **应用程序** 按钮的 "文件" 菜单的位图。

   1. 导入 filesmall.bmp 文件，其中包含11个 16x16 (16x176) 映像。 将位图的 ID 更改为 `IDB_RIBBON_FILESMALL` 。

   > [!NOTE]
   > 由于我们只需 (16x128) 的前八个16x16 图像，因此，可以选择将此位图的右端宽度从176裁剪为128。

   1. 导入 filelarge.bmp，其中包含九个 32x32 (32x288) 映像。 将位图的 ID 更改为 `IDB_RIBBON_FILELARGE` 。

1. 导入功能区类别和面板的位图。 功能区栏上的每个选项卡都是一个类别，由一个文本标签和一个可选图像组成。

   1. 导入 homesmall.bmp 位图，其中包含小按钮位图的11个16x16 图像。 将位图的 ID 更改为 `IDB_RIBBON_HOMESMALL` 。

   1. 导入 homelarge.bmp 位图，其中包含用于大按钮位图的九个32x32 图像。 将位图的 ID 更改为 `IDB_RIBBON_HOMELARGE` 。

1. 导入已调整大小的功能区面板的位图。 如果功能区太小而无法显示整个面板，则在调整大小操作后使用这些位图或面板图标。

   1. 导入 panelicons.bmp 位图，其中包含八个16x16 图像。 在 **位图编辑器** 的 "**属性**" 窗口中，将位图的宽度调整为 64 (16x64) 。 将位图的 ID 更改为 `IDB_PANEL_ICONS` 。

   > [!NOTE]
   > 由于我们只需 (16x64) 的前四个16x16 图像，因此，你可以选择将此位图的右端宽度从128裁剪为64。

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a> 向项目添加功能区资源

将使用菜单的应用程序转换为使用功能区的应用程序时，不必删除或禁用现有菜单。 只需创建一个功能区资源，添加功能区按钮，然后将新按钮与现有菜单项相关联。 尽管菜单不再可见，但功能区栏中的消息通过菜单和菜单快捷方式进行路由。

功能区包含 **应用程序** 按钮，该按钮是功能区左上角的大按钮，还有一个或多个类别选项卡。 每个类别选项卡都包含一个或多个作为功能区按钮和控件的容器的面板。 下面的过程演示如何创建功能区资源，然后自定义 **应用程序** 按钮。

### <a name="to-add-a-ribbon-resource-to-the-project"></a>向项目添加功能区资源

1. 在 **解决方案资源管理器** 中选择自由曲线项目后，在 " **项目** " 菜单中，单击 " **添加资源**"。

1. 在 " **添加资源** " 对话框中，选择 " **功能区** "，然后单击 " **新建**"。

   Visual Studio 将创建一个功能区资源并在 "设计" 视图中打开它。 功能区资源 ID 是 `IDR_RIBBON1` ，它显示在 **资源视图** 中。 功能区包含一个类别和一个面板。

1. 可以通过修改 **应用程序** 按钮的属性来自定义该按钮。 此代码中使用的消息 Id 已在 "随意画图 1.0" 的菜单中定义。

1. 在 "设计" 视图中，单击 " **应用程序** " 按钮以显示其属性。 更改属性值，如下所示： "**图像** 到"、"提示"、"要更改的 `IDB_RIBBON_MAIN`  `File`  `f` **大型图像**" `IDB_RIBBON_FILELARGE` 和 "**小型图像** 到" `IDB_RIBBON_FILESMALL` 。

1. 以下修改创建用户单击 **应用程序** 按钮时显示的菜单。 单击 "**主要项**" 旁边的 **省略号 ("**) " 以打开 "**项编辑器**"。

   1. 在选中 " **项** 类型" **按钮** 的情况下，单击 " **添加** " 以添加一个按钮。 将 **标题** 更改为，将 "ID" 更改为，并将图像更改为 `&New`  `ID_FILE_NEW`  `0` **大** 到 `0` 。

   1. 单击 " **添加** " 以添加一个按钮。 将 **标题** 更改为，将 "ID" 更改为，并将图像更改为 `&Save`  `ID_FILE_SAVE`  `2` **大** 到 `2` 。

   1. 单击 " **添加** " 以添加一个按钮。 将 **标题** 更改为，将 "ID" 更改为，并将图像更改为 `Save &As`  `ID_FILE_SAVE_AS`  `3` **大** 到 `3` 。

   1. 单击 " **添加** " 以添加一个按钮。 将 **标题** 更改为，将 "ID" 更改为，并将图像更改为 `&Print`  `ID_FILE_PRINT`  `4` **大** 到 `4` 。

   1. 将 **项目** 类型更改为 " **分隔符** "，然后单击 " **添加**"。

   1. 将 **项** 类型更改为 **按钮**。 单击 " **添加** " 以添加第五个按钮。 将 **标题** 更改为，将 "ID" 更改为，并将图像更改为 `&Close`  `ID_FILE_CLOSE`  `5` **大** 到 `5` 。

1. 以下修改将在上一步中创建的 " **打印** " 按钮下创建一个子菜单。

   1. 单击 " **打印** " 按钮，将 " **项** 类型" 更改为 " **标签**"，然后单击 " **插入**"。 将 **标题** 更改为 `Preview and print the document` 。

   1. 单击 " **打印** " 按钮，将 " **项** 类型" 更改为 " **按钮**"，然后单击 " **插入**"。 将 **标题** 更改为，将 "ID" 更改为，并将图像更改为 `&Print`  `ID_FILE_PRINT`  `4` **大** 到 `4` 。

   1. 单击 " **打印** " 按钮，然后单击 " **插入** " 以添加一个按钮。 将 **标题** 更改为，将 "ID" 更改为，并将图像更改为 `&Quick Print`  `ID_FILE_PRINT_DIRECT`  `7` **大** 到 `7` 。

   1. 单击 " **打印** " 按钮，然后单击 " **插入** " 以添加其他按钮。 将 **标题** 更改为，将 "ID" 更改为，并将图像更改为 `Print Pre&view`  `ID_FILE_PRINT_PREVIEW`  `6` **大** 到 `6` 。

   1. 你现在已经修改了 **主要项**。 单击 " **关闭** " 退出 **项编辑器**。

1. 以下修改创建显示在 **应用程序** 按钮菜单底部的 "退出" 按钮。

   1. 选择 **解决方案资源管理器** 中的 "**资源视图**" 选项卡。
   1. 在 "**属性**" 窗口中，单击 "**按钮**" 旁边的 **省略号 ("**) " 以打开 "**项编辑器**"。

   1. 在选中 " **项** 类型" **按钮** 的情况下，单击 " **添加** " 以添加一个按钮。 将 **标题** 更改为，并将其更改为 `E&xit`  `ID_APP_EXIT`  `8` 。

   1. 您已经修改了这些 **按钮**。 单击 " **关闭** " 退出 **项编辑器**。

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a> 创建功能区栏的实例

以下步骤演示如何在应用程序启动时创建功能区栏的实例。 若要向应用程序添加功能区栏，请在 mainfrm.cpp 文件中声明功能区栏。 然后，在 mainfrm.cpp 文件中，编写用于加载功能区资源的代码。

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>创建功能区栏的实例

1. 在 mainfrm.cpp 文件中，将一个数据成员添加到的 "受保护" 部分 `CMainFrame` ，即主框架的类定义。 此成员用于功能区栏。

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. 在 mainfrm.cpp 文件中，将以下代码添加到函数末尾的最后一个 **`return`** 语句前面 `CMainFrame::OnCreate` 。 它创建功能区栏的实例。

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a> 自定义功能区资源

现在，你已创建 **应用程序** 按钮，可以将元素添加到功能区。

> [!NOTE]
> 本演练为所有面板使用同一个面板图标。 但是，您可以使用其他图像列表索引来显示其他图标。

### <a name="to-add-a-home-category-and-edit-panel"></a>添加 "主页" 类别和 "编辑" 面板

1. 自由曲线程序只需要一个类别。 在 "设计" 视图的 " **工具箱**" 中，双击 " **类别** " 添加一个并显示其属性。 更改属性值，如下所示： " **标题** `&Home` "、" **大图像** 到 `IDB_RIBBON_HOMELARGE` "、" **小图像** 到" `IDB_RIBBON_HOMESMALL` 。

1. 每个功能区类别都组织为命名面板。 每个面板都包含一组用于完成相关操作的控件。 此类别有一个面板。 单击 **"面板**"，然后将 " **标题** " 更改为 `Edit` 。

1. 在 " **编辑** " 面板中，添加负责清除文档内容的按钮。 此按钮的消息 ID 已经在 `IDR_SCRIBBTYPE` 菜单资源中定义。 指定 `Clear All` 为按钮文本和修饰按钮的位图的索引。 打开 " **工具箱**"，然后将一个 **按钮** 拖到 " **编辑** " 面板。 单击该按钮，然后将 `Clear All`  `ID_EDIT_CLEAR_ALL`  `0` **大图像索引** 改为，并将 "标题" 更改为 "索引到"，将 "索引" 更改为 `0` 。

1. 保存更改，然后生成并运行该应用程序。 应显示自由曲线应用程序，并且它应在窗口顶部而不是菜单栏上具有功能区栏。 功能区栏应具有一个 "类别 **"、"****主页**" 和 "**主页**"。 添加的功能区按钮应与现有的事件处理程序相关联，" **打开**"、" **关闭**"、" **保存**"、" **打印**" 和 " **全部清除** " 按钮应按预期方式工作。

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a> 设置应用程序的外观

*可视化管理器* 是一个控制应用程序的所有绘图的全局对象。 由于原始自由曲线应用程序使用 Office 2000 用户界面 (UI) 样式，因此应用程序可能看起来更老。 可以重置应用程序以使用 Office 2007 视觉对象管理器，使其与 Office 2007 应用程序类似。

### <a name="to-set-the-look-of-the-application"></a>设置应用程序的外观

1. 在 `CMainFrame::OnCreate` 函数中，在语句前键入以下代码， `return 0;` 以更改默认视觉对象管理器和样式。

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. 保存更改，然后生成并运行该应用程序。 应用程序 UI 应与 Office 2007 UI 类似。

## <a name="next-steps"></a>后续步骤

你修改了经典的自由曲线 1.0 MFC 示例以使用 **功能区设计器**。 现在，请跳到 [第2部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。

## <a name="see-also"></a>请参阅

[演练](../mfc/walkthroughs-mfc.md)<br/>
[演练：更新 MFC 自由曲线应用程序 (第2部分) ](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)

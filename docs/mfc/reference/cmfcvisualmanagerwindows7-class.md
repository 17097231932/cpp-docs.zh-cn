---
description: 了解详细信息： CMFCVisualManagerWindows7 类
title: CMFCVisualManagerWindows7 类
ms.date: 03/27/2019
f1_keywords:
- CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::OnFillMenuImageRect
helpviewer_keywords:
- CMFCVisualManagerWindows7 Class [MFC]
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
ms.openlocfilehash: 108d4144bbcfbfcb82d91678611435f14365302e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331631"
---
# <a name="cmfcvisualmanagerwindows7-class"></a>CMFCVisualManagerWindows7 类

`CMFCVisualManagerWindows7`为应用程序提供了 Windows 7 应用程序的外观。

## <a name="syntax"></a>语法

```
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7)|默认构造函数。|
|[CMFCVisualManagerWindows7：： ~ CMFCVisualManagerWindows7](#_dtorcmfcvisualmanagerwindows7)|默认析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|`CMFCVisualManagerWindows7::CleanStyle`|清除当前视觉样式并重置默认视觉样式。|
|`CMFCVisualManagerWindows7::CleanUp`|清除用户界面中的所有对象，并重置菜单。|
|`CMFCVisualManagerWindows7::DrawNcBtn`|在框架上的非工作区中绘制一个按钮。 框架使用此方法来绘制窗口框架右上角的 "最小化"、"最大化"、"关闭" 和 "还原" 按钮。 仅当程序使用主题时，才调用此方法 `Aero` 。|
|`CMFCVisualManagerWindows7::DrawNcText`|在框架上的非工作区中绘制文本。 框架使用此方法在框架窗口顶部的标题栏中绘制应用程序标题。|
|`CMFCVisualManagerWindows7::DrawSeparator`|在 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)上绘制分隔符。|
|`CMFCVisualManagerWindows7::GetRibbonBar`|检索与用户界面关联的 [CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md) 。|
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](#getribboneditbackgroundcolor)|获取功能区编辑框背景色。|
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|重写 [CMFCVisualManager：： GetRibbonPopupBorderSize](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|重写 [CMFCVisualManager：： GetRibbonQuickAccessToolBarChevronOffset](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|重写 [CMFCVisualManager：： GetRibbonQuickAccessToolBarRightMargin](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin)|
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|重写 [CMFCVisualManagerWindows：： IsHighlightWholeMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem)|
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|重写 [CMFCVisualManager：： IsOwnerDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck)|
|`CMFCVisualManagerWindows7::IsRibbonPresent`|确定是否 `CMFCRibbonBar` 存在且可见。|
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|重写 [CMFCVisualManagerWindows：： OnDrawButtonBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|重写 [CMFCVisualManagerWindows：： OnDrawCheckBoxEx](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex)|
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|重写 [CMFCVisualManagerWindows：： OnDrawComboDropButton](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton)|
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|重写 [CMFCVisualManager：： OnDrawDefaultRibbonImage](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage)|
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|重写 [CMFCVisualManagerWindows：： OnDrawMenuBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder)|
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|重写 [CMFCVisualManager：： OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)|
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|重写 [CMFCVisualManager：： OnDrawMenuLabel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel)|
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|重写 `CMFCVisualManager::OnDrawRadioButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|重写 [CMFCVisualManager：： OnDrawRibbonApplicationButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|重写 [CMFCVisualManager：： OnDrawRibbonButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|重写 [CMFCVisualManager：： OnDrawRibbonCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|重写 [CMFCVisualManager：： OnDrawRibbonCaptionButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|重写 [CMFCVisualManager：： OnDrawRibbonCategory](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|重写 [CMFCVisualManager：： OnDrawRibbonCategoryTab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)|
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|重写 [CMFCVisualManager：： OnDrawRibbonDefaultPaneButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|重写 [CMFCVisualManager：： OnDrawRibbonGalleryButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|重写 `CMFCVisualManager::OnDrawRibbonLaunchButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|重写 [CMFCVisualManager：： OnDrawRibbonMenuCheckFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|重写 [CMFCVisualManager：： OnDrawRibbonPanel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|重写 [CMFCVisualManager：： OnDrawRibbonPanelCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|重写 [CMFCVisualManager：： OnDrawRibbonProgressBar](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)|
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|重写 [CMFCVisualManager：： OnDrawRibbonRecentFilesFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|重写 [CMFCVisualManager：： OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|重写 [CMFCVisualManager：： OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|重写 [CMFCVisualManager：： OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|重写 [CMFCVisualManager：： OnDrawRibbonStatusBarPane](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane)|
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|重写 [CMFCVisualManager：： OnDrawRibbonTabsFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe)|
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|重写 [CMFCVisualManagerWindows：： OnDrawStatusBarSizeBox](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox)|
|`CMFCVisualManagerWindows7::OnFillBarBackground`|重写 [CMFCVisualManagerWindows：： OnFillBarBackground](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground)|
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|重写 [CMFCVisualManagerWindows：： OnFillButtonInterior](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior)|
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](#onfillmenuimagerect)|框架在填充菜单项图像的区域时调用此方法。|
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|重写 [CMFCVisualManager：： OnFillRibbonButton](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton)|
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|重写 [CMFCVisualManager：： OnFillRibbonQuickAccessToolBarPopup](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup)|
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|重写 [CMFCVisualManagerWindows：： OnHighlightMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem)|
|`CMFCVisualManagerWindows7::OnNcActivate`|重写 [CMFCVisualManager：： OnNcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate)|
|`CMFCVisualManagerWindows7::OnNcPaint`|重写 [CMFCVisualManager：： OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint)|
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|重写 [CMFCVisualManagerWindows：： OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors)|
|`CMFCVisualManagerWindows7::SetResourceHandle`|设置描述可视管理器的属性的资源句柄。|
|`CMFCVisualManagerWindows7::SetStyle`|设置 GUI 的配色方案 `CMFCVisualManagerWindows7` 。|

## <a name="remarks"></a>备注

使用 `CMFCVisualManagerWindows7` 类更改应用程序的外观，以模拟默认的 Windows 7 应用程序。 如果你的应用程序在 Windows 7 之前的 Windows 版本上运行，则此类可能无效。 在这种情况下，应用程序将使用在 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)中定义的默认可视化管理器。

CMFCVisualManagerWindows7 继承了 [CMFCVisualManagerWindows 类](../../mfc/reference/cmfcvisualmanagerwindows-class.md) 和类中的多个方法 `CMFCVisualManager` 。 上一部分中列出的方法是类的新方法 `CMFCVisualManagerWindows7` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

`CMFCVisualManagerWindows7`

## <a name="requirements"></a>要求

**标头：** afxvisualmanagerwindows7

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="_dtorcmfcvisualmanagerwindows7"></a> CMFCVisualManagerWindows7：： ~ CMFCVisualManagerWindows7

默认析构函数。

```
virtual ~CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="cmfcvisualmanagerwindows7"></a> CMFCVisualManagerWindows7::CMFCVisualManagerWindows7

默认构造函数。

```
CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7getribboneditbackgroundcolor"></a><a name="getribboneditbackgroundcolor"></a> CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor

获取功能区编辑框的背景色。

```
virtual COLORREF GetRibbonEditBackgroundColor (
    CMFCRibbonRichEditCtrl* pEdit,
    BOOL bIsHighlighted,
    BOOL bIsPaneHighlighted,
    BOOL bIsDisabled);
```

### <a name="parameters"></a>parameters

*pEdit*<br/>
中指向编辑控件的指针。 此值不能为 NULL。

*bIsHighlighted*<br/>
弄返回是否突出显示功能区框。

*bIsPaneHighlighted*<br/>
弄如果突出显示了包含 *pEdit* 的功能区面板，则返回 TRUE。

*bIsDisabled*<br/>
弄返回是否禁用 *pEdit* 。

### <a name="return-value"></a>返回值

编辑框 *pEdit* 的背景色。

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagerwindows7onfillmenuimagerect"></a><a name="onfillmenuimagerect"></a> CMFCVisualManagerWindows7::OnFillMenuImageRect

当框架围绕菜单项图像填充区域时，框架会调用此方法。

```
virtual void OnFillMenuImageRect(
    CDC* pDC,
    CMFCToolBarButton* pButton,
    CRect rectangle,
    CMFCVisualManager::AFX_BUTTON_STATE state);
```

### <a name="parameters"></a>parameters

*pDC*<br/>
中指向菜单按钮的设备上下文的指针。

*pButton*<br/>
中指向的指针 `CMFCToolBarButton` 。 框架将填充此按钮的背景。

*矩形*<br/>
中指定菜单按钮图像区域边界的矩形。

*state*<br/>
中按钮状态。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerWindows 类](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

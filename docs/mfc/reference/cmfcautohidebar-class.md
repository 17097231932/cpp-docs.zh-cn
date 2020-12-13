---
description: 了解详细信息： CMFCAutoHideBar 类
title: CMFCAutoHideBar 类
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
ms.openlocfilehash: d7cea85a71b8390520d1345e12000aa700026269
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336600"
---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHideBar 类

`CMFCAutoHideBar` 类是实现自动隐藏功能的特殊工具栏类。

有关更多详细信息，请参阅位于 Visual Studio 安装的 **VC \\ atlmfc \\ src \\ mfc** 文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCAutoHideBar : public CPane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)| (重写 [CBasePane：： CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。 ) |
|[CMFCAutoHideBar::Create](#create)|创建一个控件栏并将其附加到 [CPane](../../mfc/reference/cpane-class.md) 对象。  (重写 [CPane：： Create](../../mfc/reference/cpane-class.md#create). ) |
|[CMFCAutoHideBar：： GetFirstAHWindow](#getfirstahwindow)||
|[CMFCAutoHideBar：： GetVisibleCount](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|当即将显示特殊窗格菜单时由框架调用。  (重写 [CPane：： OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)。 ) |
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)| (重写 [CPane：： SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup)。 ) |
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::StretchPane](#stretchpane)|垂直或水平拉伸窗格。  (重写 [CBasePane：： StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane)。 ) |
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|当用户将鼠标光标置于 [CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md) 上时和框架显示关联窗口的时刻之间的时间延迟。|

## <a name="remarks"></a>备注

当用户将停靠窗格切换为自动隐藏模式时，框架会自动创建 `CMFCAutoHideBar` 对象。 它还创建必要的 [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) 和 [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) 对象。 每个 `CAutoHideDockSite` 对象都与单个 `CMFCAutoHideButton` 关联。

`CMFCAutoHideBar` 类在用户鼠标悬停在 `CMFCAutoHideButton` 上方时实现 `CAutoHideDockSite` 的显示。 当工具栏收到 WM_MOUSEMOVE 消息时，`CMFCAutoHideBar` 会启动计时器。 当计时器完成时，它会向工具栏发送 WM_TIMER 事件通知。 工具栏通过检查鼠标指针是否位于它在计时器启动时所处的相同自动隐藏按钮上，来处理此事件。 如果是，则显示附加的 `CAutoHideDockSite`。

可以通过设置 `m_nShowAHWndDelay` 来控制计时器延迟的长度。 默认值为 400 毫秒。

## <a name="example"></a>示例

下列示例演示如何构造 `CMFCAutoHideBar` 对象并使用其 `GetDockSiteRow` 方法。

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)

## <a name="requirements"></a>要求

**标头：** afxautohidebar.h

## <a name="cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a> CMFCAutoHideBar：： AddAutoHideWindow

向 `CDockablePane` 窗口添加让它能够自动隐藏的功能。

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>parameters

*pAutoHideWnd*<br/>
中要隐藏的窗口。

*dwAlignment*<br/>
中用于指定自动隐藏按钮与应用程序窗口对齐方式的值。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

*DwAlignment* 参数指示自动隐藏按钮位于应用程序中的位置。 该参数可为下列任一值：

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a> CMFCAutoHideBar：： AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a> CMFCAutoHideBar：： CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>parameters

中 *bStretch*<br/>

中 *bHorz*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a> CMFCAutoHideBar：： CMFCAutoHideBar

构造 CMFCAutoHideBar 对象。

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarcreate"></a><a name="create"></a> CMFCAutoHideBar：： Create

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>parameters

*lpszClassName*<br/>

*dwStyle*<br/>

*rect*<br/>

*pParentWnd*<br/>

*nID*<br/>

*dwControlBarStyle*<br/>

*pContext*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a> CMFCAutoHideBar：： GetFirstAHWindow

返回指向应用程序中的第一个自动隐藏窗口的指针。

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>返回值

应用程序中第一个自动隐藏窗口，如果不存在则为 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a> CMFCAutoHideBar：： GetVisibleCount

获取可见自动隐藏按钮的数目。

```
int GetVisibleCount();
```

### <a name="return-value"></a>返回值

返回可见自动隐藏按钮的数目。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarm_nshowahwnddelay"></a><a name="m_nshowahwnddelay"></a> CMFCAutoHideBar：： m_nShowAHWndDelay

当用户将鼠标光标置于 [CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md) 上时和框架显示关联窗口的时刻之间的时间延迟。

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>备注

当用户将鼠标光标置于上时 `CMFCAutoHideButton` ，框架会在显示关联的窗口之前稍微延迟一些。 此参数确定延迟的长度（以毫秒为单位）。

## <a name="cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a> CMFCAutoHideBar：： OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>parameters

中 *CPoint*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a> CMFCAutoHideBar：： RemoveAutoHideWindow

删除并销毁自动隐藏窗口。

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>parameters

CDockablePane * *pAutoHideWnd* 要删除的自动隐藏窗口。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a> CMFCAutoHideBar：： SetActiveInGroup

将自动隐藏栏标记为活动。

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>parameters

中如果设置为活动，则为布尔值 *bActive* TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

请参阅 [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup)。

## <a name="cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a> CMFCAutoHideBar：： SetRecentVisibleState

```cpp
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>parameters

bState <br/>
中要设置的状态。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a> CMFCAutoHideBar：： ShowAutoHideWindow

显示自动隐藏窗口。

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>parameters

*pAutoHideWnd*<br/>
中要显示的窗口。

*bShow*<br/>
中若要显示窗口，则为 TRUE。

*bDelay*<br/>
中忽略此参数。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarstretchpane"></a><a name="stretchpane"></a> CMFCAutoHideBar：： StretchPane

调整自动隐藏栏在其折叠状态下的大小，以适应 `CMFCAutoHideButton` 对象。

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>parameters

*nLength*<br/>
中在基实现中未使用该值。 在派生的实现中，使用此值可指示已调整大小的窗格的长度。

*bVert*<br/>
中在基实现中未使用该值。 在派生的实现中，使用 TRUE 处理自动隐藏栏垂直折叠的情况，对于自动隐藏栏水平折叠的情况，请使用 FALSE。

### <a name="return-value"></a>返回值

已调整大小的窗格的最终大小。

### <a name="remarks"></a>备注

派生的类可以替代此方法以自定义该行为。

## <a name="cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a> CMFCAutoHideBar：： UnSetAutoHideMode

对一组自动隐藏栏禁用自动隐藏模式。

```cpp
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>parameters

[in] pFirstBarInGroup 指向组中第一个自动隐藏栏的指针。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a> CMFCAutoHideBar：： UpdateVisibleState

由框架在需要重绘自动隐藏栏时调用。

```cpp
void UpdateVisibleState();
```

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPane 类](../../mfc/reference/cpane-class.md)<br/>
[CAutoHideDockSite 类](../../mfc/reference/cautohidedocksite-class.md)<br/>
[CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)

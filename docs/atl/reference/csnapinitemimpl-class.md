---
description: 了解详细信息： CSnapInItemImpl 类
title: CSnapInItemImpl 类
ms.date: 11/04/2016
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: c1c63f5b60d57743087bffde214d9b8addef5b8b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140551"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl 类

此类提供用于实现管理单元节点对象的方法。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>parameters

*T*<br/>
派生自的类 `CSnapInItemImpl` 。

*bIsExtension*<br/>
如果对象是管理单元扩展，则为 TRUE;否则为 FALSE。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|将菜单项添加到上下文菜单。|
|[CSnapInItemImpl：：命令](#command)|当选择自定义菜单项时由控制台调用。|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|向管理单元的属性表添加页。|
|[CSnapInItemImpl::FillData](#filldata)|将管理单元对象上的信息复制到指定的流中。|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|检索 `RESULTDATAITEM` 管理单元的结构。|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|确定 "结果" 窗格使用的视图类型。|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|检索 `SCOPEDATAITEM` 管理单元的结构。|
|[CSnapInItemImpl：： Notify](#notify)|由控制台调用以通知用户执行的操作的管理单元。|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|调用以查看管理单元节点是否支持属性页。|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|修改管理单元对象的菜单插入标志。|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|设置指定工具栏按钮的信息。|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|更新上下文菜单项的状态。|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|更新指定工具栏按钮的状态。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CSnapInItemImpl：： m_bstrDisplayName](#m_bstrdisplayname)|管理单元对象的名称。|
|[CSnapInItemImpl：： m_resultDataItem](#m_resultdataitem)|`RESULTDATAITEM`对象使用的 Windows 结构 `CSnapInItemImpl` 。|
|[CSnapInItemImpl：： m_scopeDataItem](#m_scopedataitem)|`SCOPEDATAITEM`对象使用的 Windows 结构 `CSnapInItemImpl` 。|

## <a name="remarks"></a>备注

`CSnapInItemImpl` 为管理单元节点对象（如将菜单项和工具栏以及管理单元节点的转发命令添加到适当的处理程序函数）提供基本实现。 这些功能是使用多种不同的接口和映射类型实现的。 默认实现通过确定派生类的正确实例，然后将该消息转发到正确的实例来处理发送到 node 对象的通知。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>要求

**标头：** atlsnap

## <a name="csnapinitemimpladdmenuitems"></a><a name="addmenuitems"></a> CSnapInItemImpl::AddMenuItems

此方法实现 Win32 函数 [IExtendContextMenu：： AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)。

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>parameters

*piCallback*<br/>
中指向的指针 `IContextMenuCallback` ，它可以将项添加到上下文菜单中。

*pInsertionAllowed*<br/>
[in，out]标识 Microsoft 管理控制台 (MMC) 定义的，可使用的菜单项插入点。 这可以是以下标志的组合：

- 可在上下文菜单顶部插入 CCM_INSERTIONALLOWED_TOP 项。

- 可以在 "创建新的" 子菜单中插入 CCM_INSERTIONALLOWED_NEW 项。

- 可以在 "任务" 子菜单中插入 CCM_INSERTIONALLOWED_TASK 项。

- CCM_INSERTIONALLOWED_VIEW 项可插入 "工具栏视图" 菜单或 "结果" 窗格上下文菜单的 "视图" 子菜单中。

type<br/>
中指定对象的类型。 可以具有以下一个值：

- CCT_SCOPE 作用域窗格上下文的数据对象。

- CCT_RESULT "结果" 窗格上下文的数据对象。

- CCT_SNAPIN_MANAGER 管理单元管理器上下文的数据对象。

- CCT_UNINITIALIZED 数据对象具有无效的类型。

## <a name="csnapinitemimplcommand"></a><a name="command"></a> CSnapInItemImpl：：命令

此方法实现 Win32 函数 [IExtendContextMenu：： Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command)。

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>parameters

*lCommandID*<br/>
中指定菜单项的命令标识符。

type<br/>
中指定对象的类型。 可以具有以下一个值：

- CCT_SCOPE 作用域窗格上下文的数据对象。

- CCT_RESULT "结果" 窗格上下文的数据对象。

- CCT_SNAPIN_MANAGER 管理单元管理器上下文的数据对象。

- CCT_UNINITIALIZED 数据对象具有无效的类型。

## <a name="csnapinitemimplcreatepropertypages"></a><a name="createpropertypages"></a> CSnapInItemImpl::CreatePropertyPages

此方法实现 Win32 函数 [IExtendPropertySheet：： CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2)。

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>parameters

*lpProvider*<br/>
中指向接口的指针 `IPropertySheetCallback` 。

*柄*<br/>
中指定用于将 MMCN_PROPERTY_CHANGE 通知消息路由到适当数据类的句柄。

*pUnk*<br/>
中指向 `IExtendPropertySheet` 对象上的接口的指针，该接口包含有关节点的上下文信息。

type<br/>
中指定对象的类型。 可以具有以下一个值：

- CCT_SCOPE 作用域窗格上下文的数据对象。

- CCT_RESULT "结果" 窗格上下文的数据对象。

- CCT_SNAPIN_MANAGER 管理单元管理器上下文的数据对象。

- CCT_UNINITIALIZED 数据对象具有无效的类型。

## <a name="csnapinitemimplcsnapinitemimpl"></a><a name="csnapinitemimpl"></a> CSnapInItemImpl::CSnapInItemImpl

构造 `CSnapInItemImpl` 对象。

```
CSnapInItemImpl();
```

## <a name="csnapinitemimplfilldata"></a><a name="filldata"></a> CSnapInItemImpl::FillData

调用此函数可检索有关项的信息。

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>parameters

*cf*<br/>
中格式 (文本、格式文本或包含剪贴板) OLE 项的多格式文本。

*pStream*<br/>
中指向包含对象数据的流的指针。

### <a name="remarks"></a>备注

若要正确实现此功能，请将正确的信息复制到 stream (*pStream*) ，具体取决于 *Cf* 指示的剪贴板格式。

## <a name="csnapinitemimplgetresultviewtype"></a><a name="getresultviewtype"></a> CSnapInItemImpl::GetResultViewType

调用此函数可检索管理单元对象的结果窗格的视图类型。

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>parameters

*ppViewType*<br/>
弄指向返回的视图类型的地址的指针。

*pViewOptions*<br/>
弄指向 MMC_VIEW_OPTIONS 枚举的指针，该枚举为控制台提供由拥有的管理单元指定的选项。 此值可以为下列值之一：

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 通知控制台避免在 " **视图** " 菜单中显示标准列表视图选项。 允许管理单元仅在 "结果视图" 窗格中显示自己的自定义视图。 这是目前定义的唯一选项标志。

- MMC_VIEW_OPTIONS_NONE = 0 允许默认视图选项。

## <a name="csnapinitemimplgetscopepaneinfo"></a><a name="getscopepaneinfo"></a> CSnapInItemImpl::GetScopePaneInfo

调用此函数可检索 `SCOPEDATAITEM` 管理单元的结构。

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>parameters

*pScopeDataItem*<br/>
弄指向 `SCOPEDATAITEM` 对象的结构的指针 `CSnapInItemImpl` 。

## <a name="csnapinitemimplgetresultpaneinfo"></a><a name="getresultpaneinfo"></a> CSnapInItemImpl::GetResultPaneInfo

调用此函数可检索 `RESULTDATAITEM` 管理单元的结构。

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>parameters

*pResultDataItem*<br/>
弄指向 `RESULTDATAITEM` 对象的结构的指针 `CSnapInItemImpl` 。

## <a name="csnapinitemimplm_bstrdisplayname"></a><a name="m_bstrdisplayname"></a> CSnapInItemImpl：： m_bstrDisplayName

包含为节点项显示的字符串。

```
CComBSTR m_bstrDisplayName;
```

## <a name="csnapinitemimplm_scopedataitem"></a><a name="m_scopedataitem"></a> CSnapInItemImpl：： m_scopeDataItem

`SCOPEDATAITEM`管理单元数据对象的结构。

```
SCOPEDATAITEM m_scopeDataItem;
```

## <a name="csnapinitemimplm_resultdataitem"></a><a name="m_resultdataitem"></a> CSnapInItemImpl：： m_resultDataItem

管理单元数据对象的 [RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem) 结构。

```
RESULTDATAITEM m_resultDataItem;
```

## <a name="csnapinitemimplnotify"></a><a name="notify"></a> CSnapInItemImpl：： Notify

当用户对管理单元对象进行操作时调用。

```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```

### <a name="parameters"></a>parameters

*event*<br/>
中标识用户执行的操作。 可以执行以下通知：

- MMCN_ACTIVATE 在窗口被激活和停用时发送。

- MMCN_ADD_IMAGES 发送到将图像添加到 "结果" 窗格。

- 当用户单击某个工具栏按钮时，MMCN_BTN_CLICK 发送。

- 当用户在列表视图项上单击鼠标按钮时，MMCN_CLICK 发送。

- MMCN_DBLCLICK 用户双击列表视图项上的鼠标按钮时发送。

- MMCN_DELETE 发送，通知管理单元应删除对象。

- MMCN_EXPAND 在需要扩展或收缩文件夹时发送。

- MMCN_MINIMIZED 在窗口最小化或最大化时发送。

- MMCN_PROPERTY_CHANGE 发送，通知管理单元对象视图将要更改的管理单元对象。

- 当管理单元必须删除在指定节点下面添加的整个子树时，MMCN_REMOVE_CHILDREN 发送。

- MMCN_RENAME 第一次进行重命名查询时发送，并再次执行重命名。

- MMCN_SELECT 在 "作用域" 或 "结果视图" 窗格中选择某项时发送。

- MMCN_SHOW 第一次选中或取消选择作用域项时发送。

- MMCN_VIEW_CHANGE 在发生更改时管理单元更新所有视图时发送。

*与我们联系*<br/>
中取决于通知类型。

*param*<br/>
中取决于通知类型。

*pComponentData*<br/>
弄指向实现的对象的指针 `IComponentData` 。 如果未从转发通知，则此参数为 NULL `IComponentData::Notify` 。

*pComponent*<br/>
弄指向实现的对象的指针 `IComponent` 。 如果未从转发通知，则此参数为 NULL `IComponent::Notify` 。

type<br/>
中指定对象的类型。 可以具有以下一个值：

- CCT_SCOPE 作用域窗格上下文的数据对象。

- CCT_RESULT "结果" 窗格上下文的数据对象。

- CCT_SNAPIN_MANAGER 管理单元管理器上下文的数据对象。

- CCT_UNINITIALIZED 数据对象具有无效的类型。

## <a name="csnapinitemimplquerypagesfor"></a><a name="querypagesfor"></a> CSnapInItemImpl::QueryPagesFor

调用以查看管理单元节点是否支持属性页。

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

## <a name="csnapinitemimplsetmenuinsertionflags"></a><a name="setmenuinsertionflags"></a> CSnapInItemImpl::SetMenuInsertionFlags

调用此函数可修改 *pInsertionAllowed* 为管理单元对象指定的菜单插入标志。

```cpp
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>parameters

*bBeforeInsertion*<br/>
中如果在将项添加到上下文菜单之前应调用函数，则为非零值;否则为0。

*pInsertionAllowed*<br/>
[in，out]标识 Microsoft 管理控制台 (MMC) 定义的，可使用的菜单项插入点。 这可以是以下标志的组合：

- 可在上下文菜单顶部插入 CCM_INSERTIONALLOWED_TOP 项。

- 可以在 "创建新的" 子菜单中插入 CCM_INSERTIONALLOWED_NEW 项。

- 可以在 "任务" 子菜单中插入 CCM_INSERTIONALLOWED_TASK 项。

- CCM_INSERTIONALLOWED_VIEW 项可插入 "工具栏视图" 菜单或 "结果" 窗格上下文菜单的 "视图" 子菜单中。

### <a name="remarks"></a>备注

如果要开发主管理单元，可以重置任何插入标志，作为一种限制第三方扩展可以添加的菜单项类型的方式。 例如，主管理单元可以清除 CCM_INSERTIONALLOWED_NEW 标志，以防止扩展添加其自己的 "创建新" 菜单项。

不应尝试在 *pInsertionAllowed* 中设置最初清除的位。 MMC 的未来版本可能使用当前未定义的位，因此不应更改当前未定义的位。

## <a name="csnapinitemimplsettoolbarbuttoninfo"></a><a name="settoolbarbuttoninfo"></a> CSnapInItemImpl::SetToolbarButtonInfo

调用此函数可在创建工具栏之前修改管理单元对象的任何工具栏按钮样式。

```cpp
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>parameters

*id*<br/>
中要设置的工具栏按钮的 ID。

*fsState*<br/>
中按钮的状态标志。 可以是下列一项或多项：

- TBSTATE_CHECKED 按钮具有 TBSTYLE_CHECKED 样式，并且正在按下。

- TBSTATE_ENABLED "按钮接受用户输入。 不具有此状态的按钮不接受用户输入并且灰显。

- TBSTATE_HIDDEN 该按钮不可见，无法接收用户输入。

- TBSTATE_INDETERMINATE 按钮灰显。

- 正在按下按钮 TBSTATE_PRESSED。

- TBSTATE_WRAP 按钮后跟一个换行符。 按钮还必须具有 TBSTATE_ENABLED。

*fsType*<br/>
中按钮的状态标志。 可以是下列一项或多项：

- TBSTYLE_BUTTON 创建标准的 "推送" 按钮。

- TBSTYLE_CHECK 创建一个按钮，该按钮在用户每次单击时和未按下状态之间切换。 此按钮处于按下状态时具有不同的背景色。

- TBSTYLE_CHECKGROUP 创建一个保持按下状态的复选按钮，直至按下组中的另一个按钮。

- TBSTYLE_GROUP 创建一个始终按下的按钮，直到按下组中的另一个按钮。

- TBSTYLE_SEP 创建一个分隔符，在按钮组之间提供较小的间隔。 具有此样式的按钮不会接收用户输入。

## <a name="csnapinitemimplupdatemenustate"></a><a name="updatemenustate"></a> CSnapInItemImpl::UpdateMenuState

调用此函数以修改菜单项，然后将其插入管理单元对象的上下文菜单中。

```cpp
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>parameters

*id*<br/>
中要设置的菜单项的 ID。

*pBuf*<br/>
中一个指针，指向要更新的菜单项的字符串。

*flag*<br/>
中指定新的状态标志。 这可以是以下标志的组合：

- MF_POPUP 指定这是上下文菜单中的子菜单。 菜单项、插入点和更多子菜单可以使用其作为它们的来添加到此子菜单中 `lCommandID` `IInsertionPointID` 。

- 不允许 MF_BITMAP 和 MF_OWNERDRAW 这些标志，并将导致返回值 E_INVALIDARG。

- MF_SEPARATOR 绘制水平分隔线。 仅 `IContextMenuProvider` 允许添加 MF_SEPARATOR 集的菜单项。

- MF_CHECKED 将复选标记放在菜单项的旁边。

- MF_DISABLED 禁用菜单项，因此无法选择它，但该标志不会使其变灰。

- MF_ENABLED 启用菜单项，以便可以选择它，并将其从灰色状态还原。

- MF_GRAYED 禁用菜单项，将其灰色，因此无法选择它。

- MF_MENUBARBREAK 功能与菜单栏的 MF_MENUBREAK 标志相同。 对于下拉菜单、子菜单或快捷菜单，新列与旧列之间用竖线分隔。

- MF_MENUBREAK 将项放置在新行 (上，) 菜单栏或新列 (的下拉菜单、子菜单或快捷菜单) 没有分隔列。

- MF_UNCHECKED 不会在项 (默认) 下放置复选标记。

以下标志组不能一起使用：

- MF_DISABLED、MF_ENABLED 和 MF_GRAYED。

- MF_MENUBARBREAK 和 MF_MENUBREAK。

- MF_CHECKED 和 MF_UNCHECKED。

## <a name="csnapinitemimplupdatetoolbarbutton"></a><a name="updatetoolbarbutton"></a> CSnapInItemImpl::UpdateToolbarButton

调用此函数以在显示管理单元对象之前修改其工具栏按钮。

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>parameters

*id*<br/>
指定要更新的工具栏按钮的按钮 ID。

*fsState*<br/>
指定工具栏按钮状态。 如果要设置此状态，则返回 TRUE。 这可以是以下标志的组合：

- 启用 "按钮接受用户输入"。 不具有此状态的按钮不接受用户输入并且灰显。

- 选中此按钮时，该按钮具有检查样式并处于按下状态。

- 隐藏按钮不可见，无法接收用户输入。

- 不确定按钮灰显。

- BUTTONPRESSED 按钮正在按下。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)

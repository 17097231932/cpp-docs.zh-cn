---
title: CMFCDynamicLayout 类
ms.date: 08/29/2019
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
ms.openlocfilehash: 1c5d73897f7028768476c82824f8c0b6d530aea2
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742900"
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout 类

指定窗口中的控件如何随着用户重设窗口大小而移动和重设大小。

## <a name="syntax"></a>语法

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|构造 `CMFCDynamicLayout` 对象。|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。|
|[CMFCDynamicLayout::Adjust](#adjust)|将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。|
|[CMFCDynamicLayout::Create](#create)|存储并验证主机窗口。|
|[CMFCDynamicLayout：： GetHostWnd](#gethostwnd)|返回指向主机窗口的指针。|
|[CMFCDynamicLayout：： GetMinSize](#getminsize)|返回窗口大小，低于此大小则不调整布局。|
|[CMFCDynamicLayout：： GetWindowRect](#getwindowrect)|检索窗口的当前工作区的矩形。|
|[CMFCDynamicLayout::HasItem](#hasitem)|检查子控件是否已添加到动态布局。|
|[CMFCDynamicLayout::IsEmpty](#isempty)|检查动态布局是否未添加任何子窗口。|
|[CMFCDynamicLayout::LoadResource](#loadresource)|从 AFX_DIALOG_LAYOUT 资源读取动态布局，然后将该布局应用到主机窗口。|
|静态 [CMFCDynamicLayout：： MoveHorizontal](#movehorizontal)|获取一个 [MoveSettings](#movesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平移动子控件的程度。|
|静态 [CMFCDynamicLayout：： MoveHorizontalAndVertical](#movehorizontalandvertical)|获取一个 [MoveSettings](#movesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平移动子控件的程度。|
|静态 [CMFCDynamicLayout：： MoveNone](#movenone)|获取一个 [MoveSettings](#movesettings_structure) 值，该值表示子控件不具有垂直或水平的动作。|
|静态 [CMFCDynamicLayout：： MoveVertical](#movevertical)|获取一个 [MoveSettings](#movesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时垂直移动子控件的程度。|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|设置窗口大小，低于此大小则不调整布局。|
|静态 [CMFCDynamicLayout：： SizeHorizontal](#sizehorizontal)|获取一个 [SizeSettings](#sizesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平调整子控件的大小。|
|静态 [CMFCDynamicLayout：： SizeHorizontalAndVertical](#sizehorizontalandvertical)|获取一个 [SizeSettings](#sizesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平调整子控件的大小。|
|静态 [CMFCDynamicLayout：： SizeNone](#sizenone)|获取一个 [SizeSettings](#sizesettings_structure) 值，该值表示子控件的大小不变。|
|静态 [CMFCDynamicLayout：： SizeVertical](#sizevertical)|获取一个 [SizeSettings](#sizesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平调整子控件的大小。|

## <a name="nested-types"></a>嵌套类型

|名称|描述|
|----------|-----------------|
|[CMFCDynamicLayout::MoveSettings Structure](#movesettings_structure)|封装动态布局中控件的移动数据。|
|[CMFCDynamicLayout::SizeSettings 结构](#sizesettings_structure)|封装动态布局中控件的大小更改数据。|

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>要求

**标头：** afxlayout。h

## <a name="cmfcdynamiclayoutadditem"></a><a name="additem"></a> CMFCDynamicLayout：： AddItem

将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
要添加的窗口句柄。

*nID*<br/>
要添加的子控件 ID。

*moveSettings*<br/>
描述控件如何随窗口大小的更改而移动的结构。

*sizeSettings*<br/>
描述控件如何随窗口大小的更改而调整大小的结构。

### <a name="return-value"></a>返回值

如果成功添加了项，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

调整承载窗口的大小时，子控件的位置和大小会动态更改。

## <a name="cmfcdynamiclayoutadjust"></a><a name="adjust"></a> CMFCDynamicLayout：：调整

将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。

```cpp
void Adjust();
```

### <a name="remarks"></a>备注

调整承载窗口的大小时，子控件的位置和大小会动态更改。

## <a name="cmfcdynamiclayoutcreate"></a><a name="create"></a> CMFCDynamicLayout：： Create

存储并验证主机窗口。

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>参数

*pHostWnd*<br/>
指向主机窗口的指针。

### <a name="return-value"></a>返回值

如果创建成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutgethostwnd"></a><a name="gethostwnd"></a> CMFCDynamicLayout：： GetHostWnd

返回指向主机窗口的指针。

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>返回值

指向主机窗口的指针。

### <a name="remarks"></a>备注

默认情况下，参照此窗口重新计算所有子控件的位置。

## <a name="cmfcdynamiclayoutgetminsize"></a><a name="getminsize"></a> CMFCDynamicLayout：： GetMinSize

返回窗口大小，低于此大小则不调整布局。

```
CSize GetMinSize();
```

### <a name="return-value"></a>返回值

窗口大小，低于此大小则不调整布局。

### <a name="remarks"></a>备注

调整承载窗口的大小时，子控件的位置和大小会动态更改，但存在一个最低大小，低于此大小则不调整布局。 用户可将窗口大小调整为较小，但届时窗口的某些部分将隐藏。

## <a name="cmfcdynamiclayoutgetwindowrect"></a><a name="getwindowrect"></a> CMFCDynamicLayout：： GetWindowRect

检索窗口的当前工作区的矩形。

```cpp
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>参数

*rect*<br/>
函数返回后，此参数将包含布局区域的边框。 这是一个 out 参数；输入的值将被覆盖。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayouthasitem"></a><a name="hasitem"></a> CMFCDynamicLayout：： HasItem

检查子控件是否已添加到动态布局。

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
控件的窗口句柄。

### <a name="return-value"></a>返回值

如果布局已有此项，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutisempty"></a><a name="isempty"></a> CMFCDynamicLayout：： IsEmpty

检查动态布局是否未添加任何子窗口。

```
BOOL IsEmpty();
```

### <a name="return-value"></a>返回值

如果布局没有任何项，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutloadresource"></a><a name="loadresource"></a> CMFCDynamicLayout：： LoadResource

从 AFX_DIALOG_LAYOUT 资源读取动态布局，然后将该布局应用到主机窗口。

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>参数

*pHostWnd*<br/>
指向主机窗口的指针。

*lpResource*<br/>
指向包含 AFX_DIALOG_LAYOUT 资源的缓冲区的指针。

*dwSize*<br/>
缓冲区大小（以字节为单位）。

### <a name="return-value"></a>返回值

如果已加载资源并将其应用于主机窗口，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutmovehorizontal"></a><a name="movehorizontal"></a> CMFCDynamicLayout：： MoveHorizontal

获取一个 [MoveSettings](#movesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平移动子控件的程度。

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>参数

*nRatio*<br/>
以百分比形式定义在用户调整承载窗口大小时水平移动子控件的距离。

### <a name="return-value"></a>返回值

一个 [MoveSettings](#movesettings_structure) 值，该值封装请求的移动比率。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutmovehorizontalandvertical"></a><a name="movehorizontalandvertical"></a> CMFCDynamicLayout：： MoveHorizontalAndVertical

获取一个 [MoveSettings](#movesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平移动子控件的程度。

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>参数

*nXRatio*<br/>
以百分比形式定义在用户调整承载窗口大小时水平移动子控件的距离。

*nYRatio*<br/>
以百分比形式定义在用户调整承载窗口大小时垂直移动子控件的距离。

### <a name="return-value"></a>返回值

一个 [MoveSettings](#movesettings_structure) 值，该值封装请求的移动比率。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutmovenone"></a><a name="movenone"></a> CMFCDynamicLayout：： MoveNone

获取一个 [MoveSettings](#movesettings_structure) 值，该值表示子控件不具有垂直或水平的动作。

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>返回值

一个 [MoveSettings](#movesettings_structure) 值，它就地修复控件，使其在用户调整主机窗口的大小时不移动。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutmovesettings-structure"></a><a name="movesettings_structure"></a> CMFCDynamicLayout：： MoveSettings 结构

封装动态布局中控件的移动数据。

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>备注

这是嵌套在 `CMFCDynamicLayout` 内的类。

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout：： MoveSettings：： IsHorizontal

检查移动数据是否指定非零的垂直移动。

```
BOOL IsHorizontal() const
```

### <a name="return-value"></a>返回值

如果 `MoveSettings` 对象指定一个非零的水平移动，则为 TRUE。

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout：： MoveSettings：： IsNone

检查移动数据是否指定无移动。

```
BOOL IsNone() const
```

### <a name="return-value"></a>返回值

如果 `MoveSettings` 对象指定无移动，则为 TRUE。

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout：： MoveSettings：： IsVertical

请检查移动数据是否指定非零的垂直移动。

```
BOOL IsVertical() const
```

### <a name="return-value"></a>返回值

如果 `MoveSettings` 对象指定非零的垂直移动，则为 true。

## <a name="cmfcdynamiclayoutmovevertical"></a><a name="movevertical"></a> CMFCDynamicLayout：： MoveVertical

获取一个 [MoveSettings](#movesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时垂直移动子控件的程度。

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>参数

*nRatio*<br/>
以百分比形式定义在用户调整承载窗口大小时垂直移动子控件的距离。

### <a name="return-value"></a>返回值

一个 [MoveSettings](#movesettings_structure) 值，该值封装请求的移动比率。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutsetminsize"></a><a name="setminsize"></a> CMFCDynamicLayout：： SetMinSize

设置窗口大小，低于此大小则不调整布局。

```cpp
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>参数

*大小*<br/>
所需大小，低于此大小则不调整布局。

### <a name="remarks"></a>备注

调整承载窗口的大小时，子控件的位置和大小会动态更改，但存在一个最低大小，低于此大小则不调整布局。 用户可将窗口大小调整为较小，但届时窗口的某些部分将隐藏。

## <a name="cmfcdynamiclayoutsizehorizontal"></a><a name="sizehorizontal"></a> CMFCDynamicLayout：： SizeHorizontal

获取一个 [SizeSettings](#sizesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平调整子控件的大小。

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>参数

*nRatio*<br/>
以百分比形式定义在用户调整承载窗口大小时水平调整子控件的距离。

### <a name="return-value"></a>返回值

一个 [SizeSettings](#sizesettings_structure) 值，该值封装请求的大小比。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutsizehorizontalandvertical"></a><a name="sizehorizontalandvertical"></a> CMFCDynamicLayout：： SizeHorizontalAndVertical

获取一个 [SizeSettings](#sizesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平调整子控件的大小。

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>参数

*nXRatio*<br/>
以百分比形式定义在用户调整承载窗口大小时水平调整子控件的距离。

*nYRatio*<br/>
以百分比形式定义在用户调整承载窗口大小时垂直调整子控件的距离。

### <a name="return-value"></a>返回值

一个 [SizeSettings](#sizesettings_structure) 值，该值封装请求的大小比。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutsizenone"></a><a name="sizenone"></a> CMFCDynamicLayout：： SizeNone

获取一个 [SizeSettings](#sizesettings_structure) 值，该值表示子控件的大小不变。

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>返回值

一个 [SizeSettings](#sizesettings_structure) 值，用于修复特定大小的控件，使其在用户调整主机窗口大小时不会改变大小。

### <a name="remarks"></a>备注

## <a name="cmfcdynamiclayoutsizesettings-structure"></a><a name="sizesettings_structure"></a> CMFCDynamicLayout：： SizeSettings 结构

封装动态布局中控件的大小更改数据。

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>备注

这是嵌套在 `CMFCDynamicLayout` 内的类。

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout：： SizeSettings：： IsHorizontal

检查大小调整数据是否指定非零水平大小调整。

```
BOOL IsHorizontal() const
```

### <a name="return-value"></a>返回值

如果 `SizeSettings` 对象指定非零的水平大小调整，则为 TRUE。

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout：： SizeSettings：： IsNone

检查大小调整数据是否不指定大小调整。

```
BOOL IsNone() const
```

### <a name="return-value"></a>返回值

如果 `SizeSettings` 对象指定不重设大小，则为 true。

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout：： SizeSettings：： IsVertical

检查大小调整数据是否指定非零垂直大小调整。

```
BOOL IsVertical() const
```

### <a name="return-value"></a>返回值

如果 `SizeSettings` 对象指定非零的垂直大小调整，则为 TRUE。

## <a name="cmfcdynamiclayoutsizevertical"></a><a name="sizevertical"></a> CMFCDynamicLayout：： SizeVertical

获取一个 [SizeSettings](#sizesettings_structure) 值，该值定义在用户调整控件的宿主窗口大小时水平调整子控件的大小。

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>参数

*nRatio*<br/>
以百分比形式定义在用户调整承载窗口大小时垂直调整子控件的距离。

### <a name="return-value"></a>返回值

一个 [SizeSettings](#sizesettings_structure) 值，该值封装请求的大小比。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)

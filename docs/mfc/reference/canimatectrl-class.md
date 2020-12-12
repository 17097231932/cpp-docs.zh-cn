---
description: 了解详细信息： CAnimateCtrl 类
title: CAnimateCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: fe63e30ae53e6f5b3d308c8e09f0bfbaad76b2ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322741"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl 类

提供 Windows 公共动画控件的功能。

## <a name="syntax"></a>语法

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CAnimateCtrl：： CAnimateCtrl](#canimatectrl)|构造 `CAnimateCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CAnimateCtrl：： Close](#close)|关闭 AVI 剪辑。|
|[CAnimateCtrl：： Create](#create)|创建动画控件，并将其附加到 `CAnimateCtrl` 对象。|
|[CAnimateCtrl：： CreateEx](#createex)|创建具有指定 Windows 扩展样式的动画控件，并将其附加到 `CAnimateCtrl` 对象。|
|[CAnimateCtrl：： IsPlaying](#isplaying)|指示是否正在播放 Audio-Video 交错 (AVI) 剪辑。|
|[CAnimateCtrl：： Open](#open)|从文件或资源打开 AVI 剪辑，并显示第一帧。|
|[CAnimateCtrl：:P 布局](#play)|不用声音播放 AVI 剪辑。|
|[CAnimateCtrl：： Seek](#seek)|显示 AVI 剪辑的选定帧。|
|[CAnimateCtrl：： Stop](#stop)|停止播放 AVI 剪辑。|

## <a name="remarks"></a>备注

此控件 (，因此 `CAnimateCtrl` 类) 仅适用于在 windows 95、windows 98 和 WINDOWS NT 3.51 及更高版本下运行的程序。

动画控件是一个矩形窗口，它在 AVI (音频视频交错) 格式（标准 Windows 视频/音频格式）中显示剪辑。 AVI 剪辑是一系列位图帧，与电影相似。

动画控件只能播放简单的 AVI 剪辑。 具体而言，动画控件播放的剪辑必须满足以下要求：

- 必须有且仅有一个视频流，且它必须至少有一个帧。

- 文件中最多可以有两个流 (通常，另一个流（如果有）是音频流，尽管动画控件会忽略音频信息) 。

- 必须用 RLE8 压缩对剪辑进行解压缩或压缩。

- 视频流中不允许使用调色板更改。

可以将 AVI 剪辑作为 AVI 资源添加到应用程序，也可以将应用程序作为单独的 AVI 文件附带。

由于在显示 AVI 剪辑时，线程会继续执行，因此动画控件的一个常见用途是在长时间操作期间指示系统活动。 例如，文件资源管理器的 "查找" 对话框将在系统搜索文件时显示一个移动放大镜。

如果在对话框 `CAnimateCtrl` 中或使用对话框编辑器在对话框资源中创建对象，则当用户关闭对话框时，它将自动被销毁。

如果在 `CAnimateCtrl` 窗口中创建对象，可能需要销毁它。 如果在 `CAnimateCtrl` 堆栈上创建对象，则该对象会自动销毁。 如果 `CAnimateCtrl` 使用函数在堆上创建对象 **`new`** ，则必须对 **`delete`** 该对象调用以销毁该对象。 如果从派生新类 `CAnimateCtrl` 并在该类中分配任何内存，则重写 `CAnimateCtrl` 析构函数以释放分配。

有关使用的详细信息 `CAnimateCtrl` ，请参阅 [控件](../../mfc/controls-mfc.md) 和 [使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a> CAnimateCtrl：： CAnimateCtrl

构造 `CAnimateCtrl` 对象。

```
CAnimateCtrl();
```

### <a name="remarks"></a>备注

必须先调用 [create](#create) 成员函数，然后才能对所创建的对象执行任何其他操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a> CAnimateCtrl：： Close

关闭先前在动画控件中打开的 AVI 剪辑 (如果任何) ，并将其从内存中删除。

```
BOOL Close();
```

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

  请参阅 [CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的示例。

## <a name="canimatectrlcreate"></a><a name="create"></a> CAnimateCtrl：： Create

创建动画控件，并将其附加到 `CAnimateCtrl` 对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>parameters

*dwStyle*<br/>
指定动画控件的样式。 应用下面的 "备注" 部分中所述的任意 windows 样式组合和 Windows SDK 的 [动画控件样式](/windows/win32/Controls/animation-control-styles) 中所述的动画控件样式。

*rect*<br/>
指定动画控件的位置和大小。 它可以是 [CRect](../../atl-mfc-shared/reference/crect-class.md) 对象或 [RECT](/windows/win32/api/windef/ns-windef-rect) 结构。

*pParentWnd*<br/>
指定动画控件的父窗口，通常为 `CDialog` 。 值不得为 NULL。

*nID*<br/>
指定动画控件的 ID。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

可以通过 `CAnimateCtrl` 两个步骤构造。 首先，调用构造函数，然后调用，它将 `Create` 创建动画控件并将其附加到 `CAnimateCtrl` 对象。

将以下 [窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles) 应用于动画控件。

- 始终 WS_CHILD

- WS_VISIBLE 通常

- 很少 WS_DISABLED

如果要对动画控件使用扩展的 windows 样式，请调用 [CreateEx](#createex) 而不是 `Create` 。

除了上面列出的窗口样式以外，可能还需要将一个或多个动画控件样式应用于动画控件。 有关 [动画控件样式](/windows/win32/Controls/animation-control-styles)的详细信息，请参阅 Windows SDK。

### <a name="example"></a>示例

  请参阅 [CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的示例。

## <a name="canimatectrlcreateex"></a><a name="createex"></a> CAnimateCtrl：： CreateEx

创建一个 (子窗口) 的控件，并将其与 `CAnimateCtrl` 对象关联。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>parameters

*dwExStyle*<br/>
指定正在创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的 *dwExStyle* 参数。

*dwStyle*<br/>
指定动画控件的样式。 应用 Windows SDK 的 [动画控件样式](/windows/win32/Controls/animation-control-styles) 中所述的窗口和动画控件样式的任意组合。

*rect*<br/>
对 [矩形](/windows/win32/api/windef/ns-windef-rect) 结构的引用，该结构描述要创建的窗口的大小和位置（以 *pParentWnd* 的工作区坐标表示）。

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用 `CreateEx` 由 Windows 扩展样式指定的扩展 Windows 样式，而不是 [Create](#create) **WS_EX_**。

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a> CAnimateCtrl：： IsPlaying

指示是否正在播放 Audio-Video 交错 (AVI) 剪辑。

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>返回值

如果正在播放 AVI 剪辑，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的 [ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying) 消息。

## <a name="canimatectrlopen"></a><a name="open"></a> CAnimateCtrl：： Open

调用此函数可打开 AVI 剪辑并显示其第一帧。

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>parameters

*lpszFileName*<br/>
一个 `CString` 对象或一个指向以 null 结尾的字符串的指针，该字符串包含 avi 文件的名称或 avi 资源的名称。 如果此参数为 NULL，则系统将关闭先前为动画控件打开的 AVI 剪辑（如果有）。

*nID*<br/>
AVI 资源标识符。 如果此参数为 NULL，则系统将关闭先前为动画控件打开的 AVI 剪辑（如果有）。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

从创建动画控件的模块加载 AVI 资源。

`Open` 不支持在 AVI 剪辑中使用声音;只能打开无提示 AVI 剪辑。

如果动画控件具有 `ACS_AUTOPLAY` 样式，动画控件将在它打开剪辑后立即自动开始播放。 当线程继续执行时，它将继续在后台播放剪辑。 剪辑完成播放后，它将自动重复。

如果动画控件具有 `ACS_CENTER` 样式，则 AVI 剪辑将在控件中居中，并且控件的大小不会更改。 如果动画控件没有样式，则在将 `ACS_CENTER` avi 剪辑打开到 avi 剪辑中的图像大小时，将调整控件的大小。 控件左上角的位置将不会更改，只会改变控件的大小。

如果动画控件具有 `ACS_TRANSPARENT` 样式，则将使用透明背景（而不是在动画剪辑中指定的背景色）绘制第一帧。

### <a name="example"></a>示例

  请参阅 [CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的示例。

## <a name="canimatectrlplay"></a><a name="play"></a> CAnimateCtrl：:P 布局

调用此函数可在动画控件中播放 AVI 剪辑。

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>parameters

*n*<br/>
开始播放的帧从零开始的索引。 值必须小于65536。 值0表示从 AVI 剪辑中的第一帧开始。

*\N\n*<br/>
播放结束的帧的从零开始的索引。 值必须小于65536。 如果值为-1，则表示在 AVI 剪辑中最后一帧结束。

*nRep*<br/>
重播 AVI 剪辑的次数。 如果值为-1，表示无限期重播文件。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

当线程继续执行时，动画控件将在后台播放剪辑。 如果动画控件具有 `ACS_TRANSPARENT` 样式，则将使用透明背景播放 AVI 剪辑，而不是在动画剪辑中指定的背景色播放。

### <a name="example"></a>示例

  请参阅 [CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的示例。

## <a name="canimatectrlseek"></a><a name="seek"></a> CAnimateCtrl：： Seek

调用此函数可静态显示 AVI 剪辑的单个帧。

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>parameters

*\N\n*<br/>
要显示的帧的从零开始的索引。 值必须小于65536。 值0表示在 AVI 剪辑中显示第一帧。 如果值为-1，则表示在 AVI 剪辑中显示最后一帧。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

如果动画控件具有 `ACS_TRANSPARENT` 样式，则将使用透明背景（而不是在动画剪辑中指定的背景色）绘制 AVI 剪辑。

### <a name="example"></a>示例

请参阅 [CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的示例。

## <a name="canimatectrlstop"></a><a name="stop"></a> CAnimateCtrl：： Stop

调用此函数可停止在动画控件中播放 AVI 剪辑。

```
BOOL Stop();
```

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

  请参阅 [CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的示例。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl：： Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)

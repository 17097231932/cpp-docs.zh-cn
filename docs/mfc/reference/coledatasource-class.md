---
description: 了解详细信息： COleDataSource 类
title: COleDataSource 类
ms.date: 11/04/2016
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
ms.openlocfilehash: 1fc6dd8a7df1d8b841c4f95a14c2bd1708c94fd2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227320"
---
# <a name="coledatasource-class"></a>COleDataSource 类

充当应用程序将数据放置到的缓存，应用程序将在数据传输操作（如剪贴板或拖放操作）期间提供这些数据。

## <a name="syntax"></a>语法

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[COleDataSource：： COleDataSource](#coledatasource)|构造 `COleDataSource` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[COleDataSource：： CacheData](#cachedata)|使用结构以指定格式提供数据 `STGMEDIUM` 。|
|[COleDataSource：： CacheGlobalData](#cacheglobaldata)|使用 HGLOBAL 以指定格式提供数据。|
|[COleDataSource：:D elayRenderData](#delayrenderdata)|使用延迟呈现提供指定格式的数据。|
|[COleDataSource：:D elayRenderFileData](#delayrenderfiledata)|以指定格式在指针中提供数据 `CFile` 。|
|[COleDataSource：:D elaySetData](#delaysetdata)|为在中支持的每种格式调用 `OnSetData` 。|
|[COleDataSource：:D oDragDrop](#dodragdrop)|对数据源执行拖放操作。|
|[COleDataSource：： Empty](#empty)|清空 `COleDataSource` 数据对象。|
|[COleDataSource：： FlushClipboard](#flushclipboard)|将所有数据呈现到剪贴板。|
|[COleDataSource：： GetClipboardOwner](#getclipboardowner)|验证放置在剪贴板上的数据是否仍然存在。|
|[COleDataSource：： OnRenderData](#onrenderdata)|在延迟呈现过程中检索数据。|
|[COleDataSource：： OnRenderFileData](#onrenderfiledata)|将数据 `CFile` 作为延迟呈现的一部分检索到中。|
|[COleDataSource：： OnRenderGlobalData](#onrenderglobaldata)|将数据作为延迟呈示的一部分检索到 HGLOBAL。|
|[COleDataSource：： OnSetData](#onsetdata)|调用以替换对象中的数据 `COleDataSource` 。|
|[COleDataSource：： SetClipboard](#setclipboard)|`COleDataSource`将对象置于剪贴板上。|

## <a name="remarks"></a>备注

您可以直接创建 OLE 数据源。 此外， [COleClientItem](../../mfc/reference/coleclientitem-class.md) 和 [COLESERVERITEM](../../mfc/reference/coleserveritem-class.md) 类创建 OLE 数据源来响应其 `CopyToClipboard` 和 `DoDragDrop` 成员函数。 有关简要说明，请参阅 [COleServerItem：： CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) 。 重写 `OnGetClipboardData` 客户端项或服务器项类的成员函数，以将其他剪贴板格式添加到为 `CopyToClipboard` 或成员函数创建的 OLE 数据源中的数据 `DoDragDrop` 。

无论何时需要为传输准备数据，都应创建此类的对象，并使用数据的最合适方法为其填充数据。 将数据插入数据源的方式会直接影响数据是否立即 (立即呈现) 还是按需 (延迟呈现) 。 对于每个剪贴板格式，在该格式中，通过传递要使用的剪贴板格式 (和可选的 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构) 来提供数据，请调用 [DelayRenderData](#delayrenderdata)。

有关数据源和数据传输的详细信息，请参阅文章 [数据对象和数据源 (OLE) ](../../mfc/data-objects-and-data-sources-ole.md)。 此外，文章 [剪贴板主题](../../mfc/clipboard.md) 介绍了 OLE 剪贴板机制。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>要求

**标头：** afxole

## <a name="coledatasourcecachedata"></a><a name="cachedata"></a> COleDataSource：： CacheData

调用此函数可指定数据传输操作期间提供数据的格式。

```cpp
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>parameters

*cfFormat*<br/>
要提供数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一或本机 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 函数返回的值。

*lpStgMedium*<br/>
指向 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 结构，其中包含指定格式的数据。

*lpFormatEtc*<br/>
指向 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构，该结构描述提供数据的格式。 如果要指定超出 *cfFormat* 指定的剪贴板格式的其他格式信息，请提供此参数的值。 如果为 NULL，则将对结构中的其他字段使用默认值 `FORMATETC` 。

### <a name="remarks"></a>备注

必须提供数据，因为此函数通过使用立即呈现来提供数据。 数据会一直缓存到需要时。

使用 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 结构提供数据。 `CacheGlobalData`如果要提供的数据量足够小，可以使用 HGLOBAL 有效传输，还可以使用成员函数。

在对的成员进行调用后 `CacheData` `ptd` `lpFormatEtc` ， *lpStgMedium* 的内容由该数据对象（而不是由调用方）所有。

若要使用延迟呈现，请调用 [DelayRenderData](#delayrenderdata) 或 [DelayRenderFileData](#delayrenderfiledata) 成员函数。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章 [数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅 Windows SDK 中的 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 和 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构。

有关详细信息，请参阅 Windows SDK 中的 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

## <a name="coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a> COleDataSource：： CacheGlobalData

调用此函数可指定数据传输操作期间提供数据的格式。

```cpp
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>parameters

*cfFormat*<br/>
要提供数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一或本机 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 函数返回的值。

*hGlobal*<br/>
全局内存块的句柄，其中包含指定格式的数据。

*lpFormatEtc*<br/>
指向 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构，该结构描述提供数据的格式。 如果要指定超出 *cfFormat* 指定的剪贴板格式的其他格式信息，请提供此参数的值。 如果为 NULL，则将对结构中的其他字段使用默认值 `FORMATETC` 。

### <a name="remarks"></a>备注

此函数使用立即呈现来提供数据，因此，您必须在调用函数时提供数据;数据会一直缓存到需要时。 `CacheData`如果提供大量数据，或者需要结构化存储介质，请使用成员函数。

若要使用延迟呈现，请调用 [DelayRenderData](#delayrenderdata) 或 [DelayRenderFileData](#delayrenderfiledata) 成员函数。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章 [数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅 Windows SDK 中的 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构。

有关详细信息，请参阅 Windows SDK 中的 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

## <a name="coledatasourcecoledatasource"></a><a name="coledatasource"></a> COleDataSource：： COleDataSource

构造 `COleDataSource` 对象。

```
COleDataSource();
```

## <a name="coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a> COleDataSource：:D elayRenderData

调用此函数可指定数据传输操作期间提供数据的格式。

```cpp
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>parameters

*cfFormat*<br/>
要提供数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一或本机 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 函数返回的值。

*lpFormatEtc*<br/>
指向 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构，该结构描述提供数据的格式。 如果要指定超出 *cfFormat* 指定的剪贴板格式的其他格式信息，请提供此参数的值。 如果为 NULL，则将对结构中的其他字段使用默认值 `FORMATETC` 。

### <a name="remarks"></a>备注

此函数使用延迟呈现来提供数据，因此不会立即提供数据。 调用 [OnRenderData](#onrenderdata) 或 [OnRenderGlobalData](#onrenderglobaldata) 成员函数来请求数据。

如果不打算通过对象提供数据，请使用此函数 `CFile` 。 如果打算通过对象提供数据 `CFile` ，请调用 [DelayRenderFileData](#delayrenderfiledata) 成员函数。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章 [数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

若要使用立即呈现，请调用 [CacheData](#cachedata) 或 [CacheGlobalData](#cacheglobaldata) 成员函数。

有关详细信息，请参阅 Windows SDK 中的 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构。

有关详细信息，请参阅 Windows SDK 中的 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

## <a name="coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a> COleDataSource：:D elayRenderFileData

调用此函数可指定数据传输操作期间提供数据的格式。

```cpp
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>parameters

*cfFormat*<br/>
要提供数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一或本机 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 函数返回的值。

*lpFormatEtc*<br/>
指向 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构，该结构描述提供数据的格式。 如果要指定超出 *cfFormat* 指定的剪贴板格式的其他格式信息，请提供此参数的值。 如果为 NULL，则将对结构中的其他字段使用默认值 `FORMATETC` 。

### <a name="remarks"></a>备注

此函数使用延迟呈现来提供数据，因此不会立即提供数据。 调用 [OnRenderFileData](#onrenderfiledata) 成员函数以请求数据。

如果打算使用 `CFile` 对象来提供数据，请使用此函数。 如果不打算使用 `CFile` 对象，请调用 [DelayRenderData](#delayrenderdata) 成员函数。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章 [数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

若要使用立即呈现，请调用 [CacheData](#cachedata) 或 [CacheGlobalData](#cacheglobaldata) 成员函数。

有关详细信息，请参阅 Windows SDK 中的 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构。

有关详细信息，请参阅 Windows SDK 中的 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

## <a name="coledatasourcedelaysetdata"></a><a name="delaysetdata"></a> COleDataSource：:D elaySetData

调用此函数可支持更改数据源的内容。

```cpp
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>parameters

*cfFormat*<br/>
要在其中放置数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一或本机 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 函数返回的值。

*lpFormatEtc*<br/>
指向 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构，该结构描述要替换数据的格式。 如果要指定超出 *cfFormat* 指定的剪贴板格式的其他格式信息，请提供此参数的值。 如果为 NULL，则将对结构中的其他字段使用默认值 `FORMATETC` 。

### <a name="remarks"></a>备注

发生这种情况时，框架将调用[OnSetData](#onsetdata) 。 仅当框架从 [COleServerItem：： GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)返回数据源时，才使用此操作。 如果 `DelaySetData` 未调用，则 `OnSetData` 永远不会调用函数。 `DelaySetData` 应为每个支持的剪贴板或 `FORMATETC` 格式调用。

有关详细信息，请参阅 Windows SDK 中的 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构。

有关详细信息，请参阅 Windows SDK 中的 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

## <a name="coledatasourcedodragdrop"></a><a name="dodragdrop"></a> COleDataSource：:D oDragDrop

调用 `DoDragDrop` 成员函数以对此数据源执行拖放操作，通常在 [CWnd：： OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) 处理程序中。

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>parameters

*dwEffects*<br/>
此数据源允许的拖放操作。 可以是下列一项或多项：

- DROPEFFECT_COPY 可以执行复制操作。

- DROPEFFECT_MOVE 可以执行移动操作。

- DROPEFFECT_LINK 可以建立从已删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示可能会发生拖动滚动操作。

*lpRectStartDrag*<br/>
一个指针，指向用于定义拖动实际起始位置的矩形。 有关更多信息，请参见下面的“备注”部分。

*pDropSource*<br/>
指向放置源。 如果为 NULL，则将使用默认的 [COleDropSource](../../mfc/reference/coledropsource-class.md) 实现。

### <a name="return-value"></a>返回值

拖放操作生成的放置效果;否则 DROPEFFECT_NONE 如果操作永远不会开始，因为用户在离开提供的矩形之前释放鼠标按钮。

### <a name="remarks"></a>备注

拖放操作不会立即启动。 它会一直等待，直到鼠标光标离开 *lpRectStartDrag* 指定的矩形，或直到经过指定的毫秒数。 如果 *lpRectStartDrag* 为 NULL，则该矩形的大小为一个像素。

延迟时间由注册表项设置指定。 可以通过调用 [CWinApp：： WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) 或 [CWinApp：： WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint)来更改延迟时间。 如果未指定延迟时间，则使用默认值200毫秒。 拖动延迟时间按如下方式存储：

- Windows NT 拖动延迟时间存储在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini \Windows\DragDelay. 中。

- Windows 3. x 拖动延迟时间存储在 "[Windows}" 部分下的 WIN.INI 文件中。

- Windows 95/98 拖动延迟时间存储在 WIN.INI 的缓存版本中。

有关如何将拖动延迟信息存储在注册表或中的详细信息。INI 文件，请参阅 Windows SDK 中的 [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) 。

有关详细信息，请参阅 [OLE 拖放](../../mfc/drag-and-drop-ole.md)文章。

## <a name="coledatasourceempty"></a><a name="empty"></a> COleDataSource：： Empty

调用此函数可清空 `COleDataSource` 数据对象。

```cpp
void Empty();
```

### <a name="remarks"></a>备注

已清空缓存和延迟呈现格式，因此可重复使用。

有关详细信息，请参阅 Windows SDK 中的 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 。

## <a name="coledatasourceflushclipboard"></a><a name="flushclipboard"></a> COleDataSource：： FlushClipboard

呈现剪贴板上的数据，然后允许您在应用程序关闭后粘贴剪贴板中的数据。

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>备注

使用 [SetClipboard](#setclipboard) 将数据放置在剪贴板上。

## <a name="coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a> COleDataSource：： GetClipboardOwner

确定自上次调用 [SetClipboard](#setclipboard) 后剪贴板上的数据是否已更改，如果是，则标识当前所有者。

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>返回值

当前位于剪贴板上的数据源; 如果剪贴板上没有任何内容，或者剪贴板不是调用应用程序所拥有，则为 NULL。

## <a name="coledatasourceonrenderdata"></a><a name="onrenderdata"></a> COleDataSource：： OnRenderData

由框架调用以检索指定格式的数据。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>parameters

*lpFormatEtc*<br/>
指向 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构，指定请求信息时所用的格式。

*lpStgMedium*<br/>
指向要返回数据的 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前 `COleDataSource` 使用 [DelayRenderData](#delayrenderdata) 或 [DelayRenderFileData](#delayrenderfiledata) 成员函数在对象中放置的格式，用于延迟渲染。 如果提供的存储介质分别为文件或内存，则此函数的默认实现将调用 [OnRenderFileData](#onrenderfiledata) 或 [OnRenderGlobalData](#onrenderglobaldata) 。 如果这两种格式都未提供，则默认实现将返回0并不执行任何操作。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章 [数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如果 TYMED_NULL 了 *lpStgMedium* ->  *tymed* ，则 `STGMEDIUM` 应按照 *lpFormatEtc >tymed* 指定的方式分配和填充。 如果未 TYMED_NULL，则应将其 `STGMEDIUM` 与数据一起填充。

这是一种高级的可重写。 重写此函数以按所请求的格式和媒体提供数据。 根据您的数据，您可能需要替代此函数的其他版本之一。 如果数据大小较小且固定，请重写 `OnRenderGlobalData` 。 如果你的数据在文件中或者大小可变，请重写 `OnRenderFileData` 。

有关详细信息，请参阅 Windows SDK 中的 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 和 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构、 [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) 枚举类型和 [IDataObject：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 。

## <a name="coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a> COleDataSource：： OnRenderFileData

当指定的存储介质为文件时，由框架调用以检索指定格式的数据。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>parameters

*lpFormatEtc*<br/>
指向 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构，指定请求信息时所用的格式。

*.Pfile*<br/>
指向要在其中呈现数据的 [CFile](../../mfc/reference/cfile-class.md) 对象。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前 `COleDataSource` 使用 [DelayRenderData](#delayrenderdata) 成员函数在对象中放置的格式，用于延迟渲染。 此函数的默认实现只返回 FALSE。

这是一种高级的可重写。 重写此函数以按所请求的格式和媒体提供数据。 根据您的数据，您可能希望改为重写此函数的其他版本之一。 如果要处理多个存储媒体，请重写 [OnRenderData](#onrenderdata)。 如果你的数据在文件中或者大小可变，请重写 `OnRenderFileData` 。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章 [数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅 Windows SDK 中的 " [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构" 和 " [IDataObject：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) "。

## <a name="coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a> COleDataSource：： OnRenderGlobalData

当指定的存储介质为全局内存时，由框架调用以检索指定格式的数据。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>parameters

*lpFormatEtc*<br/>
指向 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构，指定请求信息时所用的格式。

*phGlobal*<br/>
指向全局内存的句柄，其中的数据将被返回。 如果尚未分配一个参数，则此参数可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前 `COleDataSource` 使用 [DelayRenderData](#delayrenderdata) 成员函数在对象中放置的格式，用于延迟渲染。 此函数的默认实现只返回 FALSE。

如果 *phGlobal* 为 NULL，则应在 *phGlobal* 中分配并返回新的 HGLOBAL。 否则，由 *phGlobal* 指定的 HGLOBAL 应使用数据进行填充。 放置在 HGLOBAL 中的数据量不能超过内存块的当前大小。 此外，不能将块重新分配到更大的大小。

这是一种高级的可重写。 重写此函数以按所请求的格式和媒体提供数据。 根据您的数据，您可能需要替代此函数的其他版本之一。 如果要处理多个存储媒体，请重写 [OnRenderData](#onrenderdata)。 如果数据位于文件中或大小可变，请重写 [OnRenderFileData](#onrenderfiledata)。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章 [数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅 Windows SDK 中的 " [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构" 和 " [IDataObject：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) "。

## <a name="coledatasourceonsetdata"></a><a name="onsetdata"></a> COleDataSource：： OnSetData

由框架调用以设置或替换指定格式的对象中的数据 `COleDataSource` 。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>parameters

*lpFormatEtc*<br/>
指向 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构，指定替换数据的格式。

*lpStgMedium*<br/>
指向包含将替换对象的当前内容的数据的 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 结构 `COleDataSource` 。

*bRelease*<br/>
指示在完成函数调用之后谁拥有存储介质的所有权。 调用方决定由谁来代表存储介质释放分配的资源。 调用方通过设置 *bRelease* 来实现此功能。 如果 *bRelease* 为非零值，则数据源会获得所有权，并在使用完介质后释放介质。 当 *bRelease* 为0时，调用方保留所有权，数据源只能在调用期间使用存储介质。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

在成功获取数据源之前，数据源不会获得数据的所有权。 也就是说，如果返回0，则不获取所有权 `OnSetData` 。 如果数据源获得所有权，它将通过调用 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 函数来释放存储介质。

默认实现不执行任何操作。 重写此函数以将数据替换为指定的格式。 这是一种高级的可重写。

有关详细信息，请参阅 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 和 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 结构和 Windows SDK 中的 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 和 [IDataObject：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 函数。

## <a name="coledatasourcesetclipboard"></a><a name="setclipboard"></a> COleDataSource：： SetClipboard

`COleDataSource`调用以下函数之一后，将对象中包含的数据放入剪贴板： [CacheData](#cachedata)、 [CacheGlobalData](#cacheglobaldata)、 [DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)。

```cpp
void SetClipboard();
```

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject 类](../../mfc/reference/coledataobject-class.md)

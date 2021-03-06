---
description: 了解详细信息： CPrintDialog 类
title: CPrintDialog 类
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: f662f3d2a522dc3a53ea887bb1031e9431df2e3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343396"
---
# <a name="cprintdialog-class"></a>CPrintDialog 类

封装由 Windows 公共对话框提供的打印服务。

## <a name="syntax"></a>语法

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|构造 `CPrintDialog` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|在不显示 "打印" 对话框的情况下创建打印机设备上下文。|
|[CPrintDialog：:D oModal](#domodal)|显示对话框并允许用户进行选择。|
|[CPrintDialog::GetCopies](#getcopies)|检索请求的副本数。|
|[CPrintDialog::GetDefaults](#getdefaults)|在不显示对话框的情况下检索设备默认值。|
|[CPrintDialog::GetDeviceName](#getdevicename)|检索当前所选打印机设备的名称。|
|[CPrintDialog::GetDevMode](#getdevmode)|检索 `DEVMODE` 结构。|
|[CPrintDialog：： GetDriverName](#getdrivername)|检索当前选定的打印机驱动程序的名称。|
|[CPrintDialog::GetFromPage](#getfrompage)|检索打印范围的起始页。|
|[CPrintDialog::GetPortName](#getportname)|检索当前选定的打印机端口的名称。|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|检索打印机设备上下文的句柄。|
|[CPrintDialog::GetToPage](#gettopage)|检索打印范围的结束页。|
|[CPrintDialog：:P rintAll](#printall)|确定是否打印文档的所有页。|
|[CPrintDialog：:P rintCollate](#printcollate)|确定是否请求逐份打印副本。|
|[CPrintDialog：:P rintRange](#printrange)|确定是否仅打印指定范围的页面。|
|[CPrintDialog：:P rintSelection](#printselection)|确定是否仅打印当前选定的项。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPrintDialog：： m_pd](#m_pd)|用于自定义对象的结构 `CPrintDialog` 。|

## <a name="remarks"></a>备注

通用打印对话框提供一种简单的方法来实现 "打印和打印" 设置对话框，其方式与 Windows 标准一致。

> [!NOTE]
> `CPrintDialogEx`类封装由 Windows 打印属性表提供的服务。 有关详细信息，请参阅 [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) 概述。

`CPrintDialog`的功能被 [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)，它旨在为您提供打印设置和页面设置的通用对话框。

您可以依赖于框架来处理应用程序打印过程的许多方面。 在这种情况下，框架自动显示 "用于打印的 Windows 通用" 对话框。 您还可以对应用程序进行框架处理打印，但使用自己的 "打印" 对话框替代 "常见打印" 对话框。 有关使用框架来处理打印任务的详细信息，请参阅文章 [打印](../../mfc/printing.md)。

如果希望应用程序在不使用框架的情况下处理打印，则可以使用 `CPrintDialog` 提供的构造函数的 "按原样" 类，也可以从派生您自己的对话类， `CPrintDialog` 并编写一个构造函数来满足您的需求。 在这两种情况下，这些对话框的行为类似于标准 MFC 对话框，因为它们是从类派生的 `CCommonDialog` 。

若要使用 `CPrintDialog` 对象，请先使用 `CPrintDialog` 构造函数创建对象。 构造该对话框后，您可以设置或修改 [m_pd](#m_pd) 结构中的任何值以初始化对话框控件的值。 `m_pd`结构的类型为[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)。 有关此结构的详细信息，请参阅 Windows SDK。

如果没有 `m_pd` 为和成员提供自己的句柄 `hDevMode` `hDevNames` ，请确保在 `GlobalFree` 完成该对话框后，为这些句柄调用 Windows 函数。 使用提供的框架打印设置实现时，无 `CWinApp::OnFilePrintSetup` 需释放这些句柄。 句柄由维护 `CWinApp` ，并在 `CWinApp` 的析构函数中释放。 仅当使用独立时，才需要释放这些句柄 `CPrintDialog` 。

初始化对话框控件后，调用 `DoModal` 成员函数以显示对话框，并允许用户选择打印选项。 `DoModal` 返回用户是否选择了 "确定" (IDOK ") " 或 "取消" (IDCANCEL) "按钮。

如果 `DoModal` 返回 IDOK，则可以使用 `CPrintDialog` 的成员函数来检索用户输入的信息。

此 `CPrintDialog::GetDefaults` 成员函数可用于检索当前打印机默认值，而不会显示对话框。 此成员函数不需要用户交互。

您可以使用 Windows `CommDlgExtendedError` 函数来确定初始化对话框期间是否发生了错误，并了解有关该错误的详细信息。 有关此函数的详细信息，请参阅 Windows SDK。

`CPrintDialog` 依赖于 Windows 版本3.1 及更高版本附带的 COMMDLG.DLL 文件。

若要自定义对话框，从派生类 `CPrintDialog` ，提供自定义对话框模板，并添加消息映射以处理来自扩展控件的通知消息。 所有未处理的消息应传递到基类。 不需要自定义挂钩函数。

若要以不同方式处理相同的消息，具体取决于对话框是打印还是打印设置，你必须为每个对话框都派生一个类。 您还必须重写 Windows `AttachOnSetup` 函数，该函数在 "打印" 对话框中选择 "打印设置" 按钮时处理创建新对话框的功能。

有关使用的详细信息 `CPrintDialog` ，请参阅 [通用对话框类](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>要求

**标头：** afxdlgs

## <a name="cprintdialogcprintdialog"></a><a name="cprintdialog"></a> CPrintDialog::CPrintDialog

构造 Windows 打印或打印设置对话框对象。

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>parameters

*bPrintSetupOnly*<br/>
指定是否显示标准的 "Windows 打印" 对话框或 "打印设置" 对话框。 将此参数设置为 TRUE 可显示标准的 "Windows 打印设置" 对话框。 将其设置为 FALSE 可显示 "Windows 打印" 对话框。 如果 *bPrintSetupOnly* 为 FALSE，则 "打印" 对话框中仍将显示 "打印设置" 选项按钮。

dwFlags <br/>
可用于自定义对话框的设置的一个或多个标志，使用按位 "或" 运算符组合在一起。 例如，PD_ALLPAGES 标志将默认打印范围设置为文档的所有页。 有关这些标志的详细信息，请参阅 Windows SDK 中的 [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) 结构。

*pParentWnd*<br/>
指向对话框的父窗口或所有者窗口的指针。

### <a name="remarks"></a>备注

此成员函数仅构造对象。 使用 `DoModal` 成员函数来显示对话框。

请注意，在调用构造函数时，如果 *bPrintSetupOnly* 设置为 FALSE，则会自动使用 PD_RETURNDC 标志。 调用 `DoModal` 、 `GetDefaults` 或后 `GetPrinterDC` ，将在中返回打印机 DC `m_pd.hDC` 。 必须通过调用方调用 [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) 来释放此 DC `CPrintDialog` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

## <a name="cprintdialogcreateprinterdc"></a><a name="createprinterdc"></a> CPrintDialog::CreatePrinterDC

从 [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 和 [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) 结构中 (DC) 创建打印机设备上下文。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>返回值

新创建的打印机设备上下文的句柄。

### <a name="remarks"></a>备注

此 DC 假定为当前打印机 DC，并且用户必须删除任何其他以前获得的打印机 Dc。 可以调用此函数，并使用生成的 DC，无需显示 "打印" 对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

## <a name="cprintdialogdomodal"></a><a name="domodal"></a> CPrintDialog：:D oModal

显示 "Windows 通用打印" 对话框，允许用户选择各种打印选项，如副本数、页面范围以及是否应逐份打印副本。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL，则调用 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) 函数来确定是否发生了错误。

IDOK 和 IDCANCEL 是常量，用于指示用户是否选择了 "确定" 或 "取消" 按钮。

### <a name="remarks"></a>备注

如果希望通过设置结构的成员来初始化各种打印对话框选项 `m_pd` ，应在调用之前执行此操作 `DoModal` ，但在构造对话框对象之后。

调用后 `DoModal` ，可以调用其他成员函数来检索用户在对话框中输入的设置或信息。

请注意，在调用构造函数时，如果 *bPrintSetupOnly* 设置为 FALSE，则会自动使用 PD_RETURNDC 标志。 调用 `DoModal` 、 `GetDefaults` 或后 `GetPrinterDC` ，将在中返回打印机 DC `m_pd.hDC` 。 必须通过调用方调用 [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) 来释放此 DC `CPrintDialog` 。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：： CreatePrinterDC](#createprinterdc)的示例。

## <a name="cprintdialoggetcopies"></a><a name="getcopies"></a> CPrintDialog::GetCopies

检索请求的副本数。

```
int GetCopies() const;
```

### <a name="return-value"></a>返回值

请求的副本数。

### <a name="remarks"></a>备注

在调用 `DoModal` 以检索请求的副本数后调用此函数。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：:P rintcollate](#printcollate)的示例。

## <a name="cprintdialoggetdefaults"></a><a name="getdefaults"></a> CPrintDialog::GetDefaults

在不显示对话框的情况下检索默认打印机的设备默认值。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

检索到的值放在 `m_pd` 结构中。

在某些情况下，对此函数的调用将调用的 [构造函数](#cprintdialog) ， `CPrintDialog` 并将 *bPrintSetupOnly* 设置为 FALSE。 在这些情况下， `hDevNames` 会自动分配打印机 DC 和和 `hDevMode` (位于 `m_pd` 数据成员) 中的两个句柄。

如果在 `CPrintDialog` *bPrintSetupOnly* 设置为 FALSE 的情况下调用的构造函数，则此函数将不会仅返回调用方并将其放 `hDevNames` `hDevMode` 入 `m_pd.hDevNames` 和 `m_pd.hDevMode`) 中，但也将在中返回打印机 DC `m_pd.hDC` 。 当您完成对象时，调用方负责删除打印机 DC 并在句柄上调用 Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) 函数 `CPrintDialog` 。

### <a name="example"></a>示例

此代码段获取默认打印机的设备上下文，并向用户报告打印机的分辨率（以每英寸点数为单位）。  (打印机功能的此属性通常称为 DPI。 ) 

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

## <a name="cprintdialoggetdevicename"></a><a name="getdevicename"></a> CPrintDialog::GetDeviceName

检索当前所选打印机设备的名称。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>返回值

当前选定的打印机的名称。

### <a name="remarks"></a>备注

在调用 [DoModal](#domodal) 以检索当前所选打印机的名称后，或在调用 [GetDefaults](#getdefaults) 检索默认打印机的当前设备默认值之后调用此函数。 `CString` `GetDeviceName` `lpszDeviceName` 在对[CDC：： CreateDC](../../mfc/reference/cdc-class.md#createdc)的调用中，使用指向返回的对象的指针作为的值。

### <a name="example"></a>示例

此代码片段显示用户的默认打印机名称及其连接到的端口，以及打印机使用的 "后台处理程序名称"。 此代码可能会显示一个消息框，其中显示 "你的默认打印机是使用 winspool.drv 的 \server\share 上的 HP LaserJet IIIP \\ 。"，例如。

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

## <a name="cprintdialoggetdevmode"></a><a name="getdevmode"></a> CPrintDialog::GetDevMode

检索 `DEVMODE` 结构。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>返回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)数据结构，其中包含有关打印机驱动程序的设备初始化和环境的信息。 必须使用 Windows SDK 中描述的 Windows [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) 函数来解锁此结构使用的内存。

### <a name="remarks"></a>备注

在调用 [DoModal](#domodal) 或 [GetDefaults](#getdefaults) 后调用此函数可检索有关打印设备的信息。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：:P rintcollate](#printcollate)的示例。

## <a name="cprintdialoggetdrivername"></a><a name="getdrivername"></a> CPrintDialog：： GetDriverName

检索当前选定的打印机驱动程序的名称。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>返回值

一个， `CString` 指定系统定义的驱动程序名称。

### <a name="remarks"></a>备注

在调用 [DoModal](#domodal) 或 [GetDefaults](#getdefaults) 后调用此函数可检索系统定义的打印机设备驱动程序的名称。 `CString` `GetDriverName` `lpszDriverName` 在对[CDC：： CreateDC](../../mfc/reference/cdc-class.md#createdc)的调用中，使用指向返回的对象的指针作为的值。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：： GetDeviceName](#getdevicename)的示例。

## <a name="cprintdialoggetfrompage"></a><a name="getfrompage"></a> CPrintDialog::GetFromPage

检索打印范围的起始页。

```
int GetFromPage() const;
```

### <a name="return-value"></a>返回值

要打印的页范围中的起始页码。

### <a name="remarks"></a>备注

在调用 `DoModal` 以检索要打印的页范围内的起始页码后，调用此函数。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：： m_pd](#m_pd)的示例。

## <a name="cprintdialoggetportname"></a><a name="getportname"></a> CPrintDialog::GetPortName

检索当前选定的打印机端口的名称。

```
CString GetPortName() const;
```

### <a name="return-value"></a>返回值

当前选定的打印机端口的名称。

### <a name="remarks"></a>备注

调用 [DoModal](#domodal) 或 [GetDefaults](#getdefaults) 后调用此函数可检索当前选定的打印机端口的名称。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：： GetDeviceName](#getdevicename)的示例。

## <a name="cprintdialoggetprinterdc"></a><a name="getprinterdc"></a> CPrintDialog::GetPrinterDC

检索打印机设备上下文的句柄。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>返回值

如果成功，则为打印机设备上下文的句柄;否则为 NULL。

### <a name="remarks"></a>备注

如果构造函数的 *bPrintSetupOnly* 参数为 `CPrintDialog` FALSE (指示 "打印" 对话框) 显示，则 `GetPrinterDC` 返回打印机设备上下文的句柄。 使用 Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) 函数时，必须调用该函数以删除设备上下文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

## <a name="cprintdialoggettopage"></a><a name="gettopage"></a> CPrintDialog::GetToPage

检索打印范围的结束页。

```
int GetToPage() const;
```

### <a name="return-value"></a>返回值

要打印的页范围中的结束页码。

### <a name="remarks"></a>备注

在调用 `DoModal` 以检索要打印的页范围内的结束页码后，调用此函数。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：： m_pd](#m_pd)的示例。

## <a name="cprintdialogm_pd"></a><a name="m_pd"></a> CPrintDialog：： m_pd

一个结构，其成员存储对话框对象的特性。

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>备注

构造对象之后 `CPrintDialog` ，您可以使用在 `m_pd` 调用 [DoModal](#domodal) 成员函数之前设置对话框的各个方面。 有关结构的详细信息 `m_pd` ，请参阅 Windows SDK 中的 [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) 。

如果 `m_pd` 直接修改数据成员，将重写任何默认行为。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

## <a name="cprintdialogprintall"></a><a name="printall"></a> CPrintDialog：:P rintAll

确定是否打印文档的所有页。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>返回值

如果文档中的所有页面都要打印，则为非零值;否则为0。

### <a name="remarks"></a>备注

调用后调用此函数 `DoModal` 可确定是否要打印文档中的所有页。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：： m_pd](#m_pd)的示例。

## <a name="cprintdialogprintcollate"></a><a name="printcollate"></a> CPrintDialog：:P rintCollate

确定是否请求逐份打印副本。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>返回值

如果用户在对话框中选中了 "逐份打印" 复选框，则为非零值;否则为0。

### <a name="remarks"></a>备注

调用后调用此函数 `DoModal` 可确定打印机是否应逐份打印文档的所有打印副本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

## <a name="cprintdialogprintrange"></a><a name="printrange"></a> CPrintDialog：:P rintRange

确定是否仅打印指定范围的页面。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>返回值

如果仅打印文档中的一系列页面，则为非零值;否则为0。

### <a name="remarks"></a>备注

调用后调用此函数 `DoModal` 可确定是否仅打印文档中的一系列页面。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：： m_pd](#m_pd)的示例。

## <a name="cprintdialogprintselection"></a><a name="printselection"></a> CPrintDialog：:P rintSelection

确定是否仅打印当前选定的项。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>返回值

如果仅打印选定项，则为非零值;否则为0。

### <a name="remarks"></a>备注

调用后调用此函数 `DoModal` 可确定是否仅打印当前选定的项。

### <a name="example"></a>示例

  请参阅 [CPrintDialog：： m_pd](#m_pd)的示例。

## <a name="see-also"></a>请参阅

[MFC 示例 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 结构](../../mfc/reference/cprintinfo-structure.md)

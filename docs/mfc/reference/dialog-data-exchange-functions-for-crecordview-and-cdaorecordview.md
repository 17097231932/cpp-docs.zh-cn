---
title: CRecordView 和 CDaoRecordView 的对话框数据交换函数
ms.date: 09/17/2019
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 06d0511317c21f6b132349d7d6cd6c2d6f20bc1b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837367"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的对话框数据交换函数

本主题列出了用于在 [CRecordset](../../mfc/reference/crecordset-class.md) 和 [CRecordView](../../mfc/reference/crecordview-class.md) 窗体或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 和 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 窗体之间交换数据的 DDX_Field 函数。 DAO 与 Access 数据库结合使用，并受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。

> [!NOTE]
> DDX_Field 函数类似于 DDX 函数，因为它们与窗体中的控件交换数据。 但与 DDX 不同，它们将数据与视图的关联记录集对象的字段而不是记录视图本身的字段交换。 有关详细信息，请参阅类 `CRecordView` 和 `CDaoRecordView` 。

### <a name="ddx_field-functions"></a>DDX_Field 函数

|名称|说明|
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|在 [CRecordView](../../mfc/reference/crecordview-class.md) 或 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)中的组合框中，在记录集字段数据成员和当前选择的索引之间传输整数数据。|
|[DDX_FieldCBString](#ddx_fieldcbstring)|`CString`在或中的组合框的记录集字段数据成员和编辑控件之间传输数据 `CRecordView` `CDaoRecordView` 。 将数据从记录集移到控件时，此函数将选择组合框中以指定字符串中的字符开头的项。|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|`CString`在或中的组合框的记录集字段数据成员和编辑控件之间传输数据 `CRecordView` `CDaoRecordView` 。 将数据从记录集移到控件时，此函数将选择组合框中与指定字符串完全匹配的项。|
|[DDX_FieldCheck](#ddx_fieldcheck)|在或中的记录集字段数据成员与复选框之间传输布尔 `CRecordView` 数据 `CDaoRecordView` 。|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|在或的列表框中的记录集字段数据成员和当前所选内容的索引之间传输整数 `CRecordView` 数据 `CDaoRecordView` 。|
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理列表框控件和记录集的字段数据成员之间的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 数据传输。 将数据从记录集移到控件时，此函数将在列表框中选择以指定字符串中的字符开头的项。|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理 `CString` 列表框控件和记录集的字段数据成员之间的数据传输。 将数据从记录集移到控件时，此函数将选择与指定的字符串完全匹配的第一项。|
|[DDX_FieldRadio](#ddx_fieldradio)|在或中的记录集字段数据成员和一组单选按钮之间传输整数 `CRecordView` 数据 `CDaoRecordView` 。|
|[DDX_FieldScroll](#ddx_fieldscroll)|设置或获取或中滚动条控件的滚动位置 `CRecordView` `CDaoRecordView` 。 调用 [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) 函数。|
|[DDX_FieldSlider](#ddx_fieldslider)|同步记录视图中滑块控件和 **`int`** 记录集的字段数据成员的拇指位置。 |
|[DDX_FieldText](#ddx_fieldtext)|重载版本可用于 **`int`** **UINT** **`long`** `DWORD` [CString](../../atl-mfc-shared/reference/cstringt-class.md) **`float`** **`double`** **`short`** 在或中的记录集字段数据成员和编辑框[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)之间[COleCurrency](../../mfc/reference/colecurrency-class.md)传输 `CRecordView` 、UINT、、、CString、、、、COleDateTime 和 COleCurrency 数据 `CDaoRecordView` 。|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a> DDX_FieldCBIndex

`DDX_FieldCBIndex`函数同步记录视图中组合框控件的列表框控件中的选定项的索引，以及 **`int`** 与记录视图关联的记录集的字段数据成员。

```cpp
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*index*<br/>
对关联或对象中的字段数据成员的 `CRecordset` 引用 `CDaoRecordset` 。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。

### <a name="remarks"></a>注解

将数据从记录集移到控件时，此函数将基于在 *index*中指定的值来设置控件中的选定内容。 当从记录集到控件的传输时，如果记录集字段为空，则 MFC 会将索引的值设置为0。 在从 control 到 recordset 的传输时，如果控件为空或未选择任何项，则将记录集字段设置为0。

如果使用的是基于 ODBC 的类，请使用第一个版本。 如果使用的是基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 字段的 DDX 的示例和详细信息，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>示例

有关一般 DDX_Field 示例，请参阅 [DDX_FieldText](#ddx_fieldtext) 。 此示例类似于 `DDX_FieldCBIndex` 。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a> DDX_FieldCBString

`DDX_FieldCBString` 函数管理记录视图中组合框控件的编辑控件和与记录视图关联的记录集的`CString`字段数据成员之间的[CString](../../atl-mfc-shared/reference/cstringt-class.md)数据传输。 

```cpp
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联或对象中的字段数据成员的 `CRecordset` 引用 `CDaoRecordset` 。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。

### <a name="remarks"></a>注解

将数据从记录集移到控件时，此函数将组合框中的当前选定内容设置为以 " *值*" 中指定的字符串中的字符开头的第一行。 在从记录集到控件的传输上，如果记录集字段为空，则将从组合框中删除任何选择，组合框的编辑控件将设置为空。 在从 control 到 recordset 的传输时，如果控件为空，则在字段允许时，"记录集" 字段将设置为 Null。

如果使用的是基于 ODBC 的类，请使用第一个版本。 如果使用的是基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 字段的 DDX 的示例和详细信息，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>示例

有关一般 DDX_Field 示例，请参阅 [DDX_FieldText](#ddx_fieldtext) 。 该示例包括对的调用 `DDX_FieldCBString` 。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a> DDX_FieldCBStringExact

`DDX_FieldCBStringExact` 函数管理记录视图中组合框控件的编辑控件和与记录视图关联的记录集的`CString`字段数据成员之间的[CString](../../atl-mfc-shared/reference/cstringt-class.md)数据传输。 

```cpp
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联或对象中的字段数据成员的 `CRecordset` 引用 `CDaoRecordset` 。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。

### <a name="remarks"></a>注解

将数据从记录集移到控件时，此函数将组合框中的当前选择设置为与 " *值*" 中指定的字符串完全匹配的第一行。 在从记录集到控件的传输上，如果记录集字段为空，则将从组合框中删除任何选择，组合框的编辑框将设置为空。 在从 control 到 recordset 的传输时，如果控件为空，则记录集字段将设置为 NULL。

如果使用的是基于 ODBC 的类，请使用第一个版本。 如果使用的是基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 字段的 DDX 的示例和详细信息，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>示例

有关一般 DDX_Field 示例，请参阅 [DDX_FieldText](#ddx_fieldtext) 。 对的调用将 `DDX_FieldCBStringExact` 类似。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a> DDX_FieldCheck

`DDX_FieldCheck`函数管理 **`int`** 对话框、窗体视图或控件视图对象中的复选框控件与 **`int`** 对话框、窗体视图或控件视图对象的数据成员之间的数据传输。

```cpp
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的复选框控件的资源 ID。

*value*<br/>
对用于交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。

### <a name="remarks"></a>注解

当 `DDX_FieldCheck` 调用时， *value* 设置为复选框控件的当前状态，或者控件的状态设置为 " *值*"，具体取决于传输方向。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a> DDX_FieldLBIndex

`DDX_FieldLBIndex`函数同步记录视图中列表框控件中选定项的索引，以及 **`int`** 与记录视图关联的记录集的字段数据成员。

```cpp
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*index*<br/>
对关联或对象中的字段数据成员的 `CRecordset` 引用 `CDaoRecordset` 。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。

### <a name="remarks"></a>注解

将数据从记录集移到控件时，此函数将基于在 *index*中指定的值来设置控件中的选定内容。 当从记录集到控件的传输时，如果记录集字段为空，则 MFC 会将索引的值设置为0。 在从 control 到 recordset 的传输时，如果控件为空，则 "记录集" 字段设置为0。

如果使用的是基于 ODBC 的类，请使用第一个版本。 如果使用的是基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 字段的 DDX 的示例和详细信息，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>示例

有关一般 DDX_Field 示例，请参阅 [DDX_FieldText](#ddx_fieldtext) 。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a> DDX_FieldLBString

`DDX_FieldLBString`将记录视图中列表框控件的当前选定内容 复制到与记录视图关联的记录集的[CString](../../atl-mfc-shared/reference/cstringt-class.md)字段数据成员中。

```cpp
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联或对象中的字段数据成员的 `CRecordset` 引用 `CDaoRecordset` 。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。

### <a name="remarks"></a>注解

相反，此函数将列表框中的当前选定内容设置为以 *值*指定的字符串中的字符开头的第一行。 当从记录集到控件的传输时，如果记录集字段为空，则会从列表框中删除任何选择。 在从 control 到 recordset 的传输时，如果控件为空，则记录集字段将设置为 Null。

如果使用的是基于 ODBC 的类，请使用第一个版本。 如果使用的是基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 字段的 DDX 的示例和详细信息，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>示例

有关一般 DDX_Field 示例，请参阅 [DDX_FieldText](#ddx_fieldtext) 。 对的调用将 `DDX_FieldLBString` 类似。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a> DDX_FieldLBStringExact

`DDX_FieldLBStringExact`函数将记录视图中列表框控件的当前选定内容复制到与记录视图关联的记录集的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 字段数据成员中。  

```cpp
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联或对象中的字段数据成员的 `CRecordset` 引用 `CDaoRecordset` 。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。

### <a name="remarks"></a>注解

相反，此函数将列表框中的当前选定内容设置为与 " *值*" 中指定的字符串完全匹配的第一行。 当从记录集到控件的传输时，如果记录集字段为空，则会从列表框中删除任何选择。 在从 control 到 recordset 的传输时，如果控件为空，则记录集字段将设置为 Null。

如果使用的是基于 ODBC 的类，请使用第一个版本。 如果使用的是基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 字段的 DDX 的示例和详细信息，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>示例

有关一般 DDX_Field 示例，请参阅 [DDX_FieldText](#ddx_fieldtext) 。 对的调用将 `DDX_FieldLBStringExact` 类似。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a> DDX_FieldRadio

`DDX_FieldRadio`函数将记录视图记录集的从零开始的 **`int`** 成员变量与记录视图的一组单选按钮中的当前所选单选按钮相关联。

```cpp
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
组中第一个的 ID 与 [CRecordView](../../mfc/reference/crecordview-class.md) 或 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 对象中相邻单选按钮控件的样式 WS_GROUP)  (。

*value*<br/>
对关联或对象中的字段数据成员的 `CRecordset` 引用 `CDaoRecordset` 。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。

### <a name="remarks"></a>注解

从记录集字段传输到视图时，此函数将打开第 *n* 个单选按钮 (从零开始的) 并关闭其他按钮。 相反，此函数将记录集字段设置为当前)  (选中的单选按钮的序号。 当从记录集到控件的传输时，如果记录集字段为空，则不选择任何按钮。 在从控件传输到记录集时，如果未选择任何控件，则在字段允许时，"记录集" 字段将设置为 Null。

如果使用的是基于 ODBC 的类，请使用第一个版本。 如果使用的是基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 字段的 DDX 的示例和详细信息，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>示例

有关一般 DDX_Field 示例，请参阅 [DDX_FieldText](#ddx_fieldtext) 。 对的调用将 `DDX_FieldRadio` 类似。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a> DDX_FieldScroll

`DDX_FieldScroll`函数将在记录视图和与记录视图关联的记录集的字段数据成员中同步滚动条控件的滚动位置， **`int`** (或使用您选择将其映射到) 的任何整数变量。

```cpp
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
组中第一个的 ID 与 [CRecordView](../../mfc/reference/crecordview-class.md) 或 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 对象中相邻单选按钮控件的样式 WS_GROUP)  (。

*value*<br/>
对关联或对象中的字段数据成员的 `CRecordset` 引用 `CDaoRecordset` 。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。

### <a name="remarks"></a>注解

将数据从记录集移到控件时，此函数将滚动条控件的滚动位置设置为在 " *值*" 中指定的值。 当从记录集到控件的传输时，如果记录集字段为空，则将滚动条控件设置为0。 在从 control 到 recordset 的传输时，如果控件为空，则记录集字段的值为0。

如果使用的是基于 ODBC 的类，请使用第一个版本。 如果使用的是基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 字段的 DDX 的示例和详细信息，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>示例

有关一般 DDX_Field 示例，请参阅 [DDX_FieldText](#ddx_fieldtext) 。 对的调用将 `DDX_FieldScroll` 类似。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a> DDX_FieldSlider

`DDX_FieldSlider`函数将在记录视图和 **`int`** 与记录视图关联的记录集的字段数据成员与记录视图关联的记录集的滚动块位置同步 (或使用您选择将其映射到) 的任何整数变量。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DDX_FieldSlider(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
滑块控件的资源 ID。

*value*<br/>
对要交换的值的引用。 此参数保留或将用于设置滑块控件的当前拇指位置。

*pRecordset*<br/>
一个指针，指向要 `CRecordset` 与之交换数据的关联的或 `CDaoRecordset` 对象。

### <a name="remarks"></a>注解

将数据从记录集移到滑块时，此函数将滑块的位置设置为 " *值*" 中指定的值。 在从记录集到控件的传输上，如果记录集字段为 Null，滑块控件的位置设置为0。 在从控件到记录集的传输时，如果控件为空，则记录集字段的值为0。

`DDX_FieldSlider` 不使用滑块控件交换范围信息，滑块控件可以设置范围而不只是一个位置。

如果使用的是基于 ODBC 的类，请使用函数的第一个重写。 将第二个替代用于基于 DAO 的类。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../dialog-data-exchange-and-validation.md)。 有关和字段的 DDX 的示例和详细信息 `CRecordView` `CDaoRecordView` ，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)。 有关滑块控件的信息，请参阅 [Using CSliderCtrl](../using-csliderctrl.md)。

### <a name="example"></a>示例

有关一般 DDX_Field 示例，请参阅 [DDX_FieldText](#ddx_fieldtext) 。 对的调用将 `DDX_FieldSlider` 类似。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a> DDX_FieldText

`DDX_FieldText`函数管理在 **`int`** **`short`** **`long`** [CString](../../atl-mfc-shared/reference/cstringt-class.md) **`float`** **`double`** 编辑框控件和记录集的字段数据成员之间的**BOOL**、、、DWORD、CString、、、布尔或**字节**数据的传输。

```cpp
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联或对象中的字段数据成员的 `CRecordset` 引用 `CDaoRecordset` 。 值的数据类型取决于使用的重载版本中的哪一种 `DDX_FieldText` 。

*pRecordset*<br/>
指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的指针，数据将与该对象交换。 此指针可 `DDX_FieldText` 检测并设置 Null 值。

### <a name="remarks"></a>注解

对于 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象， `DDX_FieldText` 还管理传输 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和 [COleCurrency](../../mfc/reference/colecurrency-class.md) 值。 空的编辑框控件指示 Null 值。 当从记录集到控件的传输时，如果记录集字段为空，则编辑框将设置为空。 在从 control 到 recordset 的传输时，如果控件为空，则记录集字段将设置为 Null。

如果使用的是基于 ODBC 的类，请使用带有 [CRecordset](../../mfc/reference/crecordset-class.md) 参数的版本。 如果使用的是基于 DAO 的类，请使用带有 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 参数的版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关 [CRecordView](../../mfc/reference/crecordview-class.md) 和 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 字段的 DDX 的示例和详细信息，请参阅 [记录视图](../../data/record-views-mfc-data-access.md)一文。

### <a name="example"></a>示例

[CRecordView](../../mfc/reference/crecordview-class.md) 的以下`DoDataExchange`函数包含 三种数据类型的`DDX_FieldText`函数调用：`IDC_COURSELIST` 是一个组合框; 另两个控件是编辑框。 对于 DAO 编程， *m_pSet* 参数是指向 [CRecordset](../../mfc/reference/crecordset-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)的指针。

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)

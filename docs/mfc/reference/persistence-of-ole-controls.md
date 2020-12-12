---
description: 了解更多： OLE 控件的持久性
title: OLE 控件的持久性
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 8c0ee5b81ffd21953c3ed9bcbc21a9ae30979b49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218974"
---
# <a name="persistence-of-ole-controls"></a>OLE 控件的持久性

OLE 控件的一项功能是属性持久化（或称为“序列化”），它允许 OLE 控件在文件或流中读取或写入属性值。 即使在容器应用程序销毁该控件之后，该应用程序仍可以使用序列化来存储控件的属性值。 之后，当创建控件的新实例时，OLE 控件的属性值可从文件或流中读取。

### <a name="persistence-of-ole-controls"></a>OLE 控件的持久性

|名称|描述|
|-|-|
|[PX_Blob](#px_blob)|交换存储二进制大型对象 (BLOB) 数据的控件属性。|
|[PX_Bool](#px_bool)|交换类型为 **BOOL** 的控件属性。|
|[PX_Color](#px_color)|交换控件的颜色属性。|
|[PX_Currency](#px_currency)|交换类型为 **CY** 的控件属性。|
|[PX_DataPath](#px_datapath)|交换 `CDataPathProperty` 类型的控件属性。|
|[PX_Double](#px_double)|交换类型的控件属性 **`double`** 。|
|[PX_Font](#px_font)|交换控件的字体属性。|
|[PX_Float](#px_float)|交换类型的控件属性 **`float`** 。|
|[PX_IUnknown](#px_iunknown)|交换未定义类型的控件属性。|
|[PX_Long](#px_long)|交换类型的控件属性 **`long`** 。|
|[PX_Picture](#px_picture)|交换控件的图片属性。|
|[PX_Short](#px_short)|交换类型的控件属性 **`short`** 。|
|[PX_ULong](#px_ulong)|交换类型为 **ULONG** 的控件属性。|
|[PX_UShort](#px_ushort)|交换类型为 **USHORT** 的控件属性。|
|[PXstring](#px_string)|交换字符字符串控件属性。|
|[PX_VBXFontConvert](#px_vbxfontconvert)|将 VBX 控件的字体相关属性交换到 OLE 控件字体属性中。|

此外，还 `AfxOleTypeMatchGuid` 提供了全局函数来测试 TYPEDESC 和给定 GUID 之间的匹配。

## <a name="px_blob"></a><a name="px_blob"></a> PX_Blob

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化一个属性，该属性存储 (BLOB) 数据的二进制大型对象。

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*hBlob*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*hBlobDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，将从 *hBlob* 引用的变量读取或写入属性的值。 此变量在最初第一次调用之前应初始化为 NULL `PX_Blob` (通常情况下，可以在控件的构造函数) 中完成此操作。 如果指定了 *hBlobDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的初始化或序列化进程失败，则使用此值。

句柄 *hBlob* 和 *hBlobDefault* 指的是内存块，其中包含以下内容：

- 一个 DWORD，其中包含后面紧跟的二进制数据的长度（以字节为单位）

- 包含实际二进制数据的内存块。

请注意， `PX_Blob` 在加载 BLOB 类型属性时，将使用 Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) API 分配内存。 你负责释放此内存。 因此，控件的析构函数应调用任何 BLOB 类型属性句柄上的 [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) ，以释放分配给控件的任何内存。

## <a name="px_bool"></a><a name="px_bool"></a> PX_Bool

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化 BOOL 类型的属性。

```cpp
BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue);

BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue,
    BOOL bDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*bValue*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*bDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，将从 *bValue* 引用的变量读取或写入属性的值。 如果指定了 *bDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_color"></a><a name="px_color"></a> PX_Color

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化 OLE_COLOR 类型的属性。

```cpp
BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue,
    OLE_COLOR clrDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*clrValue*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*clrDefault*<br/>
属性的默认值，由控件开发人员定义。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，将从 *clrValue* 引用的变量读取或写入属性的值。 如果指定了 *clrDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_currency"></a><a name="px_currency"></a> PX_Currency

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化 **货币** 类型的属性。

```cpp
BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue);

BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue,
    CY cyDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*cyValue*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*cyDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，将从 *cyValue* 引用的变量读取或写入属性的值。 如果指定了 *cyDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_datapath"></a><a name="px_datapath"></a> PX_DataPath

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)类型的数据路径属性。

```cpp
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*dataPathProperty*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

数据路径属性实现异步控件属性。 根据需要，将从 *dataPathProperty* 引用的变量读取或写入属性的值。

## <a name="px_double"></a><a name="px_double"></a> PX_Double

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化类型为的属性 **`double`** 。

```cpp
BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue);

BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue,
    double doubleDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*doubleValue*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*doubleDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从 *doubleValue* 引用的变量读取或写入属性的值。 如果指定了 *doubleDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_font"></a><a name="px_font"></a> PX_Font

在控件的成员函数中调用此函数 `DoPropExchange` ，以便序列化或初始化类型字体的属性。

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*文字*<br/>
对 `CFontHolder` 包含 font 属性的对象的引用。

*pFontDesc*<br/>
指向结构的指针 `FONTDESC` ，该结构包含在初始化 font 属性的默认状态时要使用的值（在 *PFONTDISPAMBIENT* 为 NULL 的情况下）。

*pFontDispAmbient*<br/>
一个指针，指向用于 `IFontDisp` 初始化 font 属性的默认状态的字体的接口。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

适当时，属性的值将在引用中进行读取或写入 `font` `CFontHolder` 。 如果指定了 *pFontDesc* 和 *pFontDispAmbient* ，则在需要时，它们用于初始化属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用这些值。 通常，为 *pFontDesc* 传递 NULL，并为 pFontDispAmbient 传递返回的环境值 `COleControl::AmbientFont` 。  请注意，由返回的 font 对象 `COleControl::AmbientFont` 必须通过调用成员函数来释放 `IFontDisp::Release` 。

## <a name="px_float"></a><a name="px_float"></a> PX_Float

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化类型为的属性 **`float`** 。

```cpp
BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue);

BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue,
    float floatDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*floatValue*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*floatDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从 *floatValue* 引用的变量读取或写入属性的值。 如果指定了 *floatDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_iunknown"></a><a name="px_iunknown"></a> PX_IUnknown

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化具有派生接口的对象所表示的属性 `IUnknown` 。

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*pUnk*<br/>
对变量的引用，该变量包含表示属性值的对象的接口。

*iid*<br/>
一个接口 ID，指示控件使用的属性对象的接口。

*pUnkDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从 *pUnk* 引用的变量读取或写入属性的值。 如果指定了 *pUnkDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_long"></a><a name="px_long"></a> PX_Long

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化类型为的属性 **`long`** 。

```cpp
BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue);

BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue,
    long lDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*左值*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*lDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从 *lValue* 引用的变量读取或写入属性的值。 如果指定了 *lDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_picture"></a><a name="px_picture"></a> PX_Picture

在控件的成员函数中调用此函数 `DoPropExchange` ，以便序列化或初始化控件的图片属性。

```cpp
BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict);

BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict,
    CPictureHolder& pictDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*图像*<br/>
对 [CPictureHolder](../../mfc/reference/cpictureholder-class.md) 对象的引用，该对象存储属性 (通常是类) 的成员变量。

*pictDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从 *pict* 引用的变量读取或写入属性的值。 如果指定了 *pictDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_short"></a><a name="px_short"></a> PX_Short

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化类型为的属性 **`short`** 。

```cpp
BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue);

BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue,
    short sDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*sValue*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*sDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从 *sValue* 引用的变量读取或写入属性的值。 如果指定了 *sDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_ulong"></a><a name="px_ulong"></a> PX_ULong

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化类型为 **ULONG** 的属性。

```cpp
BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue);

BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue,
    long ulDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
正在交换的属性的名称。

*ulValue*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*ulDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从 *ulValue* 引用的变量读取或写入属性的值。 如果指定了 *ulDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_ushort"></a><a name="px_ushort"></a> PX_UShort

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化类型为的属性 **`unsigned short`** 。

```cpp
BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue);

BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue,
    USHORT usDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
正在交换的属性的名称。

*usValue*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*usDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从 *usValue* 引用的变量读取或写入属性的值。 如果指定了 *usDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="pxstring"></a><a name="px_string"></a> PXstring

在控件的成员函数中调用此函数 `DoPropExchange` ，以序列化或初始化字符串属性。

```cpp
BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue);

BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue,
    CString strDefault);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*pszPropName*<br/>
要交换的属性的名称。

*strValue*<br/>
引用存储属性的变量 (通常为类) 的成员变量。

*strDefault*<br/>
属性的默认值。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

根据需要，从 *strValue* 引用的变量读取或写入属性的值。 如果指定了 *strDefault* ，则它将用作属性的默认值。 如果出于任何原因导致控件的序列化过程失败，则使用此值。

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a> PX_VBXFontConvert

`DoPropExchange`通过转换 VBX 控件的字体相关属性，在控件的成员函数中调用此函数以初始化字体属性。

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>parameters

*pPX*<br/>
指向 [CPropExchange](../../mfc/reference/cpropexchange-class.md) 对象的指针 (通常作为参数传递给 `DoPropExchange`) 。

*文字*<br/>
OLE 控件的 "字体" 属性，将包含已转换的 VBX 字体相关属性。

### <a name="return-value"></a>返回值

如果交换成功，则为非零值;如果不成功，则为0。

### <a name="remarks"></a>备注

此函数应仅由设计为 VBX 控件的直接替换的 OLE 控件使用。 当 Visual Basic 开发环境转换包含 VBX 控件的窗体以使用相应的替换 OLE 控件时，它将调用控件的 `IDataObject::SetData` 函数，并传入包含 VBX 控件的属性数据的属性集。 此操作反过来会导致调用控件的 `DoPropExchange` 函数。 `DoPropExchange` 可以调用 `PX_VBXFontConvert` 来将 VBX 控件的与字体相关的属性（例如，"FontName"、"FontSize"）转换 (，并将) 转换为 OLE 控件的 "字体" 属性的相应组件。

`PX_VBXFontConvert` 只应在实际从 VBX 窗体应用程序转换控件时调用。 例如：

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

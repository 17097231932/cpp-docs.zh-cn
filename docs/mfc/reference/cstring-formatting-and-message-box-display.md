---
title: CString 格式设置和消息框显示
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: e346fe6ed5235f98f9e1206e92cb53c2fd5c929f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831120"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString 格式设置和消息框显示

提供了许多用于格式化和分析对象的函数 `CString` 。 您可以在需要操作对象时使用这些功能 `CString` ，但它们特别适用于设置将出现在消息框文本中的字符串。

此组函数还包括用于显示消息框的全局例程。

### <a name="cstring-functions"></a>CString 函数

|名称|说明|
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|提取由给定源字符串中的单个字符分隔的子字符串。|
|[AfxFormatString1](#afxformatstring1)|在字符串表中包含的字符串中，用给定字符串替换格式字符 "%1"。|
|[AfxFormatString2](#afxformatstring2)|在字符串表中包含的字符串中，用两个字符串替换格式字符 "%1" 和 "%2"。|
|[AfxMessageBox](#afxmessagebox)|显示消息框。|

### <a name="requirements"></a>要求

  **标头** afxwin。h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a> AfxExtractSubString

此全局函数可用于从给定的源字符串中提取子字符串。

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>参数

*rString*<br/>
对将接收单个子字符串的 [CString](../../atl-mfc-shared/using-cstring.md) 对象的引用。

*lpszFullString*<br/>
字符串，包含要从中提取的字符串的完整文本。

*iSubString*<br/>
要从 *lpszFullString*中提取的子字符串的从零开始的索引。

*chSep*<br/>
用于分隔子字符串的分隔符字符。

### <a name="return-value"></a>返回值

如果函数成功提取所提供索引处的子字符串，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>注解

此函数可用于在已知单个字符分隔每个子字符串时从源字符串提取多个子字符串。 此函数在每次调用 *lpszFullString* 参数时从该参数的开头搜索。

如果将 *lpszFullString* 设置为 NULL，或者 *如果没有找到指定分隔符的* *iSubString*+ 1 匹配项，则此函数将返回 FALSE。 如果*lpszFullString*设置为 NULL，则不会从其原始值中修改*rString*参数;否则，如果无法为指定的索引提取子字符串，则*rString*参数将设置为空字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>要求

  **标头** afxwin。h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a> AfxFormatString1

将 *lpsz1* 所指向的字符串替换为 *nIDS*标识的模板字符串资源中的任何字符 "%1" 的实例。

```cpp
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>参数

*rString*<br/>
对在执行替换后将包含生成字符串的 `CString` 对象的引用。

*nIDS*<br/>
将对其执行替换的模板字符串的资源 ID。

*lpsz1*<br/>
将替换模板字符串中的格式字符串“%1”的字符串。

### <a name="remarks"></a>注解

新生成的字符串存储在 *rString*中。 例如，如果字符串表中的字符串为 "找不到文件 %1"，并且 *lpsz1* 等于 "C:\MYFILE.TXT"，则 *rString* 将包含字符串 "找不到 C:\MYFILE.TXT 文件"。 此函数对为发送到消息框和其他窗口的字符串设置格式很有用。

如果格式字符“%1”多次出现在字符串中，则将执行多次替换。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>要求

  **标头** afxwin。h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a> AfxFormatString2

将 *lpsz1* 所指向的字符串替换为字符 "%1" 的任何实例，并将 *lpsz2* 指向的字符串替换为 *nIDS*标识的模板字符串资源中的 "%2" 字符的任何实例。

```cpp
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>参数

*rString*<br/>
对的引用 `CString` ，它将在执行替换后包含生成的字符串。

*nIDS*<br/>
要对其执行替换的模板字符串的字符串表 ID。

*lpsz1*<br/>
将替换模板字符串中的格式字符串“%1”的字符串。

*lpsz2*<br/>
一个字符串，将替换模板字符串中的格式字符 "%2"。

### <a name="remarks"></a>注解

新生成的字符串存储在 *rString*中。 例如，如果字符串表中的字符串为 "在目录 %2 中找不到文件 %1"，则 *lpsz1* 指向 "MYFILE.TXT"， *lpsz2* 指向 "C:\MYDIR"，则 *RString* 将包含字符串 "文件 MYFILE.TXT 在目录 C:\MYDIR 中找不到"

如果多次出现格式字符 "%1" 或 "%2"，则将进行多次替换。 它们不必按数值顺序排列。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>要求

  **标头** afxwin。h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a> AfxMessageBox

在屏幕上显示一个消息框。

```
int AfxMessageBox(
    LPCTSTR lpszText,
    UINT nType = MB_OK,
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,
    UINT nType = MB_OK,
    UINT nIDHelp = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指向一个 `CString` 对象或以 null 结尾的字符串，其中包含要在消息框中显示的消息。

nType**<br/>
消息框的样式。 将任意 [消息框样式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) 应用到框。

*nIDHelp*<br/>
消息的帮助上下文 ID;0指示将使用应用程序的默认帮助上下文。

*nIDPrompt*<br/>
用于引用字符串表中的字符串的唯一 ID。

### <a name="return-value"></a>返回值

如果没有足够的内存来显示消息框，则为零;否则，将返回以下值之一：

- IDABORT 已选择 "中止" 按钮。

- IDCANCEL 选中 "取消" 按钮。

- IDIGNORE 选中 "忽略" 按钮。

- IDNO 未选择 "否" 按钮。

- IDOK 选择 "确定" 按钮。

- IDRETRY 已选择 "重试" 按钮。

- IDYES 已选择 "是" 按钮。

如果消息框有 "取消" 按钮，则在按下 ESC 键或选中 "取消" 按钮时，将返回 IDCANCEL 值。 如果消息框没有 "取消" 按钮，则按 ESC 键不起作用。

函数 [AfxFormatString1](#afxformatstring1) 和 [AfxFormatString2](#afxformatstring2) 可用于设置显示在消息框中的文本的格式。

### <a name="remarks"></a>注解

此重载函数的第一种形式是在消息框中显示 *lpszText* 指向的文本字符串，并使用 *NIDHelp* 来描述帮助上下文。 当用户按下 "帮助" 键 (通常按 F1) 时，帮助上下文用于跳转到关联的帮助主题。

函数的第二种形式使用 ID 为 *nIDPrompt* 的字符串资源，在消息框中显示消息。 可以通过 *nIDHelp*的值找到关联的帮助页。 如果使用 *nIDHelp* 的默认值 (-1) ，则将字符串资源 ID *nIDPrompt*用于帮助上下文。 有关定义帮助上下文的详细信息，请参阅 [技术说明 28](../../mfc/tn028-context-sensitive-help-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)

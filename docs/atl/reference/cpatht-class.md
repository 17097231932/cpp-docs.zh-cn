---
description: 了解详细信息： CPathT 类
title: CPathT 类
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: 01657eca0e84a9a3271f7912f565dd1dd2417506
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141084"
---
# <a name="cpatht-class"></a>CPathT 类

此类表示一个路径。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>parameters

*StringType*<br/>
要用于路径的 ATL/MFC 字符串类 (参阅 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)) 。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CPathT：:P CXSTR](#pcxstr)|常量字符串类型。|
|[CPathT：:P XSTR](#pxstr)|一种字符串类型。|
|[CPathT::XCHAR](#xchar)|一个字符类型。|

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|路径的构造函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|调用此方法可将反斜杠添加到字符串的末尾，以便为路径创建正确的语法。|
|[CPathT::AddExtension](#addextension)|调用此方法可将文件扩展名添加到路径。|
|[CPathT：： Append](#append)|调用此方法可将字符串追加到当前路径。|
|[CPathT：： BuildRoot](#buildroot)|调用此方法可从给定的驱动器号创建根路径。|
|[CPathT：：规范化](#canonicalize)|调用此方法可将路径转换为规范格式。|
|[CPathT：：合并](#combine)|调用此方法可将表示目录名称的字符串和表示文件路径名称的字符串串联到一个路径中。|
|[CPathT::CommonPrefix](#commonprefix)|调用此方法可确定指定的路径是否与当前路径共享公共前缀。|
|[CPathT::CompactPath](#compactpath)|调用此方法可通过将路径组件替换为省略号，截断文件路径以适应给定的像素宽度。|
|[CPathT::CompactPathEx](#compactpathex)|调用此方法可通过将路径组件替换为省略号来截断文件路径，使其适合给定的字符数。|
|[CPathT::FileExists](#fileexists)|调用此方法以检查此路径名称处的文件是否存在。|
|[CPathT::FindExtension](#findextension)|调用此方法可查找文件扩展名在路径中的位置。|
|[CPathT::FindFileName](#findfilename)|调用此方法可查找文件名在路径中的位置。|
|[CPathT::GetDriveNumber](#getdrivenumber)|调用此方法可在路径 "A" 到 "Z" 的范围内搜索驱动器号，并返回相应的驱动器号。|
|[CPathT：： Path.getextension 对](#getextension)|调用此方法可从路径获取文件扩展名。|
|[CPathT::IsDirectory](#isdirectory)|调用此方法以检查路径是否为有效的目录。|
|[CPathT::IsFileSpec](#isfilespec)|调用此方法可在路径中搜索任何路径分隔字符 (例如，"：" 或 " \\ " ) 。 如果不存在路径分隔字符，则将路径视为文件规范路径。|
|[CPathT::IsPrefix](#isprefix)|调用此方法以确定路径是否包含 *pszPrefix* 传递的类型的有效前缀。|
|[CPathT::IsRelative](#isrelative)|调用此方法以确定路径是否为相对路径。|
|[CPathT：： IsRoot](#isroot)|调用此方法以确定路径是否为目录根。|
|[CPathT::IsSameRoot](#issameroot)|调用此方法以确定另一个路径是否具有具有当前路径的公共根组件。|
|[CPathT::IsUNC](#isunc)|调用此方法以确定路径是否为有效的 UNC (通用命名约定) 服务器和共享的路径。|
|[CPathT::IsUNCServer](#isuncserver)|调用此方法以确定路径是否为有效的 UNC (通用命名约定仅) 服务器的路径。|
|[CPathT::IsUNCServerShare](#isuncservershare)|调用此方法以确定路径是否为有效的 UNC (通用命名约定) 共享路径， \\ \  *服务器* \  *共享*。|
|[CPathT::MakePretty](#makepretty)|调用此方法可将路径转换为所有小写字符，以便为路径指定一致的外观。|
|[CPathT::MatchSpec](#matchspec)|调用此方法以搜索包含通配符匹配类型的字符串的路径。|
|[CPathT::QuoteSpaces](#quotespaces)|如果路径包含空格，则调用此方法将路径用引号引起来。|
|[CPathT::RelativePathTo](#relativepathto)|调用此方法可创建从一个文件或文件夹到另一个文件或文件夹的相对路径。|
|[CPathT::RemoveArgs](#removeargs)|调用此方法可从路径中删除任何命令行参数。|
|[CPathT::RemoveBackslash](#removebackslash)|调用此方法可删除路径中的尾部反斜杠。|
|[CPathT::RemoveBlanks](#removeblanks)|调用此方法可从路径中删除所有前导空格和尾随空格。|
|[CPathT::RemoveExtension](#removeextension)|调用此方法可删除路径中的文件扩展名（如果有）。|
|[CPathT::RemoveFileSpec](#removefilespec)|调用此方法可删除路径中的尾随文件名和反斜杠（如果有）。|
|[CPathT::RenameExtension](#renameextension)|调用此方法可将路径中的文件扩展名替换为新扩展名。 如果文件名不包含扩展，则扩展将附加到字符串的末尾。|
|[CPathT::SkipRoot](#skiproot)|调用此方法可分析路径，忽略驱动器号或 UNC 服务器/共享路径部分。|
|[CPathT::StripPath](#strippath)|调用此方法可删除完全限定路径和文件名的路径部分。|
|[CPathT::StripToRoot](#striptoroot)|调用此方法可删除路径的所有部分（根信息除外）。|
|[CPathT::UnquoteSpaces](#unquotespaces)|调用此方法可删除路径开头和末尾的引号。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CPathT：： operator const StringType &](#operator_const_stringtype_amp)|此运算符允许将对象视为一个字符串。|
|[CPathT：： operator CPathT：:P CXSTR](#operator_cpatht__pcxstr)|此运算符允许将对象视为一个字符串。|
|[CPathT：： operator StringType &](#operator_stringtype_amp)|此运算符允许将对象视为一个字符串。|
|[CPathT：： operator + =](#operator_add_eq)|此运算符将字符串附加到路径。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPathT：： m_strPath](#m_strpath)|路径。|

## <a name="remarks"></a>备注

`CPath`、 `CPathA` 和 `CPathW` 是定义的实例化， `CPathT` 如下所示：

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>要求

**标头：** atlpath。h

## <a name="cpathtaddbackslash"></a><a name="addbackslash"></a> CPathT::AddBackslash

调用此方法可将反斜杠添加到字符串的末尾，以便为路径创建正确的语法。 如果路径已经有尾随反斜杠，则不会添加反斜杠。

```cpp
void AddBackslash();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)。

## <a name="cpathtaddextension"></a><a name="addextension"></a> CPathT::AddExtension

调用此方法可将文件扩展名添加到路径。

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>parameters

*pszExtension*<br/>
要添加的文件扩展名。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)。

## <a name="cpathtappend"></a><a name="append"></a> CPathT：： Append

调用此方法可将字符串追加到当前路径。

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>parameters

*pszMore*<br/>
要追加的字符串。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)。

## <a name="cpathtbuildroot"></a><a name="buildroot"></a> CPathT：： BuildRoot

调用此方法可从给定的驱动器号创建根路径。

```cpp
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>parameters

*iDrive*<br/>
驱动器号 (0 是：，1是 B：，依此类推) 。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)。

## <a name="cpathtcanonicalize"></a><a name="canonicalize"></a> CPathT：：规范化

调用此方法可将路径转换为规范格式。

```cpp
void Canonicalize();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)。

## <a name="cpathtcombine"></a><a name="combine"></a> CPathT：：合并

调用此方法可将表示目录名称的字符串和表示文件路径名称的字符串串联到一个路径中。

```cpp
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>parameters

*pszDir*<br/>
目录路径。

*pszFile*<br/>
文件路径。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)。

## <a name="cpathtcommonprefix"></a><a name="commonprefix"></a> CPathT::CommonPrefix

调用此方法可确定指定的路径是否与当前路径共享公共前缀。

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>parameters

*pszOther*<br/>
要与当前的路径进行比较的路径。

### <a name="return-value"></a>返回值

返回公共前缀。

### <a name="remarks"></a>备注

前缀为以下类型之一： "C： \\ \\ "、"."、".."、".. \\ \\ "。 有关详细信息，请参阅 [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)。

## <a name="cpathtcompactpath"></a><a name="compactpath"></a> CPathT::CompactPath

调用此方法可通过将路径组件替换为省略号，截断文件路径以适应给定的像素宽度。

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>parameters

*hDC*<br/>
用于字体指标的设备上下文。

*nWidth*<br/>
强制字符串适合的宽度（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)。

## <a name="cpathtcompactpathex"></a><a name="compactpathex"></a> CPathT::CompactPathEx

调用此方法可通过将路径组件替换为省略号来截断文件路径，使其适合给定的字符数。

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>parameters

*nMaxChars*<br/>
要包含在新字符串中的最大字符数，包括终止 NULL 字符。

dwFlags <br/>
保留。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)。

## <a name="cpathtcpatht"></a><a name="cpatht"></a> CPathT::CPathT

构造函数。

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>parameters

*pszPath*<br/>
指向路径字符串的指针。

*路径*<br/>
路径字符串。

## <a name="cpathtfileexists"></a><a name="fileexists"></a> CPathT::FileExists

调用此方法以检查此路径名称处的文件是否存在。

```
BOOL FileExists() const;
```

### <a name="return-value"></a>返回值

如果文件存在，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)。

## <a name="cpathtfindextension"></a><a name="findextension"></a> CPathT::FindExtension

调用此方法可查找文件扩展名在路径中的位置。

```
int FindExtension() const;
```

### <a name="return-value"></a>返回值

返回扩展前面的 "." 的位置。 如果找不到扩展，则返回-1。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)。

## <a name="cpathtfindfilename"></a><a name="findfilename"></a> CPathT::FindFileName

调用此方法可查找文件名在路径中的位置。

```
int FindFileName() const;
```

### <a name="return-value"></a>返回值

返回文件名的位置。 如果未找到文件名，则返回-1。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。

## <a name="cpathtgetdrivenumber"></a><a name="getdrivenumber"></a> CPathT::GetDriveNumber

调用此方法可在路径 "A" 到 "Z" 的范围内搜索驱动器号，并返回相应的驱动器号。

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>返回值

如果路径包含驱动器号，则返回驱动器号（从0到 25 (对应于 "A" 到 "Z" ) ）; 否则返回-1。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)。

## <a name="cpathtgetextension"></a><a name="getextension"></a> CPathT：： Path.getextension 对

调用此方法可从路径获取文件扩展名。

```
StringType GetExtension() const;
```

### <a name="return-value"></a>返回值

返回文件扩展名。

## <a name="cpathtisdirectory"></a><a name="isdirectory"></a> CPathT::IsDirectory

调用此方法以检查路径是否为有效的目录。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>返回值

如果路径是目录，则返回非零值 (16) ; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)。

## <a name="cpathtisfilespec"></a><a name="isfilespec"></a> CPathT::IsFileSpec

调用此方法可在路径中搜索任何路径分隔字符 (例如，"：" 或 " \\ " ) 。 如果不存在路径分隔字符，则将路径视为文件规范路径。

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>返回值

如果路径中没有任何路径分隔字符，则返回 TRUE; 如果有路径分隔字符，则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)。

## <a name="cpathtisprefix"></a><a name="isprefix"></a> CPathT::IsPrefix

调用此方法以确定路径是否包含 *pszPrefix* 传递的类型的有效前缀。

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>parameters

*pszPrefix*<br/>
要搜索的前缀。 前缀为以下类型之一： "C： \\ \\ "、"."、".."、".. \\ \\ "。

### <a name="return-value"></a>返回值

如果路径包含前缀，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)。

## <a name="cpathtisrelative"></a><a name="isrelative"></a> CPathT::IsRelative

调用此方法以确定路径是否为相对路径。

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>返回值

如果路径是相对路径，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)。

## <a name="cpathtisroot"></a><a name="isroot"></a> CPathT：： IsRoot

调用此方法以确定路径是否为目录根。

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>返回值

如果路径是根路径，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)。

## <a name="cpathtissameroot"></a><a name="issameroot"></a> CPathT::IsSameRoot

调用此方法以确定另一个路径是否具有具有当前路径的公共根组件。

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>parameters

*pszOther*<br/>
其他路径。

### <a name="return-value"></a>返回值

如果两个字符串具有相同的根组件，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)。

## <a name="cpathtisunc"></a><a name="isunc"></a> CPathT::IsUNC

调用此方法以确定路径是否为有效的 UNC (通用命名约定) 服务器和共享的路径。

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>返回值

如果路径是有效的 UNC 路径，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)。

## <a name="cpathtisuncserver"></a><a name="isuncserver"></a> CPathT::IsUNCServer

调用此方法以确定路径是否为有效的 UNC (通用命名约定仅) 服务器的路径。

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>返回值

如果字符串是服务器的有效 UNC 路径，则返回 TRUE，否则 (不) 共享名称; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)。

## <a name="cpathtisuncservershare"></a><a name="isuncservershare"></a> CPathT::IsUNCServerShare

调用此方法以确定路径是否为有效的 UNC (通用命名约定) 共享路径， \\ \  *服务器* \  *共享*。

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>返回值

如果路径采用的格式为 \\ \  *服务器* \  *共享*，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)。

## <a name="cpathtm_strpath"></a><a name="m_strpath"></a> CPathT：： m_strPath

路径。

```
StringType m_strPath;
```

### <a name="remarks"></a>备注

`StringType` 是的模板参数 `CPathT` 。

## <a name="cpathtmakepretty"></a><a name="makepretty"></a> CPathT::MakePretty

调用此方法可将路径转换为所有小写字符，以便为路径指定一致的外观。

```
BOOL MakePretty();
```

### <a name="return-value"></a>返回值

如果路径已转换，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)。

## <a name="cpathtmatchspec"></a><a name="matchspec"></a> CPathT::MatchSpec

调用此方法以搜索包含通配符匹配类型的字符串的路径。

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>parameters

*pszSpec*<br/>
指向要搜索的文件类型的以 null 结尾的字符串的指针。 例如，若要测试当前路径中的文件是否为 DOC 文件，应将 *pszSpec* 设置为 "* .doc"。

### <a name="return-value"></a>返回值

如果字符串匹配，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)。

## <a name="cpathtoperator-"></a><a name="operator_add_eq"></a> CPathT：： operator + =

此运算符将字符串附加到路径。

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>parameters

*pszMore*<br/>
要追加的字符串。

### <a name="return-value"></a>返回值

返回更新的路径。

## <a name="cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a> CPathT：： operator const StringType &amp;

此运算符允许将对象视为一个字符串。

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>返回值

返回一个字符串，该字符串表示由此对象管理的当前路径。

## <a name="cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a> CPathT：： operator CPathT：:P CXSTR

此运算符允许将对象视为一个字符串。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>返回值

返回一个字符串，该字符串表示由此对象管理的当前路径。

## <a name="cpathtoperator-stringtype-amp"></a><a name="operator_stringtype_amp"></a> CPathT：： operator StringType &amp;

此运算符允许将对象视为一个字符串。

```
operator StringType&() throw();
```

### <a name="return-value"></a>返回值

返回一个字符串，该字符串表示由此对象管理的当前路径。

## <a name="cpathtpcxstr"></a><a name="pcxstr"></a> CPathT：:P CXSTR

常量字符串类型。

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>备注

`StringType` 是的模板参数 `CPathT` 。

## <a name="cpathtpxstr"></a><a name="pxstr"></a> CPathT：:P XSTR

一种字符串类型。

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>备注

`StringType` 是的模板参数 `CPathT` 。

## <a name="cpathtquotespaces"></a><a name="quotespaces"></a> CPathT::QuoteSpaces

如果路径包含空格，则调用此方法将路径用引号引起来。

```cpp
void QuoteSpaces();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)。

## <a name="cpathtrelativepathto"></a><a name="relativepathto"></a> CPathT::RelativePathTo

调用此方法可创建从一个文件或文件夹到另一个文件或文件夹的相对路径。

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>parameters

*pszFrom*<br/>
相对路径的开头。

*dwAttrFrom*<br/>
*PszFrom* 的文件属性。 如果该值包含 FILE_ATTRIBUTE_DIRECTORY，则假定 *pszFrom* 为目录;否则， *pszFrom* 将被假定为文件。

*pszTo*<br/>
相对路径的终结点。

*dwAttrTo*<br/>
*PszTo* 的文件属性。 如果该值包含 FILE_ATTRIBUTE_DIRECTORY，则假定 *pszTo* 为目录;否则， *pszTo* 将被假定为文件。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)。

## <a name="cpathtremoveargs"></a><a name="removeargs"></a> CPathT::RemoveArgs

调用此方法可从路径中删除任何命令行参数。

```cpp
void RemoveArgs();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)。

## <a name="cpathtremovebackslash"></a><a name="removebackslash"></a> CPathT::RemoveBackslash

调用此方法可删除路径中的尾部反斜杠。

```cpp
void RemoveBackslash();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)。

## <a name="cpathtremoveblanks"></a><a name="removeblanks"></a> CPathT::RemoveBlanks

调用此方法可从路径中删除所有前导空格和尾随空格。

```cpp
void RemoveBlanks();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)。

## <a name="cpathtremoveextension"></a><a name="removeextension"></a> CPathT::RemoveExtension

调用此方法可删除路径中的文件扩展名（如果有）。

```cpp
void RemoveExtension();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)。

## <a name="cpathtremovefilespec"></a><a name="removefilespec"></a> CPathT::RemoveFileSpec

调用此方法可删除路径中的尾随文件名和反斜杠（如果有）。

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)。

## <a name="cpathtrenameextension"></a><a name="renameextension"></a> CPathT::RenameExtension

调用此方法可将路径中的文件扩展名替换为新扩展名。 如果文件名不包含扩展名，则扩展将附加到路径的末尾。

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>parameters

*pszExtension*<br/>
新文件扩展名，前面加一个 "." 字符。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)。

## <a name="cpathtskiproot"></a><a name="skiproot"></a> CPathT::SkipRoot

调用此方法可分析路径，忽略驱动器号或 UNC (通用命名约定) 服务器/共享路径部分。

```
int SkipRoot() const;
```

### <a name="return-value"></a>返回值

返回位于根 (驱动器号或 UNC 服务器/共享) 后面的子路径开头的位置。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)。

## <a name="cpathtstrippath"></a><a name="strippath"></a> CPathT::StripPath

调用此方法可删除完全限定路径和文件名的路径部分。

```cpp
void StripPath();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)。

## <a name="cpathtstriptoroot"></a><a name="striptoroot"></a> CPathT::StripToRoot

调用此方法可删除路径的所有部分（根信息除外）。

```
BOOL StripToRoot();
```

### <a name="return-value"></a>返回值

如果在路径中找到了有效的驱动器号，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)。

## <a name="cpathtunquotespaces"></a><a name="unquotespaces"></a> CPathT::UnquoteSpaces

调用此方法可删除路径开头和末尾的引号。

```cpp
void UnquoteSpaces();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)。

## <a name="cpathtxchar"></a><a name="xchar"></a> CPathT::XCHAR

一个字符类型。

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>备注

`StringType` 是的模板参数 `CPathT` 。

## <a name="see-also"></a>请参阅

[类](../../atl/reference/atl-classes.md)<br/>
[CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)

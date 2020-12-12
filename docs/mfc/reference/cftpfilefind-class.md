---
description: 了解详细信息： CFtpFileFind 类
title: CFtpFileFind 类
ms.date: 05/28/2020
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: 89d8a8232558c3afe9cf2f3a23d02226d8539aaf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184226"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind 类

辅助 FTP 服务器的 Internet 文件搜索。

## <a name="syntax"></a>语法

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CFtpFileFind：： CFtpFileFind](#cftpfilefind)|构造 `CFtpFileFind` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CFtpFileFind：： FindFile](#findfile)|在 FTP 服务器上查找文件。|
|[CFtpFileFind：： FindNextFile](#findnextfile)|继续对 [FindFile](#findfile)进行的文件搜索。|
|[CFtpFileFind：： GetFileURL](#getfileurl)|获取找到的文件的 URL （包括路径）。|

## <a name="remarks"></a>备注

`CFtpFileFind` 包括一些成员函数，这些函数开始搜索，查找文件，并返回有关该文件的 URL 或其他描述性信息。

用于搜索 Internet 和本地文件的其他 MFC 类包括 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) 和 [CFileFind](../../mfc/reference/cfilefind-class.md)。 与一起使用 `CFtpFileFind` ，这些类为客户端提供了一个无缝机制来查找特定文件，而不管服务器协议或文件类型 (本地计算机或远程服务器) 。 没有用于在 HTTP 服务器上搜索的 MFC 类，因为 HTTP 不支持搜索所需的直接文件操作。

有关如何使用 `CFtpFileFind` 和其他 WinInet 类的详细信息，请参阅文章 [使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="example"></a>示例

下面的代码演示如何枚举 FTP 服务器当前目录中的所有文件。

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>要求

**标头：** afxinet。h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a> CFtpFileFind：： CFtpFileFind

调用此成员函数来构造 `CFtpFileFind` 对象。

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>parameters

*pConnection*<br/>
一个指向 `CFtpConnection` 对象的指针。 可以通过调用 [CInternetSession：： GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)获取 FTP 连接。

*dwContext*<br/>
对象的上下文标识符 `CFtpFileFind` 。 有关详细信息，请参阅下面的 **备注**。

### <a name="remarks"></a>备注

*DwContext* 的默认值由 MFC 发送到 `CFtpFileFind` 创建该对象的 [CInternetSession](../../mfc/reference/cinternetsession-class.md)对象中的对象 `CFtpFileFind` 。 您可以重写默认值，以将上下文标识符设置为您选择的值。 上下文标识符返回到 [CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) ，以提供标识它的对象的状态。 有关上下文标识符的详细信息，请参阅文章 [Internet 优先步骤： WinInet](../../mfc/wininet-basics.md) 。

### <a name="example"></a>示例

  请参阅本主题前面的类概述中的示例。

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a> CFtpFileFind：： FindFile

调用此成员函数以查找 FTP 文件。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>parameters

*pstrName*<br/>
指向字符串的指针，该字符串包含要查找的文件的名称。 如果为 NULL，则调用将执行通配符搜索 ( * ) 。

dwFlags <br/>
描述如何处理此会话的标志。 这些标志可以与按位 "或" 运算符组合 ( # A0) ，如下所示：

- `INTERNET_FLAG_RELOAD`   即使是在本地缓存的数据，也可以从线路中获取数据。 这是默认标志。

- `INTERNET_FLAG_DONT_CACHE`   不要在本地或任何网关上缓存数据。

- `INTERNET_FLAG_RAW_DATA`   重写默认值，以便为 FTP)  ( [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 结构返回原始数据。

- `INTERNET_FLAG_SECURE`   通过安全套接字层或 PCT 保护网络上的事务。 此标志仅适用于 HTTP 请求。

- `INTERNET_FLAG_EXISTING_CONNECT`   如果可能，请为新请求重用服务器的现有连接， `FindFile` 而不是为每个请求创建一个新会话。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 若要获得扩展的错误信息，请调用 Win32 函数 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

调用 `FindFile` 检索第一个 ftp 文件后，可以调用 [FindNextFile](#findnextfile) 来检索后续的 ftp 文件。

### <a name="example"></a>示例

  请参阅本主题前面的示例。

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a> CFtpFileFind：： FindNextFile

调用此成员函数以继续通过调用 [FindFile](#findfile) 成员函数而开始的文件搜索。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>返回值

如果有多个文件，则为非零值;如果找到的文件是目录中的最后一个，或者如果出现错误，则为零。 若要获得扩展的错误信息，请调用 Win32 函数 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的文件是目录中的最后一个文件，或者找不到匹配的文件，则该 `GetLastError` 函数将返回 ERROR_NO_MORE_FILES。

### <a name="remarks"></a>备注

调用任何 attribute 函数之前，必须至少调用此函数一次 (请参阅 [CFileFind：： FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)) 。

`FindNextFile` 包装 Win32 函数 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)。

### <a name="example"></a>示例

  请参阅本主题前面的示例。

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a> CFtpFileFind：： GetFileURL

调用此成员函数以获取指定文件的 URL。

```
CString GetFileURL() const;
```

### <a name="return-value"></a>返回值

通用资源定位符的文件和路径 (URL) 。

### <a name="remarks"></a>备注

`GetFileURL` 类似于成员函数 [CFileFind：： GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath) ，只不过它提供 URL 格式的结果。 与一样 `CFileFind::GetFilePath` ，结果不包括文件名。 例如， `file1.txt` 位于返回中 `//moose/dir/file1.txt:` `ftp://moose/dir/` 。

## <a name="see-also"></a>请参阅

[CFileFind 类](../../mfc/reference/cfilefind-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)

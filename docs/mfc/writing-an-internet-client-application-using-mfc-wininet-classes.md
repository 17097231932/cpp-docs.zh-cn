---
description: 了解详细信息：使用 MFC WinInet 类编写 Internet 客户端应用程序
title: 使用 MFC WinInet 类编写 Internet 客户端应用程序
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
ms.openlocfilehash: 61cfe3e9892f2bde6d233728b7b95ca0edd16ee8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189127"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>使用 MFC WinInet 类编写 Internet 客户端应用程序

每个 Internet 客户端应用程序的基础是 Internet 会话。 MFC 实现 Internet 会话作为类 [CInternetSession](../mfc/reference/cinternetsession-class.md)的对象。 通过使用此类，您可以创建一个 Internet 会话或多个同时会话。

若要与服务器进行通信，需要 [CInternetConnection](../mfc/reference/cinternetconnection-class.md) 对象和 `CInternetSession` 。 您可以 `CInternetConnection` 使用 [CInternetSession：： GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection)、 [CInternetSession：： GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)或 [CInternetSession：： GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection)创建一个。 所有这些调用都特定于协议类型。 这些调用不会在服务器上打开文件以进行读取或编写。 如果您打算读取或写入数据，则必须执行单独的步骤打开文件。

对于大多数 Internet 会话， `CInternetSession` 对象使用 [CInternetFile](../mfc/reference/cinternetfile-class.md) 对象手动工作：

- 对于 Internet 会话，必须创建 [CInternetSession](../mfc/reference/cinternetsession-class.md)的实例。

- 如果你的 Internet 会话读取或写入数据，则必须创建 `CInternetFile` (或其子类、 [CHttpFile](../mfc/reference/chttpfile-class.md) 或 [CGopherFile](../mfc/reference/cgopherfile-class.md)) 的实例。 读取数据的最简单方法是调用 [CInternetSession：： OpenURL](../mfc/reference/cinternetsession-class.md#openurl)。 此函数将分析您提供的统一资源定位器 (URL)、打开与 URL 指定的服务器的连接并返回一个只读的 `CInternetFile` 对象。 `CInternetSession::OpenURL` 并不会特定于一种协议类型 - 同一调用适用于所有 FTP、HTTP 或 gopher URL。 `CInternetSession::OpenURL` 甚至会处理本地文件（返回 `CStdioFile` 而非 `CInternetFile`）。

- 如果 Internet 会话不读取或写入数据，而是执行其他任务（如删除 FTP 目录中的文件），则您可能不需要创建 `CInternetFile` 的实例。

可通过两种方法创建 `CInternetFile` 对象：

- 如果使用 `CInternetSession::OpenURL` 建立服务器连接，则调用 `OpenURL` 将返回 `CStdioFile`。

- 如果使用 `CInternetSession::GetFtpConnection` 、 `GetGopherConnection` 或 `GetHttpConnection` 来建立服务器连接，则必须分别调用 `CFtpConnection::OpenFile` 、 `CGopherConnection::OpenFile` 或 `CHttpConnection::OpenRequest` ，才能 `CInternetFile` 分别返回、 `CGopherFile` 或 `CHttpFile` 。

实现 Internet 客户端应用程序的步骤会有所不同，具体取决于你是基于创建通用 Internet 客户端， `OpenURL` 还是使用特定于协议的客户端创建一个 `GetConnection` 函数。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [如何实现编写适用于 FTP、HTTP 和 gopher 的 Internet 客户端应用程序](../mfc/steps-in-a-typical-internet-client-application.md)

- [如何实现编写打开文件的 FTP 客户端应用程序](../mfc/steps-in-a-typical-ftp-client-application.md)

- [如何实现编写一个 FTP 客户端应用程序，该应用程序不会打开文件，但会执行目录操作，如删除文件](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)

- [如何实现编写 gopher 客户端应用程序](../mfc/steps-in-a-typical-gopher-client-application.md)

- [如何实现编写 HTTP 客户端应用程序](../mfc/steps-in-a-typical-http-client-application.md)

## <a name="see-also"></a>请参阅

[ (WinInet) 的 Win32 Internet 扩展 ](../mfc/win32-internet-extensions-wininet.md)<br/>
[用于创建 Internet 客户端应用程序的 MFC 类](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[Internet 客户端类的先决条件](../mfc/prerequisites-for-internet-client-classes.md)

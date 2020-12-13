---
description: 了解有关以下内容的详细信息： Windows 套接字：对存档使用套接字
title: Windows 套接字：对存档使用套接字
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: bd5f239a0fdcee4bf6c6141994c4ca5002bdc6b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331335"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows 套接字：对存档使用套接字

本文介绍 [CSocket 编程模型](#_core_the_csocket_programming_model)。 类 [CSocket](../mfc/reference/csocket-class.md) 提供比类 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)更高的抽象级别上的套接字支持。 `CSocket` 使用 MFC 序列化协议版本，通过 MFC [CArchive](../mfc/reference/carchive-class.md) 对象将数据传入和从套接字对象传递数据。 `CSocket` 提供锁定（在管理对 Windows 消息的背景处理时）并为您提供对 `CArchive` 的访问权限（其将管理您必须使用原始 API 或类 `CAsyncSocket` 亲自进行的通信的多个方面）。

> [!TIP]
> 您可以单独使用类 `CSocket` 作为 `CAsyncSocket` 的更方便的版本，但最简单的编程模型是使用具有 `CSocket` 对象的 `CArchive`。

若要详细了解如何实现带有存档的套接字，请参阅 [Windows 套接字：包含存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)。 有关代码示例，请参阅 [Windows 套接字：操作顺序](../mfc/windows-sockets-sequence-of-operations.md) 和 [windows 套接字：使用存档的套接字的示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)。 有关通过从套接字类派生自己的类可以获得的某些功能的信息，请参阅 [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)。

> [!NOTE]
> 如果您要编写 MFC 客户端程序来与建立的（非 MFC）服务器通信，则请勿通过存档发送 C++ 对象。 除非服务器是知道您要发送的对象类型的 MFC 应用程序，否则它无法接收和反序列化对象。 有关与非 MFC 应用程序通信的主题的相关材料，另请参阅 [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)一文。

## <a name="the-csocket-programming-model"></a><a name="_core_the_csocket_programming_model"></a> CSocket 编程模型

使用 `CSocket` 对象涉及创建多个 MFC 类对象并将这些对象相关联。 在下面一般过程中，每个步骤均由服务器套接字和客户端套接字执行，步骤 3 除外，该步骤中每个套接字类型都需要不同的操作。

> [!TIP]
> 在运行时，当客户端应用程序寻求连接时，服务器应用程序通常将先开始准备好并“侦听”。 如果服务器在客户端尝试连接时未准备就绪，则您通常需要用户应用程序之后再次尝试连接。

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>在服务器套接字和客户端套接字之间设置通信

1. 构造 [CSocket](../mfc/reference/csocket-class.md) 对象。

1. 使用对象创建基础 **套接字句** 柄。

   对于 `CSocket` 客户端对象，通常应使用默认参数 [创建](../mfc/reference/casyncsocket-class.md#create)，除非需要数据报套接字。 对于 `CSocket` 服务器对象，必须在调用中指定端口 `Create` 。

    > [!NOTE]
    >  `CArchive` 不适用于数据报套接字。 如果要将 `CSocket` 用于数据报套接字，则必须如在没有存档的情况下使用 `CAsyncSocket` 一样使用此类。 由于数据报是不可靠的（不能保证到达并且可能重复或离开序列），因此它们将不能通过存档与序列化兼容。 您期待序列化操作可靠且有序地完成。 如果您尝试对数据报使用带 `CSocket` 对象的 `CArchive`，则 MFC 断言将失败。

1. 如果套接字是客户端，请调用 [CAsyncSocket：： connect](../mfc/reference/casyncsocket-class.md#connect) 将套接字对象连接到服务器套接字。

     -或-

   如果套接字是服务器，请调用 [CAsyncSocket：：侦听](../mfc/reference/casyncsocket-class.md#listen) ，开始侦听来自客户端的连接尝试。 收到连接请求时，通过调用 [CAsyncSocket：： accept](../mfc/reference/casyncsocket-class.md#accept)来接受它。

    > [!NOTE]
    >  `Accept`成员函数使用新的空 `CSocket` 对象作为其参数。 在调用之前，必须构造此对象 `Accept` 。 如果此套接字对象超出范围，则关闭连接。 不要 `Create` 为此新的套接字对象调用。

1. 创建一个 [CSocketFile](../mfc/reference/csocketfile-class.md) 对象，并将该 `CSocket` 对象与它相关联。

1. 创建一个 [CArchive](../mfc/reference/carchive-class.md) 对象，以便加载 (接收) 或存储 (发送) 数据。 存档将与 `CSocketFile` 对象关联。

   记住，`CArchive` 不适用于数据报套接字。

1. 使用 `CArchive` 对象在客户端套接字和服务器套接字之间传递数据。

   记住，给定 `CArchive` 对象将仅按一个方向移动数据：进行加载（接收）或存储（发送）。 在某些情况下，您将使用两个 `CArchive` 对象：一个用于发送数据，另一个用于接收确认。

   在接受连接并设置存档之后，你可以执行类似验证密码的任务。

1. 销毁存档、套接字文件和套接字对象。

    > [!NOTE]
    >  类 `CArchive` 提供专门用于类 `IsBufferEmpty` 的 `CSocket` 成员函数。 例如，如果缓冲区包含多条数据消息，则您需要循环至读取所有这些消息并清除缓冲区。 否则，可能无限期延迟指示有数据要接收的下一条通知。 使用 `IsBufferEmpty` 确保检索所有数据。

[Windows 套接字：操作顺序](../mfc/windows-sockets-sequence-of-operations.md)说明了此过程的双方代码示例。

有关详细信息，请参阅：

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket：： Create](../mfc/reference/csocket-class.md#create)

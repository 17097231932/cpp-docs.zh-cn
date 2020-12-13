---
description: 了解详细信息： CWinThread 类
title: CWinThread 类
ms.date: 11/04/2016
f1_keywords:
- CWinThread
- AFXWIN/CWinThread
- AFXWIN/CWinThread::CWinThread
- AFXWIN/CWinThread::CreateThread
- AFXWIN/CWinThread::ExitInstance
- AFXWIN/CWinThread::GetMainWnd
- AFXWIN/CWinThread::GetThreadPriority
- AFXWIN/CWinThread::InitInstance
- AFXWIN/CWinThread::IsIdleMessage
- AFXWIN/CWinThread::OnIdle
- AFXWIN/CWinThread::PostThreadMessage
- AFXWIN/CWinThread::PreTranslateMessage
- AFXWIN/CWinThread::ProcessMessageFilter
- AFXWIN/CWinThread::ProcessWndProcException
- AFXWIN/CWinThread::PumpMessage
- AFXWIN/CWinThread::ResumeThread
- AFXWIN/CWinThread::Run
- AFXWIN/CWinThread::SetThreadPriority
- AFXWIN/CWinThread::SuspendThread
- AFXWIN/CWinThread::m_bAutoDelete
- AFXWIN/CWinThread::m_hThread
- AFXWIN/CWinThread::m_nThreadID
- AFXWIN/CWinThread::m_pActiveWnd
- AFXWIN/CWinThread::m_pMainWnd
helpviewer_keywords:
- CWinThread [MFC], CWinThread
- CWinThread [MFC], CreateThread
- CWinThread [MFC], ExitInstance
- CWinThread [MFC], GetMainWnd
- CWinThread [MFC], GetThreadPriority
- CWinThread [MFC], InitInstance
- CWinThread [MFC], IsIdleMessage
- CWinThread [MFC], OnIdle
- CWinThread [MFC], PostThreadMessage
- CWinThread [MFC], PreTranslateMessage
- CWinThread [MFC], ProcessMessageFilter
- CWinThread [MFC], ProcessWndProcException
- CWinThread [MFC], PumpMessage
- CWinThread [MFC], ResumeThread
- CWinThread [MFC], Run
- CWinThread [MFC], SetThreadPriority
- CWinThread [MFC], SuspendThread
- CWinThread [MFC], m_bAutoDelete
- CWinThread [MFC], m_hThread
- CWinThread [MFC], m_nThreadID
- CWinThread [MFC], m_pActiveWnd
- CWinThread [MFC], m_pMainWnd
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
ms.openlocfilehash: f9f89aa6397f44c95e8958d077fe18258e3c17f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342603"
---
# <a name="cwinthread-class"></a>CWinThread 类

表示应用程序中的执行线程。

## <a name="syntax"></a>语法

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CWinThread：： CWinThread](#cwinthread)|构造 `CWinThread` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CWinThread：： CreateThread](#createthread)|开始对象的执行 `CWinThread` 。|
|[CWinThread：： ExitInstance](#exitinstance)|重写以在线程终止时进行清理。|
|[CWinThread：： GetMainWnd](#getmainwnd)|检索指向线程主窗口的指针。|
|[CWinThread：： GetThreadPriority](#getthreadpriority)|获取当前线程的优先级。|
|[CWinThread：： InitInstance](#initinstance)|重写以执行线程实例初始化。|
|[CWinThread：： IsIdleMessage](#isidlemessage)|检查特殊消息。|
|[CWinThread：： OnIdle](#onidle)|重写以执行特定于线程的空闲时间处理。|
|[CWinThread：:P ostThreadMessage](#postthreadmessage)|将消息发送到另一个 `CWinThread` 对象。|
|[CWinThread：:P reTranslateMessage](#pretranslatemessage)|在将消息调度到 Windows 函数 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 和 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)之前筛选消息。|
|[CWinThread：:P rocessMessageFilter](#processmessagefilter)|在某些消息到达应用程序之前截获这些消息。|
|[CWinThread：:P rocessWndProcException](#processwndprocexception)|截获线程消息和命令处理程序引发的所有未经处理的异常。|
|[CWinThread：:P umpMessage](#pumpmessage)|包含线程的消息循环。|
|[CWinThread：： ResumeThread](#resumethread)|减少线程的挂起计数。|
|[CWinThread：： Run](#run)|使用消息泵控制线程的函数。 重写以自定义默认的消息循环。|
|[CWinThread：：参见 setthreadpriority](#setthreadpriority)|设置当前线程的优先级。|
|[CWinThread：： SuspendThread](#suspendthread)|增加线程的挂起计数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CWinThread：： operator 句柄](#operator_handle)|检索对象的句柄 `CWinThread` 。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CWinThread：： m_bAutoDelete](#m_bautodelete)|指定是否在线程终止时销毁对象。|
|[CWinThread：： m_hThread](#m_hthread)|当前线程的句柄。|
|[CWinThread：： m_nThreadID](#m_nthreadid)|当前线程的 ID。|
|[CWinThread：： m_pActiveWnd](#m_pactivewnd)|OLE 服务器处于就地活动状态时，指向容器应用程序的主窗口的指针。|
|[CWinThread：： m_pMainWnd](#m_pmainwnd)|保存指向应用程序的主窗口的指针。|

## <a name="remarks"></a>备注

主执行线程通常由派生自的对象提供 `CWinApp` ; `CWinApp` 派生自 `CWinThread` 。 其他 `CWinThread` 对象允许在给定的应用程序中使用多个线程。

支持以下两种常规类型的线程 `CWinThread` ：工作线程和用户界面线程。 工作线程没有消息泵：例如，在电子表格应用程序中执行背景计算的线程。 用户界面线程具有消息泵并处理从系统接收的消息。 [CWinApp](../../mfc/reference/cwinapp-class.md) 和派生自它的类是用户界面线程的示例。 其他用户界面线程也可以直接从派生 `CWinThread` 。

类的对象 `CWinThread` 通常存在于线程的持续时间内。 如果要修改此行为，请将 [m_bAutoDelete](#m_bautodelete) 设置为 FALSE。

`CWinThread`类是使你的代码和 MFC 完全线程安全所必需的。 框架用于维护线程特定信息的线程本地数据由 `CWinThread` 对象管理。 由于此依赖 `CWinThread` 于处理线程本地数据，因此使用 mfc 的任何线程都必须由 mfc 创建。 例如，由运行时函数创建的线程 [_beginthread，_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) 不能使用任何 MFC api。

若要创建线程，请调用 [AfxBeginThread](application-information-and-management.md#afxbeginthread)。 有两个窗体，具体取决于你是需要辅助线程还是用户界面线程。 如果需要用户界面线程，请将传递到 `AfxBeginThread` `CRuntimeClass` 派生类的的指针 `CWinThread` 。 如果要创建工作线程，请将传递给指向 `AfxBeginThread` 控制函数的指针和控制函数的参数。 对于工作线程和用户界面线程，可以指定修改优先级、堆栈大小、创建标志和安全属性的可选参数。 `AfxBeginThread` 将返回指向新对象的指针 `CWinThread` 。

`AfxBeginThread`您可以构造一个 `CWinThread` 派生的对象，然后调用，而不是调用 `CreateThread` 。 如果要在 `CWinThread` 线程执行的连续创建和终止之间重复使用对象，则这两阶段构造方法非常有用。

有关的详细信息 `CWinThread` ，请参阅文章 [使用 c + + 和 MFC 进行](../../parallel/multithreading-with-cpp-and-mfc.md)多线程处理 [：创建 User-Interface 线程](../../parallel/multithreading-creating-user-interface-threads.md)， [多线程处理：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)和 [多线程处理：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a> CWinThread：： CreateThread

创建要在调用进程的地址空间内执行的线程。

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>parameters

*dwCreateFlags*<br/>
指定控制线程创建的其他标志。 此标志可以包含以下两个值之一：

- CREATE_SUSPENDED 启动线程，该线程的挂起计数为1。 如果要在 `CWinThread` 线程开始运行之前初始化对象的任何成员数据，如 [m_bAutoDelete](#m_bautodelete) 或派生类的任何成员，请使用 CREATE_SUSPENDED。 初始化完成后，使用 [CWinThread：： ResumeThread](#resumethread) 启动运行的线程。 在调用之前，将不会执行该线程 `CWinThread::ResumeThread` 。

- **0** 创建后立即启动线程。

*nStackSize*<br/>
指定新线程堆栈的大小（以字节为单位）。 如果为 **0**，则堆栈大小默认为与进程的主线程相同的大小。

*lpSecurityAttrs*<br/>
指向指定线程的安全属性的 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 结构。

### <a name="return-value"></a>返回值

如果成功创建线程，则为非零值;否则为0。

### <a name="remarks"></a>备注

使用 `AfxBeginThread` 创建线程对象并在一个步骤中执行它。 `CreateThread`如果要在线程执行的连续创建和终止之间重复使用线程对象，请使用。

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a> CWinThread：： CWinThread

构造 `CWinThread` 对象。

```
CWinThread();
```

### <a name="remarks"></a>备注

若要开始线程的执行，请调用 [CreateThread](#createthread) 成员函数。 通常会通过调用 [AfxBeginThread](application-information-and-management.md#afxbeginthread)创建线程，这将调用此构造函数和 `CreateThread` 。

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a> CWinThread：： ExitInstance

由框架从极少重写的 [运行](#run) 成员函数中调用，以退出线程的此实例，或者，如果对 [InitInstance](#initinstance) 的调用失败，则为。

```
virtual int ExitInstance();
```

### <a name="return-value"></a>返回值

线程的退出代码;0表示没有错误，大于0的值表示错误。 可以通过调用 [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)来检索此值。

### <a name="remarks"></a>备注

不要在成员函数内的任何位置调用此成员函数 `Run` 。 此成员函数仅在用户界面线程中使用。

`CWinThread`如果[M_BAUTODELETE](#m_bautodelete)为 TRUE，则此函数的默认实现将删除该对象。 如果希望在线程终止时执行其他清理，请重写此函数。 `ExitInstance`执行代码后，的实现应调用基类的版本。

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a> CWinThread：： GetMainWnd

如果你的应用程序是 OLE 服务器，请调用此函数来检索指向应用程序活动主窗口的指针，而不是直接引用 `m_pMainWnd` 应用程序对象的成员。

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>返回值

此函数返回一个指针，该指针指向两种类型的窗口之一。 如果你的线程是 OLE 服务器的一部分，并且具有在活动容器内就地激活的对象，则此函数将返回该对象的 [CWinApp：： m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) 数据成员 `CWinThread` 。

如果容器中没有处于就地活动状态的对象，或者您的应用程序不是 OLE 服务器，则此函数将返回您的线程对象的 [m_pMainWnd](#m_pmainwnd) 数据成员。

### <a name="remarks"></a>备注

对于用户界面线程，这等效于直接引用 `m_pActiveWnd` 应用程序对象的成员。

如果您的应用程序不是 OLE 服务器，调用此函数相当于直接引用应用程序对象的 `m_pMainWnd` 成员。

重写此函数以修改默认行为。

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a> CWinThread：： GetThreadPriority

获取此线程的当前线程优先级别。

```
int GetThreadPriority();
```

### <a name="return-value"></a>返回值

其优先级类中的当前线程优先级别。 返回的值将为以下值之一，从最高优先级到最低优先级列出：

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

有关这些优先级的详细信息，请参阅 Windows SDK 中的 [参见 setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a> CWinThread：： InitInstance

`InitInstance` 必须重写以初始化用户界面线程的每个新实例。

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>返回值

如果初始化成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

通常，重写 `InitInstance` 以执行第一次创建线程时必须完成的任务。

此成员函数仅在用户界面线程中使用。 在传递到 [AfxBeginThread](application-information-and-management.md#afxbeginthread)的控制函数中执行工作线程的初始化。

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a> CWinThread：： IsIdleMessage

重写此函数，以便在 `OnIdle` 生成特定消息后防止调用此函数。

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>parameters

*pMsg*<br/>
指向当前正在处理的消息。

### <a name="return-value"></a>返回值

如果 `OnIdle` 应在处理消息后调用，则为非零; 否则为0。

### <a name="remarks"></a>备注

默认实现不会 `OnIdle` 在冗余鼠标消息和通过插入符号闪烁生成的消息后调用。

如果应用程序创建了短暂的计时器， `OnIdle` 将频繁调用，从而导致性能问题。 若要改进此类应用程序的性能，请 `IsIdleMessage` 在应用程序的派生类中重写， `CWinApp` 以检查 WM_TIMER 消息，如下所示：

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

以这种方式处理 WM_TIMER 将提高使用短计时器的应用程序的性能。

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a> CWinThread：： m_bAutoDelete

指定 `CWinThread` 对象是否应在线程终止时自动删除。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>备注

`m_bAutoDelete`数据成员是类型为 BOOL 的公共变量。

的值 `m_bAutoDelete` 不会影响基础线程句柄的关闭方式，但会影响关闭句柄的时间。 在销毁 `CWinThread` 对象时，始终关闭线程句柄。

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a> CWinThread：： m_hThread

附加到此的线程的句柄 `CWinThread` 。

```
HANDLE m_hThread;
```

### <a name="remarks"></a>备注

`m_hThread`数据成员是类型 HANDLE 的公共变量。 仅当基本内核线程对象当前存在并且尚未关闭该句柄时，此方法才有效。

CWinThread 析构函数调用上的 CloseHandle `m_hThread` 。 如果在线程终止时 [m_bAutoDelete](#m_bautodelete) 为 TRUE，则销毁 CWinThread 对象，这会使指向 CWinThread 对象及其成员变量的任何指针失效。 您可能需要该 `m_hThread` 成员检查线程退出值或等待信号。 若要在线程执行期间保留 CWinThread 对象及其 `m_hThread` 成员，请将其设置 `m_bAutoDelete` 为 FALSE，以便继续执行线程。 否则，线程可能会终止、销毁 CWinThread 对象，并在尝试使用该句柄之前关闭句柄。 如果使用此方法，则需要删除 CWinThread 对象。

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a> CWinThread：： m_nThreadID

附加到此的线程的 ID `CWinThread` 。

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>备注

`m_nThreadID`数据成员是类型为 DWORD 的公共变量。 仅当基本内核线程对象当前存在时，此方法才有效。
另请参阅有关 [m_hThread](#m_hthread) 生存期的备注。

### <a name="example"></a>示例

  请参阅 [AfxGetThread](application-information-and-management.md#afxgetthread)的示例。

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a> CWinThread：： m_pActiveWnd

使用此数据成员可以存储指向线程活动窗口对象的指针。

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>备注

当关闭由引用的窗口时，Microsoft 基础类库会自动终止线程 `m_pActiveWnd` 。 如果此线程是应用程序的主线程，则该应用程序也将被终止。 如果此数据成员为 NULL，则将继承应用程序对象的活动窗口 `CWinApp` 。 `m_pActiveWnd` 是类型的公共变量 `CWnd*` 。

通常，在重写时设置此成员变量 `InitInstance` 。 在工作线程中，此数据成员的值继承自其父线程。

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a> CWinThread：： m_pMainWnd

使用此数据成员可以存储指向线程的主窗口对象的指针。

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>备注

当关闭由引用的窗口时，Microsoft 基础类库会自动终止线程 `m_pMainWnd` 。 如果此线程是应用程序的主线程，则该应用程序也将被终止。 如果此数据成员为 NULL，则将使用应用程序对象的主窗口来 `CWinApp` 确定何时终止线程。 `m_pMainWnd` 是类型的公共变量 `CWnd*` 。

通常，在重写时设置此成员变量 `InitInstance` 。 在工作线程中，此数据成员的值继承自其父线程。

## <a name="cwinthreadonidle"></a><a name="onidle"></a> CWinThread：： OnIdle

重写此成员函数以执行空闲时处理。

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>parameters

*lCount*<br/>
`OnIdle`当线程的消息队列为空时，每次调用一个计数器。 每次处理新消息时，此计数都将重置为0。 您可以使用 *lCount* 参数来确定线程在不处理消息的情况下空闲的相对时间长度。

### <a name="return-value"></a>返回值

若要接收更多空闲处理时间，则为非零值;如果不需要更多的空闲处理时间，则为0。

### <a name="remarks"></a>备注

`OnIdle` 当线程的消息队列为空时，在默认消息循环中调用。 使用替代来调用自己的后台空闲处理程序任务。

`OnIdle` 应返回0以指示不需要额外的空闲处理时间。 每当消息队列为空时，每次调用时， *lCount* 参数都会递增 `OnIdle` ，每次处理新消息时，都会重置为0。 可以根据此计数调用不同的空闲例程。

此成员函数的默认实现会从内存中释放临时对象和未使用的动态链接库。

此成员函数仅在用户界面线程中使用。

由于应用程序无法处理消息直到 `OnIdle` 返回，因此不会在此函数中执行长时间的任务。

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a> CWinThread：： operator 句柄

检索对象的句柄 `CWinThread` 。

```
operator HANDLE() const;
```

### <a name="return-value"></a>返回值

如果成功，则为线程对象的句柄;否则为 NULL。

### <a name="remarks"></a>备注

使用句柄直接调用 Windows Api。

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a> CWinThread：:P ostThreadMessage

调用以将用户定义的消息发布到另一个 `CWinThread` 对象。

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>parameters

*message*<br/>
用户定义消息的 ID。

*wParam*<br/>
第一个消息参数。

*lParam*<br/>
第二个消息参数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

已发布的消息通过消息映射宏 ON_THREAD_MESSAGE 映射到正确的消息处理程序。

> [!NOTE]
> 调用 [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)时，消息将被放入线程的消息队列中。 但是，由于以这种方式发布的消息不与窗口相关联，因此 MFC 不会将它们调度到消息或命令处理程序。 为了处理这些消息，请重写 `PreTranslateMessage()` CWinApp 派生类的函数，并手动处理这些消息。

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a> CWinThread：:P reTranslateMessage

重写此函数可以在将窗口消息调度到 Windows 函数 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 和 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)之前对其进行筛选。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>parameters

*pMsg*<br/>
指向包含要处理的消息的消息 [结构](/windows/win32/api/winuser/ns-winuser-msg) 。

### <a name="return-value"></a>返回值

如果消息完全在中处理 `PreTranslateMessage` 并且不应进一步处理，则为非零值。 如果应以正常方式处理消息，则为零。

### <a name="remarks"></a>备注

此成员函数仅在用户界面线程中使用。

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a> CWinThread：:P rocessMessageFilter

框架的挂钩函数调用此成员函数来筛选和响应某些 Windows 消息。

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>parameters

*code*<br/>
指定挂钩代码。 此成员函数使用代码来确定如何处理 *lpMsg。*

*lpMsg*<br/>
指向 Windows [MSG 结构](/windows/win32/api/winuser/ns-winuser-msg)的指针。

### <a name="return-value"></a>返回值

如果处理消息，则为非零值;否则为0。

### <a name="remarks"></a>备注

挂钩函数在将事件发送到应用程序的正常消息处理之前处理这些事件。

如果重写此高级功能，请确保调用基类版本以维护框架的挂钩处理。

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a> CWinThread：:P rocessWndProcException

每当处理程序未捕获某个线程消息或命令处理程序中引发的异常时，框架都会调用此成员函数。

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>parameters

*e*<br/>
指向未经处理的异常。

*pMsg*<br/>
指向包含导致框架引发异常的 windows 消息相关信息的 [消息结构](/windows/win32/api/winuser/ns-winuser-msg) 。

### <a name="return-value"></a>返回值

如果生成 WM_CREATE 异常，则为-1;否则为0。

### <a name="remarks"></a>备注

请勿直接调用此成员函数。

此成员函数的默认实现仅处理以下消息中生成的异常：

|命令|操作|
|-------------|------------|
|WM_CREATE|Fail。|
|WM_PAINT|验证受影响的窗口，从而阻止生成另一个 WM_PAINT 消息。|

重写此成员函数以提供异常的全局处理。 仅当要显示默认行为时，才调用基本功能。

此成员函数仅用于具有消息泵的线程中。

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a> CWinThread：:P umpMessage

包含线程的消息循环。

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>备注

`PumpMessage` 包含线程的消息循环。 `PumpMessage` 调用 `CWinThread` 以抽取线程的消息。 您可以 `PumpMessage` 直接调用来强制处理消息，也可以重写 `PumpMessage` 来更改其默认行为。

`PumpMessage`建议仅向高级用户直接调用并重写其默认行为。

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a> CWinThread：： ResumeThread

调用以恢复执行 [SuspendThread](#suspendthread) 成员函数挂起的线程或使用 CREATE_SUSPENDED 标志创建的线程。

```
DWORD ResumeThread();
```

### <a name="return-value"></a>返回值

如果成功，则为线程的上一个挂起计数; `0xFFFFFFFF` 否则为。 如果返回值为零，则不会挂起当前线程。 如果返回值为1，则该线程已挂起，但现在已重新启动。 如果任何返回值大于1，则表示该线程保持挂起状态。

### <a name="remarks"></a>备注

当前线程的挂起计数减少1。 如果挂起计数缩减为零，则该线程将继续执行;否则，线程将保持挂起状态。

## <a name="cwinthreadrun"></a><a name="run"></a> CWinThread：： Run

为用户界面线程提供默认的消息循环。

```
virtual int Run();
```

### <a name="return-value"></a>返回值

**`int`** 线程返回的值。 可以通过调用 [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)来检索此值。

### <a name="remarks"></a>备注

`Run` 获取并调度 Windows 消息，直到应用程序收到 [WM_QUIT](/windows/win32/winmsg/wm-quit) 消息。 如果线程的消息队列当前不包含任何消息，则 `Run` 调用 `OnIdle` 以执行空闲时处理。 传入消息将进入 [PreTranslateMessage](#pretranslatemessage) 成员函数进行特殊处理，然后进入 Windows function [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 进行标准键盘转换。 最后，调用 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函数。

`Run` 很少会重写，但你可以重写它以实现特殊行为。

此成员函数仅在用户界面线程中使用。

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a> CWinThread：：参见 setthreadpriority

此函数在其优先级类中设置当前线程的优先级。

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>parameters

*nPriority*<br/>
在其优先级类中指定新的线程优先级别。 此参数必须是以下值之一，从最高优先级到最低优先级列出：

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

有关这些优先级的详细信息，请参阅 Windows SDK 中的 [参见 setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

只能在 [CreateThread](#createthread) 成功返回后调用它。

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a> CWinThread：： SuspendThread

递增当前线程的挂起计数。

```
DWORD SuspendThread();
```

### <a name="return-value"></a>返回值

如果成功，则为线程的上一个挂起计数; `0xFFFFFFFF` 否则为。

### <a name="remarks"></a>备注

如果任何线程的挂起计数大于零，则不会执行该线程。 可以通过调用 [ResumeThread](#resumethread) 成员函数来恢复线程。

## <a name="see-also"></a>请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWinApp 类](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)

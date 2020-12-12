---
description: '了解更多相关信息： Windows Operations (c + +/CLI) '
title: Windows 操作 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows [C++], Windows-specific tasks
- .NET Framework [C++], Windows operations
- Visual C++, Windows operations
- Windows operations [C++]
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
- Visual C++, user interactive state
- user interactive state
- Visual C++, reading from Windows Registry
- registry, reading
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
- text, retrieving from Clipboard
- Clipboard, retrieving text
- current user names
- user names, retrieving
- UserName string
- .NET Framework, version
- Version property, retrieving .NET Framework version
- computer name, retrieving
- machine name, retrieving
- computer name
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
- text, storing in Clipboard
- Clipboard, storing text
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: b9a75cb4-0589-4d5b-92cb-5e8be42b4ac0
ms.openlocfilehash: 95fff25cb5c921272972e343dd3a85d53f909c52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298716"
---
# <a name="windows-operations-ccli"></a>Windows 操作 (C++/CLI)

使用 Windows SDK 演示各种特定于 Windows 的任务。

以下主题演示使用 Visual C++ 通过 Windows SDK 执行的各种 Windows 操作。

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a> 确定关闭是否已启动

下面的代码示例演示如何确定应用程序或 .NET Framework 当前是否正在终止。 这适用于访问 .NET Framework 中的静态元素，因为在关闭过程中，这些构造由系统完成，无法可靠地使用。 <xref:System.Environment.HasShutdownStarted%2A>首先检查属性，可以通过不访问这些元素来避免潜在的故障。

### <a name="example"></a>示例

```cpp
// check_shutdown.cpp
// compile with: /clr
using namespace System;
int main()
{
   if (Environment::HasShutdownStarted)
      Console::WriteLine("Shutting down.");
   else
      Console::WriteLine("Not shutting down.");
   return 0;
}
```

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a> 确定用户交互状态

下面的代码示例演示如何确定代码是否正在用户交互式上下文中运行。 如果 <xref:System.Environment.UserInteractive%2A> 为 false，则代码作为服务进程运行或从 Web 应用程序内部运行，在这种情况下，不应尝试与用户交互。

### <a name="example"></a>示例

```cpp
// user_interactive.cpp
// compile with: /clr
using namespace System;

int main()
{
   if ( Environment::UserInteractive )
      Console::WriteLine("User interactive");
   else
      Console::WriteLine("Noninteractive");
   return 0;
}
```

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a> 从 Windows 注册表读取数据

下面的代码示例使用 <xref:Microsoft.Win32.Registry.CurrentUser> 键从 Windows 注册表读取数据。 首先，使用方法枚举子项， <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> 然后使用方法打开标识子项 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> 。 与根键一样，每个子项由类表示 <xref:Microsoft.Win32.RegistryKey> 。 最后，新的 <xref:Microsoft.Win32.RegistryKey> 对象用于枚举键/值对。

### <a name="example"></a>示例

```cpp
// registry_read.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main( )
{
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );

   Console::WriteLine("Subkeys within CurrentUser root key:");
   for (int i=0; i<key->Length; i++)
   {
      Console::WriteLine("   {0}", key[i]);
   }

   Console::WriteLine("Opening subkey 'Identities'...");
   RegistryKey^ rk = nullptr;
   rk = Registry::CurrentUser->OpenSubKey("Identities");
   if (rk==nullptr)
   {
      Console::WriteLine("Registry key not found - aborting");
      return -1;
   }

   Console::WriteLine("Key/value pairs within 'Identities' key:");
   array<String^>^ name = rk->GetValueNames( );
   for (int i=0; i<name->Length; i++)
   {
      String^ value = rk->GetValue(name[i])->ToString();
      Console::WriteLine("   {0} = {1}", name[i], value);
   }

   return 0;
}
```

### <a name="remarks"></a>备注

<xref:Microsoft.Win32.Registry>类只是的静态实例的容器 <xref:Microsoft.Win32.RegistryKey> 。 每个实例都表示一个根注册表节点。 实例为、、、 <xref:Microsoft.Win32.Registry.ClassesRoot> <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser> <xref:Microsoft.Win32.Registry.LocalMachine> 和 <xref:Microsoft.Win32.Registry.Users> 。

除了静态外，类中的对象 <xref:Microsoft.Win32.Registry> 也是只读的。 此外，为 <xref:Microsoft.Win32.RegistryKey> 访问注册表对象的内容而创建的类的实例也是只读的。 有关如何重写此行为的示例，请参阅 [如何：将数据写入 Windows 注册表 (c + +/cli) ](#write_data)。

类中有两个附加的对象 <xref:Microsoft.Win32.Registry> ： <xref:Microsoft.Win32.Registry.DynData> 和 <xref:Microsoft.Win32.Registry.PerformanceData> 。 两者都是类的实例 <xref:Microsoft.Win32.RegistryKey> 。 <xref:Microsoft.Win32.Registry.DynData>对象包含动态注册表信息，仅在 windows 98 和 Windows Me 中受支持。 <xref:Microsoft.Win32.Registry.PerformanceData>对象可用于访问使用 Windows 性能监视系统的应用程序的性能计数器信息。 该 <xref:Microsoft.Win32.Registry.PerformanceData> 节点表示的信息实际上并不存储在注册表中，因此无法使用 Regedit.exe 进行查看。

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a> 读取 Windows 性能计数器

某些应用程序和 Windows 子系统通过 Windows 性能系统公开了性能数据。 可以使用 <xref:System.Diagnostics.PerformanceCounterCategory> <xref:System.Diagnostics.PerformanceCounter> 位于命名空间中的和类访问这些计数器 <xref:System.Diagnostics?displayProperty=fullName> 。

下面的代码示例使用这些类来检索和显示一个计数器，该计数器由 Windows 更新以指示处理器处于繁忙状态的时间百分比。

> [!NOTE]
> 此示例需要在 Windows Vista 上运行的管理员特权。

### <a name="example"></a>示例

```cpp
// processor_timer.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Diagnostics;
using namespace System::Timers;

ref struct TimerObject
{
public:
   static String^ m_instanceName;
   static PerformanceCounter^ m_theCounter;

public:
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)
   {
      try
      {
         Console::WriteLine("CPU time used: {0,6} ",
          m_theCounter->NextValue( ).ToString("f"));
      }
      catch(Exception^ e)
      {
         if (dynamic_cast<InvalidOperationException^>(e))
         {
            Console::WriteLine("Instance '{0}' does not exist",
                  m_instanceName);
            return;
         }
         else
         {
            Console::WriteLine("Unknown exception... ('q' to quit)");
            return;
         }
      }
   }
};

int main()
{
   String^ objectName = "Processor";
   String^ counterName = "% Processor Time";
   String^ instanceName = "_Total";

   try
   {
      if ( !PerformanceCounterCategory::Exists(objectName) )
      {
         Console::WriteLine("Object {0} does not exist", objectName);
         return -1;
      }
   }
   catch (UnauthorizedAccessException ^ex)
   {
      Console::WriteLine("You are not authorized to access this information.");
      Console::Write("If you are using Windows Vista, run the application with ");
      Console::WriteLine("administrative privileges.");
      Console::WriteLine(ex->Message);
      return -1;
   }

   if ( !PerformanceCounterCategory::CounterExists(
          counterName, objectName) )
   {
      Console::WriteLine("Counter {0} does not exist", counterName);
      return -1;
   }

   TimerObject::m_instanceName = instanceName;
   TimerObject::m_theCounter = gcnew PerformanceCounter(
          objectName, counterName, instanceName);

   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);
   aTimer->Interval = 1000;
   aTimer->Enabled = true;
   aTimer->AutoReset = true;

   Console::WriteLine("reporting CPU usage for the next 10 seconds");
   Thread::Sleep(10000);
   return 0;
}
```

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a> 从剪贴板检索文本

下面的代码示例使用 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 成员函数返回指向接口的指针 <xref:System.Windows.Forms.IDataObject> 。 然后，可以查询此接口的数据格式并用于检索实际数据。

### <a name="example"></a>示例

```cpp
// read_clipboard.cpp
// compile with: /clr
#using <system.dll>
#using <system.Drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main( )
{
   IDataObject^ data = Clipboard::GetDataObject( );

   if (data)
   {
      if (data->GetDataPresent(DataFormats::Text))
      {
         String^ text = static_cast<String^>
           (data->GetData(DataFormats::Text));
         Console::WriteLine(text);
      }
      else
         Console::WriteLine("Nontext data is in the Clipboard.");
   }
   else
   {
      Console::WriteLine("No data was found in the Clipboard.");
   }

   return 0;
}
```

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a> 检索当前用户名

下面的代码示例演示了如何检索当前用户名 (登录 Windows) 中的用户的名称。 该名称存储在 <xref:System.Environment.UserName%2A> 命名空间中定义的字符串中 <xref:System.Environment> 。

### <a name="example"></a>示例

```cpp
// username.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);
   return 0;
}
```

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a> 检索 .NET Framework 版本

下面的代码示例演示如何使用属性确定当前安装的 .NET Framework 的版本 <xref:System.Environment.Version%2A> ，它是指向 <xref:System.Version> 包含版本信息的对象的指针。

### <a name="example"></a>示例

```cpp
// dotnet_ver.cpp
// compile with: /clr
using namespace System;
int main()
{
   Version^ version = Environment::Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write(".NET Framework version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
            build, major, minor, revision);
   }
   return 0;
}
```

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a> 检索本地计算机名称

下面的代码示例演示了如何检索本地计算机名称 (显示在网络) 上的计算机名称。 可以通过获取 <xref:System.Environment.MachineName%2A> 命名空间中定义的字符串来实现此目的 <xref:System.Environment> 。

### <a name="example"></a>示例

```cpp
// machine_name.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);
   return 0;
}
```

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a> 检索 Windows 版本

下面的代码示例演示如何检索当前操作系统的平台和版本信息。 此信息存储在属性中 <xref:System.Environment.OSVersion%2A?displayProperty=fullName> ，并包含一个枚举，该枚举描述 Windows 的版本以及 <xref:System.Environment.Version%2A> 包含操作系统完全相同的对象。

### <a name="example"></a>示例

```cpp
// os_ver.cpp
// compile with: /clr
using namespace System;

int main()
{
   OperatingSystem^ osv = Environment::OSVersion;
   PlatformID id = osv->Platform;
   Console::Write("Operating system: ");

   if (id == PlatformID::Win32NT)
      Console::WriteLine("Win32NT");
   else if (id == PlatformID::Win32S)
      Console::WriteLine("Win32S");
   else if (id == PlatformID::Win32Windows)
      Console::WriteLine("Win32Windows");
   else
      Console::WriteLine("WinCE");

   Version^ version = osv->Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write("OS Version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
                   build, major, minor, revision);
   }

   return 0;
}
```

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a> 检索自启动以来经过的时间

下面的代码示例演示了如何确定计时周期计数，或自启动 Windows 以来已经过的毫秒数。 此值存储在 <xref:System.Environment.TickCount%2A?displayProperty=fullName> 成员和中，因为它是32位值，大约每24.9 天重置为零。

### <a name="example"></a>示例

```cpp
// startup_time.cpp
// compile with: /clr
using namespace System;

int main( )
{
   Int32 tc = Environment::TickCount;
   Int32 seconds = tc / 1000;
   Int32 minutes = seconds / 60;
   float hours = static_cast<float>(minutes) / 60;
   float days = hours / 24;

   Console::WriteLine("Milliseconds since startup: {0}", tc);
   Console::WriteLine("Seconds since startup: {0}", seconds);
   Console::WriteLine("Minutes since startup: {0}", minutes);
   Console::WriteLine("Hours since startup: {0}", hours);
   Console::WriteLine("Days since startup: {0}", days);

   return 0;
}
```

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a> 将文本存储在剪贴板中

下面的代码示例使用 <xref:System.Windows.Forms.Clipboard> 在命名空间中定义的对象 <xref:System.Windows.Forms> 来存储字符串。 此对象提供两个成员函数： <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> 和 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 。 通过将从派生的任何对象发送到剪贴板来存储 <xref:System.Object> 数据 <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> 。

### <a name="example"></a>示例

```cpp
// store_clipboard.cpp
// compile with: /clr
#using <System.dll>
#using <System.Drawing.dll>
#using <System.Windows.Forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main()
{
   String^ str = "This text is copied into the Clipboard.";

   // Use 'true' as the second argument if
   // the data is to remain in the clipboard
   // after the program terminates.
   Clipboard::SetDataObject(str, true);

   Console::WriteLine("Added text to the Clipboard.");

   return 0;
}
```

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a> 将数据写入 Windows 注册表

下面的代码示例使用 <xref:Microsoft.Win32.Registry.CurrentUser> 键创建 <xref:Microsoft.Win32.RegistryKey> 对应于 **软件** 密钥的类的可写实例。 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>然后，使用方法创建新键并添加到键/值对。

### <a name="example"></a>示例

```cpp
// registry_write.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main()
{
   // The second OpenSubKey argument indicates that
   // the subkey should be writable.
   RegistryKey^ rk;
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);
   if (!rk)
   {
      Console::WriteLine("Failed to open CurrentUser/Software key");
      return -1;
   }

   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");
   if (!nk)
   {
      Console::WriteLine("Failed to create 'NewRegKey'");
      return -1;
   }

   String^ newValue = "NewValue";
   try
   {
      nk->SetValue("NewKey", newValue);
      nk->SetValue("NewKey2", 44);
   }
   catch (Exception^)
   {
      Console::WriteLine("Failed to set new values in 'NewRegKey'");
      return -1;
   }

   Console::WriteLine("New key created.");
   Console::Write("Use REGEDIT.EXE to verify ");
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");
   return 0;
}
```

### <a name="remarks"></a>备注

你可以使用 .NET Framework 使用和类来访问注册表 <xref:Microsoft.Win32.Registry> ，这些 <xref:Microsoft.Win32.RegistryKey> 类在 <xref:Microsoft.Win32> 命名空间中定义。 **注册表** 类是类的静态实例的容器 <xref:Microsoft.Win32.RegistryKey> 。 每个实例都表示一个根注册表节点。 实例为、、、 <xref:Microsoft.Win32.Registry.ClassesRoot> <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser> <xref:Microsoft.Win32.Registry.LocalMachine> 和 <xref:Microsoft.Win32.Registry.Users> 。

## <a name="related-sections"></a>相关章节

<xref:System.Environment>

## <a name="see-also"></a>请参阅

[用 c + +/CLI (Visual C++ 的 .NET 编程) ](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

---
title: 混合程序集的初始化
description: 处理混合程序集的加载和初始化过程中可能发生的问题。
ms.date: 09/26/2020
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 6767e6087999138f8e62d3c5a58f972b4e2149ed
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413809"
---
# <a name="initialization-of-mixed-assemblies"></a>混合程序集的初始化

在过程中运行代码时，Windows 开发人员必须始终警惕加载程序锁 `DllMain` 。 但是，在处理 c + +/CLI 混合模式程序集时，需要考虑一些其他问题。

[DllMain](/windows/win32/Dlls/dllmain)中的代码不能访问 .Net 公共语言运行时 (CLR) 。 这意味着，不 `DllMain` 应直接或间接调用托管函数; 在中不应声明或实现托管代码 `DllMain` ; 并且在中不应发生垃圾回收或自动库加载 `DllMain` 。

## <a name="causes-of-loader-lock"></a>加载程序锁定的原因

随着 .NET 平台的引入，可以通过两种不同的机制来加载执行模块 (EXE 或 DLL) ：一个用于 Windows，用于非托管模块，另一个用于加载 .NET 程序集的 CLR。 混合 DLL 加载问题与 Microsoft Windows OS 加载程序密切相关。

当只包含 .NET 构造的程序集加载到进程中时，CLR 加载程序可以执行所有必要的加载和初始化任务。 但是，若要加载可以包含本机代码和数据的混合程序集，也必须使用 Windows 加载程序。

Windows 加载程序保证在初始化之前，没有代码可以访问该 DLL 中的代码或数据。 它可确保在部分初始化时，没有代码可以冗余加载 DLL。 为此，Windows 加载程序使用一个进程全局关键部分 (通常称为 "加载程序锁定" ) ，在模块初始化期间阻止不安全的访问。 因此，加载进程容易受到许多典型死锁情况的攻击。 对于混合程序集来说，下面的两种情况增加了死锁风险：

- 第一种情况是，如果用户试图执行编译为 Microsoft 中间语言 (MSIL) 当加载程序锁在 `DllMain` 静态初始值设定项 (（例如) ）时，它可能会导致死锁。 假设 MSIL 函数引用尚未加载的程序集中的类型。 CLR 会尝试自动加载该程序集，这可能要求 Windows 加载程序在加载程序锁上阻止。 发生死锁，因为加载程序锁已由调用序列中前面的代码持有。 但是，在加载程序锁下执行 MSIL 不能保证发生死锁。 这就使得这种情况很难诊断和修复。 在某些情况下，例如，当被引用类型的 DLL 不包含本机构造并且其所有依赖项都不包含本机结构时，加载被引用类型的 .NET 程序集不需要 Windows 加载程序。 此外，所需的程序集或其混合本机/.NET 依赖项可能已经由其他代码加载了。 因此，死锁情况很难预测，它在很大程度上取决于目标计算机的配置。

- 其次，在 .NET Framework 的1.0 和1.1 版本中加载 Dll 时，CLR 假定未持有加载程序锁，并且在加载程序锁下执行了若干无效操作。 假设不持有加载程序锁是纯 .NET Dll 的有效假设。 但由于混合 Dll 执行本机初始化例程，因此需要本机 Windows 加载程序，进而导致加载程序锁。 因此，即使开发人员在 DLL 初始化期间并未尝试执行任何 MSIL 函数，在 .NET Framework 版本1.0 和1.1 中仍有可能发生不确定的死锁。

已经从混合 DLL 加载进程中消除了所有的不确定性。 这是通过以下更改实现的：

- CLR 在加载混合 DLL 时不再作出错误的假定。

- 非托管初始化和托管初始化在两个不同的阶段执行。 非托管初始化首先通过)  (`DllMain` ，并通过进行托管初始化。支持 NET 的 `.cctor` 构造。 后者对于用户完全透明，除非 **`/Zl`** **`/NODEFAULTLIB`** 使用或。 有关详细信息，请参阅[ `/NODEFAULTLIB` (忽略库) ](../build/reference/nodefaultlib-ignore-libraries.md)和[ `/Zl` (省略默认库名称) ](../build/reference/zl-omit-default-library-name.md)。

加载程序锁还是会出现，但现在它的出现是重复出现的，因而可以检测到。 如果 `DllMain` 包含 MSIL 指令，编译器将生成警告 [编译器警告 (级别 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)。 CRT 或 CLR 都将尝试检测并报告在加载程序锁下执行 MSIL 的企图。 CRT 检测导致运行时诊断 C 运行时错误 R6033。

本文的其余部分介绍了可以在加载程序锁下执行 MSIL 的其他方案。 它演示了如何解决这些方案中的问题，以及调试技术。

## <a name="scenarios-and-workarounds"></a>情况和解决方法

在几种不同情况下，用户代码可在加载程序锁定下执行 MSIL。 开发人员必须确保在上述每种情况下，用户代码实现不会尝试执行 MSIL 指令。 下面各小节描述了所有的可能性，并讨论了如何解决最常见的情况中的问题。

### <a name="dllmain"></a>DllMain

`DllMain`函数是 DLL 的用户定义入口点。 除非用户指定，否则，每当进程或线程附加到包含 DLL 或从包含 DLL 中分离时，都会调用 `DllMain` 。 由于这种调用可以在加载程序锁被保留时发生，因此不应将用户提供的 `DllMain` 函数编译为 MSIL。 此外，以 `DllMain` 为根的调用树中的函数不能编译为 MSIL。 若要在此处解决问题， `DllMain` 应用修改定义的代码块 `#pragma unmanaged` 。 对于由 `DllMain` 调用的每个函数，应执行同样的操作。

如果这些函数必须调用一个函数，而该函数需要 MSIL 实现才能进行其他调用上下文，则可以使用一个复制策略，其中同时创建了同一函数的 .NET 版本和本机版本。

作为替代方法，如果 `DllMain` 不需要或者不需要在加载程序锁下执行，则可以删除用户提供的 `DllMain` 实现，这将消除此问题。

如果 `DllMain` 尝试直接执行 MSIL，则 [编译器警告 (级别 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) 将生成。 但编译器无法检测到这样的情况： `DllMain` 调用另一个模块中的一个函数，该函数又尝试执行 MSIL。

有关此方案的详细信息，请参阅 [诊断障碍](#impediments-to-diagnosis)。

### <a name="initializing-static-objects"></a>初始化静态对象

如果需要动态初始值设定项，初始化静态对象会导致死锁。 简单的案例 (例如，在将编译时已知的值分配给静态变量时，) 不需要动态初始化，因此不存在死锁风险。 但是，某些静态变量由函数调用、构造函数调用或无法在编译时计算的表达式进行初始化。 这些变量都需要在模块初始化过程中执行代码。

下面的代码演示了需要动态初始化的静态初始值设定项的示例：一个函数调用、对象构造和一个指针初始化。  (这些示例不是静态的，但假定在全局范围内具有相同的效果。 ) 

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

死锁风险取决于是否对包含模块进行编译 **`/clr`** ，以及是否会执行 MSIL。 具体来说，如果静态变量的编译没有 **`/clr`** (或位于 `#pragma unmanaged` 块) 中，而初始化它所需的动态初始值设定项导致执行 MSIL 指令，则可能发生死锁。 这是因为，对于未使用编译的模块 **`/clr`** ，静态变量的初始化由 DllMain 执行。 相反，在 **`/clr`** `.cctor` 非托管初始化阶段完成并且加载程序锁已释放后，使用编译的静态变量将初始化。

动态初始化静态变量导致死锁的一些解决方案。 它们按照修复问题所需的时间顺序排列在此处：

- 可以用编译包含静态变量的源文件 **`/clr`** 。

- 可使用指令将静态变量调用的所有函数编译为本机代码 `#pragma unmanaged` 。

- 手动克隆静态变量所依赖的代码，以提供具有不同名称的 .NET 版本和本机版本。 这样，开发人员就可以从本机静态初始值设定项调用本机版本，而从其他位置调用 .NET 版本。

### <a name="user-supplied-functions-affecting-startup"></a>影响启动的用户提供的函数

在启动过程中，库依赖一些由用户提供的函数进行初始化。 例如，在 c + + 中全局重载运算符（如 **`new`** 和运算符）时，将在 **`delete`** 任何位置使用用户提供的版本，包括 c + + 标准库初始化和析构。 因此，c + + 标准库和用户提供的静态初始值设定项将调用这些运算符的任何用户提供的版本。

如果将用户提供的版本编译为 MSIL，这些初始值设定项在加载程序锁被保留时会尝试执行 MSIL 指令。 用户提供 `malloc` 的结果相同。 若要解决此问题，必须使用指令将所有这些重载或用户提供的定义实现为本机代码 `#pragma unmanaged` 。

有关此方案的详细信息，请参阅 [诊断障碍](#impediments-to-diagnosis)。

### <a name="custom-locales"></a>自定义区域设置

如果用户提供了自定义全局区域设置，则使用此区域设置来初始化未来的所有 i/o 流，包括静态初始化的流。 如果将该全局区域设置对象编译为 MSIL，就可以在加载程序锁被保留时调用编译为 MSIL 的区域设置对象成员函数。

有三种方式可解决此问题：

可以使用选项编译包含所有全局 i/o 流定义的源文件 **`/clr`** 。 它禁止在加载程序锁下执行其静态初始值设定项。

自定义区域设置函数定义可以使用指令编译为本机代码 `#pragma unmanaged` 。

在加载程序锁被释放之前，避免将自定义区域设置设为全局区域设置。 当加载程序锁被释放后，使用自定义区域设置显式配置在初始化期间创建的 I/O 流。

## <a name="impediments-to-diagnosis"></a>妨碍诊断的情况

在某些情况下，很难检测到死锁的来源。 下面各小节讨论了这些情况以及解决这些问题的途径。

### <a name="implementation-in-headers"></a>头文件中的实现

在某些情况下，头文件中的函数实现会使诊断变得复杂。 内联函数和模板代码都要求在头文件中指定函数。  C++ 语言指定单一定义规则，该规则强制具有相同名称的函数的所有实现在语义上相等。 因此，C++ 链接器在合并具有给定函数的重复实现的对象文件时没有任何特别注意事项。

在 visual studio 2005 之前的 Visual Studio 版本中，链接器只是选择这些语义上等效的定义中的最大值。 完成此操作的目的是为了满足前向声明，并在不同的源文件中使用不同优化选项的情况。 它为混合本机和 .NET Dll 创建问题。

由于与启用和禁用的 c + + 文件可能同时包含相同的标头 **`/clr`** ，或者可以在块中包装 #include，因此，可以 `#pragma unmanaged` 同时具有在标头中提供实现的 MSIL 和本机版本的函数。 MSIL 和本机实现在加载程序锁下具有不同的初始化语义，这实际上违反了单一定义规则。 因此，当链接器选择最大的实现时，它可以选择函数的 MSIL 版本，即使该函数已在其他位置使用指令显式编译为本机代码 `#pragma unmanaged` 。 若要确保在 "加载程序锁定" 下永远不会调用 MSIL 版本的模板或内联函数，则必须使用指令修改在 "加载程序锁" 下调用的每个此类函数的每个定义 `#pragma unmanaged` 。 如果标头文件来自第三方，则进行此更改的最简单方法是在出现 `#pragma unmanaged` 问题的标头文件的 #include 指令前后推送和弹出指令。  (查看 [托管的非托管](../preprocessor/managed-unmanaged.md) 的示例。 ) 不过，此策略不适用于包含其他必须直接调用 .net api 的代码的标头。

为方便用户处理加载程序锁，当两种版本同时出现时，链接器将选择本机实现，而不选择托管实现。 此默认值可避免上述问题。 但在此版本中，此规则有两个例外，因为编译器有两个未解决的问题：

- 对内联函数的调用通过全局静态函数指针进行。 此方案 isn'table，因为虚拟函数是通过全局函数指针调用的。 例如，应用于对象的

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>在调试模式下诊断

加载程序锁问题的所有诊断都应该在调试版本中进行。 发布版本可能不生成诊断。 而且，在发布模式下进行的优化可能会在加载程序锁定方案下屏蔽某些 MSIL。

## <a name="how-to-debug-loader-lock-issues"></a>如何调试加载程序锁定问题

在调用 MSIL 函数时，CLR 生成的诊断会导致 CLR 暂停执行。 这进而导致在进程内运行调试对象时同时挂起 Visual C++ 混合模式调试器。 但是，当附加到进程时，it'sn't 可以使用混合调试器获取调试对象的托管调用堆栈。

为确定在有加载程序锁时调用的具体 MSIL 函数，开发人员应该完成以下步骤：

1. 确保 mscoree.dll 和 mscorwks.dll 的符号可用。

   可以通过两种方式使符号可用。 首先，可将 mscoree.dll 和 mscorwks.dll 的 PDB 添加到符号搜索路径中。 若要添加它们，请打开符号搜索路径选项对话框。  (从 " **工具** " 菜单中选择 " **选项**"。 在 " **选项** " 对话框的左窗格中，打开 " **调试** " 节点并选择 " **符号**"。 ) 将路径添加到 mscoree.dll 并将 mscorwks.dll PDB 文件添加到搜索列表。 将这些 PDB 安装到 %VSINSTALLDIR%\SDK\v2.0\symbols 中。 选择 **“确定”** 。

   其次，可以从 Microsoft Symbol Server 中下载 mscoree.dll 和 mscorwks.dll 的 PDB。 若要配置 Symbol Server，请打开符号搜索路径选项对话框。  (从 " **工具** " 菜单中选择 " **选项**"。 在 " **选项** " 对话框的左窗格中，打开 " **调试** " 节点并选择 " **符号**"。 ) 将此搜索路径添加到搜索列表： `https://msdl.microsoft.com/download/symbols` 。 向符号服务器缓存文本框中添加一个符号缓存目录。 选择 **“确定”** 。

1. 将调试程序模式设置为仅限本机模式。

   在解决方案中打开启动项目的 " **属性** " 网格。 选择“配置属性” > “调试”。 将 " **调试器类型** " 属性设置为 " **仅限本机**"。

1.  (F5) 启动调试器。

1. **`/clr`** 生成诊断后，选择 "**重试**"，然后选择 "**中断**"。

1. 打开“调用堆栈”窗口。  (在菜单栏上，选择 "**调试**  >  **Windows**  >  **调用堆栈**"。 ) 出现问题 `DllMain` 或静态初始值设定项用绿色箭头标识。 如果未标识出有问题的函数，则必须执行以下步骤来找到该函数。

1. 打开 "**即时**" 窗口 (在菜单栏上，选择 "立即**调试**  >  **Windows**"  >  **Immediate**。 ) 

1. `.load sos.dll`在 "**即时**" 窗口中输入，加载 SOS 调试服务。

1. `!dumpstack`在 "**即时**" 窗口中输入，以获取内部堆栈的完整列表 **`/clr`** 。

1. 查找最接近) 堆栈底部的第一个实例 (_CorDllMain (如果在 `DllMain` 静态初始值设定项导致问题) 或 _VTableBootstrapThunkInitHelperStub 或 (时) 或，则或。 紧挨着位于此调用下方的堆栈项是 MSIL 实现的函数的调用，该函数曾试图在有加载程序锁时执行。

1. 请参阅上一步中标识的源文件和行号，并使用 "方案" 一节中所述的方案和解决方案更正问题。

## <a name="example"></a>示例

### <a name="description"></a>说明

下面的示例演示如何通过将代码从移 `DllMain` 到全局对象的构造函数中来避免加载程序锁。

在此示例中，有一个全局托管对象，它的构造函数包含最初在中的托管对象 `DllMain` 。 此示例的第二部分引用程序集，并创建托管对象的一个实例以调用执行初始化的模块构造函数。

### <a name="code"></a>代码

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker doesn't throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

此示例演示了混合程序集的初始化问题：

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

此代码生成以下输出：

```Output
Module ctor initializing based on global instance of class.

Test called so linker doesn't throw away unused object.
```

## <a name="see-also"></a>另请参阅

[混合 (本机和托管) 程序集](../dotnet/mixed-native-and-managed-assemblies.md)

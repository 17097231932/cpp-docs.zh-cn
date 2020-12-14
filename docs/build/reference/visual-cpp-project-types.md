---
description: 了解更多： c + + 项目模板
title: Visual C++ 项目类型
ms.date: 08/13/2019
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: 924e53e0d977b4f9b3b40bf7444f8495dbe1d451
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253164"
---
# <a name="c-project-templates"></a>C++ 项目模板

Visual Studio 项目模板生成源代码文件、编译器选项、菜单、工具栏、图标、引用以及 `#include` 适合要创建的项目类型的语句。 Visual Studio 包括多种 c + + 项目模板并为其中许多项目模板提供了向导，以便可以在创建项目时对其进行自定义。 在创建项目之后，可以立即生成它并运行应用程序；在开发应用程序时最好间歇性生成该项目。

> [!NOTE]
> 你可以使用 C++ 项目模板来创建 C 语言项目。 在生成的项目中，找到文件扩展名为 .cpp 的文件并将它更改为 .c。 然后，在该项目（而非解决方案）的“项目属性”  页上，依次展开“配置属性” 和“C/C++”  ，然后选择“高级” 。 将“编译为”  设置更改为“编译为 C 代码 (/TC)” 。

## <a name="project-templates"></a>项目模板

Visual Studio 中包含的项目模板取决于安装的产品版本和工作负载。 如果已安装了 c + + 的桌面开发工作负荷，Visual Studio 将包含这些 c + + 项目模板。

### <a name="windows-desktop"></a>Windows 桌面

|项目模板|描述|
|----------------------|-----------------------------|
|[Windows 控制台应用程序](../../windows/overview-of-windows-programming-in-cpp.md)|用于创建 Windows 控制台应用程序的项目。|
|[Windows 桌面应用程序](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|用于创建 Windows 桌面 (Win32) 应用程序的项目。|
|[动态链接库](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|创建动态链接库 (DLL) 的项目。|
|[静态库](../walkthrough-creating-and-using-a-static-library-cpp.md)|创建静态库 (LIB) 的项目。|
|[Windows 桌面向导](../../windows/windows-desktop-wizard.md)|用于通过其他选项创建 Windows 桌面应用程序和库的向导。|

### <a name="general"></a>常规

|项目模板|描述|
|----------------------|-----------------------------|
|空项目|用于创建应用程序、库或 DLL 的空项目。 必须添加所需的任何代码或资源。|
|[生成文件项目](creating-a-makefile-project.md)|在 Visual Studio 项目中包装 Windows makefile 的项目。  (在 Visual Studio 中按原样打开生成文件，请使用 " [打开文件夹](../open-folder-projects-cpp.md)"。|
|“共享项”项目|用于在多个项目之间共享代码文件或资源文件的项目。 此项目类型不会生成可执行文件。|

### <a name="atl"></a>ATL

|项目模板|描述|
|----------------------|-----------------------------|
|[ATL 项目](../../atl/reference/creating-an-atl-project.md)|使用活动模板库的项目。|

### <a name="test"></a>测试

|项目模板|描述|
|----------------------|-----------------------------|
|[本机单元测试项目](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|其中包含本机 C++ 单元测试的项目。|

### <a name="mfc"></a>MFC

如果将 MFC 和 ATL 支持组件添加到 Visual Studio 安装，则这些项目模板将添加到 Visual Studio。

|项目模板|描述|
|----------------------|-----------------------------|
|[MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)|用于创建使用 Microsoft 基础类 (MFC) 库的应用程序的项目。|
|[MFC ActiveX 控件](../../mfc/reference/creating-an-mfc-activex-control.md)|用于创建使用 MFC 库的 ActiveX 控件的项目。|
|[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)|用于创建使用 MFC 库的动态链接库的项目。|

### <a name="windows-universal-apps"></a>Windows 通用应用

如果将 C++ Windows 通用平台工具组件添加到 Visual Studio 安装，则这些项目模板将添加到 Visual Studio。

有关 C++ 中 Windows 通用应用的概述，请参阅[通用 Windows 应用 (C++)](../../cppcx/universal-windows-apps-cpp.md)。

|项目模板|描述|
|----------------------|-----------------------------|
|空白应用|用于没有预定义控件或布局的单页通用 Windows 平台 (UWP) 应用的项目。|
|DirectX 11 应用|用于使用 DirectX 11 的通用 Windows 平台应用的项目。|
|DirectX 12 应用|用于使用 DirectX 12 的通用 Windows 平台应用的项目。|
|DirectX 11 和 XAML 应用|用于使用 DirectX 11 和 XAML 的通用 Windows 平台应用的项目。|
|单元测试应用|用于为通用 Windows 平台 (UWP) 应用创建单元测试应用的项目。|
|DLL|用于可由通用 Windows 平台应用或运行时组件使用的本机动态链接库 (DLL) 的项目。|
|静态库|用于可由通用 Windows 平台应用或运行时组件使用的本机静态链接库 (LIB) 的项目。|
|Windows 运行时组件|用于可由通用 Windows 平台应用使用的 Windows 运行时组件的项目，与编写应用所用的编程语言无关。|
|Windows 应用程序打包项目|用于创建 UWP 包的项目，该 UWP 包可使桌面应用程序进行侧加载或通过 Microsoft Store 进行分发。|

## <a name="todo-comments"></a>TODO 注释

许多由项目模板生成的文件都包含 TODO 注释，这些注释可帮助你标识提供自己的源代码的位置。 有关如何添加代码的详细信息，请参阅[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)和[使用资源文件](../../windows/working-with-resource-files.md)。

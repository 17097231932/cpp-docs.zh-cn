---
description: 了解详细信息：混合 (本机和托管) 程序集
title: 混合（本机和托管）程序集
ms.date: 09/18/2018
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
ms.openlocfilehash: b96ccb5a521cf009f7feabef01a292ac805b0b4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253632"
---
# <a name="mixed-native-and-managed-assemblies"></a>混合（本机和托管）程序集

混合程序集能够同时包含非托管计算机指令和 MSIL 指令。 这允许它们调用并由 .NET 组件调用，同时保持与本机 c + + 库的兼容性。 使用混合程序集，开发人员可以使用 .NET 和本机 c + + 代码的组合创作应用程序。

例如，通过使用 **/clr** 编译器开关仅重新编译一个模块，可将包含完全本机 c + + 代码的现有库引入 .net 平台。 然后，此模块可以使用 .NET 功能，但仍与应用程序的其余部分兼容。 甚至可以在同一文件中逐个函数地决定托管和本机编译 (请参阅 [托管的非托管](../preprocessor/managed-unmanaged.md)) 。

Visual C++ 仅支持通过使用 **/clr** 编译器选项来生成混合托管程序集。 **/Clr： pure** 和 **/clr： safe** 编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。 如果需要纯或可验证的托管程序集，我们建议使用 c # 创建它们。

早期版本的 Microsoft c + + 编译器工具集支持生成三个不同类型的托管程序集：混合、纯和可验证。 后两个在 [纯代码和可验证代码 (c + +/cli) ](../dotnet/pure-and-verifiable-code-cpp-cli.md)中讨论。

## <a name="in-this-section"></a>在本节中

[如何：迁移到/clr](../dotnet/how-to-migrate-to-clr.md)<br/>
介绍在应用程序中引入或升级 .NET 功能的建议步骤。

[如何：使用/clr 编译 MFC 和 ATL 代码](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
讨论如何编译现有的 MFC 和 ATL 程序以面向公共语言运行时。

[混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
介绍 "加载程序锁" 的问题和解决方案。

[混合程序集的库支持](../dotnet/library-support-for-mixed-assemblies.md)<br/>
讨论如何在 **/clr** 编译中使用本机库。

[性能注意事项](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
介绍混合程序集和数据封送处理的性能影响。

[应用程序域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
讨论 Visual C++ 对应用程序域的支持。

[双重形式转换](../dotnet/double-thunking-cpp.md)<br/>
讨论托管函数的本机入口点的性能影响。

[在使用通过/clr 生成的 COM 对象时避免 CLR 关闭异常](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
讨论如何确保正确关闭使用使用 **/clr** 编译的 COM 对象的托管应用程序。

[如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序](../dotnet/create-a-partially-trusted-application.md)<br/>
讨论如何通过删除 msvcm90.dll 上的依赖项来创建部分受信任的公共语言运行时应用程序 Visual C++。

有关混合程序集的编码准则的详细信息，请参阅 [托管/非托管代码互操作性概述](/previous-versions/dotnet/articles/ms973872(v=msdn.10))。

## <a name="see-also"></a>请参阅

- [本机和 .NET 互操作性](../dotnet/native-and-dotnet-interoperability.md)

---
description: 详细了解：演练：生成项目 (C++)
title: 演练：生成项目 (C++)
ms.date: 04/25/2019
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
ms.openlocfilehash: f606a0ead796916fa41f7669852e67d58ae3b17c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222536"
---
# <a name="walkthrough-building-a-project-c"></a>演练：生成项目 (C++)

在本演练中，特意在代码中引入 C++ 语法错误来了解什么是编译错误，以及如何修复。 编译项目时，会显示错误消息以指示所发生的问题的性质和位置。

## <a name="prerequisites"></a>先决条件

- 本演练假定你具备 C++ 语言的基础知识。

- 它还假定你已完成之前在[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中列出的相关演练。

### <a name="to-fix-compilation-errors"></a>修复编译错误

1. 在 Games.cpp 中，删除最后一行中的分号，使其类似于以下语句：

   `return 0`

1. 在菜单栏上，依次选择“生成” > “生成解决方案”   。

1. “错误列表”窗口中的消息指示生成项目过程中出现了错误。 该声明类似于以下错误消息：

   `error C2143: syntax error: missing ';' before '}'`

   若要查看有关此错误的帮助信息，请在“错误列表”窗口中将其突出显示，然后选择 F1 键。

1. 将分号重新添加到导致语法错误的行的末尾：

   `return 0;`

1. 在菜单栏上，依次选择“生成” > “生成解决方案”   。

   “输出”窗口中的消息指示项目已成功编译。

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>Game.cpp
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

## <a name="next-steps"></a>后续步骤

**上一步：** [演练：使用项目和解决方案 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)<br/>
**下一步：** [演练：测试项目 (C++)](../ide/walkthrough-testing-a-project-cpp.md)

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[项目和生成系统](../build/projects-and-build-systems-cpp.md)<br/>

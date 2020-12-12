---
description: '详细了解： (C/c + + #include 指令) '
title: '#include 指令 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 491c6f06a6e2924c61ecd56dcb2ab2e5f4243512
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300420"
---
# <a name="include-directive-cc"></a> (C/c + + 的 #include 指令) 

告知预处理器将已指定文件的内容视为它们在源程序中指令出现处出现的方式处理。

## <a name="syntax"></a>语法

> **#include** "*路径规范*" \
> **#include**\<*path-spec*>

## <a name="remarks"></a>备注

您可以将常数和宏定义组织到包含文件中，然后使用 **#include** 指令将它们添加到任何源文件中。 包含文件还可用于合并外部变量和复杂数据类型的声明。 在为此目的而创建的包含文件中，类型只能定义和命名一次。

*路径规范* 是一个文件名，可以选择性地以目录规范开头。 文件名必须命名现有文件。 *路径规范* 的语法取决于编译程序的操作系统。

有关如何在使用 [/clr](../build/reference/clr-common-language-runtime-compilation.md)编译的 c + + 应用程序中引用程序集的信息，请参阅 [#using](../preprocessor/hash-using-directive-cpp.md)。

两种语法形式都会导致指令被替换为指定包含文件的整个内容。 两种形式之间的区别在于，在未完全指定路径时预处理器搜索标头文件的顺序。 下表显示了这两种语法形式之间的差异。

|语法形式|操作|
|---|------------|
|带引号的形式|预处理器按以下顺序搜索包含文件：<br/><br/> 1) 在包含 **#include** 语句的文件所在的目录中。<br/><br/> 2) 当前打开的包含文件的目录中，以其打开的相反顺序排列。 搜索从父包含文件的目录中开始进行，然后继续向上到任何祖父包含文件的目录。<br/><br/> 3) 沿着每个 **/i** 编译器选项指定的路径。<br/><br/> 4) 沿着 INCLUDE 环境变量指定的路径。|
|尖括号形式|预处理器按以下顺序搜索包含文件：<br/><br/> 1) 沿着每个 **/i** 编译器选项指定的路径。<br/><br/> 2) 在命令行上进行编译，以及由 INCLUDE 环境变量指定的路径。|

只要找到具有给定名称的文件，预处理器就会停止搜索。 如果将包含文件的完整、明确的路径规范括 (`" "`) ，则预处理器只搜索该路径规范并忽略标准目录。

如果用双引号括起来的文件名是不完整的路径规格，则预处理器将首先搜索“父”文件的目录。 父文件是包含 **#include** 指令的文件。 例如，如果将名为 *file2* 的文件包含在名为 *file1* 的文件中，则 *file1* 是父文件。

包含文件可以 "嵌套"： **#include** 指令可以出现在由另一个 **#include** 指令命名的文件中。 例如， *file2* 可以包括 *file3*。 在这种情况下， *file1* 仍是 *file2* 的父级，但它将是 *file3* 的 "祖父"。

当包含文件嵌套并在命令行上编译时，目录搜索会从父文件的目录开始。 然后，它会遍历所有祖父文件的目录。 即，搜索将相对于包含当前正在处理的源的目录开始。 如果找不到该文件，则搜索会移动到由 [/i (其他包含目录) ](../build/reference/i-additional-include-directories.md) 编译器选项指定的目录。 最后，将搜索 INCLUDE 环境变量指定的目录。

在 Visual Studio 开发环境中，将忽略 INCLUDE 环境变量。 有关如何设置要在其中搜索包含文件和库文件的目录的信息，请参阅 " [VC + + 目录" 属性页](../build/reference/vcpp-directories-property-page.md)。

此示例使用尖括号显示文件包含：

```C
#include <stdio.h>
```

此示例将名为 STDIO.H 文件的内容添加到源程序。 尖括号导致预处理器在 INCLUDE 环境变量指定的目录中搜索 STDIO.H。H. 搜索由 **/i** 编译器选项指定的目录。

下一个示例用引号形式显示文件包含：

```C
#include "defs.h"
```

此示例将 DEFS.H 指定的文件的内容添加到源程序。 双引号意味着，预处理器将首先搜索包含父源文件的目录。

包含文件的嵌套可扩展至 10 个级别。 处理嵌套的 **#include** 后，预处理器将继续在原始源文件中插入封闭的包含文件。

**Microsoft 专用**

若要查找可包含源文件，预处理器首先搜索由 **/i** 编译器选项指定的目录。 如果 **/i** 选项不存在或失败，则预处理器将使用 INCLUDE 环境变量在尖括号中查找任意包含文件。 INCLUDE 环境变量和 **/i** 编译器选项可包含多个路径，由分号分隔 (**;**) 。 如果多个目录显示为 **/i** 选项的一部分或在 INCLUDE 环境变量中，预处理器会按照它们出现的顺序进行搜索。

例如，命令

```cmd
CL /ID:\MSVC\INCLUDE MYPROG.C
```

会促使预处理器搜索包含文件（如 STDIO.H）的目录 D:\MSVC\INCLUDE\。 命令

```cmd
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

具有同样的作用。 如果两组搜索都失败，则会生成严重的编译器错误。

如果为路径包含冒号的包含文件指定完整的文件名（例如，F:\MSVC\SPECIAL\INCL\TEST.H），则预处理器会遵循该路径。

对于指定为的包含文件 `#include "path-spec"` ，目录搜索从父文件的目录开始，然后在所有祖父文件的目录中继续进行。 也就是说，搜索将相对于包含要处理的 **#include** 指令的源文件的目录开始。 如果没有祖父文件且没有找到该文件，则搜索会像文件名括在尖括号中一样继续进行。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)\
[/I（附加包含目录）](../build/reference/i-additional-include-directories.md)

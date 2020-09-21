---
title: 运行 NMAKE
description: 了解如何运行 NMAKE。
ms.date: 02/09/2020
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: c2327e13e59ebf9df1ecba6fa66c6354641768ee
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743134"
---
# <a name="running-nmake"></a>运行 NMAKE

## <a name="syntax"></a>语法

> **NMAKE** [*选项*...][*宏*...][*目标*...][ **\@** _命令文件_...]

## <a name="remarks"></a>备注

NMAKE 仅生成指定的 *目标* ，如果未指定，则生成生成文件中的第一个目标。 第一个生成文件目标可以是生成其他目标的 [伪](description-blocks.md#pseudotargets) 目标。 NMAKE 使用通过 **/f**指定的生成文件，如果未指定 **/f** ，则使用当前目录中的生成文件文件。 如果未指定生成文件，它将使用推理规则来生成命令行 *目标*。

*命令文件*文本文件 (或响应文件) 包含命令行输入。 其他输入可以位于 \@ *命令文件*之前或之后。 允许路径。 在 *命令文件*中，分行符被视为空格。 如果宏定义包含空格，则用引号将其引起来。

## <a name="nmake-options"></a>NMAKE 选项

NMAKE 选项如下表所述。 选项前面有一个斜杠 (`/`) 或短划线 (`-`) ，并且不区分大小写。 用于 [`!CMDSWITCHES`](makefile-preprocessing-directives.md) 更改生成文件或 Tools.ini 中的选项设置。

| 选项 | 目标 |
| ------------ | ------------- |
| **/A** | 强制生成所有已计算的目标，即使与依赖项相比不过期。 不强制生成不相关的目标。 |
| **/B** | 即使时间戳相等，也强制生成。 建议仅用于速度较快的系统 (两秒钟或更少) 的解决方案。 |
| **/C** | 禁止显示默认输出，包括非致命 NMAKE 错误或警告、时间戳和 NMAKE 版权消息。 禁止使用 **/k**发出的警告。 |
| **/D** | 显示每个已评估的目标和依赖项的时间戳，并显示一条不存在的目标消息。 使用 **/p** 调试生成文件非常有用。 用于 `!CMDSWITCHES` 设置或清除部分生成文件的 **/d** 。 |
| **/E** | 导致环境变量重写生成文件宏定义。 |
| **/ERRORREPORT** [ **NONE** &#124; **PROMPT** &#124; **QUEUE** &#124; **SEND** ] | 已弃用。 [Windows 错误报告 (WER) ](/windows/win32/wer/windows-error-reporting) 设置控制报告。 |
| **/F** *filename* | 指定 *filename* 作为生成文件。 空格或制表符可以位于 *filename*之前。 为每个生成文件指定 **/f** 一次。 若要从标准输入中提供生成文件，请在 " `-` *文件名*" () 指定破折号，并使用 **F6** 或 **CTRL + Z**来结束键盘输入。 |
| **/G** | 显示指令附带的生成生成 `!INCLUDE` 。 有关详细信息，请参阅 [Makefile 预处理指令](makefile-preprocessing-directives.md)。 |
| **/Help**， **/？** | 显示 NMAKE 命令行语法的简短摘要。 |
| **/I** | 忽略所有命令的退出代码。 若要设置或清除部分生成文件的 **/i** ，请使用 `!CMDSWITCHES` 。 若要忽略部分生成文件的退出代码，请使用短划线 (`-`) 命令修饰符或 [`.IGNORE`](dot-directives.md) 。 如果 **两者** 都指定，则将重写。 |
| **遇到** | 如果命令返回错误，则继续生成不相关的依赖项。 还会发出警告，并返回退出代码1。 默认情况下，如果有任何命令返回非零退出代码，NMAKE 将暂停。 从 **/k**发出的警告被 **/c**禁止;**如果同时**指定两者，则 **/i**将重写。 |
| **/N** | 显示，但不执行命令;执行预处理命令。 不会在递归 NMAKE 调用中显示命令。 用于调试生成程序和检查时间戳。 若要设置或清除部分生成文件的 **/n** ，请使用 `!CMDSWITCHES` 。 |
| **/NOLOGO** | 禁止 NMAKE 版权消息。 |
| **/P** | 显示信息 (宏定义、推理规则、目标、 [`.SUFFIXES`](dot-directives.md) 将) 列出到标准输出，然后运行生成。 如果没有生成文件或命令行目标，它将仅显示信息。 使用 with **/d** 调试生成文件。 |
| **/Q** | 检查目标的时间戳;不运行生成。 如果所有目标都是最新的，则返回零退出代码，如果有任何目标过期，则返回非零退出代码。 执行预处理命令。 在从批处理文件运行 NMAKE 时非常有用。 |
| **/R** | 清除 `.SUFFIXES` 列表，并忽略在 Tools.ini 文件中定义或预定义的推理规则和宏。 |
| **/S** | 禁止显示已执行的命令。 若要禁止显示部分生成文件，请使用 **\@** 命令修饰符或 [`.SILENT`](dot-directives.md) 。 若要设置或清除部分生成文件的 **/s** ，请使用 `!CMDSWITCHES` 。 |
| **/T** | 更新命令行目标的时间戳 (或第一个 makefile 目标) 并执行预处理命令，但不运行生成。 |
| **/U** | 必须与 **/n**一起使用。 转储内联 NMAKE 文件，以便 **/n** 输出可以用作批处理文件。 |
| **/X** *filename* | 将 NMAKE 错误输出发送到 *文件名* 而不是标准错误。 空格或制表符可以位于 *filename*之前。 若要将错误输出发送到标准输出，请为文件名指定一个短划线 (`-`) 。 *filename* 不会影响从命令到标准错误的输出。 |
| **/Y** | 禁用批处理模式推理规则。 如果选择此选项，则所有批处理模式推理规则都将被视为常规推理规则。 |

## <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE

NMAKE 在读取生成生成之前读取 Tools.ini，除非使用 **/r** 。 它首先查找当前目录中的 Tools.ini，然后在 INIT 环境变量指定的目录中查找。 初始化文件中的 NMAKE 设置部分以开头 `[NMAKE]` ，可包含任何生成文件信息。 在以数字符号开头的单独行上指定注释 (`#`) 。

## <a name="exit-codes-from-nmake"></a>从 NMAKE 退出代码

NMAKE 返回以下退出代码：

| 代码 | 含义 |
| ---------- | ------------- |
| 0 |  (可能会出现警告)  |
| 1 | 仅当使用 **/k** 时才发出 (不完整的生成)  |
| 2 | 程序错误，可能是由以下问题之一导致的：<br /> -生成文件中的语法错误<br /> -来自命令的错误或退出代码<br /> -用户中断 |
| 4 | 系统错误-内存不足 |
| 255 | 目标不是最新的 (仅当使用 **/q** 时才发出)  |

## <a name="see-also"></a>请参阅

[NMAKE 参考](nmake-reference.md)

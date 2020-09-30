---
title: 错误 C1049
description: 描述编译器错误 C1049、无效的数字参数，并说明如何解决此错误。
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: 9b3cbe5d081e32680e5408fc4a6ddcd932db77a2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503264"
---
# <a name="fatal-error-c1049"></a>错误 C1049

> 无效的数值参数“*value*”

CL.EXE 命令行分析器找到了需要数字参数的 *值* 。

如果编译器找不到其中一个编译器选项的数字参数，则可能出现 C1049 错误：

[/constexpr：深度](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr： backtrace](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr：步骤](../../build/reference/constexpr-control-constexpr-evaluation.md)

需要数值自变量的命令行编译器选项也可能会报告 `Command line error D8004` 、、、 `Command line error D8021` `Command line warning D9002` `Command line warning D9014` 或 `Command line warning D9024` 。

若要解决此错误，请检查命令行中是否存在错误参数或缺少参数。 验证选项和参数之间是否没有意外的空格。 最终命令行可能由宏、环境变量或其他生成系统操作生成。 这就是为什么要查看传递到编译器的实际命令行很重要的原因。

- 在命令文件或生成文件中，可以使用 **echo** 命令报告实际的命令行。

- 在 Visual Studio 中，打开项目的 " **属性页** " 对话框。 在 "**配置属性**" "  >  **c/c + +**  >  **常规**" 页上，将**No**"**取消显示启动版权标志**" 属性更改为 " 选择“确定”以保存更改  。 " **输出** " 窗口现在会在你生成时，在版权行后显示命令行。

其他生成系统可能具有日志文件或详细选项，以查看使用的实际命令。 有关信息，请查看生成系统文档。

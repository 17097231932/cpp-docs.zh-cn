---
title: "“编辑并继续”错误和警告 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.enc.error_4001"
  - "vs.csharp.enc.error_4034"
  - "vs.csharp.enc.error_4003"
  - "vs.csharp.enc.error_4026"
  - "vs.csharp.enc.error_4032"
  - "vs.csharp.enc.error_4017"
  - "vs.csharp.enc.error_4053"
  - "vs.csharp.enc.error_4024"
  - "vs.csharp.enc.error_4012"
  - "vs.csharp.enc.error_4066"
  - "vs.csharp.enc.error_4020"
  - "vs.csharp.enc.error_4008"
  - "vs.csharp.enc.error_4033"
  - "vs.csharp.enc.error_4014"
  - "vs.csharp.enc.error_4023"
  - "vs.csharp.enc.error_4011"
  - "vs.csharp.enc.error_4006"
  - "vs.csharp.enc.error_4059"
  - "vs.csharp.enc.error_4015"
  - "vs.csharp.enc.error_4018"
  - "vs.csharp.enc.error_4028"
  - "vs.csharp.enc.error_4013"
  - "vs.csharp.enc.error_4009"
  - "vs.csharp.enc.error_4021"
  - "vs.csharp.enc.error_4065"
  - "vs.csharp.enc.error_4029"
  - "vs.csharp.enc.error_4058"
  - "vs.csharp.enc.error_4019"
  - "vs.csharp.enc.error_4007"
  - "vs.csharp.enc.error_4052"
  - "vs.csharp.enc.error_4025"
  - "vs.csharp.enc.error_4055"
  - "vs.csharp.enc.error_4022"
  - "vs.csharp.enc.error_4002"
  - "vs.csharp.enc.error_4016"
  - "vs.csharp.enc.error_4043"
  - "vs.csharp.enc.error_4027"
  - "vs.csharp.enc.error_4054"
  - "vs.csharp.enc.error_4004"
  - "vs.csharp.enc.error_4010"
  - "vs.csharp.enc.error_4030"
  - "vs.csharp.enc.error_4005"
  - "vs.csharp.enc.error_4035"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "编辑并继续 [C#], 错误和警告"
  - "错误 [C#], 调试"
  - "错误 [调试器], 编辑并继续"
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "susanno"
manager: "douge"
---
# “编辑并继续”错误和警告 (C#)
已对 Visual C\#“编译并继续”中不允许的代码段进行了编辑。  
  
 利用 [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]“编辑并继续”，您可以在中断模式下停止程序执行，对执行代码进行更改，然后继续执行新合并了更改后的程序。  
  
 通常情况下，影响类的公共结构的声明性代码编辑是禁止的，但对类内部的方法、属性体或私有声明进行某些编辑是允许的。 “编辑并继续”会尽可能将不可编辑的代码标记为浅灰色并显示错误消息。  
  
 有关 [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)] 的“编辑并继续”中支持的编辑的详细信息，请参阅[受支持的代码更改 \(C\#\)](../Topic/Supported%20Code%20Changes%20\(C%23\).md)。 如果需要有关特定错误或警告的详细信息，可以在 MSDN [Visual C\# IDE 论坛](http://go.microsoft.com/fwlink/?LinkId=214693)上搜索或发布。  
  
### 更正此错误  
  
1.  在**“调试”**菜单上，选择**“撤消”**可撤消更改。  
  
     \- 或 \-  
  
2.  停止调试会话，进行编辑并启动新的调试会话。  
  
## 请参阅  
 [编辑并继续 \(Visual C\#\)](../Topic/Edit%20and%20Continue%20\(Visual%20C%23\).md)
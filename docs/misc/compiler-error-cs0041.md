---
title: "编译器错误 CS0041 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0041"
ms.assetid: 80dbfe00-8cdb-4275-9574-8a215c7139d6
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0041
“type”的完全限定名对于调试信息而言太长。 请在不使用“\/debug”选项的情况下编译。  
  
 使用 [\/debug](../Topic/-debug%20\(C%23%20Compiler%20Options\).md) 编译器选项时会出现此错误。 如果你遇到此错误，请尝试删除 bin 目录中的 PDB 文件并重新编译。 如果仍然遇到此错误，你可能需要修复或重新安装 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。
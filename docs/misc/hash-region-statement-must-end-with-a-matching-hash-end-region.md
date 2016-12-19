---
title: "“#Region”语句必须以匹配的“#End Region”结束 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30681"
  - "vbc30681"
helpviewer_keywords: 
  - "BC30681"
ms.assetid: 05a0402b-da68-4ab8-b6d6-940379bc5973
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “#Region”语句必须以匹配的“#End Region”结束
使用 `#Region` 指令指定使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 代码编辑器的大纲显示功能时要展开或折叠的代码块。`#Region` 语句的开始和结束必须在同一个代码块中。  
  
 **错误 ID:** BC30681  
  
### 更正此错误  
  
1.  在代码中 `#Region` 语句后的适当位置插入 `#End Region`  
  
## 请参阅  
 [\#Region 指令](../Topic/%23Region%20Directive.md)
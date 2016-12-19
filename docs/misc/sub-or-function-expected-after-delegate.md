---
title: "“Delegate”后面应为“Sub”或“Function” | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30278"
  - "bc30278"
helpviewer_keywords: 
  - "BC30278"
ms.assetid: fee206b9-8dc0-436f-9909-abd8c17957f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Delegate”后面应为“Sub”或“Function”
`Delegate` 语句未指定 `Sub` 或 `Function` 过程。`Sub` 或 `Function` 关键字必须紧跟 `Delegate` 关键字。  
  
 **错误 ID：**BC30278  
  
### 更正此错误  
  
1.  在 `Delegate` 后紧跟 `Sub` 或 `Function` 关键字。  
  
2.  根据需要，指定过程名称、参数列表和返回类型。  
  
## 请参阅  
 [Delegate 语句](../Topic/Delegate%20Statement.md)   
 [过程](../Topic/Procedures%20in%20Visual%20Basic.md)
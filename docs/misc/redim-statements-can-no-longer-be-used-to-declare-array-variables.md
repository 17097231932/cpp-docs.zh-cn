---
title: "“ReDim”语句不能再用于声明数组变量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30811"
  - "vbc30811"
helpviewer_keywords: 
  - "BC30811"
ms.assetid: 9227a06e-a997-4b16-9977-19e2bce9035b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “ReDim”语句不能再用于声明数组变量
`ReDim` 仅可用于更改现有数组的大小。  
  
 **错误 ID：**BC30811  
  
### 更正此错误  
  
-   在声明数组时指定其大小；例如：  
  
    ```  
    Dim X(20) As Integer  
    ```  
  
## 请参阅  
 [数组摘要](../Topic/Arrays%20Summary%20\(Visual%20Basic\).md)   
 [ReDim 语句](../Topic/ReDim%20Statement%20\(Visual%20Basic\).md)   
 [ReDim Statement Changes in Visual Basic](http://msdn.microsoft.com/zh-cn/b4da14db-ff23-490f-b3c6-d7ae1b649532)
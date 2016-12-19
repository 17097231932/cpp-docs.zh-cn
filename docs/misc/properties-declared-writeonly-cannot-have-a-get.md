---
title: "声明为“WriteOnly”的属性不能有“Get” | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30023"
  - "vbc30023"
helpviewer_keywords: 
  - "BC30023"
ms.assetid: ac290f7d-cbc3-4979-a5d9-1ae1bb26e79d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 声明为“WriteOnly”的属性不能有“Get”
`Get` 过程会读取属性的值。 不能读取 `WriteOnly` 属性。  
  
 **错误 ID：**BC30023  
  
### 更正此错误  
  
-   删除 `Property` 语句中的 `WriteOnly` 关键字，或者删除属性正文中的 `Get` 过程。  
  
## 请参阅  
 [Property 语句](../Topic/Property%20Statement.md)   
 [Get 语句](../Topic/Get%20Statement.md)   
 [WriteOnly](../Topic/WriteOnly%20\(Visual%20Basic\).md)
---
title: "属性访问器不能在“Default”属性中声明为“&lt;accessmodifier&gt;” | Microsoft Docs"
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
  - "bc31107"
  - "vbc31107"
helpviewer_keywords: 
  - "BC31107"
ms.assetid: 25657b33-df85-4535-8043-69795c987175
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 属性访问器不能在“Default”属性中声明为“&lt;accessmodifier&gt;”
默认属性中的 [Get 语句](../Topic/Get%20Statement.md) 或 [Set 语句](../Topic/Set%20Statement%20\(Visual%20Basic\).md) 包括 `Private` 关键字。  
  
 默认属性不能为 `Private`，并且其各个属性过程（`Get` 或 `Set`）也不能为 `Private`。  
  
 **错误 ID：**BC31107  
  
### 更正此错误  
  
-   从 `Get` 或 `Set` 语句中删除 `Private` 关键字，或从 [Property 语句](../Topic/Property%20Statement.md) 中删除 `Default`。  
  
## 请参阅  
 [Property 过程](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [如何：声明具有混合访问级别的属性](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [如何：在 Visual Basic 中声明和调用默认属性](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)
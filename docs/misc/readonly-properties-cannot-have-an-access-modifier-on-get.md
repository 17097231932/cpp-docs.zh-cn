---
title: "“ReadOnly”属性在“Get”上不能有访问修饰符 | Microsoft Docs"
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
  - "vbc31105"
  - "bc31105"
helpviewer_keywords: 
  - "BC31105"
ms.assetid: 54066d8e-eb22-4b99-bb18-45afe61d3b33
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “ReadOnly”属性在“Get”上不能有访问修饰符
`ReadOnly` 属性声明在 [Property 语句](../Topic/Property%20Statement.md)和 [Get 语句](../Topic/Get%20Statement.md) 中都指定了访问级别。  
  
 你始终可以为该属性指定访问级别。 此外，还可以至多为其一个属性过程（`Get` 或 `Set`）指定不同的访问级别，条件是该访问级别比属性访问级别限制性更强。 无法为两个属性过程指定访问级别。  
  
 **错误 ID：**BC31105  
  
### 更正此错误  
  
-   从 `Get` 语句中删除访问修饰符。 它代表整个 `ReadOnly` 属性，并且该属性不能有两个访问级别。  
  
## 请参阅  
 [Property 过程](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [如何：声明具有混合访问级别的属性](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)
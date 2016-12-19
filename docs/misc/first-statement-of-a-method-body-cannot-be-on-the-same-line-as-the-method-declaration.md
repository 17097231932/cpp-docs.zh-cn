---
title: "方法体的第一条语句和方法声明不能位于同一行。 | Microsoft Docs"
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
  - "vbc30040"
  - "bc30040"
helpviewer_keywords: 
  - "BC30040"
ms.assetid: 27df3488-de77-499d-b9a6-08037d540cb0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法体的第一条语句和方法声明不能位于同一行。
一个 `Function`、`Sub`、`Get`、`Set` 或 `Property` 语句在源代码行上必须是独立的。  
  
 **错误 ID：**BC30040  
  
### 更正此错误  
  
1.  删除过程声明前面的所有行标签。  
  
2.  将过程声明前面的所有语句移动到上一个源代码行中。  
  
3.  将过程声明后面的所有语句移动到下一个源代码行中。  
  
## 请参阅  
 [过程](../Topic/Procedures%20in%20Visual%20Basic.md)   
 [如何：标记语句](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)
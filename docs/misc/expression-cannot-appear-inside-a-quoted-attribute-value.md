---
title: "带引号的特性值内不能出现表达式 | Microsoft Docs"
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
  - "bc31155"
  - "vbc31155"
helpviewer_keywords: 
  - "BC31155"
ms.assetid: ed3e618e-de94-4e4e-afaf-72b11073fb1d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 带引号的特性值内不能出现表达式
带引号的特性值内不能出现表达式。 请尝试删除引号。  
  
 XML 文本的特性值中的嵌入式表达式包含在引号中。  
  
 **错误 ID：**BC31155  
  
### 更正此错误  
  
-   从特性值中删除分隔引号。 下面是一个示例：  
  
    ```vb#  
    ' Generates an error. Dim elem = <outer attr="<%= value %>" /> ' Does not generate an error. Dim elem = <outer attr=<%= value %> />  
    ```  
  
## 请参阅  
 [XML 中的嵌入式表达式](../Topic/Embedded%20Expressions%20in%20XML%20\(Visual%20Basic\).md)   
 [XML 文本](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)
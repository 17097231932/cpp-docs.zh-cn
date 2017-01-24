---
title: "嵌入表达式的开头应有“%=” | Microsoft Docs"
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
  - "vbc31179"
  - "bc31179"
helpviewer_keywords: 
  - "BC31179"
ms.assetid: 20b0382e-1744-47e4-84e1-7fc926cbc4df
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 嵌入表达式的开头应有“%=”
嵌入表达式的开始标识符 `<%=` 未进行正确编码。 注意，不能在 XML 元素文本的名称中使用百分号字符 \(%\)。  
  
 **错误 ID：**BC31179  
  
### 更正此错误  
  
-   确保将嵌入表达式的开始标识符编码为 `<%=`。  
  
## 请参阅  
 [XML 中的嵌入式表达式](../Topic/Embedded%20Expressions%20in%20XML%20\(Visual%20Basic\).md)   
 [XML 文本](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)
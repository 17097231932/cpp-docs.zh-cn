---
title: "无法将类型“type1”转换为“type2” | Microsoft Docs"
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
  - "bc31193"
  - "vbc31193"
helpviewer_keywords: 
  - "BC31193"
ms.assetid: f25a9f5b-7741-4cd6-b85a-b19037ed8e49
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法将类型“type1”转换为“type2”
无法将类型“type1”转换为“type2”。 可使用“Value”属性来获取“parentElement”的第一个元素的字符串值。  
  
 已尝试将 XML 文本隐式强制转换为特定类型。 XML 文本不能隐式强制转换为指定类型。  
  
 **错误 ID：**BC31193  
  
### 更正此错误  
  
-   使用 XML 文本的 `Value` 属性来将其值作为 `String` 引用。 使用 `CType` 函数、另一个类型转换函数，或 <xref:System.Convert> 类将值强制转换为指定类型。  
  
## 请参阅  
 <xref:System.Convert>   
 [在 Visual Basic 中访问 XML](../Topic/Accessing%20XML%20in%20Visual%20Basic.md)   
 [类型转换函数](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)   
 [XML 文本](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)
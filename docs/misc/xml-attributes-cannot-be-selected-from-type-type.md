---
title: "无法从类型“type”选择 XML 特性 | Microsoft Docs"
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
  - "bc36808"
  - "vbc36808"
helpviewer_keywords: 
  - "BC36808"
ms.assetid: 76b2605c-3d9b-4e56-ba3f-99c60c668290
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法从类型“type”选择 XML 特性
已针对不属于类型 <xref:System.Xml.Linq.XElement> or `IEnumerable(Of XElement)` 的对象引用了一个 XML 特性。 有关更多信息，请参见[XML 特性轴属性](../Topic/XML%20Attribute%20Axis%20Property%20\(Visual%20Basic\).md)。  
  
```vb#  
' Generates an error. Dim var = "sample text".@attr  
```  
  
 **错误 ID：**BC36808  
  
### 更正此错误  
  
-   确保正在引用其特性的对象被强类型化为 <xref:System.Xml.Linq.XElement> 或 `IEnumerable(Of XElement)`。 下面是一个示例：  
  
    ```vb#  
    Dim elem As XElement = <root attr="value"/> Dim var = elem.@attr  
    ```  
  
## 请参阅  
 [XML 特性轴属性](../Topic/XML%20Attribute%20Axis%20Property%20\(Visual%20Basic\).md)   
 [XML 轴属性](../Topic/XML%20Axis%20Properties%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)
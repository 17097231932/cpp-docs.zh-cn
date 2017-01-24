---
title: "除非括在括号中，否则 XML 文本不能显示在此处 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31198"
  - "vbc31198"
helpviewer_keywords: 
  - "BC31198"
ms.assetid: 97b16076-39ff-430a-9c65-073d01bcb08e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 除非括在括号中，否则 XML 文本不能显示在此处
在对于 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 编译器不明确的位置处，在表达式中使用了 XML 文本声明。 也就是说，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 编译器无法确定小于字符 \(\<\) 是旨在作为比较运算符还是 XML 文本的起始字符。 以下代码提供了一个示例：  
  
 \[Visual Basic\]  
  
```  
' Generates an error. Dim queryResult = From element In elements _ Where <sample>Value</sample> = "Value" _ Select element  
```  
  
 **错误 ID：**BC31198  
  
### 更正此错误  
  
-   将 XML 文本声明括在括号内，如下面的示例所示：  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where (<sample> Value</sample>) = "Value" _ Select element  
    ```  
  
-   修改代码以引用现有 XML 文本，如下面的示例所示：  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where e.<sample>.Value = "Value" _ Select element  
    ```  
  
## 请参阅  
 [XML 文本](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML 轴属性](../Topic/XML%20Axis%20Properties%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)
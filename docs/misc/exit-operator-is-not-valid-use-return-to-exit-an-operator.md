---
title: "“Exit Operator”无效。 使用“Return”退出运算符 | Microsoft Docs"
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
  - "bc33008"
  - "vbc33008"
helpviewer_keywords: 
  - "BC33008"
ms.assetid: 8c44456b-8fd2-4168-ad8c-b6da129242ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Exit Operator”无效。 使用“Return”退出运算符
`Operator` 过程中出现 `Exit Operator` 语句。  
  
 必须使用 [Return 语句](../Topic/Return%20Statement%20\(Visual%20Basic\).md) 从 `Operator` 过程进行返回。[Exit 语句](../Topic/Exit%20Statement%20\(Visual%20Basic\).md) 不接受 `Operator` 关键字，`End Operator` 语句不会将控制权返回给调用代码。  
  
 **错误 ID：**BC33008  
  
### 更正此错误  
  
-   用 `Return` 语句替换 `Exit Operator` 语句。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
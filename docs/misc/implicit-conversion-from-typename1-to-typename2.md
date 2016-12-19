---
title: "从“&lt;typename1&gt;”隐式转换为“&lt;typename2&gt;” | Microsoft Docs"
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
  - "vbc42016"
  - "BC42016"
helpviewer_keywords: 
  - "BC42016"
ms.assetid: 7dabaab0-8258-4c17-927f-28e61f50bd3a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 从“&lt;typename1&gt;”隐式转换为“&lt;typename2&gt;”
表达式或赋值语句采用某种数据类型的值，并将其转换为另一种类型。 由于未使用任何转换关键字，因此转换是*隐式*的。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的信息，请参见 [在 Visual Basic 中配置警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC42016  
  
### 更正此错误  
  
-   如有可能，请使用数据类型相同的值，这样 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 将无需进行任何转换。  
  
-   使用 `CType` 或其他转换关键字之一，以使转换成为*显式*的。  
  
## 请参阅  
 [隐式转换和显式转换](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)   
 [类型转换函数](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)
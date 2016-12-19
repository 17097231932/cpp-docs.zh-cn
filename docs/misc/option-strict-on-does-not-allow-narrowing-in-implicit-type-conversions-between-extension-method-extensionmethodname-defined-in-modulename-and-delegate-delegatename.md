---
title: "Option Strict On 不允许对“&lt;modulename&gt;”中定义的扩展方法“&lt;extensionmethodname&gt;”和委托“&lt;delegatename&gt;”之间的隐式类型转换进行收缩。 | Microsoft Docs"
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
  - "bc36709"
  - "vbc36709"
helpviewer_keywords: 
  - "BC36709"
ms.assetid: 95d8c833-3525-411b-98e8-b7d3f61f75c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 不允许对“&lt;modulename&gt;”中定义的扩展方法“&lt;extensionmethodname&gt;”和委托“&lt;delegatename&gt;”之间的隐式类型转换进行收缩。
启用 `Option Strict` 时，你不能将委托中的参数数据类型收缩转换为分配给该委托类型的变量的扩展方法的相应参数。 委托参数的数据类型必须扩大到扩展方法的数据类型。  
  
 **错误 ID：**BC36709  
  
### 更正此错误  
  
-   更改委托或扩展方法中的参数的数据类型，使其存在所需的扩大关系。  
  
## 请参阅  
 [扩展方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [宽松委托转换](../Topic/Relaxed%20Delegate%20Conversion%20\(Visual%20Basic\).md)   
 [委托](../Topic/Delegates%20\(Visual%20Basic\).md)   
 [扩大转换和收缩转换](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [不在生成中：委托和 AddressOf 运算符](http://msdn.microsoft.com/zh-cn/7b2ed932-8598-4355-b2f7-5cedb23ee86f)
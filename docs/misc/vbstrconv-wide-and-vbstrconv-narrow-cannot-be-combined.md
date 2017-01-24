---
title: "不能组合 VbStrConv.Wide 和 VbStrConv.Narrow | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_IllegalWideNarrow"
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能组合 VbStrConv.Wide 和 VbStrConv.Narrow
你的应用程序尝试组合 `VbStrConv` 枚举成员 `Wide` 和 `Narrow`，而它们是互斥的。  
  
### 更正此错误  
  
1.  删除 `VbStrConv.Wide` 或 `VbStrConv.Narrow`。  
  
## 请参阅  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv 枚举](http://msdn.microsoft.com/zh-cn/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [介绍基于 .NET Framework 的国际应用程序](../Topic/Introduction%20to%20International%20Applications%20Based%20on%20the%20.NET%20Framework.md)
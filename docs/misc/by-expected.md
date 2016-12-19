---
title: "应为 &quot;By&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36605"
  - "bc36605"
helpviewer_keywords: 
  - "BC36605"
ms.assetid: d0397b6e-bfc2-400c-92fc-efe82036cfdb
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 应为 &quot;By&quot;
已经指定 `Order By` 或 `Group By` 子句，但其中没有 `By` 关键字。  
  
 **错误 ID：**BC36605  
  
### 更正此错误  
  
1.  将 `By` 关键字添加到 `Order By` 或 `Group By` 子句中。 下面是一个示例：  
  
    ```vb#  
    Dim customersByCountry = From cust In customers _  
                             Order By cust.Country, cust.City _  
                             Group By CountryName = cust.Country _  
                             Into RegionalCustomers = Group, Count() _  
                             Order By CountryName  
    ```  
  
## 请参阅  
 [如何：排序查询结果](../Topic/How%20to:%20Sort%20Query%20Results%20by%20Using%20LINQ%20\(Visual%20Basic\).md)   
 [Order By 子句](../Topic/Order%20By%20Clause%20\(Visual%20Basic\).md)   
 [Group By 子句](../Topic/Group%20By%20Clause%20\(Visual%20Basic\).md)   
 [Visual Basic 中的 LINQ 简介](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)
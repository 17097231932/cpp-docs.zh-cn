---
title: "编译器错误 CS1507 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1507"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1507"
ms.assetid: e1be3aba-81dc-4f65-87a4-d3f90b82dc7d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1507
生成模块时，无法链接资源文件“file”  
  
 在同一编译中使用了 [\/linkresource](../Topic/-linkresource%20\(C%23%20Compiler%20Options\).md) 和 [\/target: module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)，不允许这样做。 例如，下面的选项将生成 CS1507：  
  
```  
csc /linkresource:rf.resource /target:module in.cs  
```  
  
 但允许嵌入资源 \([\/resource](../Topic/-resource%20\(C%23%20Compiler%20Options\).md)\)。
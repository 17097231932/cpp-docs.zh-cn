---
title: "编译器错误 CS1508 | Microsoft Docs"
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
  - "CS1508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1508"
ms.assetid: 979bc615-58ce-49f8-ba73-e6cf57c56418
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1508
此程序集中已使用了资源标识符“identifier”  
  
 在编译时，将相同标识符 \(***identifier***\) 传递给了两个或更多 [\/resource](../Topic/-resource%20\(C%23%20Compiler%20Options\).md) 或 [\/linkresource](../Topic/-linkresource%20\(C%23%20Compiler%20Options\).md) 编译器选项。  
  
 例如，下面的选项生成 CS1508：  
  
```  
/resource:anyfile.bmp,DuplicatIdent /linkresource:a.bmp,DuplicatIdent  
```
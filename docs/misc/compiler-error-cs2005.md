---
title: "编译器错误 CS2005 | Microsoft Docs"
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
  - "CS2005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2005"
ms.assetid: 03535d2a-ae30-4272-ab45-e277df5ee8e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS2005
“选项”选项缺少文件规范  
  
 只指定了部分[编译器选项](../Topic/C%23%20Compiler%20Options.md)。  
  
 例如，使用 [\/recurse](../Topic/-recurse%20\(C%23%20Compiler%20Options\).md) 时，必须指定要搜索的文件：**\/recurse:***filename***.cs**。  
  
## 示例  
 下面的示例生成 CS2005。  
  
```  
// CS2005.cs // compile with: /recurse: // CS2005 expected class x { public static void Main() {} }  
```
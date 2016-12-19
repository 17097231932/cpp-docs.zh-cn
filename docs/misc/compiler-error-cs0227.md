---
title: "编译器错误 CS0227 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0227"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0227"
ms.assetid: b595a1c9-8204-4ff7-a1d0-258b0b1d6ff7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0227
不安全代码只会在使用 \/unsafe 编译的情况下出现  
  
 如果源的代码包含 [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md) 关键字，则还必须使用 [\/unsafe](../Topic/-unsafe%20\(C%23%20Compiler%20Options\).md) 编译器选项。 有关更多信息，请参见[不安全代码和指针](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)。  
  
 若要在 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 中设置不安全选项，单击主菜单中的“项目”，选择“生成”窗格，然后勾选“允许不安全代码”框。  
  
 编译不含 **\/unsafe** 时，下面的示例将生成 CS0227：  
  
```  
// CS0227.cs public class MyClass { unsafe public static void Main()   // CS0227 { } }  
```  
  
## 请参阅  
 [C\# Compiler Errors](../Topic/C%23%20Compiler%20Errors.md)
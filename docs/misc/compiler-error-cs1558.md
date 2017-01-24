---
title: "编译器错误 CS1558 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1558"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1558"
ms.assetid: ee603d66-007e-4782-9285-7ff031975f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1558
“class”没有合适的静态 Main 方法  
  
 [\/main](../Topic/-main%20\(C%23%20Compiler%20Options\).md) 编译器选项指定了一个在其中查找 **Main** 方法的类。 但是，[Main](../Topic/Main\(\)%20and%20Command-Line%20Arguments%20\(C%23%20Programming%20Guide\).md) 方法未正确定义。  
  
 以下示例由于无效的返回类型而生成 CS1558。  
  
```  
// CS1558.cs // compile with: /main:MyNamespace.MyClass namespace MyNamespace { public class MyClass { public static float Main() { return 0.0; // CS1558 because the return type is a float. } } }  
```
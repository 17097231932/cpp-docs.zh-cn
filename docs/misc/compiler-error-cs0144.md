---
title: "编译器错误 CS0144 | Microsoft Docs"
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
  - "CS0144"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0144"
ms.assetid: 3904cab1-05bd-44ec-81d0-e36c5656f742
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0144
无法创建抽象类或接口“interface”的实例  
  
 无法创建 [abstract](../Topic/abstract%20\(C%23%20Reference\).md) 类或 [interface](../Topic/interface%20\(C%23%20Reference\).md) 的实例。 有关更多信息，请参见[接口](../Topic/Interfaces%20\(C%23%20Programming%20Guide\).md)。  
  
 下面的示例生成 CS0144：  
  
```  
// CS0144.cs interface MyInterface { } public class MyClass { public static void Main() { MyInterface myInterface = new MyInterface ();   // CS0144 } }  
```
---
title: "注册服务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "服务, 注册"
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# 注册服务
若要支持按需加载，服务提供商必须用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 注册其全球服务。  
  
 在开发期间，托管服务提供商通过将特性添加到包的源代码，然后在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE中生成包，从而注册服务和服务重写。 这会在生成的程序集上运行 RegPkg.exe 实用程序，注册包并为部署做准备。 有关更多信息，请参见[如何：注册服务](../misc/how-to-register-a-service.md)。  
  
 非托管服务提供商必须用系统注册表中的服务节或服务重写节中的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 注册它们提供的服务。 下面的.reg 文件片断演示注册服务 SVsTextManager 的方式：  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
```  
  
 在上面的示例中，版本号是版本 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]（如 7.1 或 8.0），注册表项 {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} 是 SVsTextManager 服务的服务标识符 \(SID\)，默认值 {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} 是提供服务的文本管理器 VSPackage 的包 GUID。  
  
## 远程服务和后台线程  
 你提供的服务不会自动在远程方式下可用，或供后台线程使用。 若要使其可用，必须生成并注册类型库。  
  
 通过使用 Visual Studio 库 \(VSL\) 的非托管代码，可以通过这种方式注册类型库：  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE #include <VSLPackageDllEntryPoints.cpp>  
```  
  
 通过托管代码，可以添加如下生成后步骤：  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## 请参阅  
 [使用并提供服务](../Topic/Using%20and%20Providing%20Services.md)   
 [服务基础知识](../Topic/Service%20Essentials.md)
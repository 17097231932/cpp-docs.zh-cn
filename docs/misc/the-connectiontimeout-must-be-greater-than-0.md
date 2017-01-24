---
title: "ConnectionTimeout 必须大于 0 | Microsoft Docs"
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
  - "vbrNetwork_BadConnectionTimeout"
ms.assetid: 15ac09a7-47f0-44f3-9e84-5bd10bd07450
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ConnectionTimeout 必须大于 0
使用[My.Computer.Network 对象](../Topic/My.Computer.Network%20Object.md)上载和下载的文件时，必须指定一个大于 `0` 的 `connectionTimeout`。  
  
### 更正此错误  
  
-   提供一个大于 `0` 的 `connectionTimeout`。  
  
## 请参阅  
 [My.Computer.Network.UploadFile 方法](http://msdn.microsoft.com/zh-cn/5505ea3e-3dbd-460b-9f8f-62c84c0a4de6)   
 [My.Computer.Network.DownloadFile 方法](http://msdn.microsoft.com/zh-cn/aeb7ed8f-1ac9-4242-ae57-9f35914eb329)   
 [如何：上载文件](../Topic/How%20to:%20Upload%20a%20File%20in%20Visual%20Basic.md)   
 [如何：下载文件](../Topic/How%20to:%20Download%20a%20File%20in%20Visual%20Basic.md)   
 [使用 Visual Basic 在 .NET Framework 中执行的网络操作](http://msdn.microsoft.com/zh-cn/c5379021-44ef-4d6a-acf5-e951fdcab6b2)
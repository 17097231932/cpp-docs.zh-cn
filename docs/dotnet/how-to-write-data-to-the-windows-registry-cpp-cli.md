---
title: 如何： 将数据写入到 Windows 注册表 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: 3d40b978-4baa-4779-bfe3-47e2917b757f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 304bc224be8776c9793af07283c6a5697a4e49eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-data-to-the-windows-registry-ccli"></a>如何：将数据写入 Windows 注册表 (C++/CLI)
下面的代码示例使用<xref:Microsoft.Win32.Registry.CurrentUser>密钥创建的可写实例<xref:Microsoft.Win32.RegistryKey>类对应于**软件**密钥。 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>方法然后用于创建新的密钥和所添加的键/值对。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
```  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
## <a name="remarks"></a>备注  
 你可以使用.NET Framework 来访问与注册表<xref:Microsoft.Win32.Registry>和[RegistryKey](https://msdn.microsoft.com/en-us/library/microsoft.win32.registrykey.aspx)中定义的类，该类都<xref:Microsoft.Win32>命名空间。 **注册表**类是静态的实例的容器<xref:Microsoft.Win32.RegistryKey>类。 每个实例表示的根注册表节点。 两个实例<xref:Microsoft.Win32.Registry.ClassesRoot>， <xref:Microsoft.Win32.Registry.CurrentConfig>， <xref:Microsoft.Win32.Registry.CurrentUser>， <xref:Microsoft.Win32.Registry.LocalMachine>，和<xref:Microsoft.Win32.Registry.Users>。  
  
## <a name="see-also"></a>请参阅  
 [如何： 从 Windows 注册表中读取数据 (C + + /cli CLI)](../dotnet/how-to-read-data-from-the-windows-registry-cpp-cli.md)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
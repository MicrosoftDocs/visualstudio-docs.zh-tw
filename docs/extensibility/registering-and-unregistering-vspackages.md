---
title: 註冊及取消註冊 Vspackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b59a62aba3ffa189ea739061c51a04065882d3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016833"
---
# <a name="register-and-unregister-vspackages"></a>註冊和取消註冊 Vspackage
您可以使用屬性來註冊 VSPackage，但  
  
## <a name="register-a-vspackage"></a>註冊 VSPackage  
 您可以使用屬性來控制 managed Vspackage 的註冊。 所有的註冊資訊包含在 *.pkgdef*檔案。 如需有關檔案為基礎的註冊的詳細資訊，請參閱[CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)。  
  
 下列程式碼示範如何使用標準的註冊屬性來註冊 VSPackage。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{
    // ...
}  
```  
  
## <a name="unregister-an-extension"></a>取消登錄延伸模組  
 如果您已進行實驗，具有許多不同的 Vspackage，而且想要移除的實驗執行個體，您就可以執行**重設**命令。 尋求**重設 Visual Studio 的實驗執行個體**在您的電腦，[開始] 頁面上，或從命令列執行此命令：  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 如果您想要解除安裝的擴充功能，您已安裝 Visual Studio 的開發執行個體上，請移至**工具** > **擴充功能和更新**，尋找擴充功能，，按一下  **解除安裝**。  
  
 如果基於某些原因，這些方法都不成功在解除安裝擴充功能，可以取消註冊 VSPackage 組件，從命令列，如下所示：  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>使用自訂註冊屬性來登錄延伸模組  
  
在某些情況下，您可能需要建立新的註冊屬性，您的擴充功能。 若要加入新的登錄機碼，或將新的值加入至現有的索引鍵，您可以使用註冊屬性。 新的屬性必須衍生自<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>，而且它必須覆寫<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>和<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>方法。  
  
### <a name="create-a-custom-attribute"></a>建立自訂屬性  
  
下列程式碼示範如何建立新的註冊屬性。  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
public class CustomRegistrationAttribute : RegistrationAttribute  
{  
}  
```  
  
 <xref:System.AttributeUsageAttribute>屬性類別上用來指定與屬性，是否就可以使用一次以上，以及是否可繼承的程式元素 （類別、 方法等）。  
  
### <a name="create-a-registry-key"></a>建立登錄機碼  
  
下列程式碼，建立自訂的屬性**自訂**vspackage 所登錄機碼下的子機碼。  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
```  
  
### <a name="create-a-new-value-under-an-existing-registry-key"></a>建立新的值，在現有的登錄機碼下  
  
您可以新增自訂值到現有的金鑰。 下列程式碼示範如何將新的值新增至 VSPackage 註冊金鑰。  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)

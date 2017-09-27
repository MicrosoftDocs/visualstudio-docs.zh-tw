---
title: "註冊及取消註冊 Vspackage |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 312c06295492ac9bd1136ea7de9a0399f247c365
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="registering-and-unregistering-vspackages"></a>註冊和取消登錄 Vspackage
您可以使用屬性來註冊 VSPackage，但  
  
## <a name="registering-a-vspackage"></a>註冊 VSPackage  
 您可以使用屬性來控制 managed Vspackage 的註冊。 所有的登錄資訊都包含.pkgdef 檔中。 多個檔案為基礎的登錄的詳細資訊，請參閱[CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)。  
  
 下列程式碼會示範如何使用標準註冊屬性來註冊您的 VSPackage。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>取消註冊擴充功能  
 如果您已實驗許多不同的 Vspackage，而且想要移除的實驗執行個體，您可以只執行**重設**命令。 尋找**重設 Visual Studio 的實驗執行個體**您的電腦，[開始] 頁面上，或從命令列執行此命令：  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 如果您想要解除安裝擴充功能，您已安裝 Visual Studio 的開發執行個體上，請移至**工具 / 擴充功能和更新**，尋找擴充功能，然後按一下**解除安裝**。  
  
 如果基於某些原因，這些方法皆未成功在解除安裝擴充功能，可取消 VSPackage 組件，從命令列，如下所示：  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>使用自訂註冊屬性來登錄延伸模組  
  
在某些情況下，您可能需要建立新的註冊屬性，您的擴充功能。 加入新的登錄機碼，或將新值加入至現有的索引鍵，您可以使用登錄屬性。 新的屬性必須衍生自<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>，而且必須覆寫<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>和<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>方法。  
  
### <a name="creating-a-custom-attribute"></a>建立自訂屬性  
  
下列程式碼會示範如何建立新的登錄屬性。  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 <xref:System.AttributeUsageAttribute>屬性類別上用來指定屬性相關、 是否才能使用一次以上，以及是否可繼承的程式元素 （類別、 方法等）。  
  
### <a name="creating-a-registry-key"></a>建立登錄機碼  
  
下列程式碼，建立自訂屬性**自訂**之 VSPackage 所登錄機碼下的子機碼。  
  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>建立現有的登錄機碼下的新值  
  
您可以將自訂值加入到現有的金鑰。 下列程式碼會示範如何將新值加入至 VSPackage 的登錄機碼。  
  
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

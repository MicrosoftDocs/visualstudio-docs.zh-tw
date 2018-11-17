---
title: 載入 Vspackage |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e351f49ea3e9579202e21868361e5d6f3d53b8fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753873"
---
# <a name="loading-vspackages"></a>載入 VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage 會載入到 Visual Studio 中，只有需要其功能時，只有。 比方說，Visual Studio 使用專案 factory 或 VSPackage 實作的服務時，會載入 VSPackage。 這項功能稱為延遲的載入，這會盡可能以改善效能。  
  
> [!NOTE]
>  Visual Studio 可以判斷特定的 VSPackage 資訊，例如 VSPackage 提供，而不必載入 VSPackage 的命令。  
  
 Vspackage 可以例如設定自動載入在特定的使用者介面 (UI) 內容中，開啟方案時。 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>屬性會設定此內容。  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>自動載入 VSPackage 中特定的內容  
  
-   新增`ProvideAutoLoad`屬性加入 VSPackage 屬性：  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     請參閱列舉的欄位<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>如 UI 內容和其 GUID 值的清單。  
  
-   在設定的中斷點<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。  
  
-   建置 VSPackage，並開始偵錯。  
  
-   載入方案或建立一個。  
  
     VSPackage 載入，並在中斷點停止。  
  
## <a name="forcing-a-vspackage-to-load"></a>強制載入 VSPackage  
 在某些情況下 VSPackage 可能必須強制另一個要載入的 VSPackage。 比方說，輕量級 VSPackage 可能會載入較大的 VSPackage，不是 CMDUIContext 可用的內容中。  
  
 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>方法，以強制載入 VSPackage。  
  
-   插入此程式碼<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>的 VSPackage，強制載入的另一個 VSPackage 的方法：  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     初始化 VSPackage 時，它會強制`PackageToBeLoaded`載入。  
  
     強制載入不應該用於 VSPackage 通訊。 使用[使用和提供服務](../extensibility/using-and-providing-services.md)改。  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>使用自訂屬性來註冊 VSPackage  
 在某些情況下，您可能需要建立新的註冊屬性，您的擴充功能。 若要加入新的登錄機碼，或將新的值加入至現有的索引鍵，您可以使用註冊屬性。 新的屬性必須衍生自<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>，而且它必須覆寫<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>和<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>方法。  
  
## <a name="creating-a-registry-key"></a>建立登錄機碼  
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
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>建立現有的登錄機碼下的新值  
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


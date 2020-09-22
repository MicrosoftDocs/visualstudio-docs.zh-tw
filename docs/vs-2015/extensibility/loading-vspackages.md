---
title: 正在載入 Vspackage |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838945"
---
# <a name="loading-vspackages"></a>載入 VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage 只有在需要它們的功能時，才會載入 Visual Studio。 例如，當 Visual Studio 使用專案 factory 或 VSPackage 所執行的服務時，就會載入 VSPackage。 這項功能稱為延遲載入，會盡可能用來改善效能。  
  
> [!NOTE]
> Visual Studio 可以判斷特定的 VSPackage 資訊，例如 VSPackage 提供的命令，而不需要載入 VSPackage。  
  
 Vspackage 可以設定為特定使用者介面中的自動載入， (UI) 內容，例如開啟方案時。 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>屬性會設定此內容。  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>在特定內容中自動載入功能 VSPackage  
  
- 將 `ProvideAutoLoad` 屬性新增至 VSPackage 屬性：  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>如需 UI 內容和其 GUID 值清單的詳細資料，請參閱的列舉欄位。  
  
- 在方法中設定中斷點 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 。  
  
- 建立 VSPackage 並開始進行調試。  
  
- 載入解決方案或建立一個。  
  
     VSPackage 會在中斷點載入並停止。  
  
## <a name="forcing-a-vspackage-to-load"></a>強制載入 VSPackage  
 在某些情況下，VSPackage 可能必須強制載入另一個 VSPackage。 例如，輕量 VSPackage 可能會在無法以 CMDUICoNtext 形式提供的內容中載入較大的 VSPackage。  
  
 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> 方法強制載入 VSPackage。  
  
- 將此程式碼插入 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> VSPackage 的方法中，以強制載入另一個 VSPackage：  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     當 VSPackage 初始化時，它將會強制 `PackageToBeLoaded` 載入。  
  
     不應使用強制載入來進行 VSPackage 通訊。 改為使用 [和提供服務](../extensibility/using-and-providing-services.md) 。  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>使用自訂屬性來註冊 VSPackage  
 在某些情況下，您可能需要為您的延伸模組建立新的註冊屬性。 您可以使用註冊屬性來新增新的登錄機碼，或將新的值新增至現有的金鑰。 新的屬性必須衍生自 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ，而且必須覆寫 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 和 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 方法。  
  
## <a name="creating-a-registry-key"></a>建立登錄機碼  
 在下列程式碼中，自訂屬性會在要註冊的 VSPackage 機碼底下建立 **自訂** 子機碼。  
  
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
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>在現有的登錄機碼下建立新的值  
 您可以將自訂值新增至現有的索引鍵。 下列程式碼示範如何將新值新增至 VSPackage 註冊金鑰。  
  
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
 [VSPackages](../extensibility/internals/vspackages.md)

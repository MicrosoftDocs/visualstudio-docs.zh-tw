---
title: "載入 Vspackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自動載入 Vspackage"
  - "VSPackage, 載入"
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 載入 Vspackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

只有需要其功能時，只有 VSPackages 會載入 Visual Studio。 比方說，Visual Studio 會使用專案工廠或 VSPackage 實作的服務時，會載入 VSPackage。 這項功能稱為延遲的載入，盡可能使用來改善效能。  
  
> [!NOTE]
>  Visual Studio 可以判斷特定的 VSPackage 資訊，例如 VSPackage 提供，而不載入 VSPackage 的命令。  
  
 VSPackages 可以例如設定自動載入在特定的使用者介面 \(UI\) 內容中，開啟方案時。<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 屬性來設定此內容。  
  
### 自動載入 VSPackage 中特定的內容  
  
-   新增 `ProvideAutoLoad` 屬性設定為 VSPackage 屬性︰  
  
    ```c#  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     請參閱列舉的欄位 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> UI 內容及其 GUID 值的清單。  
  
-   在設定中斷點 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
-   建置 VSPackage 並開始偵錯。  
  
-   載入方案或建立一個。  
  
     VSPackage 載入，並在中斷點停止。  
  
## 強制載入 VSPackage  
 在某些情況下 VSPackage 可能強制另一個要載入的 VSPackage。 例如，輕量型 VSPackage 可能會載入大 VSPackage 中不是 CMDUIContext 可用的內容。  
  
 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> 方法，以強制載入 VSPackage。  
  
-   插入此程式碼至 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> VSPackage 可強制另一個載入 VSPackage 的方法︰  
  
    ```c#  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     當初始化 VSPackage 時，它會強制 `PackageToBeLoaded` 載入。  
  
     強制載入不應該用於 VSPackage 通訊。 請改用 [使用並提供服務](../extensibility/using-and-providing-services.md)。  
  
## 若要註冊的 VSPackage 中使用自訂屬性  
 在某些情況下，您可能需要建立新的註冊屬性，您的擴充功能。 您可以使用註冊屬性，加入新的登錄機碼，或將新值加入至現有的索引鍵。 新的屬性必須衍生自 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, ，必須覆寫和 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 和 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 方法。  
  
## 建立登錄機碼  
 下列程式碼，建立自訂屬性 **自訂** VSPackage 所註冊之機碼下的子機碼。  
  
```c#  
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
  
## 建立現有的登錄機碼下的新值  
 您可以新增自訂值到現有的金鑰。 下列程式碼示範如何將新值加入至 VSPackage 註冊金鑰。  
  
```c#  
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
  
## 請參閱  
 [Vspackage](../extensibility/internals/vspackages.md)
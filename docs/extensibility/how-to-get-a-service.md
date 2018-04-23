---
title: 如何： 取得服務 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cdf5bd925a034a64d8605c675704a0e894308ea3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-get-a-service"></a>如何： 取得服務
您通常需要取得 Visual Studio 服務來存取不同的功能。 一般情況下，Visual Studio 服務提供您可以使用的一個或多個介面。 您可以從 VSPackage 取得大部分的服務。  
  
 任何衍生自的 VSPackage<xref:Microsoft.VisualStudio.Shell.Package>和，已正確地決定位置的任何全域服務可以要求。 因為在封裝類別實作<xref:System.IServiceProvider>，衍生自封裝任何 VSPackage 也是服務提供者。  
  
 載入 Visual Studio <xref:Microsoft.VisualStudio.Shell.Package>，它會傳遞<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>初始化期間的方法。 這稱為*地點*VSPackage。 在封裝類別包裝此服務提供者，並提供<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>方法來取得服務。  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>從初始化 VSPackage 取得服務  
  
1.  每個 Visual Studio 擴充功能開頭 VSIX 部署專案，以將包含延伸模組資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 專案，名為`GetServiceExtension`。 您可以找到 VSIX 專案範本，在**新專案**對話方塊底下**Visual C# > 擴充性**。  
  
2.  現在，加入名為的自訂命令項目範本**GetServiceCommand**。 在**加入新項目**對話方塊中，移至**Visual C# > 擴充性**選取**自訂命令**。 在**名稱**視窗的底部欄位中，將命令檔名稱變更為**GetServiceCommand.cs**。 如需有關如何建立自訂的命令，[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  在 GetServiceCommand.cs，移除 MenuItemCommand 方法的主體，並加入下列程式碼：  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     這個程式碼取得 SVsActivityLog 服務，並將它轉換成<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面，可用來寫入活動記錄檔。 如需範例，請參閱[How to： 使用活動記錄檔](../extensibility/how-to-use-the-activity-log.md)。  
  
4.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
5.  在實驗性執行個體的 工具 功能表上尋找**叫用 GetServiceCommand**  按鈕。 當您按一下這個按鈕時，您應該會看到訊息方塊，表示**找到活動記錄檔服務。**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>從工具視窗或控制項容器取得服務  
 有時候您可能需要從工具視窗取得服務或控制未設置，否則就不知道您想要的服務的服務提供者已決定位置的容器。 例如，您可以寫入活動記錄檔從控制項中。  
  
 靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法依賴快取的服務提供者，它會初始化任何 VSPackage 衍生自第一次<xref:Microsoft.VisualStudio.Shell.Package>設置。  
  
 因為之前設置 VSPackage 呼叫 VSPackage 建構函式，就無法從 VSPackage 建構函式通常使用 全域服務。 請參閱[如何： 疑難排解服務](../extensibility/how-to-troubleshoot-services.md)的因應措施。  
  
 以下是方法的範例的工具視窗或其他非 VSPackage 項目中取得服務。  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>從 DTE 物件取得服務  
 您也可以取得從服務<xref:EnvDTE.DTEClass>物件。 不過，您必須取得 DTE 物件做為服務從 VSPackage 或藉由呼叫靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。  
  
 DTE 物件實作<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>，您可以用來查詢服務，方法是使用<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>。  
  
 以下是如何從 DTE 物件取得服務。  
  
```csharp  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何： 提供的服務](../extensibility/how-to-provide-a-service.md)   
 [使用並提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)
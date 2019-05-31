---
title: 作法：取得服務 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3da08f41566e5b6d2a501a9e020d589b85988016
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351939"
---
# <a name="how-to-get-a-service"></a>作法：取得服務

您通常需要取得 Visual Studio 服務，以存取不同的功能。 一般情況下，Visual Studio 服務提供您可以使用的一或多個介面。 您可以從 VSPackage 取得大部分的服務。

衍生自任何 VSPackage <xref:Microsoft.VisualStudio.Shell.Package> ，具有已正確地設置和可尋求任何全域服務。 因為`Package`類別會實作<xref:System.IServiceProvider>，衍生自任何 VSPackage`Package`也是服務提供者。

當 Visual Studio 會載入<xref:Microsoft.VisualStudio.Shell.Package>，它會傳遞<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>物件至<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>在初始化期間的方法。 這就叫做*地點*VSPackage。 `Package`類別會包裝此服務提供者，並提供<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>取得服務的方法。

## <a name="getting-a-service-from-an-initialized-vspackage"></a>從初始化的 VSPackage 中取得的服務

1. 每個 Visual Studio 擴充功能會開始使用 VSIX 部署專案，其中將包含的延伸模組資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 專案，名為`GetServiceExtension`。 您可以找到在 VSIX 專案範本**新的專案**藉由搜尋 「 vsix 」 的對話方塊。

2. 現在將新增名為的自訂命令項目範本**GetServiceCommand**。 在 **加入新項目**對話方塊中，移至**Visual C#**  > **擴充性**，然後選取**自訂命令**。 在 **名稱**視窗的底部欄位中，將命令的檔案名稱變更為*GetServiceCommand.cs*。 如需有關如何建立自訂命令[建立具有功能表命令的擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)

3. 在  *GetServiceCommand.cs*，移除主體`MenuItemCommand`方法並加入下列程式碼：

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    此程式碼取得 SVsActivityLog 服務，並將它轉換成<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面，可用來寫入活動記錄檔。 如需範例，請參閱[如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。

4. 建置此專案並開始偵錯。 實驗執行個體隨即出現。

5. 在 **工具** 功能表的實驗執行個體中，尋找**叫用 GetServiceCommand**  按鈕。 當您按一下此按鈕時，您應該會看到出現訊息方塊，指出**找到 「 活動記錄 」 服務。**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>從 工具視窗或控制項容器取得服務

有時候您可能需要從 工具視窗取得服務或控制未設置，否則就不知道您想要的服務的服務提供者已決定位置的容器。 比方說，您可能要從控制項內的活動記錄檔寫入。

靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法會初始化任何 VSPackage 衍生自第一次的快取的服務提供者需仰賴<xref:Microsoft.VisualStudio.Shell.Package>設置。

之前設置 VSPackage 呼叫 VSPackage 建構函式，因為全域服務都無法從 VSPackage 的建構函式通常使用。 請參閱[如何：疑難排解服務](../extensibility/how-to-troubleshoot-services.md)的因應措施。

以下是最好的工具視窗或其他非 VSPackage 項目中取得服務的範例。

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>從 DTE 物件取得服務

您也可以取得服務<xref:EnvDTE.DTEClass>物件。 不過，您必須取得 DTE 物件做為服務從 VSPackage 或藉由呼叫靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。

DTE 物件會實作<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>，您可以用來查詢服務，以使用<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>。

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

- [如何：提供服務](../extensibility/how-to-provide-a-service.md)
- [使用，並提供服務](../extensibility/using-and-providing-services.md)
- [服務的基本資訊](../extensibility/internals/service-essentials.md)
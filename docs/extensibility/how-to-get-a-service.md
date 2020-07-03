---
title: 如何：取得服務 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a401103112096a1089b59ba3733d19480f93e891
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905832"
---
# <a name="how-to-get-a-service"></a>如何：取得服務

您通常需要取得 Visual Studio 的服務，才能存取不同的功能。 一般來說，Visual Studio 服務會提供一或多個可供您使用的介面。 您可以從 VSPackage 取得大部分的服務。

衍生自 <xref:Microsoft.VisualStudio.Shell.Package> 且已正確放置的任何 VSPackage 都可以要求任何全域服務。 因為 `Package` 類別 <xref:System.IServiceProvider> 會執行，所以衍生自的任何 VSPackage `Package` 也是服務提供者。

當 Visual Studio 載入時 <xref:Microsoft.VisualStudio.Shell.Package> ，它會 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 在初始化期間將物件傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 方法。 這稱為*地點*VSPackage。 `Package`類別會包裝此服務提供者，並提供 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 取得服務的方法。

## <a name="getting-a-service-from-an-initialized-vspackage"></a>從初始化的 VSPackage 取得服務

1. 每個 Visual Studio 延伸模組都是以 VSIX 部署專案為開頭，其中會包含擴充功能資產。 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 名為的 VSIX 專案 `GetServiceExtension` 。 藉由搜尋「vsix」，您可以在 [**新增專案**] 對話方塊中尋找 VSIX 專案範本。

2. 現在，新增名為**GetServiceCommand**的自訂命令專案範本。 在 [**新增專案**] 對話方塊中，移至 [ **Visual c #** 擴充性]，  >  **Extensibility**然後選取 [**自訂命令**]。 在視窗底部的 [**名稱**] 欄位中，將命令檔名稱變更為*GetServiceCommand.cs*。 如需如何建立自訂命令的詳細資訊，請[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能

3. 在*GetServiceCommand.cs*中，移除方法的主體 `MenuItemCommand` ，並新增下列程式碼：

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    此程式碼會取得 SVsActivityLog 服務，並將它轉換成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 介面，可用來寫入活動記錄。 如需範例，請參閱[如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。

4. 建置此專案並開始偵錯。 實驗實例隨即出現。

5. 在實驗實例的 [**工具**] 功能表上，尋找 [叫用**GetServiceCommand** ] 按鈕。 當您按一下此按鈕時，您應該會看到一個訊息方塊，指出已**找到活動記錄服務。**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>從工具視窗或控制項容器取得服務

有時候，您可能需要從工具視窗或控制項容器中取得尚未找出的服務，或已將服務提供者與不知道您想要的服務相關聯。 例如，您可能想要從控制項內寫入活動記錄。

靜態 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 方法依賴快取的服務提供者，其會在第一次衍生自的任何 VSPackage 放置時初始化 <xref:Microsoft.VisualStudio.Shell.Package> 。

由於 VSPackage 的函式是在 VSPackage 被放置之前呼叫，因此全域服務通常無法從 VSPackage 的函式中使用。 如需解決方法，請參閱[如何：針對服務進行疑難排解](../extensibility/how-to-troubleshoot-services.md)。

以下是在工具視窗或其他非 VSPackage 專案中取得服務的方式範例。

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>從 DTE 物件取得服務

您也可以從物件取得服務 <xref:EnvDTE.DTEClass> 。 不過，您必須從 VSPackage 或藉由呼叫靜態方法，將 DTE 物件當做服務來取得 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 。

DTE 物件 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 會執行，您可以使用它來查詢服務 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 。

以下是從 DTE 物件取得服務的方法。

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
- [使用並提供服務](../extensibility/using-and-providing-services.md)
- [服務基本](../extensibility/internals/service-essentials.md)

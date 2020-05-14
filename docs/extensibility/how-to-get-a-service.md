---
title: 如何:獲取服務 |微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710963"
---
# <a name="how-to-get-a-service"></a>如何:取得服務

您通常需要獲得 Visual Studio 服務才能存取不同的功能。 通常,Visual Studio 服務提供一個或多個可以使用的介面。 您可以從 VSPackage 獲取大多數服務。

任何派生且<xref:Microsoft.VisualStudio.Shell.Package>已正確網站的 VSPackage 都可以請求任何全域服務。 由於`Package`類<xref:System.IServiceProvider>實現 ,因此派`Package`生自 的任何 VSPackage 也是服務提供者。

當 Visual Studio<xref:Microsoft.VisualStudio.Shell.Package><xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>載入<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>時 ,它會在初始化期間將物件傳遞給方法。 這稱為*坐 VS*包。 類`Package`包裝此服務提供者並提供<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>獲取服務的方法。

## <a name="getting-a-service-from-an-initialized-vspackage"></a>從初始化的 VSPackage 取得服務

1. 每個 Visual Studio 擴展都從 VSIX 部署專案開始,該專案將包含擴展資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]名為的`GetServiceExtension`VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。

2. 現在添加名為**GetService命令**的自定義命令項範本。 在「**新增新項目」** 對話框中,轉到**可視化 C#** > **擴充性**並選擇 **「自訂命令**」。 在視窗底部的**名稱「 欄**位中」,將命令檔名變更為*GetServiceCommand.cs*。 有關如何建立自訂指令的詳細資訊,[請使用選單指令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)

3. 在*GetServiceCommand.cs*中`MenuItemCommand`,刪除 方法的正文並新增以下代碼:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    此代碼獲取 SVActivityLog 服務並將其<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>轉換為介面,該介面可用於寫入活動日誌。 有關範例,請參閱[如何:使用活動日誌](../extensibility/how-to-use-the-activity-log.md)。

4. 建置此專案並開始偵錯。 出現實驗實例。

5. 在實驗實例的 **「工具」** 選單上,找到 **「調用獲取服務命令」** 按鈕。 按下此按鈕時,應看到一個消息框,其中顯示 **「找到活動日誌服務」。**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>從工具視窗或控制元件容器取得服務

有時,您可能需要從尚未設置的工具視窗或控制項容器獲取服務,或者已使用不知道所需服務的服務提供者。 例如,您可能希望從控制項內寫入活動日誌。

靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法依賴於緩存的服務提供者,該提供程式在首次對<xref:Microsoft.VisualStudio.Shell.Package>從 網站派生的任何 VSPackage 進行初始化時進行初始化。

由於 VSPackage 建構函數是在 VSPackage 進行網站之前調用的,因此在 VSPackage 構造函數中通常無法使用全域服務。 [請參閱如何:為解決方法對服務進行故障排除](../extensibility/how-to-troubleshoot-services.md)。

下面是在工具視窗或其他非 VSPackage 元素中獲取服務的方法範例。

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>從 DTE 物件取得服務

您還可以從<xref:EnvDTE.DTEClass>物件獲取服務。 但是,您必須從 VSPackage 或調用<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>靜態 方法將 DTE 物件作為服務。

DTE 物件<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>實現 ,<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>可用於使用 來查詢服務。

下面瞭解如何從 DTE 物件獲取服務。

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

- [如何:提供服務](../extensibility/how-to-provide-a-service.md)
- [使用與提供服務](../extensibility/using-and-providing-services.md)
- [服務要點](../extensibility/internals/service-essentials.md)

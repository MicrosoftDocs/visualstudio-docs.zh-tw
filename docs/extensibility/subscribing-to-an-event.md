---
title: 訂閱事件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd2933ee3e0e162740f0c7eb3f3c2307e17ec46d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647923"
---
# <a name="subscribing-to-an-event"></a>訂閱事件
本逐步解說說明如何建立工具視窗，以回應執行中檔資料表（RDT）中的事件。 工具視窗主控的使用者控制項會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。 @No__t_0 方法會將介面連接至事件。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="subscribing-to-rdt-events"></a>訂閱 RDT 事件

#### <a name="to-create-an-extension-with-a-tool-window"></a>使用工具視窗建立擴充功能

1. 使用 VSIX 範本建立名為**RDTExplorer**的專案，並加入名為**RDTExplorerWindow**的自訂工具視窗專案範本。

     如需使用工具視窗建立擴充功能的詳細資訊，請參閱[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)功能。

#### <a name="to-subscribe-to-rdt-events"></a>訂閱 RDT 事件

1. 開啟 RDTExplorerWindowControl，並刪除名為 `button1` 的按鈕。 新增 <xref:System.Windows.Forms.ListBox> 控制項，並接受預設名稱。 Grid 元素看起來應該像這樣：

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. 在程式碼視圖中開啟 RDTExplorerWindow.cs 檔案。 將下列 using 指示詞新增至檔案的開頭。

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. 修改 `RDTExplorerWindow` 類別，如此一來，除了衍生自 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 類別之外，它還會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 介面。

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。

    - 執行介面。 將游標放在 IVsRunningDocTableEvents 名稱上。 您應該會在左邊界看到燈泡。 按一下燈泡右邊的向下箭號，然後選取 [**執行介面**]。

5. 在介面中的每個方法中，使用下列程式碼取代行 `throw new NotImplementedException();`：

    ```csharp
    return VSConstants.S_OK;
    ```

6. 將 cookie 欄位新增至 RDTExplorerWindow 類別。

    ```csharp
    private uint rdtCookie;
    ```

     這會保留 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> 方法所傳回的 cookie。

7. 覆寫 RDTExplorerWindow 的 Initialize （）方法，以註冊 RDT 事件。 您應該一律取得 ToolWindowPane 的 Initialize （）方法中的服務，而不是在此函式中。

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> 服務以取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 介面。 @No__t_0 方法會將 RDT 事件連接至執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 的物件，在此案例中為 RDTExplorer 物件。

8. 更新 RDTExplorerWindow 的 Dispose （）方法。

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     @No__t_0 方法會刪除 `RDTExplorer` 與 RDT 事件通知之間的連接。

9. 將下面這一行加入至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> 處理常式的主體中，緊接在 `return` 語句之前。

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> 處理常式的主體和您想要在清單方塊中看到的其他事件加入類似的一行。

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. 建置此專案並開始偵錯。 Visual Studio 實驗實例隨即出現。

12. 開啟**RDTExplorerWindow** （**View/Other Windows/RDTExplorerWindow**）。

     [ **RDTExplorerWindow** ] 視窗隨即開啟，其中包含空白的事件清單。

13. 開啟或建立解決方案。

     當 `OnBeforeLastDocument` 和 `OnAfterFirstDocument` 事件引發時，事件清單中會顯示每個事件的通知。

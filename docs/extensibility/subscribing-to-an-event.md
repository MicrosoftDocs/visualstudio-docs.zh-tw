---
title: 訂閱事件 |Microsoft Docs
description: 瞭解如何建立工具視窗，以回應 Visual Studio SDK 中執行中檔資料表內的事件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c739dad7be8d2a000662eca478bc117699694c8a
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715869"
---
# <a name="subscribing-to-an-event"></a>訂閱事件
本逐步解說將說明如何建立工具視窗，以回應執行中的檔資料表中的事件 (RDT) 。 工具視窗會裝載可執行檔使用者控制項 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 。 方法會將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> 介面連接到事件。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="subscribing-to-rdt-events"></a>訂閱 RDT 事件

#### <a name="to-create-an-extension-with-a-tool-window"></a>使用工具視窗建立擴充功能

1. 使用 VSIX 範本來建立名為 **RDTExplorer** 的專案，並新增名為 **RDTExplorerWindow** 的自訂工具視窗專案範本。

     如需使用工具視窗建立延伸模組的詳細資訊，請參閱 [使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)功能。

#### <a name="to-subscribe-to-rdt-events"></a>訂閱 RDT 事件

1. 開啟 RDTExplorerWindowControl .xaml 檔案，然後刪除名為的按鈕 `button1` 。 新增 <xref:System.Windows.Forms.ListBox> 控制項，並接受預設名稱。 Grid 元素看起來應該像這樣：

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

3. 修改 `RDTExplorerWindow` 類別，如此一來，除了衍生自類別以外 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> ，它還會實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 介面。

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。

    - 執行介面。 將游標放在 IVsRunningDocTableEvents 名稱上。 您應該會在左邊界看到燈泡。 按一下燈泡右邊的向下箭號，然後選取 [ **執行介面**]。

5. 在介面中的每個方法中，以 `throw new NotImplementedException();` 下列程式碼取代這一行：

    ```csharp
    return VSConstants.S_OK;
    ```

6. 將 cookie 欄位加入至 RDTExplorerWindow 類別。

    ```csharp
    private uint rdtCookie;
    ```

     這會保留方法所傳回的 cookie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> 。

7. 覆寫 RDTExplorerWindow 的 Initialize ( # A1 方法以註冊 RDT 事件。 您應該一律取得 ToolWindowPane 之 Initialize ( # A1 方法中的服務，而不是在此函式中。

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>呼叫服務以取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法會將 RDT 事件連接至物件，該物件會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 在此案例中執行 RDTExplorer 物件。

8. 更新 RDTExplorerWindow 的 Dispose ( # A1 方法。

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

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>方法會刪除 `RDTExplorer` 與 RDT 事件通知之間的連接。

9. 將下列程式程式碼加入至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> 處理常式的主體中（緊接在語句之前） `return` 。

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> 處理常式主體和您想要在清單方塊中看到的其他事件中，加入類似的行。

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. 建置此專案並開始偵錯。 Visual Studio 實驗實例隨即出現。

12. 開啟 **RDTExplorerWindow** (**View/Other Windows/RDTExplorerWindow**) 。

     [ **RDTExplorerWindow** ] 視窗隨即開啟，並列出空白的事件清單。

13. 開啟或建立解決方案。

     當 `OnBeforeLastDocument` 和 `OnAfterFirstDocument` 引發事件時，事件清單中會顯示每個事件的通知。

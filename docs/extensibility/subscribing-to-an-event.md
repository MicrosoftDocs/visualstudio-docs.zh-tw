---
title: 訂閱事件 |微軟文件
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
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699692"
---
# <a name="subscribing-to-an-event"></a>訂閱事件
本演練介紹如何創建回應正在運行的文檔表 (RDT) 中的事件的工具視窗。 工具窗口承載實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>的使用者控制件。 該方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>將介面連接到事件。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="subscribing-to-rdt-events"></a>訂閱 RDT 事件

#### <a name="to-create-an-extension-with-a-tool-window"></a>使用工具視窗建立延伸

1. 使用 VSIX 範本建立名為**RDTExplorer**的專案,並添加名為**RDTExplorerWindow**的自訂工具視窗項範本。

     有關使用工具視窗建立擴充的詳細資訊,請參考[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。

#### <a name="to-subscribe-to-rdt-events"></a>訂閱 RDT 事件

1. 打開 RDTExplorerWindowControl.xaml 檔案並`button1`刪除名為的按鈕。 添加<xref:System.Windows.Forms.ListBox>控制項並接受預設名稱。 網格元素應如下所示:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. 在代碼檢視中打開RDTExplorerWindow.cs檔。 將以下使用指令添加到檔的開頭。

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. 修改類`RDTExplorerWindow`,以便除了<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>從 類派生外,它<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>還實現了 介面。

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。

    - 實現介面。 將游標放在 IV 運行文檔表事件名稱上。 你應該在左邊邊看到一個燈泡。 點選燈泡右側的向下箭頭,然後選擇 **"實現"介面**。

5. 在介面中的每個方法中,將行`throw new NotImplementedException();`替換為:

    ```csharp
    return VSConstants.S_OK;
    ```

6. 將 Cookie 欄位添加到 RDTExplorerWindow 類。

    ```csharp
    private uint rdtCookie;
    ```

     這將保存方法返回的<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Cookie。

7. 重寫 RDTExplorerWindow 的初始化() 方法以註冊 RDT 事件。 應始終在 ToolWindowPane 的初始化() 方法中獲取服務,而不是在構造函數中獲取服務。

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     調用<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>該服務以<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>獲取 介面。 該方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>將 RDT 事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>連接到實現 RDTExplorer 物件的物件。

8. 更新 RDTExplorerWindow 的 Dispose() 方法。

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

     該方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>刪除和 RDT`RDTExplorer`事件通知之間的連接。

9. 將以下行添加到處理程式的<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>正文中,`return`就在語句之前。

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. 處理<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>程式的正文和要在清單框中看到的其他事件添加類似的行。

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. 建置此專案並開始偵錯。 將顯示可視化工作室實驗實例。

12. 打開**RDTExplorer 視窗**(**檢視 / 其他視窗 / RDTExplorer 視窗**)。

     **RDTExplorer 視窗**視窗打開時,將打開一個空事件清單。

13. 打開或創建解決方案。

     觸發`OnBeforeLastDocument``OnAfterFirstDocument`事件 時,事件清單中將顯示每個事件的通知。

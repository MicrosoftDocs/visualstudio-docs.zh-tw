---
title: 訂閱事件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5dbb3c9db722ff335fd8dddadfffed57457d23ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916922"
---
# <a name="subscribing-to-an-event"></a>訂閱事件
本逐步解說說明如何建立回應事件而執行的文件資料表 (RDT) 中的工具視窗。 工具視窗裝載使用者控制項，可實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法會將介面連接到事件。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="subscribing-to-rdt-events"></a>訂閱 RDT 事件  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>若要建立擴充功能與工具視窗  
  
1.  建立專案，名為**RDTExplorer**使用 [VSIX] 範本，然後新增名為的自訂工具視窗項目範本**RDTExplorerWindow**。  
  
     如需使用工具視窗建立擴充功能的詳細資訊，請參閱[工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
#### <a name="to-subscribe-to-rdt-events"></a>訂閱 RDT 事件  
  
1.  開啟 RDTExplorerWindowControl.xaml 檔案，並刪除名為按鈕`button1`。 新增<xref:System.Windows.Forms.ListBox>控制項，並接受預設名稱。 方格項目看起來應該像這樣：  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  程式碼檢視中開啟 RDTExplorerWindow.cs 檔案。 新增下列 using 陳述式開頭的檔案。  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  修改`RDTExplorerWindow`類別，因此，除了衍生自<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類別，它會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>介面。  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。  
  
    -   實作介面。 您可以將游標置於 IVsRunningDocTableEvents 名稱。 您應該會看到燈泡左邊界中。 按一下燈泡右邊的向下箭號，然後選取**實作介面**。  
  
5.  在介面中每個方法中，取代行`throw new NotImplementedException();`以此方式：  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Cookie 將欄位加入 RDTExplorerWindow 類別。  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     這個屬性所傳回的 cookie 會存放<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法。  
  
7.  覆寫 RDTExplorerWindow initialize （） 方法，以註冊 RDT 事件。 您一律應在 ToolWindowPane 的 initialize （） 方法中，不是在建構函式取得服務。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>服務呼叫以取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法將 RDT 事件連接至該物件會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>，在此案例中，RDTExplorer 物件。  
  
8.  更新 RDTExplorerWindow 的 dispose （） 方法。  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>方法會刪除之間的連線`RDTExplorer`和 RDT 事件通知。  
  
9. 將下行新增至主體<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>處理常式，之前`return`陳述式。  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. 將類似的一行新增至主體<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>處理常式和其他您想要在清單中看到的事件。  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. 建置此專案並開始偵錯。 Visual Studio 的實驗執行個體隨即出現。  
  
12. 開啟**RDTExplorerWindow** (**檢視 / 其他 Windows / RDTExplorerWindow**)。  
  
     **RDTExplorerWindow**具有空的事件清單的視窗隨即開啟。  
  
13. 開啟或建立解決方案。  
  
     作為`OnBeforeLastDocument`和`OnAfterFirstDocument`會引發事件，每個事件的通知便會出現在事件清單。
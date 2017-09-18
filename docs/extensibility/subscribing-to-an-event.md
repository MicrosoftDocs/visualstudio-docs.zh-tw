---
title: "訂閱事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6bd1dd320ad5366ef494a8db958614d837529320
ms.lasthandoff: 02/22/2017

---
# <a name="subscribing-to-an-event"></a>訂閱事件
本逐步解說說明如何建立回應事件而執行的文件資料表 (RDT) 中的工具視窗。 工具視窗裝載使用者控制項實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法會將介面連接到事件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="subscribing-to-rdt-events"></a>訂閱 RDT 事件  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>若要建立的擴充功能與工具視窗  
  
1.  建立專案，名為**RDTExplorer**使用 VSIX 的範本，並新增名為的自訂工具視窗項目範本**RDTExplorerWindow**。  
  
     如需使用工具視窗建立擴充功能的詳細資訊，請參閱[建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
#### <a name="to-subscribe-to-rdt-events"></a>訂閱 RDT 事件  
  
1.  開啟 RDTExplorerWindowControl.xaml 檔案，並刪除名為的按鈕`button1`。 新增<xref:System.Windows.Forms.ListBox>控制，並接受預設名稱。</xref:System.Windows.Forms.ListBox> 格線項目看起來應該像這樣︰  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  在程式碼檢視中開啟 RDTExplorerWindow.cs 檔案。 新增下列 using 陳述式開頭的檔案。  
  
    ```c#  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  修改`RDTExplorerWindow`類別，因此，除了衍生自<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類別，它會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>  
  
    -   實作介面。 將游標置於 IVsRunningDocTableEvents 名稱。 您應該會看到燈泡左邊界中。 按一下燈泡右邊的向下箭頭，然後選取**實作介面**。  
  
5.  在介面中的每個方法，將這一行`throw new NotImplementedException();`與這個︰  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
6.  Cookie 將欄位加入至 RDTExplorerWindow 類別。  
  
    ```c#  
    private uint rdtCookie;   
    ```  
  
     這個屬性所傳回的 cookie 會存放<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
7.  覆寫 RDTExplorerWindow initialize （） 方法，以註冊 RDT 事件。 務必要先取得服務在 ToolWindowPane initialize （） 方法中，不是在建構函式。  
  
    ```c#  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>服務呼叫以取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> </xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法連線到該物件會實作的 RDT 事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>，在此情況下，RDTExplorer 物件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
8.  更新 RDTExplorerWindow dispose （） 方法。  
  
    ```c#  
    protected override void Dispose(bool disposing)  
    {  
        // Release the RDT cookie.  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));  
        rdt.UnadviseRunningDocTableEvents(rdtCookie);  
  
        base.Dispose(disposing);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>方法會刪除之間的連線`RDTExplorer`和 RDT 事件通知。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>  
  
9. 將下行新增至主體<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>處理常式之前`return`陳述式。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>  
  
    ```c#  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. 將類似的一行加入至主體<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>處理常式和其他您想要在清單方塊中看見的事件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>  
  
    ```c#  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. 建置此專案並開始偵錯。 Visual Studio 的實驗執行個體隨即出現。  
  
12. 開啟**RDTExplorerWindow** (**檢視 / 其他視窗 / RDTExplorerWindow**)。  
  
     **RDTExplorerWindow**開啟空的事件清單 視窗。  
  
13. 開啟或建立的方案。  
  
     做為`OnBeforeLastDocument`和`OnAfterFirstDocument`會引發事件，每個事件通知就會出現在事件清單。

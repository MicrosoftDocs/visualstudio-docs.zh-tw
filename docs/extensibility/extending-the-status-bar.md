---
title: "擴充 [狀態] 列 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "狀態列關於狀態列"
  - "狀態列概觀"
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 擴充 [狀態] 列
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 Visual Studio 的 \[狀態\] 列在 IDE 底部，以顯示資訊。  
  
 當您擴充 \[狀態\] 列時，您可以在四個區域中顯示資訊和 UI: 意見區域、 進度列、 動畫區域和設計工具區域。 意見反應區域可讓您顯示文字並反白顯示的文字。 進度列顯示短時間執行作業，例如儲存檔案的累加進度。 動畫區域會顯示針對長時間執行作業或作業尚無法確定的長度，如建置方案中的多個專案的連續形成迴路動畫。 與設計工具區域顯示的游標位置列和資料行數目。  
  
 您可以使用，以取得狀態列 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 介面 \(從 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 服務\)。 此外，任何物件上的視窗框架的地方可註冊為用戶端物件的狀態列實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 介面。 每次啟動視窗時，Visual Studio 會查詢物件上的該視窗的地方 `IVsStatusbarUser` 介面。 如果找到，則會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 方法傳回的介面和物件可以更新從該方法內的狀態列。 例如文件視窗中，可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 方法來更新設計工具區域中的資訊，當它們變成使用中時。  
  
 下列程序假設您了解如何建立 VSIX 專案，並加入自訂的功能表命令。 如需詳細資訊，請參閱 [建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## 修改 \[狀態\] 列  
 此程序會示範如何設定並取得文字、 顯示靜態文字，以及 \[狀態\] 列的意見區域中顯示的文字反白顯示。  
  
#### 讀取和寫入至 \[狀態\] 列  
  
1.  建立 VSIX 專案，名為 **TestStatusBarExtension** ，並新增名為功能表命令 **TestStatusBarCommand**。  
  
2.  在 TestStatusBarCommand.cs，取代命令處理常式方法程式碼 \(MenuItemCallback\) 下列:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3.  編譯程式碼，並開始偵錯。  
  
4.  開啟 **工具** \] 功能表中的 Visual Studio 的實驗執行個體。 按一下 \[ **叫用 TestStatusBarCommand** \] 按鈕。  
  
     您應該會看到現在讀取狀態列中的文字 **「 我們剛剛寫入狀態列 」** 而且會出現訊息方塊具有相同的文字。  
  
#### 更新進度列  
  
1.  在此程序中，我們將說明如何初始化及更新進度列。  
  
2.  開啟 TestStatusBarCommand.cs 檔案，並使用下列程式碼來取代 MenuItemCallback 方法:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3.  編譯程式碼，並開始偵錯。  
  
4.  開啟 **工具** \] 功能表中的 Visual Studio 的實驗執行個體。 按一下 \[ **叫用 TestStatusBarCommand** \] 按鈕。  
  
     您應該會看到現在讀取狀態列中的文字 **「 進度列寫入 「**您也應該會看到進度列會更新每秒 20 秒。 之後，會清除 \[狀態\] 列及進度列。  
  
#### 顯示動畫  
  
1.  狀態列會顯示迴圈的動畫，表示一長時間執行的作業 \(例如，建置方案中的多個專案\)。 如果看不到這個動畫，請確定您有正確 **工具 \/ 選項** 設定:  
  
     移至 **工具\/選項 \/ 一般** 索引標籤，然後取消核取 **自動調整根據用戶端效能的視覺效果**。 然後檢查子選項 **啟用豐富型用戶端視覺體驗**。 此外，您現在應該可以看到此動畫，當您建置您的 Visual Studio 的實驗性執行個體中的專案。  
  
     此程序中，我們會顯示標準的 Visual Studio 動畫代表建置專案或方案。  
  
2.  開啟 TestStatusBarCommand.cs 檔案，並使用下列程式碼來取代 MenuItemCallback 方法:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3.  編譯程式碼，並開始偵錯。  
  
4.  開啟 **工具** 實驗性執行個體的 Visual Studio，然後按一下功能表 **叫用 TestStatusBarCommand**。  
  
     當您看到訊息方塊時，應該還會看到 \[狀態\] 列中的動畫最右邊。 當您關閉訊息方塊時，就會消失動畫。
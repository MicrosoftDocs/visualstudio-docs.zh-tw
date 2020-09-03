---
title: 擴充狀態列 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28fc1155279ec624cea576b5a70a25800d4ff837
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204420"
---
# <a name="extending-the-status-bar"></a>延伸狀態列
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 IDE 底部的 Visual Studio 狀態列來顯示資訊。  
  
 當您擴充狀態列時，您可以在四個區域中顯示資訊和 UI：意見反應區域、進度列、動畫區域和設計工具區域。 [意見反應] 區域可讓您顯示文字，並醒目提示顯示的文字。 進度列會顯示短時間執行之作業的累加進度，例如儲存檔案。 動畫區域會針對長時間執行的作業或不確定長度的作業（例如在方案中建立多個專案）顯示持續迴圈的動畫。 而且，設計工具區域會顯示游標位置的行號和欄號。  
  
 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 服務) 中的介面 (來取得狀態列 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 。 此外，在視窗框架上放置的任何物件都可以藉由實作為狀態列用戶端物件來註冊該 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 介面。 每當啟動視窗時，Visual Studio 會針對介面查詢位於該視窗的物件 `IVsStatusbarUser` 。 如果找到，它會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 在傳回的介面上呼叫方法，而物件可以從該方法中更新狀態列。 例如，文件視窗可以在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 設計工具區域中使用方法來更新其作用中的資訊。  
  
 下列程式假設您已瞭解如何建立 VSIX 專案並加入自訂功能表命令。 如需詳細資訊，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。  
  
## <a name="modifying-the-status-bar"></a>修改狀態列  
 此程式示範如何設定和取得文字、顯示靜態文字，以及反白顯示狀態列的意見反應區域中顯示的文字。  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>讀取和寫入狀態列  
  
1. 建立名為 **TestStatusBarExtension** 的 VSIX 專案，並新增名為 **TestStatusBarCommand**的功能表命令。  
  
2. 在 TestStatusBarCommand.cs 中，以下列程式碼取代命令處理常式方法程式碼 (MenuItemCallback) ：  
  
    ```csharp  
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
  
3. 編譯器代碼並開始進行偵錯工具。  
  
4. 在 Visual Studio 的實驗實例中開啟 [ **工具** ] 功能表。 按一下 [叫用 **TestStatusBarCommand** ] 按鈕。  
  
     您應該會看到狀態列中的文字現在會顯示「 **我們剛剛寫到狀態列」。** 出現的訊息方塊具有相同的文字。  
  
#### <a name="updating-the-progress-bar"></a>更新進度列  
  
1. 在此程式中，我們將示範如何初始化和更新進度列。  
  
2. 開啟 TestStatusBarCommand.cs 檔案，並以下列程式碼取代 MenuItemCallback 方法：  
  
    ```csharp  
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
  
3. 編譯器代碼並開始進行偵錯工具。  
  
4. 在 Visual Studio 的實驗實例中開啟 [ **工具** ] 功能表。 按一下 [叫用 **TestStatusBarCommand** 按鈕。  
  
     您應該會看到狀態列中的文字現在會讀取「**寫入進度**列」。 您也應該會看到每秒更新的進度列20秒。 之後會清除狀態列和進度列。  
  
#### <a name="displaying-an-animation"></a>顯示動畫  
  
1. 狀態列會顯示一個迴圈動畫，表示長時間執行的作業 (例如，在方案中建立多個專案) 。 如果看不到此動畫，請確定您有正確的 **工具/選項** 設定：  
  
     移至 [ **工具/選項/一般** ] 索引標籤，並取消核取 [ **根據用戶端效能自動調整視覺效果**]。 然後檢查子選項是否 **啟用豐富型用戶端視覺體驗**。 當您在 Visual Studio 的實驗實例中建立專案時，您現在應該可以看到動畫。  
  
     在這個程式中，我們會顯示代表建立專案或方案的標準 Visual Studio 動畫。  
  
2. 開啟 TestStatusBarCommand.cs 檔案，並以下列程式碼取代 MenuItemCallback 方法：  
  
    ```csharp  
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
  
3. 編譯器代碼並開始進行偵錯工具。  
  
4. 在 Visual Studio 的實驗實例中開啟 [ **工具** ] 功能表，然後按一下 [叫用 **TestStatusBarCommand**]。  
  
     當您看到訊息方塊時，您也應該會在最右邊的狀態列中看到動畫。 當您關閉訊息方塊時，動畫會消失。

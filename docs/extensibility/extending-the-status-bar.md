---
title: 擴展狀態列 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711548"
---
# <a name="extend-the-status-bar"></a>延伸狀態列
您可以使用 IDE 底部的可視化工作室狀態列來顯示資訊。

 擴展狀態列時,可以在四個區域中顯示資訊和 UI:反饋區域、進度列、動畫區域和設計器區域。 回饋區域允許您顯示文字並突出顯示顯示的文本。 進度列顯示短運行操作(如儲存檔)的增量進度。 動畫區域顯示連續循環動畫,用於長時間運行的操作或不確定長度的操作,例如在解決方案中生成多個專案。 設計器區域顯示游標位置的行號和列號。

 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>介面(從服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>) 獲取狀態列。 此外,任何位於視窗框架上的物件都可以通過實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>介面註冊為狀態列用戶端物件。 每當激活視窗時,Visual Studio 都會查詢該視窗中`IVsStatusbarUser`為 介面設置的物件。 如果找到,它將調用返回<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>的介面上的方法,並且物件可以從該方法內更新狀態列。 例如,文檔視窗可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>方法 在設計器區域中的資訊變為活動時更新它們。

 以下過程假定您瞭解如何創建 VSIX 專案和添加自訂功能表命令。 關於詳細資訊,請參閱[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

## <a name="modify-the-status-bar"></a>變更狀態列
 此過程展示如何設定和獲取文本、顯示靜態文字以及突出顯示狀態列的反饋區域中顯示的文本。

### <a name="read-and-write-to-the-status-bar"></a>讀取並寫入狀態列

1. 建立名為**TestStatusBar 延伸的**VSIX 專案,並加入名為**TestStatusBar 命令的選單指令**。

2. 在*TestStatusBarCommand.cs*中,將命令處理程式方法`MenuItemCallback`代碼 () 取代為以下內容:

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

3. 編譯代碼並開始調試。

4. 打開視覺化工作室實驗實例中的 **「工具**」功能表。 點選 **「調用測試狀態列命令」 按鈕**。

     您應該看到狀態列中的文本現在顯示 **「我們剛剛寫入狀態列」。** 顯示的消息框具有相同的文本。

### <a name="update-the-progress-bar"></a>更新進度列

1. 在此過程中,我們將演示如何初始化和更新進度列。

2. 開啟*TestStatusBarCommand.cs*`MenuItemCallback`檔案, 並將該方法取代為以下代碼:

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

3. 編譯代碼並開始調試。

4. 打開視覺化工作室實驗實例中的 **「工具**」功能表。 點選 **「調用測試狀態列命令」 按鈕**。

     您應該看到狀態列中的文字現在讀取 **「寫入進度」 欄。** 您還應看到進度條每秒鐘更新 20 秒。 之後,將清除狀態列和進度條。

### <a name="display-an-animation"></a>顯示動畫

1. 狀態列顯示一個循環動畫,指示長時間運行的操作(例如,在解決方案中生成多個專案)。 如果看不到此動畫,請確保具有正確的**工具** > **選項**設定:

     跳到 **'工具** > **選項** > **一般**' 選項卡並取消選取**的效能自動調整視覺體驗**。 然後檢查子選項**啟用豐富的用戶端視覺體驗**。 現在,在 Visual Studio 的實驗實例中構建專案時,您應該能夠看到動畫。

     在此過程中,我們顯示代表構建專案或解決方案的標準 Visual Studio 動畫。

2. 開啟*TestStatusBarCommand.cs*`MenuItemCallback`檔案, 並將該方法取代為以下代碼:

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

3. 編譯代碼並開始調試。

4. 打開視覺化工作室實驗實例中的 **「工具**」功能表,然後單擊 **「調用測試狀態欄命令**」。。

     當您看到消息框時,還應在最右側的狀態欄中看到動畫。 關閉消息框時,動畫將消失。

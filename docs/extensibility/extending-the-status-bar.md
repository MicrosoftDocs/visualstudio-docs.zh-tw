---
title: 擴充狀態列 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c555c2a23b52d475b01fbf8cc2086167acc423dc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342871"
---
# <a name="extend-the-status-bar"></a>擴充狀態列
您可以使用 Visual Studio 的 [狀態] 列在 IDE 底部，以顯示資訊。

 當您擴充狀態列時，您可以在四個區域中顯示資訊和 UI： 意見反應區域、 進度列、 動畫區域和設計工具區域。 意見反應區域可讓您顯示文字並反白顯示的文字。 進度列會顯示短期執行的作業，例如儲存檔案的累加進度。 動畫區域顯示持續形成迴路的動畫長時間執行作業或未定的長度，例如建置多個專案方案中的作業。 與設計工具區域顯示的游標位置的行和資料行數目。

 您可以使用，以取得狀態列<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>介面 (從<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>服務)。 此外，任何物件上的視窗框架的地方可以註冊為用戶端物件狀態列藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>介面。 Visual Studio 視窗已啟動，只要查詢該視窗上的地方物件`IVsStatusbarUser`介面。 如果找到，則會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>上傳回的介面和物件的方法可以更新從該方法中的狀態列。 文件視窗，比方說，可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>方法來更新設計工具區域中的資訊，當它們變成作用中時。

 下列程序假設您了解如何建立 VSIX 專案，並加入自訂功能表命令。 如需資訊，請參閱[建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。

## <a name="modify-the-status-bar"></a>修改 [狀態] 列
 此程序會示範如何設定和取得文字、 顯示靜態文字，並反白顯示在狀態列的意見反應區域中顯示的文字。

### <a name="read-and-write-to-the-status-bar"></a>讀取和寫入狀態列

1. 建立 VSIX 專案，名為**TestStatusBarExtension** ，並新增名為的功能表命令**TestStatusBarCommand**。

2. 在  *TestStatusBarCommand.cs*，取代命令處理常式方法的程式碼 (`MenuItemCallback`) 取代為下列：

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

3. 編譯程式碼，並開始偵錯。

4. 開啟**工具**功能表中的 Visual Studio 實驗執行個體。 按一下 [**叫用 TestStatusBarCommand** ] 按鈕。

     您應該會看到現在讀取狀態列中的文字**剛才撰寫的狀態列。** 而且會出現訊息方塊具有相同的文字。

### <a name="update-the-progress-bar"></a>更新進度列

1. 在此程序中，我們將說明如何初始化和更新進度列。

2. 開啟*TestStatusBarCommand.cs*檔案，並將`MenuItemCallback`為下列程式碼的方法：

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

3. 編譯程式碼，並開始偵錯。

4. 開啟**工具**功能表中的 Visual Studio 實驗執行個體。 按一下 [**叫用 TestStatusBarCommand** ] 按鈕。

     您應該會看到現在讀取狀態列中的文字**寫入進度列。** 您也應該會看到進度列會更新每秒 20 秒。 在這之後會清除狀態列 」 和 「 進度列。

### <a name="display-an-animation"></a>顯示的動畫

1. 狀態列會顯示迴圈的動畫，表示在長時間執行的作業 （例如，建置方案中的多個專案）。 如果看不到這個動畫，請確定您已確實**工具** > **選項**設定：

     移至**工具** > **選項** > **一般**索引標籤，然後取消核取 **自動調整基礎用戶端上的視覺效果效能**。 然後檢查子選項**啟用豐富的用戶端視覺效果**。 您現在應該能夠看到此動畫，當您建置您的 Visual Studio 的實驗性執行個體中的專案。

     此程序中，我們會顯示標準的 Visual Studio 動畫表示建置專案或方案。

2. 開啟*TestStatusBarCommand.cs*檔案，並將`MenuItemCallback`為下列程式碼的方法：

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

3. 編譯程式碼，並開始偵錯。

4. 開啟**工具**Visual Studio，然後按一下 實驗性執行個體中的功能表**叫用 TestStatusBarCommand**。

     當您看到訊息方塊時，您應該也在最右邊會看到 [狀態] 列中的動畫。 當您關閉訊息方塊時，就會消失動畫。
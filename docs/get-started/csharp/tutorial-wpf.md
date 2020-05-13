---
title: 以 C# 搭配 WPF 撰寫的 Hello World 應用程式
description: 使用 Windows Presentation Foundation (WPF) UI 架構，透過 Visual Studio 以 C# 建立一個簡單的 Windows Desktop .NET 應用程式。
ms.custom: seodec18, get-started
ms.date: 08/09/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8a29a75b21351d94c818837f07ff22785a07b5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579988"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>教程：使用 C 創建一個簡單的應用程式\#

藉由完成這個教學課程，讓自己更熟悉許多可在使用 Visual Studio 開發應用程式時運用的工具、對話方塊和設計工具。 當您在學習如何使用整合式開發環境 ([IDE](visual-studio-ide.md)) 時，您會建立簡單的 "Hello, World" 應用程式、設計 UI、新增程式碼，以及進行偵錯。

## <a name="prerequisites"></a>必要條件

::: moniker range="vs-2017"
如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?)頁面免費進行安裝。
::: moniker-end
::: moniker range=">=vs-2019"

- 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。
- 在本教程中，可以使用 .NET 框架或 .NET Core。 .NET 核心是更新、更現代的框架。 .NET 核心需要視覺化工作室 2019 版本 16.3 或更高版本。
::: moniker-end

## <a name="configure-the-ide"></a>設定 IDE

::: moniker range="vs-2017"

當您第一次開啟 Visual Studio 時，系統會提示您登入。 這在此教學課程中為選擇性步驟。 接下來您可能會看到對話方塊，要求您選擇開發設定和色彩佈景主題。 保留預設值，然後選擇 [啟動 Visual Studio]****。

![選擇設定對話方塊](../media/exploreide-settings.png)

Visual Studio 啟動後，您會看到工具視窗、功能表和工具列，以及主視窗空間。 工具視窗會停駐在應用程式視窗的左右端，同時 [ **快速啟動**]、功能表列和標準工具列則位於視窗的上方。 位於應用程式視窗中央的是 [ **起始頁**]。 當您載入方案或專案時，編輯器和設計工具會出現在 [起始頁] **** 所在的空間中。 在開發應用程式時，您大部分時間都會在此中央區域工作。

![應用常規設置的視覺化工作室 2017 IDE](../media/exploreide-idewithgeneralsettings.png "應用常規設置的視覺化工作室 2017 IDE 螢幕截圖")

::: moniker-end

::: moniker range=">=vs-2019"

當您啟動 Visual Studio 時，會先開啟 [開始] 視窗。 選取 [不使用程式碼繼續]**** 以開啟開發環境。 您會看到工具視窗、功能表和工具列，以及主視窗空間。 [工具] 視窗會停駐在應用程式視窗的左側和右側，搜尋方塊、功能表列和標準工具列則位於視窗上方。 當您載入方案或專案時，編輯器和設計工具會出現在應用程式視窗的中央區域。 在開發應用程式時，您大部分時間都會在此中央區域工作。

::: moniker-end

## <a name="create-the-project"></a>建立專案

當您在 Visual Studio 中建立應用程式時，您需要先建立一個專案和一個方案。 在這個範例中，您將建立 Windows Presentation Foundation (WPF) 專案。

::: moniker range="vs-2017"

1. 建立新專案。 在功能表列上，選擇 **"檔** > **新專案** > **"。**

     ![在功能表列上，選擇"檔"、"新建"、"專案"](../media/exploreide-filenewproject.png "功能表列的螢幕截圖，您選擇檔，新建，專案")

1. 在 [新增專案]**** 對話方塊中，選取 [已安裝]**** >  [Visual C#]**** >  [Windows 桌面]**** 類別，然後選取 [WPF 應用程式 (.NET Framework)]**** 範本。 將專案命名為 **HelloWPFApp**，然後選取 [確定]****。

     ![Visual Studio [新增專案] 對話方塊中的 WPF 應用程式範本](media/exploreide-newprojectcsharp.png "新專案對話方塊中 WPF 應用範本的螢幕截圖")

::: moniker-end

::: moniker range="vs-2019"

1. 開啟 Visual Studio 2019。

1. 在開始視窗中，選擇 [建立新專案]****。

   ![檢視 [建立新專案] 視窗](../../get-started/media/vs-2019/start-window-create-new-project.png ""創建新專案"視窗的螢幕截圖")

1. 在 **"創建新專案**"螢幕上，搜索"WPF"，選擇**WPF 應用程式 （.NET Core），** 然後選擇 **"下一步**"。

   ![[建立新專案] 對話方塊中的 WPF 應用程式範本](media/vs-2019/exploreide-newprojectcsharp-vs2019.png ""創建新專案"對話方塊中 WPF 應用範本的螢幕截圖")

   > [!NOTE]
   > 您可能會找到兩個 WPF 桌面範本，一個用於 .NET 框架，另一個用於 .NET Core。 .NET 核心範本在 Visual Studio 2019 版本 16.3 及更高版本中提供。 您可以為本教程使用任一，但我們建議 .NET Core 進行新的開發。

1. 在下一個畫面上，為專案指定名稱 **HelloWPFApp**，然後選擇 [建立]****。

   ![將專案命名為"HelloWPFApp"](./media/vs-2019/exploreide-nameproject.png "您命名專案的視窗螢幕截圖")

::: moniker-end

Visual Studio 會建立 HelloWPFApp 專案和方案，而且**方案總管**會顯示各種不同檔案。 **WPF 設計工具**會在分割檢視中顯示 *MainWindow.xaml* 的設計檢視和 XAML 檢視。 您可以滑動分隔器來增加或減少顯示任一檢視。 您可以選擇只查看視覺檢視，或只查看 XAML 檢視。

![IDE 中的 WPF 專案和解決方案](media/exploreide-wpfproject-cs.png "IDE 中 WPF 專案和解決方案的螢幕截圖")

> [!NOTE]
> 如需 XAML (eXtensible Application Markup Language) 的詳細資訊，請參閱 [WPF 的 XAML 概觀](/dotnet/framework/wpf/advanced/xaml-overview-wpf)頁面。

建立專案之後，您可以進行自訂。 若要這麼做，請選擇 [檢視]**** 功能表中的 [屬性]**** 視窗，或按 **F4**。 然後，您可以顯示和變更應用程式中專案項目、控制項及其他項目的選項。

   ![屬性視窗](../media/exploreide-hellowpfappfiles.png "具有 WPF 檔應用名稱的屬性視窗的螢幕截圖")   

### <a name="change-the-name-of-mainwindowxaml"></a>變更 MainWindow.xaml 的名稱

讓我們給 MainWindow 一個更具體的名稱。 在**解決方案資源管理器**中，按右鍵*MainWindow.xaml*並選擇**重命名**。 將檔重命名為*問候語.xaml*。

## <a name="design-the-user-interface-ui"></a>設計使用者介面 (UI)

如果設計器未打開，請選擇*問候.xaml，* 然後按**Shift**+**F7**打開設計器。

我們會將三種類型的控制項新增至這個應用程式：一個 <xref:System.Windows.Controls.TextBlock> 控制項、兩個 <xref:System.Windows.Controls.RadioButton> 控制項和一個 <xref:System.Windows.Controls.Button> 控制項。

### <a name="add-a-textblock-control"></a>新增 TextBlock 控制項

1. 按**Ctrl**+**Q**啟動搜索框並鍵入**工具箱**。 從結果清單中選擇 [檢視] > [工具箱]****。

1. 在 [工具箱]**** 中展開 [通用 WPF 控制項]**** 節點以查看 TextBlock 控制項。

     ![已反白顯示 [TextBlock] 控制項的 [工具箱]](../media/exploreide-textblocktoolbox.png "突出顯示了"文本阻止"控制項的工具箱視窗的螢幕截圖")

1. 選擇 TextBlock 項目並將它拖曳至設計介面上的視窗，即可將 **TextBlock** 控制項加入設計介面。 將控制項置中靠近視窗頂端。 在 Visual Studio 2019 及更高版本中，您可以使用紅色準則來居中控制項。

    您的視窗應該會和下圖類似：

    ![問候表單上的 [TextBlock] 控制項](../media/exploreide-greetingswithtextblockonly.png "問候語表單上的 TextBlock 控制項的螢幕截圖")

   XAML 標記應該看起來與下列範例相似：

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>自訂文字區塊中的文字

1. 在 XAML 檢視中，找出 **TextBlock** 的標記並將 **Text** 屬性從 `TextBox` 變更為 `Select a message option and then choose the Display button.`

   XAML 標記應該看起來與下列範例相似：

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. 視需要再次將 TextBlock 置中，然後按 **Ctrl+S** 或使用 [檔案]**** 功能表項目來儲存您的變更。

接下來，您將向表單添加兩[個"無線電按鈕"](/dotnet/framework/wpf/controls/radiobutton)控制項。

### <a name="add-radio-buttons"></a>新增選項按鈕

1. 在 [工具箱]**** 中，尋找 **RadioButton** 控制項。

     ![已選取 [RadioButton] 控制項的 [工具箱] 視窗](../media/exploreide-radiobuttontoolbox.png "選中"選項按鈕"控制項的工具箱視窗的螢幕截圖")

1. 選擇 **RadioButton** 項目並將它拖曳至設計介面的視窗，即可將兩個 RadioButton 控制項新增至設計介面。 移動按鈕 (選取它們並使用方向鍵)，讓按鈕並排顯示於 TextBlock 控制項下。 使用紅色準則對齊控制項。

   您的視窗應該會像這樣：

   ![具有 TextBlock 和兩個選項按鈕的問候表單](../media/exploreide-greetingswithradiobuttons.png "帶有文字區塊和兩個選項按鈕的問候表單的螢幕截圖")

1. 在左側 RadioButton 控制項的 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性 (在 [ **屬性** ] 視窗頂端的屬性) 變更為 `HelloButton`。

    ![RadioButton 的 [屬性] 視窗](../media/exploreide-buttonproperties.png ""收音機按鈕"屬性視窗的螢幕截圖")

1. 在右邊 RadioButton 控制項的 [屬性]**** 視窗中，將 [名稱]**** 屬性變更為 `GoodbyeButton`，然後儲存您的變更。

接下來，您將會為每個 RadioButton 控制項加入顯示文字。 下列步驟會更新 RadioButton 控制項的 [ **內容** ] 屬性。

### <a name="add-display-text-for-each-radio-button"></a>為每個選項按鈕新增顯示的文字

1. 更新**Content**和`HelloButton`和`GoodbyeButton``"Hello"`和`"Goodbye"`XAML 中的內容屬性。 XAML 標記現在看起來應該會類似下列範例：

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>設定預設勾選的選項按鈕

在此步驟中，我們會設定預設勾選 HelloButton，這樣就一律會選取兩個選項按鈕的其中一個。

1. 在 XAML 檢視中，找出 HelloButton 的標記。

1. 加入 **IsChecked** 屬性，並將它設定為 **True**。 具體而言，請新增 `IsChecked="True"`。

   XAML 標記現在看起來應該會類似下列範例：

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

要添加的最後一個 UI 元素是[Button](/dotnet/framework/wpf/controls/button)控制項。

### <a name="add-the-button-control"></a>新增按鈕控制項

1. 在 [工具箱]**** 中尋找 **Button** 控制項，然後將它拖曳至設計檢視中的表單，將它新增至設計介面的 RadioButton 控制項底下。 如果您使用的是 Visual Studio 2019 或更高版本，則紅線可説明您將控制項居中。

1. 在 XAML 檢視中，將 Button 控制項的 [內容]**** 值從 `Content="Button"` 變更為 `Content="Display"`，然後儲存變更。

     您的視窗應該會和下圖類似。

     ![具有控制項標籤的問候表單](media/exploreide-greetingswithcontrollabels-cs.png "帶有控制標籤的問候語表單的螢幕截圖")

   XAML 標記現在看起來應該會類似下列範例：

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>將程式碼新增至顯示按鈕

此應用程式執行時，會在使用者選擇選項按鈕並選擇 [顯示]**** 按鈕之後顯示訊息方塊。 一個訊息方塊會顯示 Hello，而另外一個會顯示 Goodbye。 若要建立這個行為，您必須將程式碼新增至 *Greetings.xaml.cs* 中的 `Button_Click` 事件。

1. 在設計介面上，按兩下 [ **顯示** ] 按鈕。

     *Greetings.xaml.cs* 隨即開啟，並將游標置於 `Button_Click` 事件中。

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {

    }
    ```

1. 輸入下列程式碼：

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. 儲存應用程式。

## <a name="debug-and-test-the-application"></a>偵錯和測試應用程式

接下來，您會偵錯應用程式以尋找錯誤，並測試兩個訊息方塊是否都正確出現。 下列指示會告訴您如何建置和啟動偵錯工具，不過您稍後也可閱讀 [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) 和[對 WPF 進行偵錯](../../debugger/debugging-wpf.md)以取得詳細資訊。

### <a name="find-and-fix-errors"></a>尋找和修正錯誤

在此步驟中，您將發現之前更改*MainWindow.xaml*檔的名稱時造成的錯誤。

#### <a name="start-debugging-and-find-the-error"></a>開始偵錯並找出錯誤

1. 按 **F5** 或依序選取 [偵錯]**** 和 [開始偵錯]****，來啟動偵錯工具。

   [中斷模式]**** 視窗隨即出現，而 [輸出]**** 視窗會指出發生了 IOException：找不到資源 'mainwindow.xaml'。

   ![IO 異常消息](../media/exploreide-ioexception.png "IOException 訊息的螢幕擷取畫面")

1. 通過選擇**調試** > **停止調試停止調試**，停止調試器。

我們已在這個教學課程開始時，將 *MainWindow.xaml* 重新命名為 *Greetings.xaml*，但程式碼仍會參考 *MainWindow.xaml* 作為應用程式的啟動 URI，因此專案無法啟動。

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>指定 Greetings.xaml 作為啟動 URI

1. 在 [方案總管]**** 中，開啟 *App.xaml* 檔。

1. 將 `StartupUri="MainWindow.xaml"` 變更為 `StartupUri="Greetings.xaml"`，然後儲存變更。

再次啟動偵錯工具 (按 **F5**)。 您應該看到應用程式**的問候**視窗。

::: moniker range="vs-2017"
![正在執行的應用程式螢幕擷取畫面](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![正在執行的應用程式螢幕擷取畫面](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

立即關閉應用程式視窗停止偵錯。

### <a name="debug-with-breakpoints"></a>使用中斷點進行偵錯

新增一些中斷點，即可在偵錯時測試程式碼。 您可以通過選擇 **"調試** > **切換中斷點**"來添加中斷點，通過按一下程式碼旁邊的編輯器的左邊距，按一下要進行中斷的程式碼，或者按**F9**。

#### <a name="add-breakpoints"></a>新增中斷點

1. 打開*Greetings.xaml.cs*，然後選擇以下行：`MessageBox.Show("Hello.")`

1. 依序選取 [ **偵錯**] 和 [ **切換中斷點**]，以新增中斷點。

     在編輯器視窗最左緣、程式碼行的旁邊會出現一個紅色圓圈。

1. 請選取下列程式碼行： `MessageBox.Show("Goodbye.")`。

1. 按 **F9** 鍵新增中斷點，然後按 **F5** 開始偵錯。

1. 在 [ **Greetings** ] 視窗中，選擇 [ **Hello** ] 選項按鈕，然後選擇 [ **顯示** ] 按鈕。

    程式碼行 `MessageBox.Show("Hello.")` 會以黃色反白顯示。 在 IDE 底部，[自動變數]、[區域變數] 和 [監看式] 視窗會一起停駐在左邊，而 [呼叫堆疊]、[中斷點]、[例外狀況設定]、[命令]、[即時運算] 和 [輸出] 視窗會一起停駐在右邊。

    ![調試器中的中斷點](media/exploreide-debugbreakpoint.png "偵錯工具中的中斷點螢幕擷取畫面")

1. 在功能表列上，選擇 **"調試** > **步出**"。

     應用程式會繼續執行，而且會顯示含有文字 "Hello" 的訊息方塊。

1. 選擇訊息方塊上的 [ **確定** ] 按鈕將它關閉。

1. 在 [ **Greetings** ] 視窗中，選擇 [ **Goodbye** ] 選項按鈕，然後選擇 [ **顯示** ] 按鈕。

     程式碼行 `MessageBox.Show("Goodbye.")` 會以黃色反白顯示。

1. 選擇 **F5** 鍵繼續偵錯。 當訊息方塊出現時，選擇訊息方塊中的 [ **確定** ] 按鈕關閉它。

1. 關閉應用程式視窗停止偵錯。

1. 在功能表列上，選擇 **"調試** > **禁用所有中斷點**"。

### <a name="view-a-representation-of-the-ui-elements"></a>查看 UI 元素的表示形式

在正在運行的應用中，您應該會看到一個顯示在視窗頂部的小部件。 這是一個運行時協助程式，提供對一些有用的調試功能的快速訪問。 按一下第一個按鈕"**轉到即時視覺化樹**"。 您應該會看到一個包含頁面所有可視元素的樹的視窗。 展開節點以查找添加的按鈕。

![即時視覺化樹視窗的螢幕截圖](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>建置應用程式的發行版本

既然已經驗證應用程式的運作一切正常，您就可以準備其發行組建。

1. 在主功能表上，選擇 **"生成** > **乾淨"解決方案**以刪除在以前的生成期間創建的中間檔和輸出檔案。 這並非必要動作，但它可清除偵錯組建輸出。

1. 通過使用工具列上的下拉控制項（當前表示"調試"），將 HelloWPFApp 的組建組態從**調試**更改為**發佈**。

1. 通過選擇**生成** > **生成解決方案**來構建解決方案。

恭喜您完成此教學課程！ 您可以在解決方案和專案目錄下找到構建的 *.exe* *（...HelloWPFApp_HelloWPFApp_bin_release）。*

## <a name="next-steps"></a>後續步驟

恭喜您完成此教學課程！ 若要更深入了解，請繼續下列教學課程。

> [!div class="nextstepaction"]
> [繼續進行其他 WPF 教學課程](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>另請參閱

- [生產力祕訣](../../ide/productivity-features.md)

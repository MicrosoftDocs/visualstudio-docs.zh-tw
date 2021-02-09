---
title: 以 C# 搭配 WPF 撰寫的 Hello World 應用程式
description: 使用 Windows Presentation Foundation (WPF) UI 架構，透過 Visual Studio 以 C# 建立一個簡單的 Windows Desktop .NET 應用程式。
ms.custom: seodec18, get-started
ms.date: 08/09/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: tutorial
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 4384a724b57de565e03637057e16fc26e8213e5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924876"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>教學課程：使用 C 建立簡單的應用程式\#

藉由完成這個教學課程，讓自己更熟悉許多可在使用 Visual Studio 開發應用程式時運用的工具、對話方塊和設計工具。 當您在學習如何使用整合式開發環境 ([IDE](visual-studio-ide.md)) 時，您會建立簡單的 "Hello, World" 應用程式、設計 UI、新增程式碼，以及進行偵錯。

## <a name="prerequisites"></a>必要條件

::: moniker range="vs-2017"
如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?)頁面免費進行安裝。
::: moniker-end
::: moniker range=">=vs-2019"

- 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。
- 您可以在本教學課程中使用 .NET Framework 或 .NET Core。 .NET Core 是較新且更新式的架構。 .NET Core 需要 Visual Studio 2019 16.3 版或更新版本。
::: moniker-end

## <a name="configure-the-ide"></a>設定 IDE

::: moniker range="vs-2017"

當您第一次開啟 Visual Studio 時，系統會提示您登入。 這在此教學課程中為選擇性步驟。 接下來您可能會看到對話方塊，要求您選擇開發設定和色彩佈景主題。 保留預設值，然後選擇 [啟動 Visual Studio]。

![選擇設定對話方塊](../media/exploreide-settings.png)

Visual Studio 啟動後，您會看到工具視窗、功能表和工具列，以及主視窗空間。 工具視窗會停駐在應用程式視窗的左右端，同時 [ **快速啟動**]、功能表列和標準工具列則位於視窗的上方。 位於應用程式視窗中央的是 [ **起始頁**]。 當您載入方案或專案時，編輯器和設計工具會出現在 [起始頁]  所在的空間中。 在開發應用程式時，您大部分時間都會在此中央區域工作。

![Visual Studio 已套用一般設定的 2017 IDE](../media/exploreide-idewithgeneralsettings.png "已套用一般設定的 Visual Studio 2017 IDE 螢幕擷取畫面")

::: moniker-end

::: moniker range=">=vs-2019"

當您啟動 Visual Studio 時，會先開啟 [開始] 視窗。 選取 [不使用程式碼繼續] 以開啟開發環境。 您會看到工具視窗、功能表和工具列，以及主視窗空間。 [工具] 視窗會停駐在應用程式視窗的左側和右側，搜尋方塊、功能表列和標準工具列則位於視窗上方。 當您載入方案或專案時，編輯器和設計工具會出現在應用程式視窗的中央區域。 在開發應用程式時，您大部分時間都會在此中央區域工作。

::: moniker-end

## <a name="create-the-project"></a>建立專案

當您在 Visual Studio 中建立應用程式時，您需要先建立一個專案和一個方案。 在這個範例中，您將建立 Windows Presentation Foundation (WPF) 專案。

::: moniker range="vs-2017"

1. 建立新專案。 在功能表列上 **，選取 [** 檔案  >  **新增**  >  **專案**]。

     ![在功能表列上，選擇 [檔案]、[新增]、[專案]](../media/exploreide-filenewproject.png "在功能表列中選擇 [檔案]、[新增]、[專案] 的螢幕擷取畫面")

1. 在 [新增專案] 對話方塊中，選取 [已安裝] >  [Visual C#] >  [Windows 桌面] 類別，然後選取 [WPF 應用程式 (.NET Framework)] 範本。 將專案命名為 **HelloWPFApp**，然後選取 [確定]。

     ![Visual Studio [新增專案] 對話方塊中的 WPF 應用程式範本](media/exploreide-newprojectcsharp.png "[新增專案] 對話方塊中 WPF 應用程式範本的螢幕擷取畫面")

::: moniker-end

::: moniker range="vs-2019"

1. 開啟 Visual Studio 2019。

1. 在開始視窗中，選擇 [建立新專案]。

   ![檢視 [建立新專案] 視窗](../../get-started/media/vs-2019/start-window-create-new-project.png "[建立新專案] 視窗的螢幕擷取畫面")

1. 在 [ **建立新專案** ] 畫面上，搜尋 "wpf"，選擇 [ **wpf 應用程式 ( .net Core])**，然後選擇 **[下一步]**。

   ![[建立新專案] 對話方塊中的 WPF 應用程式範本](media/vs-2019/exploreide-newprojectcsharp-vs2019.png "[建立新專案] 對話方塊中 WPF 應用程式範本的螢幕擷取畫面")

   > [!NOTE]
   > 您可能會發現兩個 WPF 桌面範本，一個用於 .NET Framework，另一個用於 .NET Core。 .NET Core 範本可在 Visual Studio 2019 16.3 版和更新版本中使用。 您可以在本教學課程中使用其中一個，但建議您針對新的開發使用 .NET Core。

1. 在下一個畫面上，為專案指定名稱 **HelloWPFApp**，然後選擇 [建立]。

   ![將您的專案命名為 ' HelloWPFApp '](./media/vs-2019/exploreide-nameproject.png "您為專案命名之視窗的螢幕擷取畫面")

::: moniker-end

Visual Studio 會建立 HelloWPFApp 專案和方案，而且 **方案總管** 會顯示各種不同檔案。 **WPF 設計工具** 會在分割檢視中顯示 *MainWindow.xaml* 的設計檢視和 XAML 檢視。 您可以滑動分隔器來增加或減少顯示任一檢視。 您可以選擇只查看視覺檢視，或只查看 XAML 檢視。

![IDE 中的 WPF 專案和方案](media/exploreide-wpfproject-cs.png "IDE 中 WPF 專案和方案的螢幕擷取畫面")

> [!NOTE]
> 如需 XAML (eXtensible Application Markup Language) 的詳細資訊，請參閱 [WPF 的 XAML 概觀](/dotnet/framework/wpf/advanced/xaml-overview-wpf)頁面。

建立專案之後，您可以進行自訂。 若要這麼做，請選擇 [檢視] 功能表中的 [屬性] 視窗，或按 **F4**。 然後，您可以顯示和變更應用程式中專案項目、控制項及其他項目的選項。

   ![屬性視窗](../media/exploreide-hellowpfappfiles.png "使用 WPF 檔案應用程式名稱屬性視窗的螢幕擷取畫面")   

### <a name="change-the-name-of-mainwindowxaml"></a>變更 MainWindow.xaml 的名稱

讓我們給 MainWindow 一個更具體的名稱。 在 **方案總管** 中，以滑鼠右鍵按一下 *MainWindow* ，然後選擇 [ **重新命名**]。 將檔案重新命名為 *問候. xaml*。

## <a name="design-the-user-interface-ui"></a>設計使用者介面 (UI)

如果設計工具未開啟，請選取 [*問候語*]，然後按 **Shift** + **F7** 以開啟設計工具。

我們會將三種類型的控制項新增至這個應用程式：一個 <xref:System.Windows.Controls.TextBlock> 控制項、兩個 <xref:System.Windows.Controls.RadioButton> 控制項和一個 <xref:System.Windows.Controls.Button> 控制項。

### <a name="add-a-textblock-control"></a>新增 TextBlock 控制項

1. 按下 **Ctrl** + **Q** 以啟動搜尋方塊，然後輸入 [**工具箱**]。 從結果清單中選擇 [檢視] > [工具箱]。

1. 在 [工具箱] 中展開 [通用 WPF 控制項] 節點以查看 TextBlock 控制項。

     ![已反白顯示 [TextBlock] 控制項的 [工具箱]](../media/exploreide-textblocktoolbox.png "已反白顯示 TextBlock 控制項的 [工具箱] 視窗螢幕擷取畫面")

1. 選擇 TextBlock 項目並將它拖曳至設計介面上的視窗，即可將 **TextBlock** 控制項加入設計介面。 將控制項置中靠近視窗頂端。 在 Visual Studio 2019 和更新版本中，您可以使用紅色的指導方針來將控制項置中。

    您的視窗應該會和下圖類似：

    ![問候表單上的 [TextBlock] 控制項](../media/exploreide-greetingswithtextblockonly.png "問候表單上 TextBlock 控制項的螢幕擷取畫面")

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

1. 視需要再次將 TextBlock 置中，然後按 **Ctrl+S** 或使用 [檔案] 功能表項目來儲存您的變更。

接下來，您要將兩個 [選項按鈕](/dotnet/framework/wpf/controls/radiobutton) 控制項加入表單中。

### <a name="add-radio-buttons"></a>新增選項按鈕

1. 在 [工具箱] 中，尋找 **RadioButton** 控制項。

     ![已選取 [RadioButton] 控制項的 [工具箱] 視窗](../media/exploreide-radiobuttontoolbox.png "選取選項按鈕控制項的 [工具箱] 視窗螢幕擷取畫面")

1. 選擇 **RadioButton** 項目並將它拖曳至設計介面的視窗，即可將兩個 RadioButton 控制項新增至設計介面。 移動按鈕 (選取它們並使用方向鍵)，讓按鈕並排顯示於 TextBlock 控制項下。 使用紅色的指導方針來對齊控制項。

   您的視窗應該會像這樣：

   ![具有 TextBlock 和兩個選項按鈕的問候表單](../media/exploreide-greetingswithradiobuttons.png "具有 TextBlock 和兩個選項按鈕的問候表單螢幕擷取畫面")

1. 在左側 RadioButton 控制項的 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性 (在 [ **屬性** ] 視窗頂端的屬性) 變更為 `HelloButton`。

    ![RadioButton 的 [屬性] 視窗](../media/exploreide-buttonproperties.png "[選項按鈕屬性] 視窗的螢幕擷取畫面")

1. 在右邊 RadioButton 控制項的 [屬性] 視窗中，將 [名稱] 屬性變更為 `GoodbyeButton`，然後儲存您的變更。

接下來，您將會為每個 RadioButton 控制項加入顯示文字。 下列步驟會更新 RadioButton 控制項的 [ **內容** ] 屬性。

### <a name="add-display-text-for-each-radio-button"></a>為每個選項按鈕新增顯示的文字

1. 在 XAML 中，將和的 **內容** 屬性更新為 `HelloButton` `GoodbyeButton` `"Hello"` 和 `"Goodbye"` 。 XAML 標記現在看起來應該會類似下列範例：

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

您將加入的最後一個 UI 元素是 [按鈕](/dotnet/framework/wpf/controls/button) 控制項。

### <a name="add-the-button-control"></a>新增按鈕控制項

1. 在 [工具箱] 中尋找 **Button** 控制項，然後將它拖曳至設計檢視中的表單，將它新增至設計介面的 RadioButton 控制項底下。 如果您使用 Visual Studio 2019 或更新版本，則會有一條紅線可協助您將控制項置中。

1. 在 XAML 檢視中，將 Button 控制項的 [內容] 值從 `Content="Button"` 變更為 `Content="Display"`，然後儲存變更。

     您的視窗應該會和下圖類似。

     ![具有控制項標籤的問候表單](media/exploreide-greetingswithcontrollabels-cs.png "具有控制項標籤的問候表單螢幕擷取畫面")

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

此應用程式執行時，會在使用者選擇選項按鈕並選擇 [顯示] 按鈕之後顯示訊息方塊。 一個訊息方塊會顯示 Hello，而另外一個會顯示 Goodbye。 若要建立這個行為，您必須將程式碼新增至 *Greetings.xaml.cs* 中的 `Button_Click` 事件。

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

在此步驟中，您將會發現我們先前藉由變更 *MainWindow .xaml* 檔案的名稱所造成的錯誤。

#### <a name="start-debugging-and-find-the-error"></a>開始偵錯並找出錯誤

1. 按 **F5** 或依序選取 [偵錯] 和 [開始偵錯]，來啟動偵錯工具。

   [中斷模式] 視窗隨即出現，而 [輸出] 視窗會指出發生了 IOException：找不到資源 'mainwindow.xaml'。

   ![IOException 訊息](../media/exploreide-ioexception.png "IOException 訊息的螢幕擷取畫面")

1. 選擇 [ **Debug** 停止錯] 以停止偵錯工具  >  ****。

我們已在這個教學課程開始時，將 *MainWindow.xaml* 重新命名為 *Greetings.xaml*，但程式碼仍會參考 *MainWindow.xaml* 作為應用程式的啟動 URI，因此專案無法啟動。

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>指定 Greetings.xaml 作為啟動 URI

1. 在 [方案總管]中，開啟 *App.xaml* 檔。

1. 將 `StartupUri="MainWindow.xaml"` 變更為 `StartupUri="Greetings.xaml"`，然後儲存變更。

再次啟動偵錯工具 (按 **F5**)。 您應該會看到應用程式的 **問候語** 視窗。

::: moniker range="vs-2017"
![正在執行的應用程式螢幕擷取畫面](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![正在執行的應用程式螢幕擷取畫面](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

立即關閉應用程式視窗停止偵錯。

### <a name="debug-with-breakpoints"></a>使用中斷點進行偵錯

新增一些中斷點，即可在偵錯時測試程式碼。 若要加入中斷點，您可以選擇 [ **Debug**  >  **切換中斷點**]，方法是在編輯器的左邊界中，按一下您想要發生中斷的程式程式碼旁邊，或是按 **F9**。

#### <a name="add-breakpoints"></a>新增中斷點

1. 開啟 *Greetings.xaml.cs*，然後選取下列程式程式碼： `MessageBox.Show("Hello.")`

1. 依序選取 [ **偵錯**] 和 [ **切換中斷點**]，以新增中斷點。

     在編輯器視窗最左緣、程式碼行的旁邊會出現一個紅色圓圈。

1. 請選取下列程式碼行： `MessageBox.Show("Goodbye.")`。

1. 按 **F9** 鍵新增中斷點，然後按 **F5** 開始偵錯。

1. 在 [ **Greetings** ] 視窗中，選擇 [ **Hello** ] 選項按鈕，然後選擇 [ **顯示** ] 按鈕。

    程式碼行 `MessageBox.Show("Hello.")` 會以黃色反白顯示。 在 IDE 底部，[自動變數]、[區域變數] 和 [監看式] 視窗會一起停駐在左邊，而 [呼叫堆疊]、[中斷點]、[例外狀況設定]、[命令]、[即時運算] 和 [輸出] 視窗會一起停駐在右邊。

    ![偵錯工具中的中斷點](media/exploreide-debugbreakpoint.png "偵錯工具中的中斷點螢幕擷取畫面")

1. 在功能表列上，選擇 [ **Debug**  >  **跳出**]。

     應用程式會繼續執行，而且會顯示含有文字 "Hello" 的訊息方塊。

1. 選擇訊息方塊上的 [ **確定** ] 按鈕將它關閉。

1. 在 [ **Greetings** ] 視窗中，選擇 [ **Goodbye** ] 選項按鈕，然後選擇 [ **顯示** ] 按鈕。

     程式碼行 `MessageBox.Show("Goodbye.")` 會以黃色反白顯示。

1. 選擇 **F5** 鍵繼續偵錯。 當訊息方塊出現時，選擇訊息方塊中的 [ **確定** ] 按鈕關閉它。

1. 關閉應用程式視窗停止偵錯。

1. 在功能表列上，選擇 [ **Debug**  >  **停用所有中斷點**]。

### <a name="view-a-representation-of-the-ui-elements"></a>查看 UI 元素的標記法

在執行中的應用程式中，您應該會看到顯示在視窗頂端的小工具。 這是執行時間協助程式，可讓您快速存取某些實用的偵錯工具功能。 按一下第一個按鈕， **移至 [即時視覺化樹狀結構**]。 您應該會看到一個具有樹狀結構的視窗，其中包含頁面的所有視覺元素。 展開節點以尋找您新增的按鈕。

![即時視覺化樹狀結構視窗的螢幕擷取畫面](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>建置應用程式的發行版本

既然已經驗證應用程式的運作一切正常，您就可以準備其發行組建。

1. 在主功能表上，選取 [**建立**  >  **清除方案**]，以刪除在先前組建期間建立的中繼檔案和輸出檔案。 這並非必要動作，但它可清除偵錯組建輸出。

1. 使用工具列上的下拉式控制項，將 HelloWPFApp 的組建設定從 **Debug** 變更為 **Release** ， (它會顯示目前) 的 "Debug"。

1. 選擇 [**組建**  >  **組建方案**] 來建立方案。

恭喜您完成此教學課程！ 您可以在方案和專案目錄下找到您所建立的 *.exe* (*..\HelloWPFApp\HelloWPFApp\bin\Release*) 。

## <a name="next-steps"></a>下一步

恭喜您完成此教學課程！ 若要更深入了解，請繼續下列教學課程。

> [!div class="nextstepaction"]
> [繼續進行其他 WPF 教學課程](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>另請參閱

- [生產力祕訣](../../ide/productivity-features.md)

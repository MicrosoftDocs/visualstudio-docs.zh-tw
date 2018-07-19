---
title: 快速入門：在 Visual Studio 中使用 XAML 和 C# 來建立您的第一個通用 Windows 平台應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology:
- vs-acquisition
ms.topic: quickstart
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: dd638a539b8956716aa60b5361bd003c18d35f9b
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36283321"
---
# <a name="quickstart-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>快速入門：在 Visual Studio 中使用 XAML 和 C&#35; 來建立您的第一個通用 Windows 平台應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立一個可在任何 Windows 10 裝置上執行的 "Hello World" 應用程式。 為了這樣做，您將使用「通用 Windows 平台」(UWP) 專案範本、Extensible Application Markup Language (XAML) 及 C# 程式設計語言。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

## <a name="create-a-project"></a>建立專案

首先，請建立一個「通用 Windows 平台」專案。 此專案類型隨附您需要的所有範本檔案，甚至是在您新增任何項目之前便已完備！

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual C#]，然後選擇 [Windows 通用]。 在中間窗格中，選擇 [空白應用程式 (通用 Windows)]。 接著，將專案命名為 *HelloWorld*，然後選擇 [確定]。

   ![Visual Studio IDE 中 [新增專案] 對話方塊的「Windows 通用」專案範本](../ide/media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > 如果您看不到 [空白應用程式 (通用 Windows)] 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。<br><br>![從 [新增專案] 對話方塊中按一下 [開啟 Visual Studio 安裝程式] 連結](../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Visual Studio 安裝程式即會啟動。 選擇 [通用 Windows 平台開發] 工作負載，然後選擇 [修改]。<br><br>![「Visual Studio 安裝程式」中的 [通用 Windows 平台開發] 工作負載](../ide/media/uwp-dev-workload.png)

4. 當 [新增通用 Windows 平台專案] 對話方塊出現時，選擇 [確定]。

   ![在 [新增通用 Windows 平台專案] 對話方塊中，接受預設的 [目標版本] 和 [最低版本] 設定](../ide/media/new-uwp-project-target-minver-dialog.png)

  > [!NOTE]
  > 如果這是您第一次使用 Visual Studio 來建立 UWP 應用程式，可能會出現 [設定] 對話方塊。 請選擇 [開發人員模式]，然後選擇 [是]。<br><br>
 ![在 UWP [設定] 對話方塊中啟用 [開發人員模式]](../ide/media/enable-developer-mode.png)<br><br>Visual Studio 會為您安裝額外的「開發人員模式」套件。 當套件安裝完成時，請關閉 [設定] 對話方塊。

## <a name="create-the-application"></a>建立應用程式

現在即可開始進行開發。 您將新增按鈕控制項、為按鈕新增動作，然後啟動 "Hello World" 應用程式來看看它的樣子。

### <a name="add-a-button-to-the-design-canvas"></a>將按鈕新增至設計畫布

1. 在 [方案總管] 中，按兩下 [MainPage.xaml] 以開啟分割檢視。

  ![從 [方案總管] 中開啟 MainPage.xaml ](../ide/media/uwp-solution-explorer-MainPage-xaml.png)

  有兩個窗格：[XAML 設計工具] (其中包含設計畫布) 和 [XAML 編輯器] (可供您新增或變更程式碼)。

  ![XAML 編輯器中的 [XAML 設計工具] 窗格](../ide/media/uwp-xaml-editor.png)

2. 選擇 [工具箱] 以開啟 [工具箱] 飛出視窗。

  ![按一下 [工具箱] 以開啟 [工具箱] 飛出視窗](../ide/media/uwp-toolbox.png)

  (如果沒有看到 [工具箱] 選項，您可以從功能表列中開啟它。 若要這樣做，請選擇 [檢視] > [工具列]。 或按 **Ctrl**+**Alt**+**X**)。

3. 按一下**固定**圖示，以固定 [工具箱] 視窗。

  ![按一下 [釘選] 圖示以固定 [工具箱] 視窗](../ide/media/uwp-toolbox-autohide.png)

4. 按一下 [Button] 控制項，然後將它拖曳至設計畫布。

   ![按一下 [Button] 控制項，然後將它拖曳至設計畫布](../ide/media/uwp-toolbox-add-button-control.png)

  如果您查看 [XAML 編輯器] 中的程式碼，就會看到在該處也新增了 Button：

  ![按一下 [Button] 控制項，然後將它拖曳至設計畫布](../ide/media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>為按鈕新增標籤

1. 在 [XAML 編輯器] 中，將 Button Content 值從 "Button" 變更為 "Hello World!"

   ![將 Button Content 值變更為 Hello World](../ide/media/uwp-change-button-text-in-xaml-code-window.png)

2. 請注意，[XAML 設計工具] 中的按鈕也會變更。

   ![按鈕在設計畫布上變更為 Hello World](../ide/media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>新增事件處理常式

「事件處理常式」聽起來很複雜，但它其實只是事件發生時所呼叫程式碼的另一個名稱。 在此案例中，它會為 "Hello World!" 按鈕。

1. 按兩下設計畫布上的按鈕控制項。

2. 編輯 *MainPage.xaml.cs* (程式碼後置頁面) 中的事件處理常式程式碼。

 這是開始有趣的地方。 預設的事件處理常式看起來會像這樣：

   ![預設的 Button_Click 事件處理常式 ](../ide/media/uwp-button-click-code.png)

 我們會變更它，讓它看起來像這樣：

    ![新的非同步 Button_Click 事件處理常式 ](../ide/media/uwp-add-hello-world-async-code.png)

  以下是要複製和貼上的程式碼：

  ```C#
  private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
  ```

#### <a name="what-did-we-just-do"></a>我們剛剛做了什麼？

程式碼使用一些 Windows API 來建立語音合成物件，然後提供一些文字給它說出。 (如需使用 `SpeechSynthesis` 的詳細資訊，請參閱 <xref:System.Speech.Synthesis>)。

## <a name="run-the-application"></a>執行應用程式

現在即可建置、部署及啟動 "Hello World" UWP 應用程式，來看看其外觀和音效。 方式如下：

1. 選擇 [本機電腦] 來啟動應用程式。

   ![按一下 [本機電腦] 以啟動 UWP 應用程式並對其進行偵錯](../ide/media/uwp-start-or-debug.png)

   (或者，您也可以從功能表列中選擇 [偵錯] > [開始偵錯]，或按 **F5**，來啟動應用程式)。

2. 檢視您的應用程式 (在啟動顯示畫面消失後會立即出現)。 應用程式應該看起來像這樣：

   ![UWP "Hello World" 應用程式](../ide/media/uwp-hello-world-app.png)

3. 按一下 [Hello World] 按鈕。

 您的 Windows 10 裝置字面上會顯示 "Hello, World!"

4. 若要關閉此應用程式，請按一下工具列中的 [停止偵錯] 按鈕。 (或者，您也可以從功能表列中選擇 [偵錯] > [開始偵錯]，或按 **Shift**+**F5**)。

## <a name="next-steps"></a>後續步驟

恭喜您完成此快速入門！ 我們希望您已了解有關 UWP 和 Visual Studio IDE 的一些基本概念。 若要深入了解，請繼續進行下列教學課程：

> [!div class="nextstepaction"]
> [建立使用者介面](/windows/uwp/design/basics/xaml-basics-ui)

---
title: 教學課程：使用 Visual Studio & C 建立 UWP 應用程式#
description: 在 Visual Studio 中使用 XAML 和 C# 建立 UWP 應用程式
titleSuffix: ''
ms.custom: vs-acquisition, get-started, SEO-VS-2020
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 2e89c58e3c0dca2b5d009a592d3f242646339f8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390290"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>教學課程：使用 XAML 和 C&#35; 在 Visual Studio 中建立您的第一個通用 Windows 平臺應用程式

在這個 Visual Studio 整合式開發環境 (IDE) 的簡介中，您將建立一個可在任何 Windows 10 裝置上執行的 "Hello World" 應用程式。 為了這樣做，您將使用「通用 Windows 平台」(UWP) 專案範本、Extensible Application Markup Language (XAML) 及 C# 程式設計語言。

::: moniker range="vs-2017"
如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。
::: moniker-end
::: moniker range="vs-2019"
如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。
::: moniker-end

## <a name="create-a-project"></a>建立專案

首先，請建立一個「通用 Windows 平台」專案。 此專案類型隨附您需要的所有範本檔案，甚至是在您新增任何項目之前便已完備！

::: moniker range="vs-2017"
1. 開啟 Visual Studio。

1. 從頂端功能表列中 **，選擇 [** 檔案 > **新增** > **專案**]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual C#]，然後選擇 [Windows 通用]。 在中間窗格中，選擇 [空白應用程式 (通用 Windows)]。 接著，將專案命名為 *HelloWorld*，然後選擇 [確定]。

   > [!NOTE]
   > 請確定來源專案的位置位於 **新的技術檔案系統 (NTFS)** 格式化的磁片磁碟機，例如作業系統 (作業系統) 磁片磁碟機。 否則，您可能會遇到建立和執行專案的問題。 

   ![Visual Studio IDE 中 [新增專案] 對話方塊的「Windows 通用」專案範本](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > 如果您看不到 [空白應用程式 (通用 Windows)] 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。<br><br>![從 [新增專案] 對話方塊中按一下 [開啟 Visual Studio 安裝程式] 連結](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Visual Studio 安裝程式即會啟動。 選擇 [通用 Windows 平台開發] 工作負載，然後選擇 [修改]。<br><br>![「Visual Studio 安裝程式」中的 [通用 Windows 平台開發] 工作負載](media/uwp-dev-workload.png)

1. 在 [新增通用 Windows 平台專案] 對話方塊中，接受預設的 **目標版本** 和 **最低版本** 設定。

   ![在 [新增通用 Windows 平台專案] 對話方塊中，接受預設的 [目標版本] 和 [最低版本] 設定](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. 開啟 Visual Studio，並在開始視窗中選擇 [建立新專案]。

1. 在 [建立新專案] 畫面上，於搜尋方塊中輸入 *通用 Windows*、選擇適用於 **空白應用程式 (通用 Windows)** 的 C# 範本，然後選擇 [下一步]。

   ![[建立新專案] 畫面的螢幕擷取畫面](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > 如果您看不到 [空白應用程式 (通用 Windows)] 專案範本，請按一下 [安裝更多工具與功能] 連結。<br><br>![按一下 [安裝更多工具與功能] 連結](media/vs-2019/uwp-not-finding.png)<br><br>Visual Studio 安裝程式即會啟動。 選擇 [通用 Windows 平台開發] 工作負載，然後選擇 [修改]。<br><br>![「Visual Studio 安裝程式」中的 [通用 Windows 平台開發] 工作負載](media/uwp-dev-workload.png)

1. 提供專案名稱 _HelloWorld_，然後選擇 [ **建立**]。

   ![設定您的專案畫面](media/vs-2019/uwp-configure-your-project.png)

1. 在 [新增通用 Windows 平台專案] 對話方塊中，接受預設的 **目標版本** 和 **最低版本** 設定。

   ![[新增通用 Windows 平臺專案] 對話方塊中的 [接受預設目標版本] 和 [最小版本] 設定](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > 如果這是您第一次使用 Visual Studio 來建立 UWP 應用程式，可能會出現 [設定] 對話方塊。 請選擇 [開發人員模式]，然後選擇 [是]。<br><br>
   > ![在 UWP [設定] 對話方塊中啟用 [開發人員模式]](media/enable-developer-mode.png)<br><br>Visual Studio 會為您安裝額外的「開發人員模式」套件。 當套件安裝完成時，請關閉 [設定] 對話方塊。

## <a name="create-the-application"></a>建立應用程式

現在即可開始進行開發。 您將新增按鈕控制項、為按鈕新增動作，然後啟動 "Hello World" 應用程式來看看它的樣子。

### <a name="add-a-button-to-the-design-canvas"></a>將按鈕新增至設計畫布

1. 在 [方案總管] 中，按兩下 [MainPage.xaml] 以開啟分割檢視。

   ::: moniker range="vs-2017"
   ![從 [方案總管] 中開啟 MainPage.xaml ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![從 [方案總管] 中開啟 MainPage.xaml](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   有兩個窗格：[XAML 設計工具] (其中包含設計畫布) 和 [XAML 編輯器] (可供您新增或變更程式碼)。

   ![XAML 編輯器中的 [XAML 設計工具] 窗格](media/uwp-xaml-editor.png)

1. 選擇 [工具箱] 以開啟 [工具箱] 飛出視窗。

   ![按一下 [工具箱] 以開啟 [工具箱] 飛出視窗](media/uwp-toolbox.png)

    (如果沒有看到 [ **工具箱** ] 選項，您可以從功能表列開啟它。 若要這樣做，請選擇 [**視圖**  >  **工具列**]。 或者，按下 **Ctrl** + **Alt** + **X**. ) 

1. 按一下 **釘** 選圖示以停駐 [工具箱] 視窗。

   ![按一下 [釘選] 圖示以固定 [工具箱] 視窗](media/uwp-toolbox-autohide.png)

1. 按一下 [Button] 控制項，然後將它拖曳至設計畫布。

   ![按一下 [Button] 控制項，然後將它拖曳至設計畫布](media/uwp-toolbox-add-button-control.png)

   如果您查看 **XAML 編輯器** 中的程式碼，您會看到該按鈕也已新增至該處：

   ![XAML 編輯器中的顯示按鈕](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>為按鈕新增標籤

1. 在 **XAML 編輯器** 中，將按鈕內容值從 "button" 變更為 "Hello World！"

   ![將 Button Content 值變更為 Hello World](media/uwp-change-button-text-in-xaml-code-window.png)

1. 請注意， **XAML 設計工具** 中的按鈕也會變更。

   ![按鈕在設計畫布上變更為 Hello World](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>新增事件處理常式

「事件處理常式」聽起來很複雜，但它其實只是事件發生時所呼叫程式碼的另一個名稱。 在此案例中，它會為 "Hello World!" 按鈕。

1. 按兩下設計畫布上的按鈕控制項。

1. 編輯 *MainPage.xaml.cs* 程式碼後置頁面中的事件處理常式程式碼。

   這是開始有趣的地方。 預設的事件處理常式看起來就像這樣：

   ![預設的 Button_Click 事件處理常式 ](media/uwp-button-click-code.png)

   讓我們來變更它，讓它看起來像這樣：

   ![新的非同步 Button_Click 事件處理常式 ](media/uwp-add-hello-world-async-code.png)

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

#### <a name="what-did-we-just-do"></a>我們剛才做了什麼？

程式碼使用一些 Windows API 來建立語音合成物件，然後提供一些文字給它說出。 (如需使用 `SpeechSynthesis` 的詳細資訊，請參閱 <xref:System.Speech.Synthesis>)。

## <a name="run-the-application"></a>執行應用程式

::: moniker range="vs-2017"
現在即可建置、部署及啟動 "Hello World" UWP 應用程式，來看看其外觀和音效。 方法如下。

1. 使用 [播放] 按鈕 (它的文字為 **本機電腦**)，在本機電腦上啟動應用程式。

   ![按一下 [本機電腦] 以啟動 UWP 應用程式並對其進行偵錯](media/uwp-start-or-debug.png)

    (或者，您可以從功能表列選擇 [ **Debug** > **開始** 錯]，或按 F5 啟動應用程式。 ) 

1. 檢視您的應用程式 (在啟動顯示畫面消失後會立即出現)。 應用程式應該看起來像這樣：

   ![UWP "Hello World" 應用程式](media/uwp-hello-world-app.png)

1. 按一下 [Hello World] 按鈕。

   您的 Windows 10 裝置字面上會顯示 "Hello, World!"

1. 若要關閉此應用程式，請按一下工具列中的 [停止偵錯] 按鈕。  (或者，請從功能表列選擇 [ **Debug**  >  **停止** 錯]，或按 Shift + F5。 ) 

::: moniker-end
::: moniker range=">=vs-2019"
現在即可建置、部署及啟動 "Hello World" UWP 應用程式，來看看其外觀和音效。 方法如下。

1. 使用 [播放] 按鈕 (它的文字為 **本機電腦**)，在本機電腦上啟動應用程式。

   ![按一下 [本機電腦] 以啟動 UWP 應用程式並對其進行偵錯](media/uwp-start-or-debug.png)

    (或者，您可以從功能表列選擇 [ **Debug** > **開始** 錯]，或按 F5 啟動應用程式。 ) 

1. 檢視您的應用程式 (在啟動顯示畫面消失後會立即出現)。 應用程式應該看起來像這樣：

   ![UWP "Hello World" 應用程式](media/vs-2019/uwp-hello-world-app.png)

1. 按一下 [Hello World] 按鈕。

   您的 Windows 10 裝置字面上會顯示 "Hello, World!"

1. 若要關閉此應用程式，請按一下工具列中的 [停止偵錯] 按鈕。  (或者，請從功能表列選擇 [ **Debug**  >  **停止** 錯]，或按 Shift + F5。 ) 

::: moniker-end

## <a name="next-steps"></a>後續步驟

恭喜您完成此教學課程！ 我們希望您已了解有關 UWP 和 Visual Studio IDE 的一些基本概念。 若要深入了解，請繼續下列教學課程：

> [!div class="nextstepaction"]
> [建立使用者介面](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>另請參閱

- [UWP 概觀](/windows/uwp/get-started/universal-application-platform-guide)
- [取得 UWP app 範例](/windows/uwp/get-started/get-uwp-app-samples)

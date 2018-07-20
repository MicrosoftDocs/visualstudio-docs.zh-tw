---
title: 了解如何使用 Visual Studio 偵錯工具進行偵錯
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1144e7e33709510cb03ed02cb62020f81e8e8b62
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303142"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>教學課程： 了解如何使用 Visual Studio 進行偵錯

本主題將介紹 Visual Studio 偵錯工具的逐步解說中的功能。 如果您想要偵錯工具功能的較高層級檢視，請參閱[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)。 當您*偵錯您的應用程式*，通常表示您正在附加偵錯工具執行您的應用程式。 當您這樣做時，偵錯工具會提供許多方式來看看您的程式碼如何在執行。 您可以逐步執行程式碼，並查看儲存在變數中的值，您可以設定變數值變更時，請參閱監看式、 您可以檢查您的程式碼的執行路徑 et al。如果這是您嘗試偵錯程式碼的第一次，您可能想要閱讀[偵錯適用於徹底初學者](../debugger/debugging-absolute-beginners.md)再進行本主題。

您可以是讀取沿著，以查看偵錯工具的功能，或您可以下載完整功能的教學課程中所使用的範例，並自行遵循的步驟。 若要下載範例，並遵循指示，請前往[相片檢視器示範](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a)。

|         |         |
|---------|---------|
|  ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片")  |    [觀看影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171)偵錯，會顯示類似的步驟。 |

雖然示範應用程式是 C# 的功能都適用於 c + +、 Visual Basic、 JavaScript 和 Visual Studio （除了註明） 支援其他語言。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 啟動偵錯工具，並叫用中斷點。
> * 了解逐步執行偵錯工具中的程式碼的命令
> * 檢查資料提示和偵錯工具視窗中的變數
> * 檢查呼叫堆疊
> * 使用例外狀況協助程式

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 和。**.NET 桌面開發**工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

    如果您需要安裝工作負載，但已擁有 Visual Studio，請在 [新增專案] 對話方塊 (選取 [檔案] > [新增] > [專案]) 的左窗格中，按一下 [開啟 Visual Studio 安裝程式]。 Visual Studio 安裝程式即會啟動。 選擇。**NET 桌面開發**工作負載，然後選擇**修改**。

## <a name="start-the-debugger"></a>開始偵錯工具 ！

1. 若要跟著做 Visual Studio 中的這些步驟，請下載範例[本頁](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a)。

    > [!IMPORTANT]
    > 您需要安裝 Visual Studio.NET 桌面開發工作負載示範中執行我們會使用應用程式。

2. 將解壓縮的專案。

3. 開啟 Visual Studio，然後選取**檔案 > 開啟** 功能表命令，然後選擇**專案/方案**，然後開啟您下載專案的資料夾。

     ![開啟範例專案](../debugger/media/dbg-tour-open-project.png "開啟專案")

3. 開啟 WPF 相片檢視器示範 > C# 資料夾中，選擇*photoapp.sln*檔案，然後選取**開啟**。

     在 Visual Studio 中，開啟專案。 在右窗格中的 [方案總管] 會顯示所有專案檔。

    ![方案總管檔](../debugger/media/dbg-tour-solution-explorer.png "方案總管")

4. 按下**F5** (**偵錯 > 啟動偵錯**) 或**開始偵錯**按鈕![開始偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")偵錯 工具列中。

     ![相片檢視器應用程式](../debugger/media/dbg-tour-wpf-app.png "相片檢視器應用程式")

     F5 開始偵錯工具附加至應用程式的程序，而向右移，現在我們還沒有加入任何中斷點，或完成任何特別動作來檢查程式碼的應用程式。 因此應用程式只會載入，請參閱相片影像。

     在本教學課程中，我們會仔細看看此應用程式使用偵錯工具，並取得了解偵錯工具功能。

5. 停止偵錯工具，藉由按下的紅色的停駐![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯") 按鈕。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>設定中斷點並開始偵錯工具

若要偵錯，您需要偵錯工具附加至應用程式處理序啟動您的應用程式。

1. 在  `MainWindow` MainWindow.xaml.cs 的建構函式程式碼的第一行的左邊的界，即可設定中斷點。

     ![設定中斷點](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。 

6. 按下**F5**或**開始偵錯**按鈕，應用程式會啟動並偵錯工具執行的程式碼行，您在其中設定中斷點。

    黃色箭號表示陳述式的偵錯工具暫停時，這也會在相同的點 （此陳述式尚未執行） 的暫停應用程式執行。

    F5 繼續執行應用程式到下一個中斷點。 （如果尚未執行的應用程式，F5 啟動偵錯工具並於第一個中斷點停止。）

    當您知道程式碼行或您想要詳細檢查的程式碼的區段時，中斷點會是很有用的功能。

## <a name="optional-restart-your-app-quickly"></a>（選擇性）快速重新啟動您的應用程式

按一下 [**重新啟動**![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp")中偵錯] 工具列按鈕 (**Ctrl** + **Shift**  +  **F5**)。

當您按下**重新啟動**，節省時間與停止應用程式，並重新啟動偵錯工具。 偵錯工具會在叫用時執行程式碼的第一個中斷點暫停。

偵錯工具停在您設定的中斷點，在`MainWindow`建構函式。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>使用逐步執行命令的偵錯工具中巡覽程式碼

大部分，我們會使用的鍵盤快速鍵在這裡，因為它是一個好的方法，以取得快速在偵錯工具 （對等命令例如功能表命令會顯示在括號內） 中執行您的應用程式。

1. 按下**F11** (**偵錯 > 逐步**) 兩次，請前進到應用程式執行`InitializeComponent()`函式。

     ![使用 F11 來逐步執行程式碼](../debugger/media/dbg-tour-f11.png "F11 逐步執行")

     是 F11**逐步執行**命令，並往前推進應用程式執行一個陳述式一次。 F11 是檢查大部分的詳細資料中的執行流程的好方法。 （若要更快速移動，透過程式碼，我們將示範一些其他選項也。）根據預設，偵錯工具會略過非使用者程式碼 (如果您想要更多詳細資料，請參閱[Just My Code](../debugger/just-my-code.md))。

     >[!NOTE]
     > 在 managed 程式碼，您會看到對話方塊，詢問您是否要在您自動不進入屬性和運算子 （預設行為） 時收到通知。 如果您想要變更此設定之後，停用**不進入屬性和運算子**中設定**工具 > 選項**下的功能表**偵錯**。

2. 按下**F10** (**偵錯 > 不進入函式**) 多次，直到在第一行中的程式碼的偵錯工具停止`OnApplicationStartup`事件處理常式。

     ![使用 F10 不進入函式程式碼](../debugger/media/dbg-tour-f10-step-over.png "F10 不進入函式")

     F10 進階偵錯工具，而不需要逐步執行函式或方法，應用程式程式碼 （仍執行的程式碼）。 按下 F10`InitializeComponent`方法呼叫 （而不是 F11)，我們會跳過之實作程式碼`InitializeComponent`（我們不關心的立即的可能）。

## <a name="step-into-a-property"></a>逐步執行屬性

1. 偵錯工具暫停在這行程式碼：

    ````c#
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    程式碼行上按一下滑鼠右鍵，然後選擇 **逐步執行至特定**，然後**SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![使用逐步執行至特定的功能](../debugger/media/dbg-tour-step-into-specific.png "逐步執行至特定")

    如前文所述，根據預設，偵錯工具會略過受管理的屬性和欄位，但**逐步執行至特定**命令可讓您覆寫這個行為。 現在，我們想要看會發生什麼事時`Path.set`屬性 set 存取子執行。 **逐步執行至特定**取得我們`Path.set`此處的程式碼。

     ![逐步執行至特定的結果](../debugger/media/dbg-tour-step-into-specific-2.png "逐步執行至特定")

     `Update`方法在此程式碼看起來可能很有趣，因此可讓使用偵錯工具來檢查該鄰近的程式碼。

5. 將滑鼠停留`Update`方法，直到綠色**執行至點選處** 按鈕![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick")出現在左邊。

     ![使用 執行至點選功能](../debugger/media/dbg-tour-run-to-click-2.png "執行至點選處")

    >  [!NOTE]
    > **執行至點選處** 按鈕的新[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。 如果您沒有看到綠色箭號按鈕，改用 F11 在此範例中進入偵錯工具。

6. 按一下 [**執行至點選處**] 按鈕![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick")。

    使用此按鈕，類似於設定暫時中斷點的。 **執行至點選處**便於快速瀏覽應用程式程式碼 （您可以按一下任何開啟的檔案中） 的可見區域內。

    偵錯工具將會前往`Update`方法實作。

7. 按下**F11**逐步執行至`Update`方法。

     ![逐步執行的 Update 方法的結果](../debugger/media/dbg-tour-update-method.png "步驟到 Update 方法")

    在這裡，我們找到更多的程式碼看起來很有趣，應用程式會取得所有項目。*jpg*檔案位於特定的目錄，然後再建立 每個檔案的相片物件。 此程式碼會讓我們開始檢查您的應用程式狀態 （變數），偵錯工具的好機會。 我們將在本教學課程的後續小節來這麼做。

    功能可讓您檢查變數是其中一個最實用的功能，在偵錯工具，而且有不同的方式來進行。 通常，當您嘗試偵錯問題時，會嘗試找出是否變數會儲存您希望他們能夠在特定時間的值。

## <a name="examine-the-call-stack"></a>檢查呼叫堆疊

在暫停期間`Update`方法中，按一下**呼叫堆疊**視窗中，預設在右下方的窗格中開啟。

![檢查呼叫堆疊](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

**呼叫堆疊**視窗會顯示方法和函式會取得呼叫的順序。 第一行會顯示目前的函式 (`Update`導覽應用程式中的方法)。 第二行顯示`Update`已從呼叫`Path.set`屬性，並依此類推。

>  [!NOTE]
> **呼叫堆疊**視窗是類似於偵錯觀點來看一些像是 Eclipse Ide 中。

呼叫堆疊會檢查並了解應用程式的執行流程的好方法。

您可以按兩下去看看該來源的程式碼的程式碼行，即，也會變更目前正在檢查偵錯工具的範圍。 此動作不前移偵錯工具。

您也可以使用滑鼠右鍵功能表，從**呼叫堆疊**視窗來進行其他動作。 比方說，您可以在其中插入指定的函式的中斷點，讓偵錯工具使用**執行至游標處**，並移檢查原始程式碼。 如需詳細資訊，請參閱 <<c0> [ 如何： 檢查 呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="step-out"></a>跳離函式

假設您已完成檢查`Update`方法在 data.cs 中，而且您想要利用函式，並且保留在偵錯工具。 您可以使用**跳離函式**命令。

1. 按下**Shift** + **F11** (或**偵錯 > 跳離函式**)。

     此命令會繼續應用程式執行 （並往前推進偵錯工具） 直到目前的函式傳回。

     您應該會回到`Update`在 data.cs 中的方法呼叫。

2. 按下**Shift** + **F11**同樣地，且偵錯工具會在呼叫堆疊中向上回到`OnApplicationStartup`事件處理常式。

## <a name="run-to-cursor"></a>執行至游標處

1. 選擇**停止偵錯**紅色按鈕![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯")或是**Shift** + **F5**.

2. 在 `Update`方法中的*data.cs 中*，以滑鼠右鍵按一下`Add`方法呼叫，然後選擇**執行至游標處**。 此命令會啟動偵錯，並在目前這一行程式碼中設定暫時中斷點。

     ![使用 執行至資料指標功能](../debugger/media/dbg-tour-run-to-cursor.png "執行至游標處")

    您應該在中斷點上暫停`MainWindow`（因為這是第一個中斷點您設定）。

3. 按下**F5**前往`Add`方法，您所選取的位置**執行至游標處**。

    您正在編輯程式碼，而且想要快速設定暫時中斷點並開始偵錯工具時，則此命令會很有用。

## <a name="change-the-execution-flow"></a>變更執行流程

1. 偵錯工具上的暫停`Add`方法呼叫時，使用滑鼠來抓取 （執行指標） 的黃色箭號，在左邊，並移動到一行的黃色箭頭`foreach`迴圈。

     ![將執行指標](../debugger/media/dbg-tour-move-the-execution-pointer.gif "執行將指標移至")

    藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或重新執行程式碼，不需要重新啟動偵錯工具。

2. 現在，按下**F5**。

    您可以看到新增至應用程式視窗的映像。 因為您正在重新執行中的程式碼`foreach`迴圈中，一些映像已新增兩次 ！

    > [!WARNING]
    > 您通常需要謹慎使用這項功能，以及您會看到工具提示中的警告。 您可能會太看到其他警告。 將指標移無法還原成先前的應用程式狀態的應用程式。

## <a name="inspect-variables-with-data-tips"></a>檢查資料提示中使用的變數

1. 開啟*data.cs 中*在相片檢視器示範應用程式中，以滑鼠右鍵按一下`private void Update`函式宣告，然後選擇**執行至游標處**（停止應用程式第一次如果已在執行）。

    附加偵錯工具，這將會暫停應用程式。 這可讓我們來檢查其狀態。

2. 將滑鼠停留`Add`方法呼叫，並按一下 [**執行至點選處**] 按鈕![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick")。

3. 現在，將滑鼠游標停留的檔案物件 (`f`)，您會看到其預設屬性值、 檔名*市場 031.jpg*。

     ![檢視資料提示](../debugger/media/dbg-tour-data-tips.gif "檢視資料提示方塊")

4. 展開以查看其屬性，例如物件`FullPath`屬性。

    通常，偵錯時，您希望能很快地檢查屬性值的物件，而且資料提示很適合用來執行它。

    > [!TIP]
    > 最受支援的語言，您可以編輯中間的偵錯工具工作階段的程式碼，如果您發現您想要變更的項目。 如需詳細資訊，請參閱 <<c0> [ 編輯後繼續](../debugger/edit-and-continue.md)。 若要使用此應用程式中的該功能，不過，我們必須先更新的.NET framework 的應用程式的版本。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>檢查變數與 [自動變數] 和 [區域變數] 視窗

1. 看看**自動變數**底部的程式碼編輯器 視窗。

     ![檢查 [自動變數] 視窗中的變數](../debugger/media/dbg-tour-autos-window.png "自動變數視窗")

    在 [**自動變數**] 視窗中，您會看到變數和其目前的值。 **自動變數**視窗會顯示目前這一行或上述列上使用的所有變數 （c + + 中，視窗會都顯示變數前面的三行程式碼中。 檢查特定語言行為的文件）。

    > [!NOTE]
    > 在 JavaScript 中，**區域變數**但不是支援 視窗**自動變數**視窗。

2. 接下來，看看**區域變數**視窗。

    **區域變數**視窗會顯示目前的範圍中的變數。

    ![檢查 [區域變數] 視窗中的變數](../debugger/media/dbg-tour-locals-window.png "[區域變數] 視窗")

    目前，`this`物件和檔案物件 (`f`) 會在目前範圍中。 如需詳細資訊，請參閱 <<c0> [ 檢查變數，在 [自動變數] 和 [區域變數] Windows](../debugger/autos-and-locals-windows.md)。

## <a name="set-a-watch"></a>設定監看式

1. 在主要程式碼編輯器] 視窗中，以滑鼠右鍵按一下該檔案物件 (`f`)，然後選擇 [**新增監看式**。

    您可以使用**監看式**視窗上，指定變數 （或運算式），您要留意。

    現在，您可以監看式上設定`File`物件，而您可以看到當您瀏覽偵錯工具變更其值。 不同於其他變數視窗中，**監看式**視窗一律會顯示變數，您所監看 （它們呈現灰色時超出範圍）。

2. 在上`Add`方法中，按一下綠色![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick")按鈕 （或按 f11 鍵幾次） 中向前`foreach`迴圈。

    ![設定變數的監看式](../debugger/media/dbg-tour-watch-window.png "監看式視窗")

    您也可能會看到第一個圖片加入到主視窗的執行範例應用程式，但這發生在不同的應用程式執行緒，因此影像可能還無法看到。

    如需詳細資訊，請參閱[設定使用監看式及快速監看式 Windows 監看式](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>檢查例外狀況

1. 在執行的應用程式視窗中，刪除中的文字**路徑**輸入的方塊，然後選取**變更** 按鈕。

     ![導致擲回例外狀況](../debugger/media/dbg-tour-cause-an-exception.png "造成例外狀況")

     應用程式會擲回的例外狀況，並偵錯工具帶您前往擲回例外狀況的程式碼行。

     ![例外狀況協助程式](../debugger/media/dbg-tour-exception-helper.png "例外狀況協助程式")

     在這裡，**例外狀況協助程式**說明`System.ArgumentException`和錯誤訊息，指出此路徑不是合法的表單。 因此，我們知道錯誤發生在方法或函式的引數。

     在此範例中，`DirectoryInfo`呼叫的協助，空的字串儲存在錯誤`value`變數。 (將滑鼠停留`value`查看空的字串。)

     例外狀況協助程式是很棒的功能，可協助您偵錯錯誤。 您也可以執行下列動作檢視錯誤詳細資料，然後從例外狀況協助程式新增監看式。 或者，如果有需要您可以變更條件擲回特定例外狀況。

    >  [!NOTE]
    > 例外狀況協助程式取代了例外狀況助理中[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

2. 依序展開**例外狀況設定**節點以查看更多選項如何處理此例外狀況類型，但您不需要變更任何項目針對此教學課程 ！

3. 按 **F5** 繼續執行應用程式。

若要深入了解偵錯工具的功能，請參閱[偵錯工具祕訣和訣竅](../debugger/debugger-tips-and-tricks.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何啟動偵錯工具，逐步執行程式碼，並檢查變數。 若要高階查看偵錯工具功能，以及其他更多資訊的連結。

> [!div class="nextstepaction"]
> [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)

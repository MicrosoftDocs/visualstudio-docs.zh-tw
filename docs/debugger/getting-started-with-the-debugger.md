---
title: "了解如何使用 Visual Studio 偵錯 |Microsoft 文件"
ms.custom: H1HackMay2017
ms.date: 10/11/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a09e0c54f1d7f0e49f08ddf65afbeb030a7087f1
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="learn-to-debug-using-visual-studio"></a>了解如何使用 Visual Studio 偵錯

本主題將介紹 Visual Studio 偵錯工具的逐步解說中的功能。 如果您想要偵錯工具功能的高階檢視，請參閱[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)。

您可以請閱讀沿著，以查看偵錯工具的功能或您可以下載完整功能的教學課程中使用的範例，並自行遵循的步驟。 若要下載範例，並遵循指示，請移至[相片檢視器示範](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a)。

|         |         |
|---------|---------|
|  ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片")  |    [觀看影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171)偵錯，會顯示類似的步驟。 |

雖然此示範應用程式是 C#，功能也適用於 c + +、 Visual Basic、 JavaScript 和 Visual Studio （除非註明） 支援其他語言。

## <a name="start-the-debugger"></a>開始偵錯工具 ！

1. 若要進行 Visual Studio 中的這些步驟，下載範例[本頁](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a)。

    > [!IMPORTANT]
    > 您需要安裝 Visual Studio.NET 桌面開發的工作負載，我們會使用應用程式執行此示範中使用。

2. 將解壓縮的專案。

3. 開啟 Visual Studio，然後選取**檔案 > 開啟**功能表命令，然後選擇 **專案/方案**，然後開啟您已經下載這個專案的資料夾。

     ![開啟範例專案](../debugger/media/dbg-tour-open-project.png "開啟專案")

3. 開啟 WPF 相片檢視器示範 > C# 資料夾，選擇 photoapp.sln 檔案，並選取**開啟**。

     在 Visual Studio 中，開啟專案。 在右窗格中的 [方案總管] 會顯示所有專案檔。

    ![方案總管檔](../debugger/media/dbg-tour-solution-explorer.png "方案總管")

4. 按下 F5 (**偵錯 > 開始偵錯**或**開始偵錯**按鈕![開始偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")偵錯 工具列中)。

     ![相片檢視器應用程式](../debugger/media/dbg-tour-wpf-app.png "相片檢視器應用程式")

     F5 啟動偵錯工具附加至應用程式的程序，但右邊，現在我們尚未加入任何中斷點，或執行任何特殊作業，檢查程式碼的應用程式。 因此應用程式只會載入，而且您看見相片影像。

     在此教學課程中，我們將探討這個應用程式使用偵錯工具，並取得查看偵錯工具的功能。

5. 按下紅色 stop 停止偵錯工具![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯") 按鈕。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>設定中斷點並開始偵錯工具

若要偵錯，您需要偵錯工具附加至應用程式處理序啟動您的應用程式。

1. 在`MainWindow`建構函式的 MainWindow.xaml.cs 中，按一下左邊的界的第一行程式碼中設定中斷點。

     ![設定中斷點](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

6. 按 F5 或**開始偵錯**按鈕，應用程式會啟動，以及偵錯工具執行的程式碼行，您可以設定中斷點。

    黃色箭號表示該陳述式暫停偵錯工具，這也會在相同的點 （此陳述式尚未執行） 的暫停應用程式執行。

    F5 繼續執行應用程式到下一個中斷點。 （如果尚未執行的應用程式，f5 鍵啟動偵錯工具和第一個中斷點停止。）

    當您知道的一行程式碼或您想要檢查詳細資料中的程式碼區段，中斷點會很有用的功能。

## <a name="restart-your-app-quickly"></a>快速地重新啟動您的應用程式

1. 按一下**重新啟動**![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp")中偵錯工具列 （Ctrl + Shift + F5） 按鈕。

    當您按**重新啟動**，它可以節省時間和停止應用程式及重新啟動偵錯工具。 偵錯工具會在叫用時執行程式碼的第一個中斷點上暫停。

    您設定，在中斷點再次停止偵錯工具`MainWindow`建構函式。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>巡覽偵錯工具使用步驟命令的程式碼

大部分，我們使用的鍵盤快速鍵，因為它是一個好的方法，以取得快速在偵錯工具 （對等的命令例如功能表命令會顯示在括號中） 中執行您的應用程式。

1. 請按下 F11 (**偵錯 > 逐步執行**) 兩次，前進到應用程式執行`InitializeComponent()`函式。

     ![使用 F11 逐步執行程式碼](../debugger/media/dbg-tour-f11.png "F11 逐步執行")

     F11 是**逐步執行**命令，並往前移應用程式執行一個陳述式一次。 F11 是檢查大部分的詳細資料中的執行流程的好方法。 （若要更快速移動，透過程式碼，我們會示範一些其他選項也。）根據預設，偵錯工具會略過非使用者程式碼 (如果您想要更多詳細資料，請參閱[Just My Code](../debugger/just-my-code.md))。

     >[!NOTE]
     > 在 managed 程式碼，您會看到對話方塊，詢問您是否要收到通知您自動不進入屬性和運算子 （預設行為）。 如果您想要變更設定之後，停用**不進入屬性和運算子**中設定**工具 > 選項**下的單**偵錯**。

2. 按下 F10 (**偵錯 > 不進入函式**) 幾次，直到在第一行中的程式碼的偵錯工具停止`OnApplicationStartup`事件處理常式。

     ![不進入函式的程式碼使用 F10](../debugger/media/dbg-tour-f10-step-over.png "F10 不進入函式")

     F10 鍵逐步執行函式或方法 （仍執行的程式碼） 的應用程式程式碼中沒有進階偵錯工具。 按下 F10`InitializeComponent`方法呼叫 （而不是 F11)，我們會跳過的實作程式碼`InitializeComponent`（我們正在不感興趣現在的可能）。

## <a name="step-into-a-property"></a>逐步執行屬性

1. 偵錯工具暫停上這行程式碼：

    ````
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    程式碼行上按一下滑鼠右鍵，然後選擇 **逐步執行至特定**，然後**SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![使用特定功能逐步](../debugger/media/dbg-tour-step-into-specific.png "逐步執行至特定")

    如先前所述，根據預設，偵錯工具會略過受管理的屬性和欄位，但**逐步執行至特定**命令可讓您覆寫這個行為。 現在，我們想要看起來會發生什麼事時`Path.set`屬性 setter 執行。 **逐步執行至特定**取得我們`Path.set`以下程式碼。

     ![逐步執行至特定的結果](../debugger/media/dbg-tour-step-into-specific-2.png "逐步執行至特定")

     `Update`方法在此程式碼看起來可能很有趣，如此可讓使用偵錯工具來檢查向上關閉該程式碼。

5. 將滑鼠停留在`Update`方法，直到綠色**按一下執行**按鈕![按一下執行](../debugger/media/dbg-tour-run-to-click.png "RunToClick")出現在左邊。

     ![使用 執行至，請按一下功能](../debugger/media/dbg-tour-run-to-click-2.png "執行，然後按一下")

    >  [!NOTE] 
    > **執行按一下**按鈕的新[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。 如果您沒有看到綠色箭號按鈕，改用 F11 在此範例中前進偵錯工具。

6. 按一下**執行按一下**按鈕![執行按一下](../debugger/media/dbg-tour-run-to-click.png "RunToClick")。

    類似於設定暫時中斷點使用此按鈕。 **按一下以執行**便於快速瀏覽 （您可以按一下任何開啟的檔案） 的應用程式程式碼可見區域內。

    偵錯工具會前往`Update`方法實作。

7. 按 f11 逐步執行`Update`方法。

     ![逐步執行更新方法的結果](../debugger/media/dbg-tour-update-method.png "步驟到 Update 方法")

    在這裡，我們找到某些更多的程式碼看起來很有趣。應用程式會取得所有 *.jpg 檔案位於特定的目錄，並建立每個檔案的相片物件。 此程式碼可讓我們開始檢查您的應用程式狀態 （變數），偵錯工具的好機會。 我們會執行，在本教學課程的下一節。

    功能可讓您檢查變數是其中一個最有用的功能，偵錯工具，而且有不同的方式來進行。 通常，當您嘗試偵錯問題，您會嘗試找出是否變數會儲存您希望他們能夠在特定時間的值。

## <a name="examine-the-call-stack"></a>檢查呼叫堆疊

- 在暫停期間`Update`方法中，按一下 **呼叫堆疊**視窗中，這是預設在右下方的窗格中開啟。

     ![檢查呼叫堆疊](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

    **呼叫堆疊** 視窗會顯示方法和函式會取得呼叫所在的順序。 第一行會顯示目前的函式 (`Update`教學課程應用程式中的方法)。 第二行顯示`Update`呼叫`Path.set`屬性，依此類推。

    >  [!NOTE]
    > **呼叫堆疊**視窗是類似於偵錯觀點來看，某些像 Eclipse Ide 中。

    呼叫堆疊是很好的方式來檢查，並了解應用程式的執行流程。

    您可以按兩下要查看原始程式碼的程式碼行並，也會變更目前正在檢查偵錯工具的範圍。 此動作不前移偵錯工具。

    您也可以使用滑鼠右鍵功能表從**呼叫堆疊**視窗來執行其他動作。 例如，您可以在其中插入指定的函式的中斷點、 前進偵錯工具使用**執行至游標處**，並移檢查原始程式碼。 如需詳細資訊，請參閱[How to： 檢查呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="step-out"></a>跳離函式

假設您已完成檢查`Update`方法中 Data.cs，而且您想要取得移到函式，並且保留在偵錯工具。 您可以使用**跳離函式**命令。

1. 按 Shift + f11 鍵 (或**偵錯 > 跳離函式**)。

     此命令會繼續執行應用程式 （和進階偵錯工具） 直到目前的函式傳回。

     您應該在`Update`中 Data.cs 方法呼叫。

2. 按 Shift + f11 鍵，以及偵錯工具在呼叫堆疊向上移回`OnApplicationStartup`事件處理常式。

## <a name="run-to-cursor"></a>執行至游標處

1. 選擇**停止偵錯**的紅色按鈕![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯")或 Shift + F5。

2. 在`Update`方法中 Data.cs，以滑鼠右鍵按一下`Add`方法呼叫，並選擇**執行至游標處**。 此命令會開始偵錯，並在目前的程式碼行上設定暫時中斷點。

     ![使用 執行至資料指標功能](../debugger/media/dbg-tour-run-to-cursor.png "執行至游標處")

    您應該在中斷點上暫停`MainWindow`（因為這是第一個中斷點您設定）。

3. 按 F5，前進到`Add`方法其中選取**執行至游標處**。

    此命令時，您正在編輯程式碼，而且想要快速地設定暫時中斷點並開始偵錯工具。

## <a name="change-the-execution-flow"></a>變更執行流程

1. 偵錯工具暫停上`Add`呼叫方法時，使用滑鼠來抓取 （執行指標） 的黃色箭號左邊和移動一行來向上的黃色箭頭`foreach`迴圈。

     ![執行將指標移至](../debugger/media/dbg-tour-move-the-execution-pointer.gif "執行將指標移至")

    藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或執行程式碼並不會重新啟動偵錯工具。

2. 現在，請按 F5。

    您可以查看加入至應用程式視窗的映像。 因為您正在重新執行中的程式碼`foreach`兩次已加入迴圈中，某些影像 ！
    
    > [!WARNING]
    > 通常需要謹慎使用這項功能，您會看到工具提示中的警告。 您可能會太看到其他警告。 移動指標無法還原成先前的應用程式狀態的應用程式。

## <a name="inspect-variables-with-data-tips"></a>檢查資料提示使用的變數

1. 開啟 Data.cs 相片檢視器示範應用程式中，以滑鼠右鍵按一下`private void Update`函式宣告，並選擇**執行至游標處**（停止應用程式第一次如果已在執行）。

    這將會附加偵錯工具暫停應用程式。 這可讓我們檢查它的狀態。

2. 將滑鼠停留在`Add`方法呼叫，並按一下**執行按一下**按鈕![執行按一下](../debugger/media/dbg-tour-run-to-click.png "RunToClick")。

3. 現在，將滑鼠停留在 「 檔案 」 物件 (`f`)，並查看其預設屬性值、 檔案名稱`market 031.jpg`。

     ![檢視資料提示方塊](../debugger/media/dbg-tour-data-tips.gif "檢視資料提示方塊")

4. 展開以查看所有內容，例如物件`FullPath`屬性。

    通常，偵錯時，您會想快速檢查物件的屬性值的方法，以及資料提示是很好的方法。

    > [!TIP]
    > 最受支援的語言，您可以編輯程式碼進行偵錯工具工作階段，如果您發現您想要變更的項目。 如需詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。 此應用程式中使用該功能，不過，我們會先更新應用程式的.NET Framework 版本。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>檢查 [自動變數] 和 [區域變數] 視窗的變數

1. 查看**自動變數**底部的程式碼編輯器 視窗。

     ![檢查自動變數 視窗中的變數](../debugger/media/dbg-tour-autos-window.png "自動變數視窗")

    在**自動變數**視窗中，您會看到變數和其目前的值。 **自動變數** 視窗會顯示目前這一行或前一行上使用的所有變數 （在 c + +，視窗會都顯示變數前面三行程式碼中。 檢查語言特定行為的文件）。

    > [!NOTE]
    > 在 JavaScript 中，**區域變數**但不是支援視窗**自動變數**視窗。

2. 接下來，看看**區域變數**視窗。

    **區域變數** 視窗會顯示目前領域中的變數。

    ![檢查 [區域變數] 視窗中的變數](../debugger/media/dbg-tour-locals-window.png "[區域變數] 視窗")

    目前，`this`物件和檔案物件 (`f`) 會在目前範圍中。 如需詳細資訊，請參閱[檢查變數中的 [自動變數] 和 [區域變數] 視窗](../debugger/autos-and-locals-windows.md)。

## <a name="set-a-watch"></a>設定 監看式

1. 在主要的程式碼編輯器視窗中，以滑鼠右鍵按一下 「 檔案 」 物件 (`f`)，然後選擇 **加入監看式**。

    您可以使用**監看式**指定變數 （或運算式），您想要特別注意落在視窗。

    現在，您需要設定上的監看式`File`物件，而且您可以看到其值變更隨著您瀏覽偵錯工具。 不同於其他變數視窗，**監看式**視窗一律會顯示變數您觀賞 （它們灰色時超出範圍）。

2. 上`Add`方法中，按一下綠色![執行按一下](../debugger/media/dbg-tour-run-to-click.png "RunToClick")按鈕一次 （或幾次按下 F11） 中向前`foreach`迴圈。

    ![在變數上設定監看式](../debugger/media/dbg-tour-watch-window.png "監看式視窗")

    您也可能會看到第一張圖片，加入到主視窗的執行範例應用程式，但這會發生在不同的應用程式執行緒，所以映像可能不會顯示尚未。

    如需詳細資訊，請參閱[設定使用監看式和快速監看式視窗的監看式](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>檢查例外狀況

1. 在執行的應用程式視窗中，刪除中的文字**路徑**輸入的方塊，然後選取**變更** 按鈕。

     ![導致擲回例外狀況](../debugger/media/dbg-tour-cause-an-exception.png "造成例外狀況")

     應用程式會擲回的例外狀況，並在偵錯工具會帶您前往發生例外狀況的程式碼行。
     
     ![例外狀況協助程式](../debugger/media/dbg-tour-exception-helper.png "例外狀況協助程式")

     在這裡，**例外狀況協助程式**示範`System.ArgumentException`和錯誤訊息，指出此路徑不是合法的表單。 因此，我們會知道方法或函式的引數發生錯誤。

     在此範例中，`DirectoryInfo`呼叫空白的字串儲存在發生錯誤`value`變數。 (將滑鼠停留在`value`檢視的空白字串。)

     例外狀況協助程式是很棒的功能，可協助您偵錯錯誤。 您也可以執行下列作業檢視錯誤詳細資料，並從例外狀況協助程式加入監看式。 或者，如果需要您可以變更擲回特定例外狀況的條件。

    >  [!NOTE] 
    > 例外狀況協助程式取代了例外狀況助理中[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

2. 展開**例外狀況設定**節點以查看更多選項如何處理此例外狀況類型，但您不需要變更任何項目為本教學課程 ！

3. 按 f5 鍵繼續應用程式。

若要深入了解偵錯工具的功能，請參閱[偵錯工具秘訣和訣竅](../debugger/debugger-tips-and-tricks.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 偵錯](../debugger/index.md)  
[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)

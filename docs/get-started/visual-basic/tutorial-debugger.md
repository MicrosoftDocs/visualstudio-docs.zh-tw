---
title: 教學課程： Debug Visual Basic 程式碼
description: 學習 Visual Studio 偵錯工具的功能，以及如何啟動偵錯工具、逐步執行程式碼，以及檢查 Visual Basic 應用程式中的資料。
ms.custom: debug-experiment, seodec18, get-started
ms.date: 02/03/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- VB
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42dd3c6b7301162e239bc87764056fdda2d08413
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308411"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>教學課程：了解如何使用 Visual Studio 對 Visual Basic 程式碼進行偵錯

本文以逐步解說介紹 Visual Studio 偵錯工具的功能。 如果您希望檢視偵錯工具功能的概要，請參閱[偵錯工具簡介](../../debugger/debugger-feature-tour.md)。 當您「偵錯您的應用程式」，通常表示您正在執行附加偵錯工具的應用程式。 執行此作業時，偵錯工具會提供許多方式來查看您程式碼所執行的功能。 您可以逐步執行程式碼並查看儲存在變數中的值、可以設定變數的監看式以查看值變更、可以檢查程式碼的執行路徑，查看是否正在執行程式碼的分支，依此類推。 如果這是您第一次嘗試偵錯程式碼，您可能需要先閱讀[適用於徹底初學者偵錯](../../debugger/debugging-absolute-beginners.md)，再瀏覽本文。

雖然示範應用程式是 Visual Basic 的，但大部分的功能都適用于 c #、c + +、F #、Python、JavaScript 和其他 Visual Studio 所支援的語言 (F # 不支援編輯後繼續。 F# 和 JavaScript 不支援 [自動變數] 視窗)。 螢幕擷取畫面位於 Visual Basic 中。

在本教學課程中，您將：

> [!div class="checklist"]
> * 啟動偵錯工具，並叫用中斷點。
> * 了解命令以在偵錯工具中逐步執行程式碼
> * 檢查資料提示和偵錯工具視窗中的變數
> * 檢查呼叫堆疊

## <a name="prerequisites"></a>先決條件

::: moniker range=">=vs-2019"

您必須安裝 Visual Studio 2019 和 **.Net Core 跨平臺開發** 工作負載。

::: moniker-end
::: moniker range="vs-2017"

您必須安裝 Visual Studio 2017 和 **.Net Core 跨平臺開發** 工作負載。

::: moniker-end

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2022"

如果您尚未安裝 Visual Studio 2022 Preview，請前往 [Visual Studio 2022 preview 下載](https://visualstudio.microsoft.com/vs/preview/vs2022) 頁面，免費進行安裝。

::: moniker-end

如果您需要安裝工作負載，但已有 Visual Studio，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 Visual Studio 安裝程式即會啟動。 選擇 **.Net Core 跨平臺開發** 工作負載，然後選擇 [ **修改**]。

## <a name="create-a-project"></a>建立專案

首先，您會建立 .NET Core 主控台應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案！

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中 **，選擇 [** 檔案 > **新增** > **專案**]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual Basic]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 然後將專案命名為 *開始使用-調試*。

     如果您沒有看到 [主控台應用程式 (.NET Core)] 專案範本，請在 [新增專案] 對話方塊的左窗格中，選擇 [開啟 Visual Studio 安裝程式] 連結。

     Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。

   如果 [開始] 視窗未開啟，請 **選擇 [** 檔案 > **開始視窗]**。

1. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

1. 在 [建立新專案] 視窗的搜尋方塊中輸入或鍵入 ASP.NET。 接下來，從語言清單中選擇 **Visual Basic**，然後從平台清單中選擇 **Windows**。 

   套用語言和平臺篩選器之後，請選擇適用于 .NET Core 的 **主控台應用程式** 範本，然後選擇 [ **下一步]**。

   ![選擇主控台應用程式的 Visual Basic 範本](../visual-basic/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > 如果您沒有看到 [ **主控台應用程式** ] 範本，您可以從 [ **建立新專案** ] 視窗進行安裝。 在 [找不到您要找的資料嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。 接下來，在 Visual Studio 安裝程式中選擇 **.NET Core 跨平台開發** 工作負載。

1. 在 [**設定您的新專案**] 視窗中，輸入或輸入 [**專案名稱**] 方塊中的 [開始使用 *-偵錯工具*]。 然後選擇 **[下一步]**。

1. 選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。

   Visual Studio 會隨即開啟您的新專案。
   
::: moniker-end

## <a name="create-the-application"></a>建立應用程式

1. 在 *Program* 中，以下列程式碼取代所有的預設程式碼：

    ```vb
    Imports System

    Class ArrayExample
        Public Shared Sub Main()
            Dim letters As Char() = {"f"c, "r"c, "e"c, "d"c, " "c, "s"c, "m"c, "i"c, "t"c, "h"c}
            Dim name As String = ""
            Dim a As Integer() = New Integer(9) {}

            For i As Integer = 0 To letters.Length - 1
                name += letters(i)
                a(i) = i + 1
                SendMessage(name, a(i))
            Next

            Console.ReadKey()
        End Sub

        Private Shared Sub SendMessage(ByVal name As String, ByVal msg As Integer)
            Console.WriteLine("Hello, " & name & "! Count to " & msg)
        End Sub
    End Class
    ```

## <a name="start-the-debugger"></a>啟動偵錯工具！

1. 按 **F5** (**Debug > 開始調試**) **或啟動調試按鈕**![開始](../../debugger/media/dbg-tour-start-debugging.png "[偵錯]")在調試工具列中進行調試。

     **F5** 鍵會啟動應用程式並將偵錯工具附加至應用程式處理序，但目前我們還沒有做任何特別動作來檢查程式碼。 因此應用程式只會載入，且您會看到主控台輸出。

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     在本教學課程中，我們將使用偵錯工具仔細查看這個應用程式，並了解偵錯工具功能。

2. 按下紅色的停止 [停止 ![調試](../../debugger/media/dbg-tour-stop-debugging.png "[停止偵錯]")程式] 按鈕，以停止偵錯工具 (**Shift**  +  **F5**) 。

3. 在主控台視窗中，按下按鍵以關閉主控台視窗。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>設定中斷點，並啟動偵錯工具

1. 在 `Main` 函式的 `For` 迴圈中，按一下下列程式碼行的左邊界來設定中斷點：

    `name += letters(i)`

    當您設定中斷點時，會出現紅色圓形 ![中斷點](../../debugger/media/dbg-breakpoint.png "中斷點") 。

    中斷點是可靠的偵錯工具最基本且最基本的功能之一。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。

2. 按 **F5** 或 [ **開始調試** 程式] 按鈕 ![開始調試](../../debugger/media/dbg-tour-start-debugging.png "[偵錯]")程式，應用程式會啟動，而偵錯工具會執行到您設定中斷點的程式程式碼。

    ![設定並叫用中斷點](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    黃色箭號表示偵錯工具暫停時的陳述式，這也表示會在相同的點暫停執行應用程式 (尚未執行此陳述式)。

     如果尚未執行應用程式，則 **F5** 鍵會啟動偵錯工具並在第一個中斷點停止。 否則，**F5** 鍵會繼續執行應用程式到下一個中斷點。

    如果您知道要詳細檢查的程式碼行或程式碼區段，則中斷點是一個很有用的功能。 如需您可以設定之不同中斷點類型（例如條件式中斷點）的詳細資訊，請參閱 [使用中斷點](../../debugger/using-breakpoints.md)。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>使用逐步執行命令在偵錯工具中巡覽程式碼

在大部分情況下，我們會在這裡使用鍵盤快速鍵，因為這是在偵錯工具中快速執行應用程式的好方法 (功能表命令等對等命令會顯示在括弧內)。

1. 在方法的迴圈中暫停時 `For` `Main` ，請按 **F11** (或選擇 [ **Debug] > [逐步** 執行]) 兩次，以繼續進行 `SendMessage` 方法呼叫。

     按下 **F11** 兩次之後，您應該會在下面這行程式碼：

     `SendMessage(name, a(i))`

1. 再按一次 **F11** ，逐步執行 `SendMessage` 方法。

     黃色指標會前進到 `SendMessage` 方法中。

     ![使用 F11 來逐步執行程式碼](../visual-basic/media/get-started-f11-vb.png "F10 逐步執行")

     F11 鍵是 **逐步執行** 命令，可將應用程式執行一次往前推進一個陳述式。 F11 鍵是以最詳細的方式檢查執行流程的好方法  (透過程式碼更快地移動，我們也會示範一些其他選項 ) 。根據預設，偵錯工具會略過非使用者程式碼 (如果您需要更多詳細資料，請參閱 [Just My Code](../../debugger/just-my-code.md)) 。

     假設您已完成方法的檢查 `SendMessage` ，而您想要退出該方法，但仍留在偵錯工具中。 您可以使用 [跳離函式] 命令完成這項動作。

1. 按 **Shift**  +  **F11** (或 **Debug > 跳出**) 。

     此命令會繼續執行應用程式 (，並在目前的方法或函式傳回之前，將偵錯工具) 前進。

     您應該會回到 `For` 方法中的迴圈，並在 `Main` `SendMessage` 方法呼叫中暫停。

1. 按 **F11** 數次，直到 `SendMessage` 再次回到方法呼叫為止。

1. 在方法呼叫中暫停時，請按 **F10** (或選擇 [ **Debug >** 不進入) 一次]。

     ![使用 F10 來跳過程式碼](../visual-basic/media/get-started-step-over-vb.png "F10 跳過")

     請注意，這次偵錯工具不會逐步執行 `SendMessage` 方法。 **F10** 鍵會推進偵錯工具，而不需要逐步執行應用程式程式碼中的函式或方法 (此程式碼仍會執行)。 藉由在 `SendMessage` 方法呼叫上按 **F10** 鍵 (而非 **F11** 鍵)，我們略過了 `SendMessage` 的實作程式碼 (現在對我們不太重要)。 如需在程式碼中移動不同方式的詳細資訊，請參閱在 [偵錯工具中流覽程式碼](../../debugger/navigating-through-code-with-the-debugger.md)。

## <a name="navigate-code-using-run-to-click"></a>使用 [執行至點選處] 來巡覽程式碼

1. 按 **F5** 再次前進至中斷點。

1. 在 [程式碼編輯器] 中，將滑鼠游標移到方法中的方法上，直到出現綠色的 [執行] 按鈕，然後 `Console.WriteLine` `SendMessage` 按一下 [![執行](../../debugger/media/dbg-tour-run-to-click.png ">runtoclick")] 按鈕才會出現在左邊。  按鈕的工具提示會顯示「執行到這裡」。

     ![使用執行至按一下功能](../visual-basic/media/get-started-run-to-click-vb.png "執行至點選處")

   > [!NOTE]
   > [執行至點選處] 按鈕是 [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] 的新功能。  (如果您沒有看到綠色箭號按鈕，請使用此範例中的 **F11** 來將偵錯工具移至正確的位置。 ) 

2. 按一下 [ **執行** ] 按鈕 ![執行以](../../debugger/media/dbg-tour-run-to-click.png ">runtoclick")按一下。

    偵錯工具會前進到 `Console.WriteLine` 方法。

    使用此按鈕類似於設定暫時中斷點。 [執行至點選處] 方便您在應用程式程式碼的可見區域內快速瀏覽 (您可以按一下任何開啟的檔案)。

## <a name="restart-your-app-quickly"></a>快速重新啟動您的應用程式

按一下偵錯工具列中的 [**重新** 啟動 ![重新開機應用程式](../../debugger/media/dbg-tour-restart.png ">restartapp")] 按鈕， (**Ctrl**  +  **Shift**  +  **F5**) 。

相對於停止應用程式並重新啟動偵錯工具，按下 [重新啟動] 可讓您節省時間。 偵錯工具會在執行程式碼叫用的第一個中斷點處暫停。

偵錯工具會在您先前在迴圈內部設定的中斷點停止 `For` 。

## <a name="inspect-variables-with-data-tips"></a>使用資料提示來檢查變數

可讓您檢查變數的功能是偵錯工具最實用功能之一，而且有不同的方法來完成此作業。 通常當您嘗試偵錯問題時，您會嘗試確定變數是否會儲存您希望其在特定時間具有的值。

1. 在語句上暫停時 `name += letters[i]` ，將滑鼠停留在變數上， `letters` 您會看到它是預設值，也就是陣列中第一個元素的值 `"f"c` 。

1. 接下來，將滑鼠停留在 `name` 變數上，您會看到其目前的值，也就是空字串。

1. 按 **F5** (或 **Debug**  >  **Continue**) 幾次，以逐一 `For` 查看迴圈中的數次、在中斷點再次暫停，並在變數上 `name` 每次檢查其值時將滑鼠停留在變數上。

     ![查看資料提示](../visual-basic/media/get-started-data-tip-vb.png "查看資料提示")

     變數的值會隨著迴圈的每個反復專案而改變 `For` ，並顯示的值、then、等等 `f` `fr` `fre` 。

     很多時候，您會希望在偵錯時快速檢查變數的屬性值，以查看其是否如您預期的儲存值，而資料提示是很適合的方法。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>使用 [自動變數] 和 [區域變數] 視窗來檢查變數

1. 查看程式碼編輯器底部的 [自動變數] 視窗。

    如果已關閉，請選擇 [ **Debug** Windows 自動變數]，以在偵錯工具中暫停時開啟該檔案  >    >  ****。

    在 [自動變數] 視窗中，您會看到變數及其目前的值。 [自動變數] 視窗會顯示在目前行或前述行 (請查看文件以了解語言特定行為) 中使用的所有變數。

1. 接下來，在 [自動變數] 視窗旁的索引標籤中查看 [區域變數] 視窗。

1. 展開 `letters` 變數以顯示其包含的元素。

     ![檢查 [區域變數] 視窗中的變數](../visual-basic/media/get-started-locals-window-vb.png "本機視窗")

    [區域變數] 視窗會顯示位在目前[範圍](https://www.wikipedia.org/wiki/Scope_(computer_science))中的變數，即為目前執行內容。

## <a name="set-a-watch"></a>設定監看式

1. 在主要程式碼編輯器視窗中，以滑鼠右鍵按一下 `name` 變數，然後選擇 [ **加入監看式]**。

    [監看式] 視窗隨即在程式碼編輯器底部開啟。 您可以使用 [監看式] 視窗來指定您要留意的變數 (或運算式)。

    現在，您已在變數上設定監看式 `name` ，當您在偵錯工具中移動時，您可以看到其值變更。 不同於其他變數視窗，[監看式] 視窗一律會顯示所監看的變數 (它們在超出範圍時會呈現灰色)。

## <a name="examine-the-call-stack"></a>檢查呼叫堆疊

1. 在 `For` 迴圈中暫停時，按一下 [呼叫堆疊] 視窗，此視窗預設會在右下方的窗格中開啟。

    如果已關閉，請選擇 [ **Debug**  >  **Windows**  >  **呼叫堆疊**]，以在偵錯工具中暫停時開啟該檔案。

2. 按一下 **F11** 幾次，直到您看到偵錯工具在方法中暫停為止 `SendMessage` 。 查看 [呼叫堆疊] 視窗。

    ![檢查呼叫堆疊](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

    [呼叫堆疊] 視窗會顯示方法和函式的呼叫順序。 第一行會顯示目前的函式 (此應用程式中的 `SendMessage` 方法)。 第二行會顯示已從 `Main` 方法呼叫 `SendMessage`，依此類推。

   > [!NOTE]
   > [呼叫堆疊] 視窗類似於某些 IDE (例如 Eclipse) 中的 [偵錯] 檢視方塊。

    呼叫堆疊是檢查並了解應用程式執行流程的好方法。

    您可以按兩下某一行的程式碼來查看其原始程式碼，這也會變更偵錯工具所檢查的目前範圍。 此動作不會讓偵錯工具往前推進。

    您也可以從 [呼叫堆疊] 視窗使用滑鼠右鍵功能表來執行其他動作。 例如，您可以在指定的函式中插入中斷點，使用 [執行至游標處] 讓偵錯工具往前推進，並檢查原始程式碼。 如需詳細資訊，請參閱[如何：檢查呼叫堆疊](../../debugger/how-to-use-the-call-stack-window.md)。

## <a name="change-the-execution-flow"></a>變更執行流程

1. 按 **F11** 兩次以執行 `Console.WriteLine` 方法。

1. 當偵錯工具在方法呼叫中暫停時 `SendMessage` ，請使用滑鼠抓取左側的黃色箭號 (執行指標) 左邊，然後將黃色箭號向左移動一行 `Console.WriteLine` 。

1. 按 **F11** 鍵。

    偵錯工具會重新執行 `Console.WriteLine` 方法 (您會在主控台視窗輸出中看到)。

    藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或重新執行程式碼而不重新啟動偵錯工具。

    > [!WARNING]
    > 您通常需要謹慎使用這項功能，您會在工具提示中看到一則警告。 也可能會看到其他警告。 移動指標無法將應用程式還原成先前的應用程式狀態。

1. 按 **F5** 鍵繼續執行應用程式。

    恭喜您完成此教學課程！

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何啟動偵錯工具、逐步執行程式碼，以及檢查變數。 建議您進一步查看偵錯工具功能，以及詳細資訊的連結。

> [!div class="nextstepaction"]
> [偵錯工具簡介](../../debugger/debugger-feature-tour.md)

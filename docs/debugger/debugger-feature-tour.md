---
title: 偵錯工具簡介
description: 快速看看不同的 Visual Studio 偵錯工具的功能。
ms.custom: mvc
ms.date: 03/27/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de27a6b3fd5b182ac2fa0ad12ed04e4d1105d9ac
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691088"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>初探 Visual Studio 偵錯工具

本主題將介紹 Visual Studio 偵錯工具的功能。 如果您想要跟著做 Visual Studio 中開啟您自己的應用程式，您可以這樣做，或您可以依照範例應用程式使用[初級開發人員指南](../debugger/getting-started-with-the-debugger.md)。

這裡說明的功能都適用於 C#、 c + +、 Visual Basic、 JavaScript 和 Visual Studio （除非註明） 支援其他語言。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>設定中斷點並開始偵錯工具

若要偵錯，您需要偵錯工具附加至應用程式處理序啟動您的應用程式。 F5 (**偵錯 > 開始偵錯**) 是最常見的方法。 不過，現在您可以設定任何中斷點來檢查您的應用程式的程式碼，因此我們會先執行，然後開始偵錯。

如果您有程式碼編輯器中開啟的檔案，您可以按一下程式碼行的左邊界來設定中斷點。

![設定中斷點](../debugger/media/dbg-tour-set-a-breakpoint.gif "設定中斷點")

按下 F5 (**偵錯 > 開始偵錯**) 和偵錯工具執行到它遇到第一個中斷點。 如果應用程式尚未執行，F5 啟動偵錯工具，並在第一個中斷點停止。

當您知道的一行程式碼或您想要檢查詳細資料中的程式碼區段，中斷點會很有用的功能。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>巡覽偵錯工具使用步驟命令的程式碼

因為它們可讓瀏覽應用程式程式碼的速度較快，我們提供的大部分命令的鍵盤快速鍵。 （對等命令例如功能表命令會顯示在括號中）。

若要附加偵錯工具中啟動應用程式，請按 F11 (**偵錯 > 逐步執行**)。 F11 是**逐步執行**命令，並往前移應用程式執行一個陳述式一次。 當您使用 F11 應用程式時，偵錯工具會中斷執行的第一個陳述式。

![F11 逐步執行](../debugger/media/dbg-tour-f11.png "F11 逐步執行")

黃色箭號表示該陳述式暫停偵錯工具，這也會在相同的點 （此陳述式尚未執行） 的暫停應用程式執行。

F11 是檢查大部分的詳細資料中的執行流程的好方法。 （若要更快速移動，透過程式碼，我們會示範一些其他選項也。）根據預設，偵錯工具會略過非使用者程式碼 (如果您想要更多詳細資料，請參閱[Just My Code](../debugger/just-my-code.md))。

>[!NOTE]
> 在 managed 程式碼，您會看到對話方塊，詢問您是否要收到通知您自動不進入屬性和運算子 （預設行為）。 如果您想要變更設定之後，停用**不進入屬性和運算子**中設定**工具 > 選項**下的單**偵錯**。

## <a name="step-over-code-to-skip-functions"></a>不進入程式碼以略過函式

當您的函式或方法呼叫的程式碼行上，您可以按下 F10 (**偵錯 > 不進入函式**) 而不是 F11。

F10 鍵逐步執行函式或方法 （仍執行的程式碼） 的應用程式程式碼中沒有進階偵錯工具。 按 F10，則可略過您不感興趣的程式碼。 如此一來，您可以快速地取得您會更感興趣的程式碼。

## <a name="step-into-a-property"></a>逐步執行屬性

如先前所述，根據預設，偵錯工具會略過受管理的屬性和欄位，但**逐步執行至特定**命令可讓您覆寫這個行為。

屬性或欄位上按一下滑鼠右鍵，然後選擇 **逐步執行至特定**，然後選擇其中一個可用的選項。

![逐步執行特定](../debugger/media/dbg-tour-step-into-specific.png "逐步執行至特定")

在此範例中，**逐步執行至特定**代碼，以取得我們`Path.set`。

![逐步執行特定](../debugger/media/dbg-tour-step-into-specific-2.png "逐步執行至特定")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>執行快速地使用滑鼠的程式碼中的點

在 偵錯工具，將滑鼠停留在一行程式碼，直到**執行按一下**（執行的執行到此處） 按鈕![按一下執行](../debugger/media/dbg-tour-run-to-click.png "RunToClick")出現在左邊。

![按一下以執行](../debugger/media/dbg-tour-run-to-click-2.png "執行，然後按一下")

> [!NOTE]
> **執行按一下**的新功能 （執行的執行到此處） 按鈕[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

按一下**執行按一下**（執行的執行到此處） 按鈕。 偵錯工具將前移至下一行程式碼您所按的位置。

類似於設定暫時中斷點使用此按鈕。 此命令也是很方便用來快速瀏覽應用程式程式碼可見區域內。 您可以使用**執行按一下**任何開啟的檔案中。

## <a name="advance-the-debugger-out-of-the-current-function"></a>進階偵錯工具，移到目前函式

有時候，您可能想要繼續您的偵錯工作階段，但向前移動，目前的函式偵錯工具。

按 Shift + f11 鍵 (或**偵錯 > 跳離函式**)。

此命令會繼續執行應用程式 （和進階偵錯工具） 直到目前的函式傳回。

## <a name="run-to-cursor"></a>執行至游標處

按下停止偵錯工具**停止偵錯**的紅色按鈕![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯")或 Shift + F5。

以滑鼠右鍵按一下您的應用程式中的程式碼行，然後選擇 **執行至游標處**。 此命令會開始偵錯，並在目前的程式碼行上設定暫時中斷點。

![執行至游標處](../debugger/media/dbg-tour-run-to-cursor.png "執行至游標處")

如果您已設定中斷點，偵錯工具會暫停它遇到第一個中斷點。

按 f5 鍵，直到您到達您選取其中一行程式碼**執行至游標處**。

此命令時，您正在編輯程式碼，而且想要快速地設定暫時中斷點並開始偵錯工具。

> [!NOTE]
> 您可以使用**執行至游標處**中**呼叫堆疊**您偵錯時的視窗。

## <a name="restart-your-app-quickly"></a>快速地重新啟動您的應用程式

按一下**重新啟動**![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "重新啟動應用程式")中偵錯工具列按鈕 (**Ctrl + Shift + F5**)。

當您按**重新啟動**，它可以節省時間和停止應用程式及重新啟動偵錯工具。 偵錯工具會在叫用時執行程式碼的第一個中斷點上暫停。

如果您想要停止偵錯工具，並重新進入程式碼編輯器中，您可以按紅色停止![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯")按鈕而非**重新啟動**。

## <a name="inspect-variables-with-data-tips"></a>檢查資料提示使用的變數

您現在知道您的工作環境一點，您已開始檢查您的應用程式狀態 （變數），偵錯工具的好機會。 功能可讓您檢查變數是一些最實用的功能，偵錯工具，而且有不同的方式來進行。 通常，當您嘗試偵錯問題，您會嘗試找出是否變數會儲存您希望他們能夠在特定應用程式狀態的值。

暫停偵錯工具後，將滑鼠停留在滑鼠的物件，並查看其預設屬性值 (在此範例中，檔案名稱`market 031.jpg`預設屬性值)。

![檢視資料提示方塊](../debugger/media/dbg-tour-data-tips.gif "檢視資料提示方塊")

展開以查看其所有屬性的物件 (例如`FullPath`屬性在此範例中)。

通常，偵錯時，您會想快速檢查物件的屬性值的方法，以及資料提示是很好的方法。

> [!TIP]
> 最受支援的語言，您可以編輯程式碼進行偵錯工作階段。 如需詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>檢查 [自動變數] 和 [區域變數] 視窗的變數

偵錯時，看看**自動變數**底部的程式碼編輯器 視窗。

![[自動變數] 視窗](../debugger/media/dbg-tour-autos-window.png "自動變數視窗")

在**自動變數**視窗中，您會看到沿著其目前值和其類型的變數。 **自動變數** 視窗會顯示目前這一行或前一行上使用的所有變數 （在 c + +，視窗會都顯示變數前面三行程式碼中。 檢查語言特定行為的文件）。

> [!NOTE]
> 在 JavaScript 中，**區域變數**但不是支援視窗**自動變數**視窗。

接下來，看看**區域變數**視窗。 **區域變數** 視窗會顯示目前在範圍中的變數。

![[區域變數] 視窗](../debugger/media/dbg-tour-locals-window.png "[區域變數] 視窗")

在此範例中，`this`物件和物件`f`範圍中。 如需詳細資訊，請參閱[檢查變數中的 [自動變數] 和 [區域變數] 視窗](../debugger/autos-and-locals-windows.md)。

## <a name="set-a-watch"></a>設定 監看式

您可以使用**監看式**指定變數 （或運算式），您想要特別注意落在視窗。

偵錯時，以滑鼠右鍵按一下物件，然後選擇 **加入監看式**。

![監看式視窗](../debugger/media/dbg-tour-watch-window.png "監看式視窗")

在此範例中，您必須上設定的監看式`f`物件，而且您可以看到其值變更隨著您瀏覽偵錯工具。 不同於其他變數視窗，**監看式**windows 永遠顯示變數您觀賞 （它們灰色時超出範圍）。

如需詳細資訊，請參閱[設定使用監看式和快速監看式視窗的監看式](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>檢查呼叫堆疊

按一下**呼叫堆疊**視窗時您正在偵錯，這是預設在右下方的窗格中開啟。

![檢查 呼叫堆疊](../debugger/media/dbg-tour-call-stack.png "檢查呼叫堆疊")

**呼叫堆疊** 視窗會顯示方法和函式會取得呼叫所在的順序。 第一行會顯示目前的函式 (`Update`方法在此範例中)。 第二行顯示`Update`呼叫`Path.set`屬性，依此類推。 呼叫堆疊是很好的方式來檢查，並了解應用程式的執行流程。

> [!NOTE]
> **呼叫堆疊**視窗是類似於偵錯觀點來看，某些像 Eclipse Ide 中。

您可以按兩下要查看原始程式碼的程式碼行並，也會變更目前正在檢查偵錯工具的範圍。 偵錯工具不會前進。

您也可以使用滑鼠右鍵功能表從**呼叫堆疊**視窗來執行其他動作。 例如，您可以插入到特定的函式的中斷點、 重新啟動您的應用程式使用**執行至游標處**，並移檢查原始程式碼。 請參閱[How to： 檢查呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="examine-an-exception"></a>檢查例外狀況

當您的應用程式擲回例外狀況時，偵錯工具會帶您前往發生例外狀況的程式碼行。

![例外狀況協助程式](../debugger/media/dbg-tour-exception-helper.png "例外狀況協助程式")

在此範例中，**例外狀況協助程式**示範`System.Argument`例外狀況和錯誤訊息，指出此路徑不是合法的表單。 因此，我們會知道方法或函式的引數發生錯誤。

在此範例中，`DirectoryInfo`呼叫空白的字串儲存在發生錯誤`value`變數。

例外狀況協助程式是很棒的功能，可協助您偵錯錯誤。 您也可以執行下列作業檢視錯誤詳細資料，並從例外狀況協助程式加入監看式。 或者，如果需要您可以變更擲回特定例外狀況的條件。

>  [!NOTE]
> 例外狀況協助程式取代了例外狀況助理中[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

展開**例外狀況設定**節點以查看更多選項如何處理此例外狀況類型，但您不需要變更任何項目為本教學課程 ！

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>偵錯即時 Azure App Service 中的 ASP.NET 應用程式

**快照偵錯工具**您感興趣的程式碼執行時，會在實際執行應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

![啟動快照集偵錯工具](../debugger/media/snapshot-launch.png "啟動快照集偵錯工具")

使用 Azure App Service 中執行的 ASP.NET 應用程式的快照集的集合。 ASP.NET 應用程式必須執行.NET Framework 4.6.1 或更新版本，且必須.NET Core 2.0 或更新版本的 Windows 上執行 ASP.NET Core 應用程式。

如需詳細資訊，請參閱[即時使用快照集偵錯工具的 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)。

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>檢視快照集具有 IntelliTrace 步驟回 (Visual Studio Enterprise)

**IntelliTrace 步驟後**自動快照的應用程式在每個中斷點和偵錯工具事件步驟。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

您可以使用[偵錯] 工具列的 [逐步返回] 和 [逐步前進] 按鈕，來巡覽及檢視快照集。 這些按鈕可巡覽出現在 [診斷工具] 視窗之 [事件] 索引標籤中的事件。

![逐步執行向後和向前按鈕](../debugger/media/intellitrace-step-back-icons-description.png  "步驟向後和向前按鈕")

如需詳細資訊，請參閱[使用 IntelliTrace 回溯檢視快照集](../debugger/how-to-use-intellitrace-step-back.md)頁面。

## <a name="next-steps"></a>後續步驟

在本教學課程，過許多偵錯工具的功能概覽。 您可以使用範例應用程式的這些功能更深入探討

> [!div class="nextstepaction"]
> [了解使用 Visual Studio 進行偵錯](../debugger/getting-started-with-the-debugger.md)

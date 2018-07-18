---
title: 開始使用 VS 2017 中的偵錯
description: 開始偵錯使用 Visual Studio 偵錯工具的應用程式
ms.custom: mvc
ms.date: 06/15/2018
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
ms.openlocfilehash: 7a6d0354e7e7c5f59c070baa6e6913d85cf7c06d
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433544"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>搶先了解 Visual Studio 偵錯工具

本主題將介紹 Visual Studio 所提供的偵錯工具。 在 Visual Studio 中，當您*偵錯您的應用程式*，通常表示您正在附加偵錯工具執行應用程式 (也就是在偵錯工具模式中)。 當您這樣做時，偵錯工具會提供許多方式來看看您的程式碼如何在執行。 您可以逐步執行程式碼，並查看儲存在變數中的值，您可以設定變數值變更時，請參閱監看式、 您可以檢查您的程式碼的執行路徑 et al。如果這是您嘗試偵錯程式碼的第一次，您可能想要閱讀[偵錯適用於徹底初學者](../debugger/debugging-absolute-beginners.md)再進行本主題。

此處所述的功能都適用於 C#、 c + +、 Visual Basic、 JavaScript 和 Visual Studio （除了註明） 支援其他語言項目。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>設定中斷點並開始偵錯工具

若要偵錯，您需要偵錯工具附加至應用程式處理序啟動您的應用程式。 **F5** (**偵錯 > 啟動偵錯**) 是最常見的方式，若要這麼做。 不過，現在您可以設定任何中斷點，以檢查您的應用程式的程式碼，因此我們會先執行，然後啟動偵錯。 中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。 

如果您有程式碼編輯器中開啟的檔案時，您可以設定中斷點的程式碼行左邊界中按一下。

![設定中斷點](../debugger/media/dbg-tour-set-a-breakpoint.gif "設定中斷點")

按下**F5** (**偵錯 > 啟動偵錯**) 或**開始偵錯**按鈕![開始偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")中偵錯 工具列中，並遇到的第一個中斷點來偵錯工具執行。 如果尚未執行的應用程式，F5 啟動偵錯工具，並在第一個中斷點停止。

當您知道程式碼行或您想要詳細檢查的程式碼的區段時，中斷點會是很有用的功能。

## <a name="navigate"></a> 使用逐步執行命令的偵錯工具中巡覽程式碼

因為它們可讓應用程式程式碼的瀏覽更快速，我們可以提供的大部分命令的鍵盤快速鍵。 （對等命令例如功能表命令會顯示在括號中）。

若要附加偵錯工具啟動應用程式，請按**F11** (**偵錯 > 逐步執行**)。 是 F11**逐步執行**命令，並往前推進應用程式執行一個陳述式一次。 當您啟動應用程式使用 F11 時，取得執行的第一個陳述式會中斷偵錯工具。

![F11 逐步執行](../debugger/media/dbg-tour-f11.png "F11 逐步執行")

黃色箭號表示陳述式的偵錯工具暫停時，這也會在相同的點 （此陳述式尚未執行） 的暫停應用程式執行。

F11 是檢查大部分的詳細資料中的執行流程的好方法。 （若要更快速移動，透過程式碼，我們將示範一些其他選項。）根據預設，偵錯工具會略過非使用者程式碼 (如果您想要更多詳細資料，請參閱[Just My Code](../debugger/just-my-code.md))。

>[!NOTE]
> 在 managed 程式碼，您會看到對話方塊，詢問您是否要在您自動不進入屬性和運算子 （預設行為） 時收到通知。 如果您想要變更此設定之後，停用**不進入屬性和運算子**中設定**工具 > 選項**下的功能表**偵錯**。

## <a name="step-over-code-to-skip-functions"></a>不進入程式碼以略過函式

當您在函式或方法呼叫的程式碼行上，您可以按下**F10** (**偵錯 > 不進入函式**) 而不是 f11 鍵。

F10 進階偵錯工具，而不需要逐步執行函式或方法，應用程式程式碼 （仍執行的程式碼）。 按 F10，則可略過您不感興趣的程式碼。 如此一來，您可以快速地取得您感興趣的程式碼。

## <a name="step-into-a-property"></a>逐步執行屬性

如前文所述，根據預設，偵錯工具會略過受管理的屬性和欄位，但**逐步執行至特定**命令可讓您覆寫這個行為。

以滑鼠右鍵按一下屬性或欄位，然後選擇 **逐步執行至特定**，然後選擇其中一個可用的選項。

![逐步執行特定](../debugger/media/dbg-tour-step-into-specific.png "逐步執行至特定")

在此範例中，**逐步執行至特定**代碼，以取得我們`Path.set`。

![逐步執行特定](../debugger/media/dbg-tour-step-into-specific-2.png "逐步執行至特定")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>使用滑鼠來快速程式碼中的點執行

在 [偵錯工具，停留在一行程式碼，直到**執行至點選處**（執行到這裡）] 按鈕![執行至點選處](../debugger/media/dbg-tour-run-to-click.png "RunToClick")出現在左邊。

![執行至點選處](../debugger/media/dbg-tour-run-to-click-2.png "執行至點選處")

> [!NOTE]
> **執行至點選處**的新功能 （執行到這裡） 按鈕[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

按一下 [**執行至點選處**（執行到這裡）] 按鈕。 偵錯工具將前移至下一行程式碼您所按的位置。

使用此按鈕，類似於設定暫時中斷點的。 此命令也是方便快速瀏覽應用程式程式碼可見區域內。 您可以使用**執行至點選處**任何開啟的檔案中。

## <a name="advance-the-debugger-out-of-the-current-function"></a>進入偵錯工具，從目前的函式

有時候，您可能要繼續您的偵錯工作階段，但讓偵錯工具，一直到目前的函式。

按下**Shift + F11** (或**偵錯 > 跳離函式**)。

此命令會繼續應用程式執行 （並往前推進偵錯工具） 直到目前的函式傳回。

## <a name="run-to-cursor"></a>執行至游標處

停止偵錯工具，藉由按下**停止偵錯**紅色按鈕![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯")或是**Shift**  + **F5**。

以滑鼠右鍵按一下您的應用程式中的程式碼行，然後選擇 **執行至游標處**。 此命令會啟動偵錯，並在目前這一行程式碼中設定暫時中斷點。

![執行至游標處](../debugger/media/dbg-tour-run-to-cursor.png "執行至游標處")

如果您已設定中斷點，偵錯工具會在第一個達到的中斷點上暫停。

按下**F5**直到您到達您所選取的其中一行程式碼**執行至游標處**。

您正在編輯程式碼，而且想要快速設定暫時中斷點，並在此同時開始偵錯工具時，則此命令會很有用。

> [!NOTE]
> 您可以使用**執行至游標處**中**呼叫堆疊**視窗時進行偵錯。

## <a name="restart-your-app-quickly"></a>快速重新啟動您的應用程式

按一下**重新啟動**![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "重新啟動應用程式")中偵錯工具列按鈕 (**Ctrl + Shift + F5**)。

當您按下**重新啟動**，節省時間與停止應用程式，並重新啟動偵錯工具。 偵錯工具會在叫用時執行程式碼的第一個中斷點暫停。

如果您想要停止偵錯工具，以取回程式碼編輯器中，您可以按下的紅色的停駐![停止偵錯](../debugger/media/dbg-tour-stop-debugging.png "停止偵錯")按鈕，而非**重新啟動**。

## <a name="inspect-variables-with-data-tips"></a>檢查資料提示中使用的變數

既然您已經知道您的工作環境一點，您會有即可開始檢查您的應用程式狀態 （變數），偵錯工具的好機會。 功能可讓您檢查變數是一些最實用的功能，在偵錯工具，而且有不同的方式來進行。 通常，當您嘗試偵錯問題，您會嘗試找出是否變數會儲存您預期的方式在特定的應用程式狀態中的值。

當偵錯工具暫停時，將滑鼠移至的物件，使用滑鼠，您會看到它的預設屬性值 (在此範例中，檔案名稱`market 031.jpg`是預設屬性值)。

![檢視資料提示](../debugger/media/dbg-tour-data-tips.gif "檢視資料提示方塊")

展開以查看其所有屬性的物件 (例如`FullPath`在此範例中的屬性)。

通常，偵錯時，您希望能很快地檢查屬性值的物件，而且資料提示很適合用來執行它。

> [!TIP]
> 最受支援的語言，您可以編輯程式碼偵錯工作階段的中間。 如需詳細資訊，請參閱 <<c0> [ 編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>檢查變數與 [自動變數] 和 [區域變數] 視窗

偵錯時，看看**自動變數**底部的程式碼編輯器 視窗。

![[自動變數] 視窗](../debugger/media/dbg-tour-autos-window.png "自動變數視窗")

在 [**自動變數**] 視窗中，您會看到沿著其目前的值和其類型的變數。 **自動變數**視窗會顯示目前這一行或上述列上使用的所有變數 （c + + 中，視窗會都顯示變數前面的三行程式碼中。 檢查特定語言行為的文件）。

> [!NOTE]
> 在 JavaScript 中，**區域變數**但不是支援 視窗**自動變數**視窗。

接下來，看看**區域變數**視窗。 **區域變數**視窗會顯示目前在範圍內的變數。

![[區域變數] 視窗](../debugger/media/dbg-tour-locals-window.png "[區域變數] 視窗")

在此範例中，`this`物件和物件`f`範圍內。 如需詳細資訊，請參閱 <<c0> [ 檢查變數，在 [自動變數] 和 [區域變數] Windows](../debugger/autos-and-locals-windows.md)。

## <a name="set-a-watch"></a>設定監看式

您可以使用**監看式**視窗上，指定變數 （或運算式），您要留意。

偵錯時，請以滑鼠右鍵按一下物件，然後選擇 **新增監看式**。

![監看式視窗](../debugger/media/dbg-tour-watch-window.png "監看式視窗")

在此範例中，您有上設定監看式`f`物件，而您可以看到當您瀏覽偵錯工具變更其值。 不同於其他變數視窗中，**監看式**windows 永遠顯示的變數，您所監看 （它們呈現灰色時超出範圍）。

如需詳細資訊，請參閱[設定使用監看式及快速監看式 Windows 監看式](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>檢查呼叫堆疊

按一下 **呼叫堆疊**視窗時進行偵錯，也就是預設在右下方的窗格中開啟。

![檢查 呼叫堆疊](../debugger/media/dbg-tour-call-stack.png "檢查呼叫堆疊")

**呼叫堆疊**視窗會顯示方法和函式會取得呼叫的順序。 第一行會顯示目前的函式 (`Update`方法在此範例中)。 第二行顯示`Update`已從呼叫`Path.set`屬性，並依此類推。 呼叫堆疊會檢查並了解應用程式的執行流程的好方法。

> [!NOTE]
> **呼叫堆疊**視窗是類似於偵錯觀點來看一些像是 Eclipse Ide 中。

您可以按兩下去看看該來源的程式碼的程式碼行，即，也會變更目前正在檢查偵錯工具的範圍。 偵錯工具不前移。

您也可以使用滑鼠右鍵功能表，從**呼叫堆疊**視窗來進行其他動作。 例如，您可以在其中插入特定的函式的中斷點、 重新啟動您的應用程式使用**執行至游標處**，並移檢查原始程式碼。 請參閱[如何： 檢查呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="exception"></a> 檢查例外狀況

當您的應用程式擲回例外狀況時，偵錯工具會帶您前往擲回例外狀況的程式碼行。

![例外狀況協助程式](../debugger/media/dbg-tour-exception-helper.png "例外狀況協助程式")

在此範例中，**例外狀況協助程式**說明`System.Argument`例外狀況和錯誤訊息，指出此路徑不是合法的表單。 因此，我們知道錯誤發生在方法或函式的引數。

在此範例中，`DirectoryInfo`呼叫的協助，空的字串儲存在錯誤`value`變數。

例外狀況協助程式是很棒的功能，可協助您偵錯錯誤。 您也可以執行下列動作檢視錯誤詳細資料，然後從例外狀況協助程式新增監看式。 或者，如果有需要您可以變更條件擲回特定例外狀況。

>  [!NOTE]
> 例外狀況協助程式取代了例外狀況助理中[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

依序展開**例外狀況設定**節點以查看更多選項如何處理此例外狀況類型，但您不需要變更任何項目針對此教學課程 ！

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>偵錯 Azure App Service 中的即時 ASP.NET 應用程式

**快照集偵錯工具**您感興趣的程式碼執行時，會在生產應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

![啟動快照集偵錯工具](../debugger/media/snapshot-launch.png "啟動快照集偵錯工具")

快照集集合適用於 Azure App Service 中執行的 ASP.NET 應用程式。 ASP.NET 應用程式必須執行.NET framework 4.6.1 或更新版本，且必須在.NET Core 2.0 或更新版本 Windows 上執行 ASP.NET Core 應用程式。

如需詳細資訊，請參閱 <<c0> [ 偵錯即時 ASP.NET 應用程式中使用快照集偵錯工具](../debugger/debug-live-azure-applications.md)。

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>檢視快照集，使用 IntelliTrace 倒退 (Visual Studio Enterprise)

**IntelliTrace 回溯**自動快照的應用程式在每個中斷點和偵錯工具逐步執行事件。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

您可以使用[偵錯] 工具列的 [逐步返回] 和 [逐步前進] 按鈕，來巡覽及檢視快照集。 這些按鈕可巡覽出現在 [診斷工具] 視窗之 [事件] 索引標籤中的事件。

![逐步執行向後和向前按鈕](../debugger/media/intellitrace-step-back-icons-description.png  "逐步返回] 和 [向前按鈕")

如需詳細資訊，請參閱[使用 IntelliTrace 回溯檢視快照集](../debugger/how-to-use-intellitrace-step-back.md)頁面。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已經使用許多的偵錯工具功能的概觀。 您可能想要更深入的了解這些功能使用的範例應用程式

> [!div class="nextstepaction"]
> [了解使用 Visual Studio 進行偵錯](../debugger/getting-started-with-the-debugger.md)

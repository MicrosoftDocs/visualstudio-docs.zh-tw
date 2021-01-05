---
title: 偵錯工具簡介
description: 使用 Visual Studio 偵錯工具開始偵錯應用程式
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6d451735042374f0e3c6fb2154cd54520a069fc
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761429"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Visual Studio 偵錯工具初探

本主題將介紹 Visual Studio 所提供的偵錯工具。 在 Visual Studio 內容中，當您「偵錯您的應用程式」，通常表示您正在執行附加偵錯工具的應用程式 (也就是在偵錯工具模式下)。 執行此作業時，偵錯工具會提供許多方式來查看您程式碼所執行的功能。 您可以逐步執行程式碼，並查看儲存在變數中的值，您可以設定變數的監看式以查看值何時變更，您可以檢查程式碼的執行路徑，例如 al。如果這是您第一次嘗試進行程式碼的偵錯工具，您可能會想要先閱讀 [絕對初學者的偵錯工具](../debugger/debugging-absolute-beginners.md) ，再進行本主題。

此處所述的功能適用於 C#、C++、Visual Basic、JavaScript 及 Visual Studio 支援的其他語言 (除非另外註明)。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>設定中斷點，並啟動偵錯工具

若要偵錯，您必須啟動已將偵錯工具附加到應用程式處理序的應用程式。 **F5** 鍵 ([偵錯] > [開始偵錯]) 是執行此作業的最常見方式。 不過，目前您可能尚未設定任何中斷點來檢查應用程式程式碼；因此我們會先執行此作業，再開始偵錯。 中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。

如果您已在程式碼編輯器中開啟檔案，透過按一下程式碼行左側的邊界即可設定中斷點。

![設定中斷點](../debugger/media/dbg-tour-set-a-breakpoint.gif "設定中斷點")

按 **F5** (**Debug > 開始調試** 程式) 或 **啟動偵錯工具按鈕在** 偵錯工具列中 ![啟動調試](../debugger/media/dbg-tour-start-debugging.png "[偵錯]") 程式，偵錯工具會執行到它遇到的第一個中斷點。 如果尚未執行應用程式，則 F5 鍵會啟動偵錯工具並在第一個中斷點停止。

如果您知道要詳細檢查的程式碼行或程式碼區段，則中斷點是一個很有用的功能。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> 使用逐步執行命令在偵錯工具中流覽程式碼

我們提供了大部分命令的鍵盤快速鍵，因為它們可讓應用程式程式碼的巡覽更加快速。 (功能表命令等對等命令會顯示在括弧中)。

若要啟動已附加偵錯工具的應用程式，請按下 **F11** 鍵 ([偵錯] > [逐步執行])。 F11 鍵是 **逐步執行** 命令，可將應用程式執行一次往前推進一個陳述式。 當您使用 F11 鍵啟動應用程式時，偵錯工具會在執行的第一個陳述式上中斷。

![F11 逐步執行](../debugger/media/dbg-tour-f11.png "F11 逐步執行")

黃色箭號表示偵錯工具暫停時的陳述式，這也表示會在相同的點暫停執行應用程式 (尚未執行此陳述式)。

F11 鍵是以最詳細的方式檢查執行流程的好方法  (透過程式碼更快地移動，我們也會示範一些其他選項 ) 。根據預設，偵錯工具會略過非使用者程式碼 (如果您需要更多詳細資料，請參閱 [Just My Code](../debugger/just-my-code.md)) 。

>[!NOTE]
> 在受控程式碼中，您會看到一個對話方塊，詢問您是否要在自動不進入屬性和運算子 (預設行為) 時收到通知。 如果您想要在稍後變更此設定，請在 [工具] > [選項] 功能表的 [偵錯] 下方停用 [不進入屬性和運算子] 設定。

## <a name="step-over-code-to-skip-functions"></a>不進入程式碼以略過函式

當您位在函式或方法呼叫的程式碼行上時，可以按下 **F10** 鍵 ([偵錯] > [不進入函式])，而不是 F11 鍵。

F10 鍵會推進偵錯工具，而不需要逐步執行應用程式程式碼中的函式或方法 (此程式碼仍會執行)。 按下 F10 鍵即可略過您不感興趣的程式碼。 如此一來，您可以快速地取得您更感興趣的程式碼。

## <a name="step-into-a-property"></a>逐步執行屬性

如前文所述，根據預設，偵錯工具會略過受控屬性和欄位，但 [逐步執行至特定處] 命令可讓您覆寫這個行為。

以滑鼠右鍵按一下屬性或欄位，並選擇 [逐步執行至特定處]，然後選擇其中一個可用的選項。

![Visual Studio 偵錯工具的螢幕擷取畫面，其中已反白顯示一行程式碼。 在內容功能表上選取 [逐步執行特定]，並選取 [設定方法]。](../debugger/media/dbg-tour-step-into-specific.png)

在此範例中，[逐步執行至特定處] 會將我們帶到 `Path.set` 的程式碼。

![Visual Studio 偵錯工具的螢幕擷取畫面，其中顯示路徑的程式碼。請設定。 集合函數周圍的大括弧會以黃色反白顯示。](../debugger/media/dbg-tour-step-into-specific-2.png)

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>使用滑鼠快速執行至程式碼中的某一點

在偵錯工具中，將滑鼠停留在程式程式碼上，直到執行 **以按一下** (執行至這裡) 按鈕 ![ 從 Visual Studio 偵錯工具的 [執行] 按鈕的螢幕擷取畫面。 按鈕表示執行應執行至放置按鈕的行。](../debugger/media/dbg-tour-run-to-click.png) 出現在左側。

![Visual Studio 偵錯工具的螢幕擷取畫面，其中顯示 [執行到按一下] 按鈕，顯示在 Update 函式的呼叫左邊。](../debugger/media/dbg-tour-run-to-click-2.png)

> [!NOTE]
> [執行至點選處] (執行到這裡) 按鈕會於 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 開始提供。

按一下 [執行至點選處] (執行到這裡) 按鈕。 偵錯工具將前進至您所點選的程式碼行。

使用此按鈕類似於設定暫時中斷點。 這個命令也方便您在應用程式程式碼的可見區域內快速瀏覽。 您可以在任何開啟的檔案中使用 [執行至點選處]。

## <a name="advance-the-debugger-out-of-the-current-function"></a>在目前的函式外推進偵錯工具

有時候，您可能想要繼續偵錯工作階段，但讓偵錯工具一直推進到目前的函式。

按下 **Shift + F11** (或 [偵錯] > [跳離函式])。

此命令會繼續執行應用程式 (並往前推進偵錯工具)，直到目前的函式傳回為止。

## <a name="run-to-cursor"></a>執行至游標處

當您在偵錯工具) 中編輯程式碼 (而不是暫停時，請以滑鼠右鍵按一下應用程式中的程式程式碼，然後選擇 [ **執行至游標處**]。 此命令會開始偵錯，並在目前這一行程式碼上設定暫時中斷點。

![執行至游標處](../debugger/media/dbg-tour-run-to-cursor.png "執行至游標處")

如果您已設定中斷點，偵錯工具會在第一個叫用的中斷點上暫停。

按下 **F5** 鍵，直到您到達已選取 [執行至游標處] 的程式碼行為止。

如果您正在編輯程式碼，而且想要快速設定暫時中斷點並同時啟動偵錯工具，此命令很有用。

> [!NOTE]
> 您可以在進行偵錯時，於 [呼叫堆疊] 視窗中使用 [執行至游標處]。

## <a name="restart-your-app-quickly"></a>快速重新啟動您的應用程式

按一下偵錯工具列中的 [ **重新** 啟動 ![重新開機應用程式](../debugger/media/dbg-tour-restart.png "重新開機應用程式") ] 按鈕， (**Ctrl + Shift + F5**) 。

相對於停止應用程式並重新啟動偵錯工具，按下 [重新啟動] 可讓您節省時間。 偵錯工具會在執行程式碼叫用的第一個中斷點處暫停。

如果您想要停止偵錯工具並回到 [程式碼編輯器]，您可以按下紅色的停止 [停止 ![調試](../debugger/media/dbg-tour-stop-debugging.png "[停止偵錯]") 程式] 按鈕，而不是 [ **重新開機**]。

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>編輯您的程式碼並繼續進行 (c #、VB、c + +、XAML) 的偵錯工具

在 Visual Studio 所支援的大部分語言中，您可以在偵錯工具的過程中編輯程式碼，並繼續進行偵錯工具。 若要使用這項功能，請在偵錯工具中暫停時，按一下您的程式碼，並進行編輯，然後按 **F5**、 **F10** 或 **F11** 以繼續進行偵錯工具。

![編輯後繼續調試](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

如需使用功能和功能限制的詳細資訊，請參閱 [編輯後繼續](../debugger/edit-and-continue.md)。

若要在偵錯工具期間修改 XAML 程式碼，請參閱 [使用 XAML 熱重新載入撰寫和](../xaml-tools/xaml-hot-reload.md)偵測執行中的 xaml 程式碼。

## <a name="inspect-variables-with-data-tips"></a>使用資料提示來檢查變數

現在您已稍為了解工作環境，接下來正好可以使用偵錯工具開始檢查應用程式狀態 (變數)。 可讓您檢查變數的功能是偵錯工具最實用功能之一，而且有不同的方法來完成此作業。 通常當您嘗試偵錯問題時，您會嘗試確定變數是否會儲存您希望其在特定應用程式狀態具有的值。

在偵錯工具中暫停時，請使用滑鼠將指標移至物件上方，您會看到它的預設屬性值 (在此範例中，檔案名稱 `market 031.jpg` 是預設屬性值)。

![查看資料提示](../debugger/media/dbg-tour-data-tips.gif "查看資料提示")

展開物件以查看其所有屬性 (例如此範例中的 `FullPath` 屬性)。

通常在偵錯時，您希望能夠快速地檢查物件的屬性值，而資料提示很適合用來執行此作業。

> [!TIP]
> 在大部分支援的語言中，您可以在偵錯工作階段期間編輯程式碼。 如需詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>使用 [自動變數] 和 [區域變數] 視窗來檢查變數

進行偵錯時，請查看程式碼編輯器底部的 [自動變數] 視窗。

![自動變數視窗](../debugger/media/dbg-tour-autos-window.png "自動變數視窗")

在 [自動變數] 視窗中，您會看到變數及其目前值和其類型。 [自動變數] 視窗會顯示目前這一行或上一行中使用的所有變數 (在 C++ 中，此視窗會顯示前三行程式碼中的變數。 請參閱文件以了解語言特定行為)。

> [!NOTE]
> 在 JavaScript 中，支援 [區域變數] 視窗，但不支援 [自動變數] 視窗。

接下來，請查看 [區域變數] 視窗。 [區域變數] 視窗會顯示位在目前範圍中的變數。

![本機視窗](../debugger/media/dbg-tour-locals-window.png "[區域變數] 視窗")

在此範例中，`this` 物件和 `f` 物件都在範圍內。 如需詳細資訊，請參閱[在 [自動變數] 和 [區域變數] 視窗中檢查變數](../debugger/autos-and-locals-windows.md)。

## <a name="set-a-watch"></a>設定監看式

您可以使用 [監看式] 視窗來指定您要留意的變數 (或運算式)。

進行偵錯時，請以滑鼠右鍵按一下物件，然後選擇 [新增監看式]。

![監看式視窗](../debugger/media/dbg-tour-watch-window.png "監看式視窗")

在此範例中，您已於 `f` 物件上設定監看式，當您在偵錯工具中移動時，就可以看到其值的變更。 不同於其他變數視窗，[監看式] 視窗一律會顯示所監看的變數 (它們在超出範圍時會呈現灰色)。

如需詳細資訊，請參閱[使用 [監看式] 及 [快速監看式視窗] 設定監看式](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>檢查呼叫堆疊

在您進行偵錯時按一下 [呼叫堆疊] 視窗，此視窗預設會在右下方的窗格中開啟。

![檢查呼叫堆疊](../debugger/media/dbg-tour-call-stack.png "檢查呼叫堆疊")

[呼叫堆疊] 視窗會顯示方法和函式的呼叫順序。 第一行會顯示目前的函式 (此範例中的 `Update` 方法)。 第二行會顯示已從 `Path.set` 屬性呼叫 `Update`，依此類推。 呼叫堆疊是檢查並了解應用程式執行流程的好方法。

> [!NOTE]
> [呼叫堆疊] 視窗類似於某些 IDE (例如 Eclipse) 中的 [偵錯] 檢視方塊。

您可以按兩下某一行的程式碼來查看其原始程式碼，這也會變更偵錯工具所檢查的目前範圍。 這不會讓偵錯工具往前推進。

您也可以從 [呼叫堆疊] 視窗使用滑鼠右鍵功能表來執行其他動作。 例如，您可以在特定的函式中插入中斷點，使用 [執行至游標處] 重新啟動應用程式，並檢查原始程式碼。 請參閱[如何：檢查呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="examine-an-exception"></a><a name="exception"></a> 檢查例外狀況

當您的應用程式擲回例外狀況時，偵錯工具會帶您前往擲回例外狀況的程式碼行。

![例外狀況協助程式](../debugger/media/dbg-tour-exception-helper.png "例外狀況協助程式")

在此範例中，**例外狀況協助程式** 會顯示 `System.Argument` 例外狀況和錯誤訊息，指出此路徑格式不合法。 因此，我們知道方法或函式的引數發生錯誤。

在此範例中，`DirectoryInfo` 呼叫會對儲存在 `value` 變數中的空字串發出錯誤。

例外狀況協助程式是可協助您偵錯錯誤的絶佳功能。 您也可以執行檢視錯誤詳細資料，以及從例外狀況協助程式新增監看式等作業。 或者；如有必要，您可以變更擲回特定例外狀況的條件。 如需如何在程式碼中處理例外狀況的詳細資訊，請參閱[偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)。

> [!NOTE]
> 例外狀況協助程式會取代 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 中開始的例外狀況助理。

請展開 [例外狀況設定] 節點以查看如何處理此例外狀況類型的更多選項，但是您不需要變更此導覽的任何項目！

## <a name="configure-debugging"></a>設定偵錯

您可以將專案設定為以 [Debug 或 Release](../debugger/how-to-set-debug-and-release-configurations.md)設定的形式建立、設定要進行偵錯工具的專案屬性，或設定要進行偵錯工具的 [一般設定](../debugger/how-to-specify-debugger-settings.md) 。 此外，您可以設定偵錯工具，以使用 [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) 屬性等功能或 c/c + + 的 [NatVis 架構](create-custom-views-of-native-objects.md)來顯示自訂資訊。

每個專案類型都有特定的調試屬性。 例如，您可以在啟動應用程式時，指定要傳遞給該應用程式的引數。 您可以用滑鼠右鍵按一下方案總管中的專案，然後選取 [ **屬性**]，來存取專案特定屬性。 調試屬性通常會出現在 [ **組建** ] 或 [ **調試** ] 索引標籤中，視特定的專案類型而定。

![專案屬性](../debugger/media/dbg-tour-project-properties.png "專案屬性")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>偵錯 Azure App Service 中的即時 ASP.NET 應用程式

當您感興趣的程式碼執行時， **快照偵錯工具** 會取得生產環境中應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

![啟動快照偵錯工具](../debugger/media/snapshot-launch.png "啟動快照偵錯工具")

快照集合適用於 Azure App Service 中執行的 ASP.NET 應用程式。 ASP.NET 應用程式必須在 .NET Framework 4.6.1 或更新版本上執行，而 ASP.NET Core 應用程式必須在 Windows 的 .NET Core 2.0 或更新版本上執行。

如需詳細資訊，請參閱[使用快照偵錯工具偵錯即時 ASP.NET 應用程式](../debugger/debug-live-azure-applications.md)。

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>使用 IntelliTrace 回溯檢視快照集 (Visual Studio Enterprise)

**IntelliTrace 回溯** 會自動擷取應用程式在每個中斷點，以及偵錯工具步驟事件的快照。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

您可以使用[偵錯] 工具列的 [逐步返回] 和 [逐步前進] 按鈕，來巡覽及檢視快照集。 這些按鈕可巡覽出現在 [診斷工具] 視窗之 [事件] 索引標籤中的事件。

![逐步執行和向前按鈕](../debugger/media/intellitrace-step-back-icons-description.png  "逐步執行和向前按鈕")

如需詳細資訊，請參閱[使用 IntelliTrace 檢查先前的應用程式狀態](../debugger/view-historical-application-state.md)頁面。

## <a name="debug-performance-issues"></a>Debug 效能問題

如果您的應用程式執行速度太慢或使用過多的記憶體，您可能需要提早流量分析工具測試您的應用程式。 如需分析工具的詳細資訊（例如 CPU 使用量工具和記憶體分析器），請參閱程式碼 [剖析工具的第一看](../profiling/profiling-feature-tour.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已快速瀏覽過許多偵錯工具功能。 建議您深入了解這些功能，例如中斷點。

> [!div class="nextstepaction"]
> [了解如何使用中斷點](../debugger/using-breakpoints.md)

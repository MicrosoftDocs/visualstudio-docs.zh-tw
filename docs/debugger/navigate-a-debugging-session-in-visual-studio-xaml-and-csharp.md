---
title: "巡覽 （Xaml 和 C#） 的 Visual Studio 中偵錯工作階段 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c7679aff620b415a8b3c7f7b226d808d0f3f492
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>在 Visual Studio 中巡覽偵錯工作階段 (Xaml 和 C#)
本快速入門示範如何巡覽 Visual Studio 偵錯工作階段，以及如何檢視與變更工作階段中的程式狀態。  
  
 本快速入門適用於不熟悉使用 Visual Studio 偵錯的開發人員，以及想要深入了解在 Visual Studio 偵錯工作階段中巡覽的開發人員。 它不會教導偵錯本身的藝術。 範例程式碼中的方法僅針對示範本主題中所述的偵錯程序而設計。 這些方法不會採用應用程式或函式設計的最佳作法。 事實上，您很快就會發現這些方法與應用程式本身根本沒有太大功用。  
  
 本快速入門各節的設計盡可能獨立，因此您可以跳過包含您已經熟悉的資訊的任何小節。 您也不需要建立範例應用程式。不過，我們建議您這麼做，因此我們已經讓程序變得盡可能容易。  
  
 **偵錯工具鍵盤快速鍵。** Visual Studio 偵錯工具巡覽已針對滑鼠和鍵盤進行最佳化。 本主題中的許多步驟都會以括號備註的方式加上鍵盤快速鍵。 例如，(鍵盤：F5) 表示輸入 F5 鍵可啟動或繼續偵錯工具的執行。  
  
## <a name="in-this-topic"></a>本主題內容  
 您可以了解如何：  
  
-   [建立範例應用程式](#BKMK_CreateTheApplication)  
  
-   [設定並執行至中斷點、逐步執行方法，以及檢查程式資料](#BKMK_StepInto)  
  
-   [逐步執行、不進入和跳離方法](#BKMK_StepIntoOverOut)  
  
-   [設定條件中斷點、執行至游標處，並將變數視覺化](#BKMK_ConditionCursorVisualize)  
  
-   [編輯後繼續，從例外狀況中復原](#BKMK_EditContinueRecoverExceptions)  
  
##  <a name="BKMK_CreateTheApplication"></a> 建立範例應用程式  
 偵錯與程式碼中，有關，因此範例應用程式僅會使用 UWP 應用程式的架構建立原始程式檔可以看到巡覽偵錯工作階段如何運作以及如何檢查及變更程式狀態。 您將叫用的所有程式碼都是從主頁面的建構函式中呼叫，不會加入任何控制項，也不會處理任何事件。  
  
 **建立預設的 C# UWP 應用程式。** 開啟 Visual Studio。 在首頁上，選擇 [新增專案]  連結。 在 新增專案 對話方塊中，選擇  **Visual C#**中**已安裝**清單，然後選擇**Windows 通用**。 在專案範本清單中選擇**空白應用程式 (通用 Windows)**。 Visual Studio 會建立新的方案和專案，並顯示 MainPage.xaml 設計工具和 XAML 程式碼編輯器。  
  
 **開啟 MainPage.xaml.cs 原始程式檔。** 以滑鼠右鍵按一下 XML 編輯器中的任何位置，然後選擇 **檢視程式碼**。 MainPage.xaml.cs 程式碼後置檔案便會顯示。 請注意，檔案中僅會列出一個方法，也就是 `MainPage()` 建構函式。  
  
 **使用範例程式碼取代 MainPage 建構函式。** 刪除 MainPage() 方法。 依照此連結：[偵錯工具巡覽範例程式碼 （Xaml 和 C#）](../debugger/debugger-navigation-sample-code-xaml-and-csharp.md)，然後將複製到剪貼簿 C# 區段中列出的程式碼。 (選擇**回**瀏覽器或說明檢視器，以返回本快速入門頁面中。)在 Visual Studio 編輯器中，貼上 `partial class MainPage` 區塊中的程式碼。 選擇 CTRL + S 以儲存檔案。  
  
 您現在可以依照本主題中的範例進行。  
  
##  <a name="BKMK_StepInto"></a> 設定並執行至中斷點、逐步執行方法，以及檢查程式資料  
 您可以開始偵錯工作階段的最常見方式是從 [偵錯]  功能表選擇 [開始偵錯]  (鍵盤：F5)。 執行開始並繼續到到達中斷點、您以手動方式暫停執行、發生例外狀況，或應用程式結束為止。  
  
 當偵錯工具暫停執行時，可以將滑鼠游標停留在變數上，以檢視資料提示中作用中變數的值。 您也可以開啟 [區域變數] 和 [自動變數] 視窗，以查看作用中變數及其目前值的清單。 將一或多個變數加入至監看式視窗可讓您在應用程式繼續執行時，將焦點放在變數的值上。  
  
 暫停執行應用程式 (這也稱為中斷至偵錯工具中) 之後，您可以控制執行程式碼其餘部分的方式。 您可以逐行繼續、從方法呼叫移動到方法本身，或者您可以在單一步驟中執行已呼叫的方法。 這些程序稱為逐步執行應用程式。 您也可以繼續以標準方式執行應用程式，執行到您已經設定的下一個中斷點，或放置游標所在的那一行。 您可以隨時停止偵錯工作階段。 偵錯工具的設計是為執行必要的清除作業以及結束執行。  
  
### <a name="example-1"></a>範例 1  
 在此範例中，您在 MainPage.xaml.cs 檔案的 MainPage 建構函式中設定中斷點、逐步執行至第一個方法、檢視變數值，然後停止偵錯。  
  
 **設定中斷點。** 在 MainPage 建構函式的陳述式 `methodTrack = "Main Page";` 中設定中斷點。 選擇原始程式碼編輯器陰影裝訂邊的一行 (鍵盤：將游標放在該行，然後選擇 F9 鍵)。  
  
 ![逐步執行](../debugger/media/dbg_basics_stepinto.png "DBG_Basics_StepInto")  
  
 中斷點圖示會出現在巡覽邊中。  
  
 **執行至中斷點。** 選擇 [偵錯]  on the  (鍵盤：F5)。  
  
 應用程式便會開始執行，並在您設定中斷點所在的陳述式之前立即暫停執行。 裝訂邊中的目前行圖示會識別您的位置，且目前的陳述式會反白顯示。  
  
 ![設定中斷點](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
 您現在可以控制應用程式的執行，而且可以在逐步執行程式陳述式時，檢查程式狀態。  
  
 **逐步執行方法。** On the  功能表上，選擇 [逐步執行]  (鍵盤：F11)。  
  
 ![目前這一行](../debugger/media/dbg_basics_currentline.png "DBG_Basics_CurrentLine")  
  
 請注意，偵錯工具會移至下一行，也就是 Example1 方法的呼叫。 再次選擇 [逐步執行]。 偵錯工具會移至 Example1 方法的進入點。 這表示此方法已在呼叫堆疊上載入，而且已配置的本機變數的記憶體。  
  
 當您逐步執行一行程式碼時，偵錯工具會執行下列其中一個動作：  
  
-   如果下一個陳述式不是您方案中某個函式的呼叫，偵錯工具會執行該陳述式、移至下一個陳述式，然後暫停執行。  
  
-   如果該陳述式是您方案中某個函式的呼叫，偵錯工具就會移至已呼叫的函式的進入點，然後暫停執行。  
  
 繼續逐步執行 Example1 的陳述式，直到您到達結束點為止。 偵錯工具會反白顯示方法的右大括號。  
  
 **檢查資料提示中的變數值。** 當您將滑鼠游標停留在變數名稱上時，變數的名稱、值和類型會顯示在資料提示中。  
  
 ![偵錯工具資料提示方塊](../debugger/media/dbg_basics_datatip.png "DBG_Basics_DataTip")  
  
 將滑鼠游標停留在變數 `a`上。 注意名稱、值和資料類型。 將滑鼠游標停留在變數 `methodTrack`上。 再次注意名稱、值和資料類型。  
  
 **檢查 [區域變數] 視窗中的變數值。** 在**偵錯**功能表上，指向**Windows**，然後選擇 **區域變數**。 (鍵盤：Alt+4)。  
  
 ![[區域變數] 視窗](../debugger/media/dbg_basics_localswindow.png "DBG_Basics_LocalsWindow")  
  
 [區域變數] 視窗是函式的參數和變數的樹狀結構檢視。 物件變數的屬性是物件本身的子節點。 `this` 變數是每個物件方法中，表示物件本身的一個隱藏參數。 在本案例中，它代表 MainPage 類別。 `methodTrack` 是 MainPage 類別的成員，因此，其值和資料類型會列在 `this`下面的那一行中。 展開 [ `this` ] 節點來檢視 `methodTrack` 資訊。  
  
 **加入 methodTrack 變數的監看式。** `methodWatch` 變數用於這個整個快速入門中，以顯示範例中呼叫的方法。 若要更輕鬆地檢視變數的值，請將它加入至監看式視窗。 以滑鼠右鍵按一下 [區域變數] 視窗中的變數名稱，然後選擇 [加入監看式] 。  
  
 ![監看式視窗](../debugger/media/dbg_basics_watchwindow.png "DBG_Basics_WatchWindow")  
  
 您可以在監看式視窗中監看多個變數。 每次暫停執行時，都會更新監看的變數的值，例如 [區域變數] 和資料提示視窗中的值。 您也可以將變數從程式碼編輯器加入至監看式視窗。 選取要監看的變數，按一下滑鼠右鍵，然後選擇 [加入監看式] 。  
  
##  <a name="BKMK_StepIntoOverOut"></a> 逐步執行、不進入和跳離方法  
 相較於逐步執行由父方法呼叫的方法，不進入方法會執行子方法，然後在父方法繼續時，暫停在呼叫中的方法中執行。 當您熟悉方法運作的方式，並確定其執行將不會影響您正在調查的問題時，您可能會不進入方法。  
  
 不進入不包含方法呼叫的程式碼行時，執行該行的方式就像逐步執行該行一樣。  
  
 跳離子方法會繼續執行方法，然後在該方法傳回到其呼叫中的方法之後暫停執行。 當您判定函式的其餘部分並不重要時，可能會跳離長的函式。  
  
 不進入和跳離函式都會執行該函式。  
  
 ![步驟到、 不進入和跳離方法](../debugger/media/dbg_basics_stepintooverout.png "DBG_Basics_StepIntoOverOut")  
  
### <a name="example-2"></a>範例 2  
 在此範例中，您將逐步執行、不進入和跳離方法。  
  
 **在 MainPage 建構函式中呼叫 Example2 方法。** 編輯 MainPage 建構函式，並將 `methodTrack = String.Empty;` 後面的那一行取代為 `Example2();`。  
  
 ![從 Demo 方法呼叫 Example2](../debugger/media/dbg_basics_callexample2.png "DBG_Basics_CallExample2")  
  
 **執行至中斷點。** 選擇 [偵錯]  on the  (鍵盤：F5)。 偵錯工具會在中斷點暫停執行。  
  
 **不進入程式碼行。** 在 [新專案]  功能表上，選擇 [逐步執行]  (鍵盤：F10)。 偵錯工具會以逐步執行陳述式的相同方式執行 `methodTrack = "MainPage";` 陳述式。  
  
 **逐步執行 Example2 和 Example2_A。** 選擇 F11 鍵，逐步執行 Example 2 方法。 繼續逐步執行 Example2 陳述式，直到您到達 `int x = Example2_A();`這一行為止。 再次逐步執行這一行，以移至 Example2_A 的進入點。 繼續逐步執行 Example2_A 的每個陳述式，直到您回到 Example2 為止。  
  
 ![範例 2](../debugger/media/dbg_basics_example2.png "DBG_Basics_Example2")  
  
 **不進入函式。** 請注意 Example2 中的下一行 `int y = Example2_A();` 基本上與上一行相同。 您可以安全地不進入這一行。 選擇 F10 鍵，從 Example2 的接續部分移至 Example2_A 的這個第二次呼叫。 選擇 F10，不進入這個方法。 請注意， `methodTrack` 字串表示 Example2_A 方法執行了兩次。 您也會注意到偵錯工具立即移至下一行。 它不會在 Example2 繼續的點暫停執行。  
  
 **跳離函式。** 選擇 F11 鍵，逐步執行 Example2_B 方法。 請注意，Example2_B 與 Example2_A 非常不同。 若要跳離方法，請選擇 [偵錯]  功能表上的 [跳離函式]  (鍵盤：Shift + F11)。 請注意， `methodTrack` 變數表示已執行 Example2_B，且偵錯工具已經回到 Example2 繼續的點。  
  
 **停止偵錯。** 在 [偵錯] 功能表上，選擇 [停止偵錯] (鍵盤：Shift+F5)。 這樣會結束偵錯工作階段。  
  
##  <a name="BKMK_ConditionCursorVisualize"></a> 設定條件中斷點、執行至游標處，並將變數視覺化  
 條件中斷點會指定導致偵錯工具暫停執行的條件。 條件是由可以評估為 true 或 false 的任何程式碼運算式所指定。 例如，只有在變數達到特定的值時，您才可能會使用條件中斷點檢查經常呼叫的方法中的程式狀態。  
  
 執行至游標處，就像設定一次性中斷點。 執行暫停時，您可以選取來源中的一行，並繼續執行，直到到達選取的行為止。 例如，您可能會逐步執行方法中的迴圈，並判定迴圈中的程式碼正確執行。 您可以執行至迴圈執行後所放置的游標處，而不是逐步執行迴圈的每個反覆項目。  
  
 有時候很難在資料提示資料列或變數視窗中檢視變數值。 偵錯工具可以在文字視覺化檢視中，顯示可捲動視窗中呈現值的格式化檢視的字串、HTML 和 Xml。  
  
### <a name="example-3"></a>範例 3  
 在此範例中，您會設定一個條件中斷點，以便在迴圈的特定反覆項目上中斷，然後執行至迴圈之後所放置的游標處。 您也會在文字視覺化檢視中檢視變數的值。  
  
 **在 MainPage 建構函式中呼叫 Example3 方法。** 編輯 MainPage 建構函式，並將 `methodTrack = String.Empty;` 後面的那一行取代為 `Example3();`。  
  
 ![從 Demo 方法呼叫 Example3](../debugger/media/dbg_basics_callexample3.png "DBG_Basics_CallExample3")  
  
 **執行至中斷點。** 選擇 [偵錯]  on the  (鍵盤：F5)。 偵錯工具會在 MainPage 方法中的中斷點暫停執行。  
  
 **逐步執行 Example3 方法。** 選擇 [偵錯]  功能表上的 [開始偵錯]  (鍵盤：F11)，移至 Example3 方法的進入點。 繼續逐步執行方法，直到您已經逐一查看 `for` 區塊的一個或兩個迴圈為止。 請注意，逐步執行全部 1000 個反覆運算需要很長的時間。  
  
 **設定條件中斷點。** 在程式碼視窗的左裝訂邊上，以滑鼠右鍵按一下線條`x += i;`，然後選擇 **條件**。 選擇 [條件]  核取方塊，然後在文字方塊中輸入 `i == 500;` 。 選擇 [為 True]  選項，然後選擇 [確定] 。 中斷點可讓您檢查 `for` 迴圈的第 500 個反覆項目的值。  
  
 ![中斷點條件 對話方塊](../debugger/media/dbg_basics_breakpointcondition.png "DBG_Basics_BreakpointCondition")  
  
 您可以用其白色十字形狀識別條件中斷點圖示。  
  
 ![條件式中斷點](../debugger/media/dbg_basics_conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")  
  
 **執行至中斷點。** 選擇 [偵錯] 功能表上的 [繼續] (鍵盤：F5)。 在 [區域變數] 視窗中，確認 `i` 的目前值為 500。 請注意，變數 `s` 是以單行表示，其長度遠超過視窗。  
  
 **將字串變數將變數視覺化。** 在 **的 [值]** 的 [值] `s`。  
  
 [文字視覺化檢視] 視窗隨即出現，且字串的值會以多行字串呈現。  
  
 **執行至游標處。** 以滑鼠右鍵按一下 `methodTrack += "->Example3";` 這一行，然後選擇 [條件]  (鍵盤：將游標移到該行；Ctrl + F10)。 偵錯工具會完成迴圈反覆項目，然後在該行暫停執行。  
  
 **停止偵錯。** 在 [偵錯] 功能表上，選擇 [停止偵錯] (鍵盤：Shift+F5)。 這樣會結束偵錯工作階段。  
  
##  <a name="BKMK_EditContinueRecoverExceptions"></a> 編輯後繼續，從例外狀況中復原  
 在某些情況下，當您在 Visual Studio 偵錯工具內中斷程式碼時，您會有機會變更變數的值，甚至是陳述式的邏輯。 此功能稱為「編輯後繼續」。  
  
 當您例外狀況中斷時，編輯後繼續可能特別實用。 您可以「回溯」例外狀況，將執行移到剛好在例外狀況發生前的點，然後變更違反的變數或陳述式，並在不會擲回例外狀況的狀態繼續目前的偵錯工作階段，而不需要停止並重新啟動冗長且所涉及程序的偵錯，以避免例外狀況。  
  
 雖然您可以在多種情況下使用編輯後繼續，但是不支援編輯後繼續的特定條件難以指定，因為條件取決於程式設計語言、程式堆疊的目前狀態，以及偵錯工具是否能夠在不中斷程序的情況下變更狀態。 判斷是否支援編輯變更最好的方式就是嘗試。如果不支援變更，偵錯工具可讓您立即知道。  
  
### <a name="example-4"></a>範例 4  
 在此範例中，您會將偵錯工具執行至例外狀況、倒轉例外狀況、更正方法的邏輯，然後變更變數的值，讓您可以繼續執行此方法。  
  
 **在 MainPage 建構函式中呼叫 Example4 方法。** 編輯 MainPage() 建構函式，並將 `methodTrack = String.Empty;` 後面的那一行取代為 `Example4();`。  
  
 ![從 Demo 方法呼叫 Example4](../debugger/media/dbg_basics_callexample4.png "DBG_Basics_CallExample4")  
  
 **執行至例外狀況。** 選擇 [偵錯]  on the  (鍵盤：F5)。 再按 F5 一次，繼續執行。 偵錯工具會在 Example4 方法中的例外狀況暫停執行，並顯示例外狀況對話方塊。  
  
 ![例外狀況對話方塊](../debugger/media/dbg_basics_exceptiondlg.png "DBG_Basics_ExceptionDlg")  
  
 **變更程式邏輯。** 錯誤明顯是在 `if` 條件中：當 `x` 等於 0 時，應該變更 `x` 的值；當 `x` 不等於零時，則不應該變更。 選擇 [中斷]  以修正方法的邏輯。 當您嘗試編輯該行時，另一個對話方塊隨即出現。  
  
 ![編輯後繼續對話方塊](../debugger/media/dbg_basics_editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")  
  
 選擇 [編輯]  ，然後將 `if (x != 0)` 這一行變更為 `if (x == 0)`。 偵錯工具會將程式邏輯的變更保存至原始程式檔。  
  
 **變更變數值。** 在資料提示或 [區域變數] 視窗中，檢查 `x` 的值。 它仍然是 0 (零)。 如果您嘗試執行造成原始例外狀況的陳述式，它將只會再擲回一次。 您可以變更 `x`的值。 在 [區域變數] 視窗中，按兩下 [x]  資料列的 [值]  資料行。 將值從 0 變更為 1。  
  
 ![編輯 [區域變數] 視窗中的值](../debugger/media/dbg_basics_editandcontinuefix.png "DBG_Basics_EditAndContinueFix")  
  
 選擇 F11 鍵，逐步執行先前擲回例外狀況的陳述式。 請注意，執行該行不會產生錯誤。 再次選擇 F11 鍵。  
  
 **停止偵錯。** On the  功能表上，選擇 [逐步執行] **Stop ging** (鍵盤：Shift+F5)。 這樣會結束偵錯工作階段。  
  
## <a name="see-also"></a>另請參閱  
 [開始偵錯工作階段 （VB、 C#、 c + + 和 XAML）](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)   
 [觸發暫停、 繼續及背景事件用於 UWP 應用程式)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [偵錯 Visual Studio 中的應用程式](../debugger/debug-store-apps-in-visual-studio.md)
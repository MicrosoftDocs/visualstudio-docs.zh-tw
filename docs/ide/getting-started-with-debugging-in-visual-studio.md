---
title: "Visual Studio 中的使用者偵錯入門 | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e858d24a37fec49468981b44d450212ba2fa3654
ms.sourcegitcommit: 3285243d6c0521266053340fe06505885d12178b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2018
---
# <a name="get-started-with-debugging-in-visual-studio"></a>Visual Studio 中的使用者偵錯入門
Visual Studio 提供一組強大的整合式專案建置和偵錯工具。 在本主題中，可了解如何開始使用最基本的偵錯 UI 功能。  

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)頁面免費進行安裝。

## <a name="my-code-doesnt-work-help-me-visual-studio"></a>我的程式碼無法運作。 幫幫我，Visual Studio！  
 所以說，您已經找出了編輯器並建立了一些程式碼。 現在，您要開始偵錯程式碼。 在 Visual Studio 中，如同大部分的 IDE，有兩個階段用以偵錯：建置程式碼來攔截和解決專案及編譯器錯誤；且在環境中執行該程式碼來攔截和解決執行階段及動態錯誤。  

### <a name="build-your-code"></a>建置程式碼  
 有兩種基本類型的建置組態：[偵錯]和 [發行]。 第一個組態會產生較慢、較大的可執行檔，讓您擁有更豐富的互動式執行階段偵錯體驗，但絕不應該釋出這個可執行檔。 第二個會建置較快、較為最佳化的可執行檔，適合釋出 (至少從編譯器的觀點來看是如此)。 預設建置組態是 [偵錯]。

建置專案最簡單的做法是按下 **F7**，但您也可以從主功能表選取 [建置] > [建置方案] 來開始建置。  

 ![Visual Studio 建置專案功能表選取項目](../ide/media/vs_ide_gs_debug_build_menu_item.png "Vs_ide_gs_debug_build_menu_item")  

 您可以在 Visual Studio UI 底部的 [輸出] 狀態視窗觀察建置程序。 這裡會顯示錯誤、警告和建置作業。 如果有錯誤 (或者如果您有高於已設定層級的警告)，您的建置將會失敗。 您可以按一下這些錯誤和警告，移至發生錯誤和警告的程式行。 請再按 **F7** 一次 (只重新編譯有錯誤的檔案) 來重建專案，或是按 **Ctrl+Alt+F7** (對於全新且完整的重建)。  

 在編輯器下方的結果視窗中有兩個索引標籤式的建置視窗：[輸出] 視窗，其中包含編譯器的原始輸出 (包含錯誤訊息)；以及 [錯誤清單] 視窗，提供可排序和可篩選的所有錯誤及警告清單。  

 成功後，您會在 [輸出] 視窗中看到與這個類似的結果。  

 ![Visual Studio 成功組建輸出](../ide/media/vs_ide_gs_debug_success_build.PNG "vs_ide_gs_debug_success_build")  

### <a name="review-the-error-list"></a>檢視錯誤清單  
 除非您不修改先前編譯成功的程式碼，否則可能還是會有錯誤。 如果您是撰寫程式碼的新手，您可能會有許多錯誤。 錯誤有時會很明顯，例如簡單的語法錯誤或不正確的變數名稱，但有時候它們會很難了解，只有隱密的程式碼引導您。 如需更清楚地檢視問題，請巡覽至組建 [輸出] 視窗底部，然後按一下 [錯誤清單] 索引標籤。這會讓您更有組織地檢視專案的錯誤和警告，並提供您一些額外的選項。  

 ![Visual Studio 輸出和錯誤清單](../ide/media/vs_ide_gs_debug_bad_build_error_list.PNG "Vs_ide_gs_debug_bad_build_error_list")  

 在 [錯誤清單] 視窗中按一下錯誤行，然後跳至發生錯誤的行。 (或者，按一下右上方的 [快速啟動] 列，並鍵入「行號」，然後按 Enter 鍵，來開啟行號。 這是到達 [選項] 視窗項目的最快速方式，您可以在其中開啟行號。 了解如何使用 [快速啟動] 列，並且替您省下很多的 UI 點選！)  

 ![使用行號的 Visual Studio 編輯器](../ide/media/vs_ide_gs_debug_line_numbers.png "Vs_ide_gs_debug_line_numbers")  

 ![Visual Studio 行號選項](../ide/media/vs_ide_gs_debug_options_line_numbers.png "Vs_ide_gs_debug_options_line_numbers")  

 使用 **Ctrl+G** 快速跳至發生錯誤的行號。  

 錯誤會用紅色「波浪線」的底線加以識別。 如需其他詳細資料，請將滑鼠游標暫留在這上面。 請予以修正，然後它就會消失 (儘管您在修正時可能會導入新的錯誤)。 (這稱為「迴歸」)。  

 ![Visual Studio 錯誤動態顯示](../ide/media/vs_ide_gs_debug_error_hover1.png "Vs_ide_gs_debug_error_hover1")  

 逐一查核錯誤清單，並處理您程式碼中的所有錯誤。  

 ![Visual Studio 偵錯錯誤視窗](../ide/media/vs_ide_gs_debug_error_list.PNG "Vs_ide_gs_debug_error_list")  

### <a name="review-errors-in-detail"></a>詳細檢閱錯誤  
 有許多錯誤以編譯器的術語敘述時，可能會對您沒有任何意義。 在這種情況下，您會需要其他資訊。 在 [錯誤清單] 視窗中，您可以滑鼠右鍵按一下對應的項目行，然後從操作功能表中選取 [顯示錯誤說明]，以自動到 Bing 搜尋更多錯誤 (或警告) 的相關資訊。  

 ![Visual Studio 錯誤清單 Bing 搜尋](../ide/media/vs_ide_gs_debug_error_list_error_help.png "Vs_ide_gs_debug_error_list_error_help")  

 這樣會在 Visual Studio 內啟動索引標籤，其中裝載錯誤碼和文字的 Bing 搜尋結果。 這些結果可能來自網際網路上的許多不同來源，並非全部都有幫助。  

 或者，您可以在 [錯誤清單] 的 [程式碼] 資料行中按一下超連結的錯誤碼值。 這只會啟動有關錯誤碼的 Bing 搜尋。  

### <a name="use-light-bulbs-to-fix-or-refactor-code"></a>使用燈泡來修正或重構程式碼  
 燈泡是 Visual Studio 的新功能，可讓您重構程式碼內嵌。 這是可迅速有效地修正常見警告之簡單方式。 若要存取，請以滑鼠右鍵按一下警告波浪線 (或按 **Ctrl+**. ，若滑鼠游標在波浪線上暫留)，然後選取 [快速動作]。  

 ![Visual Studio 燈泡快速選項](../ide/media/vs_ide_gs_debug_light_bulb1.png "Vs_ide_gs_debug_light_bulb1")  

 您會看到一份可能的修正或重構清單，可套用至該程式碼行。  

 ![Visual Studio 燈泡預覽](../ide/media/vs_ide_gs_debug_light_bulb_preview_changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")  

 只要程式碼分析器判斷有修正、重構或改善程式碼的機會，即可使用燈泡。 按一下任何一行程式碼，再按一下滑鼠右鍵開啟操作功能表，然後選取 [快速動作] (如果您希望更有效率，也可以按 **Ctrl+**.)。 如果有可用的區域重構或改善選項，就會顯示它們；否則，`No quick options available here` 訊息會顯示在 IDE 的左下角邊框。  

 ![Visual Studio 燈泡「無選項」文字](../ide/media/vs_ide_gs_debug_light_bulb_no_options.PNG "Vs_ide_gs_debug_light_bulb_no_options")  

 有經驗之後，您可以快速地使用方向鍵和 **Ctrl+**. 來檢查 [快速選項] 重構機會，並清除程式碼！  

 如需燈泡的詳細資訊，請參閱[執行燈泡提示的快速動作](../ide/perform-quick-actions-with-light-bulbs.md)。  

### <a name="debug-your-running-code"></a>偵錯您執行的程式碼  
 既然您已成功建置程式碼並已稍加清除，請按 **F5** 或選取 [偵錯] > [開始偵錯] 予以執行。 這會在偵錯環境中啟動您的應用程式，如此一來您可詳細觀察其行為。 應用程式執行時，Visual Studio IDE 就會變更：[輸出] 視窗由兩個新的視窗所取代 (在預設視窗組態中)、[自動變數/區域變數/監看式] 索引標籤式視窗和 [呼叫堆疊/中斷點/例外狀況設定/輸出] 索引標籤式視窗。 這些視窗有多個索引標籤，可讓您在執行時檢查和評估應用程式變數、執行緒、呼叫堆疊以及各種其他行為。  

 ![Visual Studio 自動變數和呼叫堆疊視窗](../ide/media/vs_ide_gs_debug_autos_and_call_stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")  

 您可以按 **Shift+F5** 或按一下 [停止] 按鈕停止應用程式。 或者，您只需關閉應用程式的主視窗 (或命令列對話方塊)。  

 如果您的程式碼完美地如預期運作，那麼恭喜您！ 不過，如果它停止回應或當機，或是提供給您一些奇怪的結果，那麼您需找出這些問題的來源，並修正 Bug。  

### <a name="set-simple-breakpoints"></a>設定簡單的中斷點  
 中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。 設定及移除中斷點之後，您不需要重建專案。  

 按一下您想讓中斷發生的程式碼行最旁邊的邊界或按 **F9**，在目前的程式碼中設定中斷點。 當您執行程式碼時，在執行這行程式碼的指令之前，它會先暫停 (或「中斷」)。  

 ![Visual Studio 中斷點](../ide/media/vs_ide_gs_debug_breakpoint1.png "Vs_ide_gs_debug_breakpoint1")   

 中斷點的常見用途包含：  

1.  若要縮小造成當機或停止回應的來源，請在您認為會導致失敗的整個方法呼叫程式碼中四處散佈中斷點。 當您在偵錯工具中執行程式碼時，請移除中斷點，然後將此中斷點重設得更為密集，直到您找出有問題的那一行程式碼。  請參閱下一節以了解如何在偵錯工具中執行程式碼。

2.  當您引入新的程式碼時，請在其開頭設定中斷點，並執行程式碼，確定它會如預期地表現。

3.  如果您已實作複雜的行為，請對演算碼設置中斷點，如此當程式中斷時，您可以檢查變數和資料的值。  

4.  如果您要撰寫 C 或 C++ 程式碼，當要偵錯記憶體相關的失敗時，請使用中斷點來停止程式碼，以便您檢查位址值 (尋找 NULL) 和參考計數。  

 如需使用中斷點的詳細資訊，請參閱[使用中斷點](../debugger/using-breakpoints.md)。  

### <a name="inspect-your-code-at-run-time"></a>在執行階段檢查您的程式碼  
 當您執行的程式碼叫用中斷點並暫停時，標示為黃色的程式碼 (目前的陳述式) 仍尚未執行。 此時，您可能想要執行目前的陳述式，然後檢查變更的值。 您可以使用數個「步驟」命令在偵錯工具中執行程式碼。 如果所標示的程式碼為方法呼叫，您可以按 **F11** 逐步執行。 您也可以按 **F10**，讓這行程式碼「不進入函式」。 如需其他命令與如何逐步執行程式碼的詳細資料，請閱讀[使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。

 ![Visual Studio 執行階段值檢查](../ide/media/vs_ide_gs_debug_hit_breakpoint.PNG "vs_ide_gs_debug_inspect_value")

 在上圖中，您可以按下 **F10** 或 **F11** 讓偵錯工具前進一個陳述式 (因為這裡沒有任何方法呼叫，所以兩個命令有相同的結果)。

 當偵錯工具暫停時，您可以檢查變數和呼叫堆疊來判斷發生了什麼狀況。 這些是在您預期會看見的範圍內的值嗎？ 呼叫的順序正確嗎？  

 ![Visual Studio 執行階段值檢查](../ide/media/vs_ide_gs_debug_inspect_value.PNG "vs_ide_gs_debug_inspect_value")  

 將滑鼠停留在變數，以查看變數的值和目前包含的參考。 如果您看到非預期的值，則前面的程式碼或呼叫行程式碼可能有 Bug。  如需更詳細的資訊，請[深入了解](../debugger/getting-started-with-the-debugger.md)使用偵錯工具。

 此外，Visual Studio 會顯示 [診斷工具] 視窗，其中您可以觀察隨時間推移的應用程式之 CPU 和記憶體使用量。 稍後在應用程式開發中，您可以使用這些工具來尋找非預期的繁重 CPU 使用量或記憶體配置。 搭配 [監看式] 視窗和中斷點使用，以判斷是什麼造成非預期的繁重使用量或資源未釋放。  如需詳細資訊，請參閱[分析功能導覽](../profiling/profiling-feature-tour.md)。

### <a name="run-unit-tests"></a>執行單元測試  
 單元測試是您對抗程式碼 Bug 的第一道防線；因為正確完成時，它們會測試單一的程式碼「單位」，一般是單一函式，而且通常比偵錯完整的程式更容易偵錯。 Visual Studio 會安裝 Managed 和原生程式碼的 Microsoft 單元測試架構。 請使用單元測試架構來建立並執行單元測試，然後報告這些測試的結果。 當您進行變更來測試程式碼是否仍正常運作時，請重新執行單元測試。 當您使用 Visual Studio Enterprise 版本時，可以在每次建置後自動執行測試。  

 若要開始使用，請參閱[使用 IntelliTest 為程式碼產生單元測試](../test/generate-unit-tests-for-your-code-with-intellitest.md)。  

 若要深入了解 Visual Studio 中的單元測試，以及了解它們如何協助您建立更高品質的程式碼，請參閱[單元測試基本概念](../test/unit-test-basics.md)。  

### <a name="perform-static-code-analysis"></a>執行靜態程式碼分析  
 「靜態程式碼分析」是一種花俏的說法，實際來說就是：「自動檢查程式碼的常見問題，這些可能導致執行階段錯誤或程式碼管理的問題」。 一旦我們清除阻礙建置的明顯錯誤，請習慣於立即執行靜態程式碼分析，花一些時間來處理這可能產生的警告。 您今後可省去一些麻煩，也可了解一些程式碼樣式的技巧。  

 按 **Alt+F11** (或從上方功能表選取 [分析] -> [針對方案執行程式碼分析]) 來啟動靜態程式碼分析。 如果您有大量程式碼，這可能需要一些時間。  

 ![Visual Studio 程式碼分析功能表項目](../ide/media/vs_ide_gs_debug_run_code_analysis.png "Vs_ide_gs_debug_run_code_analysis")  

 任何新的或已更新的警告都會出現在 IDE 底部的 [錯誤清單] 索引標籤中。 按一下以移至這些警告。  

 ![Visual Studio 錯誤清單 (含警告)](../ide/media/vs_ide_gs_debug_code_analysis_warning_error_list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")  

 警告會以亮黃綠色波浪線識別，而非紅色。 如需詳細資訊，請將滑鼠游標暫留於此，並以滑鼠右鍵按一下以取得操作功能表，這有助於修正或重構選項。  

 ![Visual Studio 程式碼分析警告動態顯示](../ide/media/vs_ide_gs_debug_code_analysis_warning_hover.png "vs_ide_gs_debug_code_analysis_warning_hover")  

## <a name="see-also"></a>請參閱  
 [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)  
 [深入了解使用偵錯工具](../debugger/getting-started-with-the-debugger.md)

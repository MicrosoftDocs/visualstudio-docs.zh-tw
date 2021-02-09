---
title: 修正程式錯誤並改善程式碼
description: 本文描述 Visual Studio 如何透過一些基本方法來協助您尋找並修正您程式碼中的問題，包括建置錯誤、程式碼分析、偵錯工具和單元測試。
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6da05729be409b142f6c9cec2c543fb2b9171ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869423"
---
# <a name="make-code-work-in-visual-studio"></a>讓程式碼在 Visual Studio 中運作

Visual Studio 提供一組強大的整合式專案建置和偵錯工具。 在本文中，了解 Visual Studio 如何協助您使用建置輸出、程式碼分析、偵錯工具和單元測試，來找出您程式碼中的問題。

您已了解編輯器並建立了一些程式碼。 現在，您想要確定程式碼正常運作。 在 Visual Studio 中，如同大部分的 IDE，有兩個階段用以讓程式碼運作：建置程式碼來攔截和解決專案及編譯器錯誤，以及執行程式碼來尋找執行階段及動態錯誤。

## <a name="build-your-code"></a>建置程式碼

有兩種基本類型的建置組態：[偵錯]和 [發行]。 [偵錯] 組態會產生較慢、較大的可執行檔，讓您擁有更豐富的互動式執行階段偵錯體驗。 絕不應該釋出 [偵錯] 可執行檔。 [發行] 組態會建置較快、已最佳化的可執行檔，其適合釋出 (至少從編譯器的觀點來看是如此)。 預設建置組態是 [偵錯]。

建置專案最簡單的做法是按下 **F7** 鍵，但您也可以從主功能表選取 [建置] > [建置方案] 來開始建置。

![Visual Studio 建置專案功能表選取項目](../ide/media/vs_ide_gs_debug_build_menu_item.png)

您可以在 Visual Studio UI 底部的 [輸出] 視窗觀察建置程序。 這裡會顯示錯誤、警告和建置作業。 如果有錯誤 (或者如果您有高於已設定層級的警告)，您的建置會失敗。 您可以按一下這些錯誤和警告，移至發生錯誤和警告的程式行。 請再按 **F7** 鍵一次 (只重新編譯有錯誤的檔案) 來重建專案，或是按 **Ctrl**+**Alt**+**F7** (對於全新且完整的重建)。

在編輯器下方的結果視窗中有兩個索引標籤式視窗：[輸出] 視窗，其中包含編譯器的原始輸出 (包含錯誤訊息)；以及 [錯誤清單] 視窗，提供可排序和可篩選的所有錯誤及警告清單。

建置成功時，您會在 [輸出] 視窗中看到與這個類似的結果：

![Visual Studio 的組建輸出成功](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>檢視錯誤清單

除非您不修改先前編譯成功的程式碼，否則可能還是會有錯誤。 如果您是撰寫程式碼的新手，您可能會有許多錯誤。 錯誤有時會很明顯，例如簡單的語法錯誤或不正確的變數名稱，但有時候它們會很難了解，只有隱密的程式碼引導您。 若要清楚瞭解問題，請流覽至 [組建 **輸出** ] 視窗底部，然後按一下 [ **錯誤清單** ] 索引標籤。這會讓您更有條理地查看專案的錯誤和警告，也提供您一些額外的選項。

![Visual Studio 輸出和錯誤清單](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

在 [錯誤清單] 視窗中按一下錯誤行，跳至發生錯誤的行。  (或開啟行號，請按下 **Ctrl** + **Q**、輸入 **行號**，然後從結果中選擇 [**開啟或關閉行號**]。 這是到達 [選項] 對話方塊的最快速方式，您可以在其中開啟行號。)

![使用行號的 Visual Studio 編輯器](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio 行號選項](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

按 **Ctrl** + **G** 可快速跳至發生錯誤的行號。

錯誤會用紅色「波浪線」的底線加以識別。 如需其他詳細資料，請將滑鼠游標暫留在這上面。 請予以修正，然後它就會消失 (儘管您在修正時可能會導入新的錯誤)。 (這稱為「迴歸」)。

![Visual Studio 錯誤動態顯示](../ide/media/vs_ide_gs_debug_error_hover1.png)

逐一查核錯誤清單，並處理您程式碼中的所有錯誤。

![Visual Studio 偵錯錯誤視窗](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>詳細檢閱錯誤

有許多錯誤以編譯器的術語敘述時，可能會對您沒有任何意義。 在這種情況下，您會需要其他資訊。 您可以從 [錯誤清單] 視窗執行自動化 Bing 搜尋，來取得錯誤或警告的詳細資訊。 以滑鼠右鍵按一下對應的項目行，然後從操作功能表選取 [顯示錯誤說明]，或是在 [錯誤清單] 的 [程式碼] 欄中，按一下超連結的錯誤碼值。

![Visual Studio 錯誤清單 Bing 搜尋](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

根據您的設定，可能會由您的網頁瀏覽器顯示錯誤碼和文字的搜尋結果，或是在 Visual Studio 中開啟一個索引標籤並顯示 Bing 搜尋結果。 這些結果可能來自網際網路上的許多不同來源，並非全部都有幫助。

## <a name="use-code-analysis"></a>使用程式碼分析

程式碼分析器會尋找可能導致執行階段錯誤或程式碼管理問題的常見程式碼問題。

### <a name="c-and-visual-basic-code-analysis"></a>C# 和 Visual Basic 程式碼分析

Visual Studio 包含一組內建的 [.NET Compiler Platform 分析器](../code-quality/roslyn-analyzers-overview.md)，其會檢查您鍵入的 C# 和 Visual Basic 程式碼。 您可以將其他分析器安裝為 Visual Studio 延伸模組或 NuGet 套件。 如果發現違反規則，則會在 [錯誤清單] 和 [程式碼編輯器] 中將其報告為違規程序代碼底下的波浪線。

### <a name="c-code-analysis"></a>C++ 程式碼分析

若要分析 C++ 程式碼，請執行[靜態程式碼分析](/cpp/code-quality/quick-start-code-analysis-for-c-cpp)。 一旦我們清除阻礙成功建置的明顯錯誤，請習慣於立即執行靜態程式碼分析，花一些時間來處理這可能產生的警告。 您今後可省去一些麻煩，也可了解一些程式碼樣式的技巧。

按下 **Alt** + **F11** (或  >  從上方功能表選取 [分析 **針對方案執行程式碼分析**]) 來啟動靜態程式碼分析。

![Visual Studio 程式碼分析功能表項目](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

任何新的或已更新的警告都會出現在 IDE 底部的 [錯誤清單] 索引標籤中。 按一下以跳至程式碼中的這些警告。

![Visual Studio 錯誤清單 (含警告)](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>使用「快速動作」來修正或重構程式碼

[快速動作](../ide/quick-actions.md)可從燈泡或螺絲起子圖示使用，讓您重構程式碼內嵌。 這是可迅速有效地修正 C#、C++ 和 Visual Basic 程式碼中常見警告的簡單方式。 若要存取，請以滑鼠右鍵按一下警告波浪線，然後選取 [快速動作與重構]。 或者，當游標位於具有彩色波浪線的行上時，請按下 **Ctrl** + **。** 或是選取邊邊的燈泡、錯誤燈泡或螺絲起子圖示。 您會看到一份可能的修正或重構清單，可套用至該程式碼行。

![Visual Studio 燈泡預覽](../ide/media/quick-actions-options.png)

只要程式碼分析器判斷有修正、重構或改善程式碼的機會，即可使用快速動作。 按一下任何一行程式碼，再按一下滑鼠右鍵開啟操作功能表，然後選取 [快速動作與重構]。 如果有重構或改進選項可用，則會顯示這些選項。 否則會在 IDE 左下角顯示 [No quick actions available here] \(沒有任何可用的快速動作\) 訊息。

![文字：No quick actions available here (沒有任何可用的快速動作)](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

使用經驗，您可以快速地使用方向鍵和 **Ctrl** + **。** 找出輕鬆重構的機會，並清除您的程式碼！

::: moniker range="vs-2019"

## <a name="run-code-cleanup"></a>執行程式碼清除

Visual Studio 透過編輯器底部的 [程式 **代碼清除**] 按鈕，提供 [c # 程式碼檔案的隨選格式](code-styles-and-code-cleanup.md#apply-code-styles)，包括程式碼樣式喜好設定。

![Visual Studio 2019 中的 [程式碼清除] 按鈕](media/execute-code-cleanup.png)

除了將檔案格式化以進行空格、縮排等，程式 **代碼清除** 也會套用一組您定義的程式碼樣式慣例。 系統會從 [EditorConfig 檔案](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) (如果您針對專案有該檔案的話) 讀取您針對每個程式碼樣式的偏好設定，或是從 [選項] 對話方塊中的[程式碼樣式設定](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box)讀取那些偏好設定。

::: moniker-end

## <a name="debug-your-running-code"></a>偵錯您執行的程式碼

既然您已成功建立程式碼並執行一些清除，請按 **F5** 或選取 [ **Debug**  >  **開始調試** 程式] 來執行它。 這會在偵錯環境中啟動您的應用程式，如此一來您可詳細觀察其行為。 應用程式執行時，Visual Studio IDE 就會變更：[輸出] 視窗由兩個新的視窗所取代 (在預設視窗組態中)、[自動變數/區域變數/監看式] 索引標籤式視窗和 [呼叫堆疊/中斷點/例外狀況設定/輸出] 索引標籤式視窗。 這些視窗有多個索引標籤，可讓您在執行時檢查和評估應用程式變數、執行緒、呼叫堆疊以及各種其他行為。

![Visual Studio 自動變數和呼叫堆疊視窗](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

按 **Shift** + **F5** 或按一下 [**停止**] 按鈕，以停止您的應用程式。 或者，您可以直接關閉應用程式的主視窗 (或命令列對話方塊) 。

如果您的程式碼完美地如預期運作，那麼恭喜您！ 但是，如果它停止回應或當機，或是提供給您一些奇怪的結果，您將需要找出這些問題的來源，並修正 bug。

### <a name="set-simple-breakpoints"></a>設定簡單的中斷點

[中斷點](../debugger/using-breakpoints.md) 是可靠偵錯工具最基本且最基本的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。 設定及移除中斷點之後，您不需要重建專案。

按一下您想讓中斷發生的程式碼行最旁邊的邊界或按 **F9**，在目前的程式碼中設定中斷點。 當您執行程式碼時，在執行這行程式碼的指令之前，它會先暫停 (或「中斷」)。

![Visual Studio 中斷點](../ide/media/vs_ide_gs_debug_breakpoint1.png)

中斷點的常見用途包含：

- 若要縮小損毀或沒有回應的程式的來源，請在您認為會導致失敗的方法呼叫程式碼前後散佈中斷點。 當您在偵錯工具中執行程式碼時，請移除中斷點，然後將此中斷點重設得更為密集，直到您找出有問題的那一行程式碼。 請參閱下一節以了解如何在偵錯工具中執行程式碼。

- 當您引入新的程式碼時，請在其開頭設定中斷點，並執行程式碼，確定它會如預期地表現。

- 如果您已實作複雜的行為，請對演算碼設置中斷點，如此當程式中斷時，您可以檢查變數和資料的值。

- 如果您要撰寫 C 或 C++ 程式碼，當要偵錯記憶體相關的失敗時，請使用中斷點來停止程式碼，以便您檢查位址值 (尋找 NULL) 和參考計數。

如需使用中斷點的詳細資訊，請參閱[使用中斷點](../debugger/using-breakpoints.md)。

### <a name="inspect-your-code-at-run-time"></a>在執行階段檢查您的程式碼

當您執行的程式碼叫用中斷點並暫停時，標示為黃色的程式碼 (目前的陳述式) 仍尚未執行。 此時，您可能想要執行目前的陳述式，然後檢查變更的值。 您可以使用數個「步驟」命令在偵錯工具中執行程式碼。 如果標示的程式碼為方法呼叫，您可以按 **F11** 逐步執行它。 您也可以按下 **F10** *，不* 進入程式程式碼。 如需其他命令與如何逐步執行程式碼的詳細資料，請閱讀[使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。

![Visual Studio 程式碼視窗的螢幕擷取畫面。 左邊裝訂邊中的紅色點表示以黃色標示的程式程式碼上的中斷點。](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

在上圖中，您可以按下 **F10** 或 **F11** 讓偵錯工具前進一個陳述式 (因為這裡沒有任何方法呼叫，所以兩個命令有相同的結果)。

當偵錯工具暫停時，您可以檢查變數和呼叫堆疊來判斷發生了什麼狀況。 這些是在您預期會看見的範圍內的值嗎？ 呼叫的順序正確嗎？

![Visual Studio 程式碼視窗的螢幕擷取畫面。 在以黃色標示的程式程式碼上，會選取變數，而下拉式清單會顯示其目前的值和參考。](../ide/media/vs_ide_gs_debug_inspect_value.png)

將滑鼠停留在變數上方，以查看其目前值和參考。 如果您看到非預期的值，則前面的程式碼或呼叫行程式碼可能有 Bug。 如需更深入的偵錯資訊，請[深入了解](../debugger/debugger-feature-tour.md)如何使用偵錯工具。

此外，Visual Studio 會顯示 [診斷工具] 視窗，其中您可以觀察隨時間推移的應用程式之 CPU 和記憶體使用量。 稍後在應用程式開發中，您可以使用這些工具來尋找非預期的繁重 CPU 使用量或記憶體配置。 將它與 [ **監看** 式] 視窗和中斷點一起使用，以判斷造成非預期的大量使用量或未發行資源的原因。 如需詳細資訊，請參閱[分析功能導覽](../profiling/profiling-feature-tour.md)。

## <a name="run-unit-tests"></a>執行單元測試

單元測試是您對抗程式碼 Bug 的第一道防線；因為正確完成時，它們會測試單一的程式碼「單元」，一般是單一函式，而且比完整的程式更容易偵錯。 Visual Studio 會安裝 Managed 和原生程式碼的 Microsoft 單元測試架構。 請使用單元測試架構來建立並執行單元測試，然後報告這些測試的結果。 當您進行變更來測試程式碼是否仍正常運作時，請重新執行單元測試。 使用 Visual Studio Enterprise 版本，您可以在每次建置後自動執行測試。

若要開始使用，請參閱[使用 IntelliTest 為程式碼產生單元測試](../test/generate-unit-tests-for-your-code-with-intellitest.md)。

若要深入了解 Visual Studio 中的單元測試，以及了解它們如何協助您建立更高品質的程式碼，請參閱[單元測試基本概念](../test/unit-test-basics.md)。

## <a name="see-also"></a>另請參閱

- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [深入了解使用偵錯工具](../debugger/index.yml)
- [產生及修正程式嗎](../ide/code-generation-in-visual-studio.md)

---
title: 選項對話方塊、一般、調試Microsoft Docs
description: 設定 Visual Studio 偵錯工具選項，以符合您的偵錯工具需求。 您可以設定中斷行為、調試層級、顯示行為，以及其他更多。
ms.custom: SEO-VS-2020
ms.date: 06/04/2020
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 928499957ca90dda718f324827968f10cbb3a141
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870567"
---
# <a name="general-debugging-options"></a>一般調試選項

若要設定 Visual Studio 偵錯工具選項，請選取 [**工具**  >  **選項**]，然後在 [**調試** 程式] 底下選取或取消選取 [**一般**] 選項旁的方塊。 您可以使用 [**工具** 匯  >  **入和匯出設定**] 來還原所有預設設定，以  >  **重設所有設定**。 若要重設設定子集，請先使用 [匯 **入和匯出設定] 嚮導** 來儲存您的設定，然後再進行要測試的變更，然後在之後匯入儲存的設定。

您可以設定下列 **一般** 選項：

**刪除所有中斷點之前請先詢問**：在完成 [ **刪除所有中斷點** ] 命令之前需要確認。

**當一個進程中斷時中斷所有進程**：中斷時，會同時中斷附加偵錯工具的所有進程。

**中斷跨 AppDomain 或 managed/原生界限的例外** 狀況：在 managed 或混合模式的偵錯工具中，當下列條件成立時，common language runtime 可以攔截跨應用程式域界限或 managed/原生界限的例外狀況：

1. 當機器碼使用 COM Interop 呼叫受控程式碼，且受控程式碼擲回例外狀況時。 請參閱 [COM Interop 簡介](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop)。

2. 當在應用程式定義域 1 中執行的受控程式碼呼叫應用程式定義域 2 中的受控程式碼，且應用程式定義域 2 中的程式碼擲回例外狀況時。 請參閱[使用應用程式定義域設計程式](/dotnet/articles/framework/app-domains/index)。

3. 當程式碼使用反映呼叫函式時，該函式會擲回例外狀況。 請參閱 [反映](/dotnet/framework/reflection-and-codedom/reflection)。

在條件2和3中，例外狀況有時候是由 managed 程式碼攔截， `mscorlib` 而不是由 common language runtime 所捕捉。 這個選項不會影響被 `mscorlib` 攔截之例外狀況的中斷。

**啟用位址層級的偵錯工具**：啟用 **在 [反** 組解碼] 視窗、[緩存 **器] 視窗** 和位址中斷點) 的位址層 (級進行偵錯工具的 advanced 功能。

- **如果無法使用來源，則顯示** 反組解碼：當 **您對無法** 使用來源的程式碼進行偵錯工具時，會自動顯示 [反組解碼] 視窗。

**啟用中斷點篩選**：可讓您在中斷點上設定篩選，使其只會影響特定的進程、執行緒或電腦。

**使用新的例外** 狀況協助程式：啟用取代例外狀況小幫手的例外狀況協助程式。 從 Visual Studio 2017 開始支援 (的例外狀況協助程式) 

> [!NOTE]
> 針對 managed 程式碼，此選項先前稱為「 **啟用例外狀況助理** 」。

**啟用 Just My Code**：偵錯工具只會在使用者程式碼中顯示 ( "My Code" ) ，忽略系統程式碼和其他已優化或沒有偵錯工具代碼的程式碼。

- **如果啟動時沒有使用者程式碼 (僅限受管理的)**：從啟用 Just My Code 開始時，此選項會警告您，指出沒有任何使用者程式碼 ( "My Code" ) 。

**啟用 .NET Framework 的來源逐步** 執行：讓偵錯工具逐步執行 .NET Framework 來源。 啟用此選項會自動停用 Just My Code。 .NET Framework 的符號將會下載至快取位置。 使用 [ **選項** ] 對話方塊的 [ **調試** 類別目錄]、[ **符號** ] 頁面來變更快取位置。

不進入 **屬性和運算子 (managed)**：防止偵錯工具逐步執行 managed 程式碼中的屬性和運算子。

**啟用屬性評估及其他隱含函式呼叫**：在變數視窗和 [ **快速** 監看式] 對話方塊中開啟屬性的自動評估和隱含函式呼叫。

- 在 **變數 (視窗中的物件上呼叫字串轉換函式（僅限 c # 和 JavaScript）)**：在變數視窗中評估物件時執行隱含字串轉換呼叫。 結果會顯示為字串，而不是類型名稱。 只適用於偵錯 C# 程式碼時。 DebuggerDisplay 屬性可能會覆寫此設定 (請參閱 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)) 。

**啟用來源伺服器支援**：告知 Visual Studio 偵錯工具，從執行 SrcSrv () 通訊協定的來源伺服器取得來源檔案 `srcsrv.dll` 。 Team Foundation Server 和 Windows 偵錯工具這兩個來源伺服器會實作通訊協定。 如需有關 SrcSrv 設定的詳細資訊，請參閱 [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) 檔。 此外，請參閱 [指定符號 ( .pdb) 和來源](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔案。

> [!IMPORTANT]
> 因為讀取 *.pdb* 檔案可以執行檔案中的任意程式碼，請確定您信任伺服器。

- 將 **來源伺服器診斷訊息列印到輸出視窗**：啟用來源伺服器支援時，此設定會開啟診斷顯示。

- **允許部分信任元件的來源伺服器僅 (受控)**：啟用來源伺服器支援時，此設定會覆寫不會針對部分信任元件的來源進行的預設行為。

- **一律執行不受信任的來源伺服器命令而不提示**：啟用來源伺服器支援時，此設定會覆寫執行未受信任命令時提示的預設行為。

**啟用來源連結支援**：告知 Visual Studio 偵錯工具下載包含來源連結資訊之 *.pdb* 檔案的來源檔案。 如需來源連結的詳細資訊，請參閱 [來源連結規格](/dotnet/standard/library-guidance/sourcelink)。

> [!IMPORTANT]
> 由於來源連結會使用 HTTP 或 HTTPs 下載檔案，因此請確定您信任 *.pdb* 檔。

- **切換回 Git 認證管理員所有來源連結要求的驗證**：當啟用來源連結支援，且來源連結要求驗證失敗時，Visual Studio 接著會呼叫 Git 認證管理員。

**反白顯示中斷點的整個原始程式列及目前的語句 (c + + 僅)**：當偵錯工具反白顯示中斷點或目前的語句時，它會反白顯示整行。

**要求原始程式檔必須完全符合原始版本**：指示偵錯工具確認原始程式檔是否符合用來建立您正在進行偵錯工具之可執行檔的原始程式碼版本。 當版本不相符時，系統會提示您尋找相符的來源。 如果找不到相符的原始程式檔，偵錯期間將不會顯示原始程式碼。

將 **所有輸出視窗文字重新導向到 [即時運算] 視窗**：將通常出現在 [**輸出**] 視窗中的所有偵錯工具訊息傳送到 [即時運算 **] 視窗。**

**在變數視窗中顯示物件的原始結構**：關閉所有物件結構視圖自訂。 如需有關視圖自訂的詳細資訊，請參閱 [建立受控物件的自訂視圖](../debugger/create-custom-views-of-managed-objects.md)。

**在模組載入時隱藏 JIT 優化 (僅限 Managed)**：當載入模組且在附加偵錯工具時編譯 jit 時，停用 managed 程式碼的 jit 優化。 停用最佳化可更容易偵錯一些問題，但消耗較多效能。 如果正在使用 Just My Code，隱藏 JIT 最佳化會使非使用者程式碼顯示為使用者程式碼 ("My Code")。 如需詳細資訊，請參閱 [JIT 優化和調試](../debugger/jit-optimization-and-debugging.md)程式。

**啟用 ASP.NET (Chrome、Microsoft Edge 和 IE) 的 JavaScript 調試** 程式：啟用 ASP.NET apps 的腳本偵錯工具。 第一次在 Chrome 中使用時，您可能需要登入瀏覽器，以啟用您已安裝的 Chrome 擴充功能。 停用此選項可還原為舊版行為。

::: moniker range=">= vs-2019"
**使用多目標 javascript 偵錯工具來偵測適用目標中的 javascript (需要重新開機偵錯工具)** 可同時連線至瀏覽器和後端，讓您可以在用戶端和伺服器中，直接從編輯器進行程式碼的偵錯工具。
::: moniker-end

**載入 dll 匯出 (僅限原生)**：載入 dll 匯出資料表。 若您使用 Windows 訊息、Windows 程序 (WindowProc)、COM 物件、封送處理或是任何您沒有其符號的 dll，則 dll 匯出資料表的符號資訊會很有幫助。 讀取 dll 匯出資訊會產生一些額外負荷。 因此，這項功能預設為關閉。

若您想知道 dll 匯出表中可使用的符號，請使用 `dumpbin /exports`。 這些符號適用於任何 32 位元系統 dll。 讀取 `dumpbin /exports` 輸出時，您可以看到確實的函式名稱，包含非英數字元。 這對設定函式的中斷點來說很有幫助。 dll 匯出表中的函式名稱在偵錯工具中的其他位置可能會顯示為已被截斷。 這些呼叫都按呼叫順序列出，目前的函式 (巢狀最深處) 列在頂端。 如需詳細資訊，請參閱 [dumpbin /exports](/cpp/build/reference/dash-exports)。

**顯示平行堆疊圖表下圖**：控制堆疊在 [ **平行堆疊** ] 視窗中顯示的方向。

**如果寫入的資料未變更值，請忽略 GPU 記憶體存取例外** 狀況：如果資料未變更，會忽略在調試期間偵測到的競爭條件。 如需詳細資訊，請參閱將 [GPU 程式碼進行調試](../debugger/debugging-gpu-code.md)程式。

**使用 Managed 相容性模式**：將預設的調試引擎取代為舊版，以啟用這些案例：

- 您使用的是 c #、Visual Basic 或 F # 以外的 .NET 語言，其提供自己的運算式評估工具 (這包括 c + +/CLI) 。

- 您想要在混合模式偵錯工具期間啟用 c + + 專案的 [編輯後繼續]。

> [!NOTE]
> 選擇 [Managed 相容性模式] 會停用某些只在預設的偵錯工具中執行的功能。 舊版的偵錯工具引擎已在 Visual Studio 2012 中取代。

::: moniker range="vs-2017"
**使用舊版 c # 和 VB 運算式評估** 工具：偵錯工具將使用 Visual Studio 2013 c # 或 Visual Basic 運算式評估工具，而不是 Visual Studio 2015 Roslyn 為基礎的運算式評估工具。
::: moniker-end

**針對可能不安全的進程使用自訂偵錯工具視覺化程式時發出警告， (僅限 Managed)**：當您使用的自訂偵錯工具視覺化程式在已調試的進程中執行程式碼時，Visual Studio 警告您，因為它可能正在執行 unsafe 程式碼。

**啟用 windows 偵錯工具堆積配置器 (僅限原生)**：啟用 windows 偵錯工具堆積來改善堆積診斷。 啟用此選項會影響偵錯效能。

**啟用 XAML 的 UI 偵錯工具**：當您開始 (**F5**) 支援的專案類型進行偵錯工具時，將會出現即時視覺化樹狀結構和即時屬性流覽視窗。 如需詳細資訊，請參閱 [在偵錯工具時檢查 XAML 屬性](../xaml-tools/inspect-xaml-properties-while-debugging.md)。

- **在 [即時視覺化樹狀結構] 中預覽選取的元素**：也會在 [ **即時視覺化樹狀** ] 視窗中選取其內容已選取的 XAML 元素。

- **顯示應用程式中的執行時間工具**：在正在進行調試的 XAML 應用程式主視窗上，顯示工具列中的 **即時視覺化樹狀** 命令。 此選項是在 Visual Studio 2015 Update 2 中引進。

- **啟用 XAML 熱重新載入**：可讓您在應用程式執行時，將 XAML 熱重新載入功能與 XAML 程式碼搭配使用。  (這項功能先前稱為「XAML 編輯後繼續」 ) 

::: moniker range=">= vs-2019" 
- **只啟用我的 XAML**：從 Visual Studio 2019 16.4 版開始， **即時視覺化樹狀結構** 預設只會顯示分類為使用者程式碼的 xaml。 如果您停用此選項，則工具中會顯示所有產生的 XAML 程式碼。

- **選取元素時關閉選取模式** 從 Visual Studio 2019 16.4 版開始，應用程式內工具列元素選取器按鈕 (**啟用選取專案**) 在選取元素時關閉。 如果您停用此選項，則在您再次按一下 [應用程式內] 工具列按鈕之前，元素選取會保持開啟。

- **將檔儲存 XAML 熱重新載入** 從 Visual Studio 2019 16.6 版開始，會在您儲存檔時套用 XAML 熱重新載入。

::: moniker-end

在進行 **調試時啟用診斷工具**：當您進行調試時，會出現 **診斷工具** 視窗。

**顯示調試** 程式時所經過的時間 PerfTip：程式碼視窗會在您進行偵錯工具時，顯示指定方法呼叫的經過時間。

**啟用 [編輯後繼續**]：在進行調試時啟用 [編輯後繼續] 功能。

- **啟用原生編輯後繼續**：您可以在對原生 c + + 程式碼進行偵錯工具時，使用編輯後繼續功能。 如需詳細資訊，請參閱 [ (c + +) ](../debugger/edit-and-continue-visual-cpp.md)的 [編輯後繼續]。

- **在 [繼續 (僅限原生) 上套用變更**： Visual Studio 自動編譯，並套用您從中斷狀態繼續程式時所做的任何未處理常式代碼變更。 如果未選取，您可以選擇使用 [**調試** 程式] 功能表下的 [套用程式 **代碼變更**] 專案套用變更。

- **警告過時的程式碼 (僅限原生)**：取得過時程式碼的警告。

當偵錯工具時，**在編輯器中顯示執行以按一下按鈕**：當選取這個選項時，會在進行偵錯工具時顯示 [[執行到按一下](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse)] 按鈕。

**當偵錯工具停止時，自動關閉主控台**：告知 Visual Studio 關閉偵錯工具結束時的主控台。

::: moniker range=">= vs-2019"
**啟用快速運算式評估 (僅限 Managed)**：讓偵錯工具透過模擬簡單屬性和方法的執行，以嘗試更快的評估。

**在外部進程中載入 debug 符號 (僅限原生)** 啟用此 [記憶體優化](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/) ，同時進行調試。

**在偵錯工具中中斷時將 Visual Studio 帶入前景** 當您在偵錯工具中暫停時，將 Visual Studio 切換至前景。
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>舊版 Visual Studio 中的可用選項

如果您使用較舊版本的 Visual Studio，可能會有一些額外的選項。

**啟用適用于 Uwp JAVAscript 應用程式的 Edge 開發人員工具 (實驗性)**：在 Microsoft Edge 中啟用 uwp javascript 應用程式的開發人員工具。

**針對 ASP.NET 啟用舊版 Chrome javascript 偵錯工具**：啟用適用于 ASP.NET 應用程式的舊版 chrome javascript 腳本偵錯工具。 第一次在 Chrome 中使用時，您可能需要登入瀏覽器，以啟用您已安裝的 Chrome 擴充功能。

**啟用 [例外狀況助理**]：針對 managed 程式碼，啟用 [例外狀況助理]。 從 Visual Studio 2017 開始，例外狀況協助程式會取代例外狀況小幫手。

**在未處理的例外狀況回溯呼叫堆疊**：讓 [ **呼叫堆疊** ] 視窗將呼叫堆疊復原到未處理的例外狀況發生之前的時間點。

以 **系統管理員身分執行 Visual Studio 時，請使用實驗性的方式啟動 Chrome JavaScript 調試**：告知 Visual Studio 嘗試在 JavaScript 調試過程中啟動 chrome 的新方式。

**如果啟動時沒有符號 (原生)**：當您在偵錯工具沒有符號資訊的程式時，顯示警告對話方塊。

**如果啟動時停用腳本調試** 程式，就會發出警告：當偵錯工具啟動時，如果停用腳本偵測，則會顯示警告對話方塊。

**使用原生相容性模式**：選取此選項時，偵錯工具會使用 Visual Studio 2010 原生偵錯工具，而不是新的原生偵錯工具。

- 當您正在進行 .NET c + + 程式碼的偵錯工具時，請使用這個選項，因為新的偵錯工具引擎不支援評估 .NET c + + 運算式。 然而，啟用 [原生相容性模式] 會停用許多相依於目前偵錯工具實作以進行運作的功能。 例如，舊版引擎缺少許多內建類型的視覺化檢視，例如 `std::string` Visual Studio 2015 專案。   在這些情況下，請使用 Visual Studio 2013 專案，以獲得最佳的偵錯工具體驗。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)

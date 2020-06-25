---
title: 選項對話方塊、[一般]、[調試] |Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5b03d7b45e488d7e8026a7d6835bbfba1efa210
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286553"
---
# <a name="general-debugging-options"></a>一般調試選項

若要設定 Visual Studio 偵錯工具選項，請選取 [**工具**] [  >  **選項**]，然後在 [偵測] 下選取或取消選取 [**一般**] 選項旁的方塊。 **Debugging** 您可以使用 [**工具**] [匯  >  **入和匯出設定**] [  >  **重設所有設定**] 來還原所有預設設定。 若要重設設定的子集，請使用 [匯**入和匯出設定] 嚮導**儲存您的設定，然後再進行您要測試的變更，然後在之後匯入儲存的設定。

您可以設定下列**一般**選項：

**刪除所有中斷點之前先詢問**：在完成 [**刪除所有中斷點**] 命令之前需要確認。

**當一個進程中斷時，中斷所有進程**：當發生中斷時，同時中斷附加偵錯工具的所有進程。

在**例外狀況跨越 AppDomain 或 managed/原生界限時中斷**：在 managed 或混合模式的偵錯工具中，當下列條件成立時，common language runtime 可以攔截跨應用程式域界限或 managed/原生界限的例外狀況：

1. 當機器碼使用 COM Interop 呼叫受控程式碼，且受控程式碼擲回例外狀況時。 請參閱 [COM Interop 簡介](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop)。

2. 當在應用程式定義域 1 中執行的受控程式碼呼叫應用程式定義域 2 中的受控程式碼，且應用程式定義域 2 中的程式碼擲回例外狀況時。 請參閱[使用應用程式定義域設計程式](/dotnet/articles/framework/app-domains/index)。

3. 當程式碼使用反映呼叫函數時，該函式會擲回例外狀況。 請參閱[反映](/dotnet/framework/reflection-and-codedom/reflection)。

在條件2和3中，例外狀況有時會由中的 managed 程式碼攔截， `mscorlib` 而不是由 common language runtime 攔截。 這個選項不會影響被 `mscorlib` 攔截之例外狀況的中斷。

**啟用位址層級的調試**程式：啟用在位址層級（[反組**解碼] 視窗、[緩存**器 **] 視窗和**位址中斷點）進行偵錯工具的「高級」功能。

- **如果無法使用來源**，則顯示反組解碼：當您的程式碼無法使用來源時，會自動顯示 [反組**解碼] 視窗**。

**啟用中斷點篩選**：可讓您在中斷點上設定篩選，使其只會影響特定的進程、執行緒或電腦。

**使用新的例外**狀況協助程式：啟用取代例外狀況小幫手的例外狀況 helper。 （從 Visual Studio 2017 開始支援例外狀況 Helper）

> [!NOTE]
> 若為 managed 程式碼，此選項先前稱為 **[啟用例外狀況助理**]。

**啟用 Just My Code**：偵錯工具只會顯示並逐步執行使用者程式碼（"My Code"），忽略系統程式碼和其他已優化或不具有偵錯工具符號的程式碼。

- **如果啟動時沒有使用者程式碼則警告（僅限 Managed）**：啟動時，如果啟用 Just My Code，則此選項會在沒有使用者代碼（"My Code"）時警告您。

**啟用 .NET Framework 原始碼逐步**執行：允許偵錯工具逐步執行 .NET Framework 來源。 啟用此選項會自動停用 Just My Code。 .NET Framework 符號會下載到快取位置。 使用 [**選項**] 對話方塊、[**調試**類別目錄]、[**符號**] 頁面來變更快取位置。

不進入**屬性和運算子（僅限 Managed）**：防止偵錯工具逐步執行 Managed 程式碼中的屬性和運算子。

**啟用屬性評估及其他隱含函式呼叫**：開啟 [變數] 視窗和 [**快速**監看式] 對話方塊中的屬性自動評估和隱含函式呼叫。

- 在**變數視窗中呼叫物件的字串轉換函式（僅限 c # 和 JavaScript）**：評估變數視窗中的物件時，執行隱含字串轉換呼叫。 結果會顯示為字串，而不是類型名稱。 只適用於偵錯 C# 程式碼時。 DebuggerDisplay 屬性可能會覆寫此設定（請參閱[使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)）。

**啟用來源伺服器支援**：告訴 Visual Studio 偵錯工具從執行 SrcSrv （）通訊協定的來源伺服器取得來源檔案 `srcsrv.dll` 。 Team Foundation Server 和 Windows 偵錯工具這兩個來源伺服器會實作通訊協定。 如需有關 SrcSrv 設定的詳細資訊，請參閱[SrcSrv](/windows-hardware/drivers/debugger/srcsrv)檔。 此外，請參閱[指定符號（.pdb）和原始檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

> [!IMPORTANT]
> 因為讀取 *.pdb* 檔案可以執行檔案中的任意程式碼，請確定您信任伺服器。

- 將**來源伺服器診斷訊息列印到 [輸出] 視窗**：啟用 [來源伺服器支援] 時，此設定會開啟 [診斷顯示]。

- **允許部分信任元件的來源伺服器（僅限受控）**：啟用來源伺服器支援時，此設定會覆寫未抓取部分信任元件來源的預設行為。

- **一律執行不受信任的來源伺服器命令而不提示**：當啟用來源伺服器支援時，此設定會覆寫執行不受信任的命令時提示的預設行為。

**啟用來源連結支援**：告訴 Visual Studio 偵錯工具下載包含來源連結資訊之 *.pdb*檔案的來源檔案。 如需來源連結的詳細資訊，請參閱[來源連結規格](/dotnet/standard/library-guidance/sourcelink)。

> [!IMPORTANT]
> 因為來源連結會使用 HTTP 或 HTTPs 來下載檔案，所以請確定您信任 *.pdb*檔案。

- **切換回所有來源連結要求的 Git 認證管理員驗證**：當來源連結支援已啟用，且來源連結要求驗證失敗時，Visual Studio 接著呼叫 Git 認證管理員。

**反白顯示中斷點的整個原始程式列和目前的語句（僅限 c + +）**：當偵錯工具強調顯示中斷點或目前的語句時，它會將整行醒目提示。

**來源檔案必須完全符合原始版本**：告訴偵錯工具驗證來源檔案是否符合用來建立您要進行偵錯工具之可執行檔的原始程式碼版本。 當版本不相符時，系統會提示您尋找相符的來源。 如果找不到相符的原始程式檔，偵錯期間將不會顯示原始程式碼。

將**所有輸出視窗文字重新導向到**即時運算視窗：將通常會出現在 [**輸出**] 視窗中的所有偵錯工具訊息，傳送至 [即時**運算] 視窗**。

**在變數視窗中顯示物件的原始結構**：關閉所有物件結構視圖自訂。 如需有關視圖自訂的詳細資訊，請參閱[建立 managed 物件的自訂視圖](../debugger/create-custom-views-of-managed-objects.md)。

**在模組載入時隱藏 jit 優化（僅限 Managed）**：在載入模組時停用 managed 程式碼的 jit 優化，並在附加偵錯工具時編譯 jit。 停用最佳化可更容易偵錯一些問題，但消耗較多效能。 如果正在使用 Just My Code，隱藏 JIT 最佳化會使非使用者程式碼顯示為使用者程式碼 ("My Code")。 如需詳細資訊，請參閱[JIT 優化和調試](../debugger/jit-optimization-and-debugging.md)程式。

**啟用 ASP.NET 的 JavaScript 偵錯工具（Chrome、Microsoft Edge 和 IE）**：啟用 ASP.NET 應用程式的腳本偵錯工具。 第一次在 Chrome 中使用時，您可能需要登入瀏覽器，以啟用您已安裝的 Chrome 延伸模組。 停用此選項以還原成舊版行為。

::: moniker range=">= vs-2019"
**啟用使用多目標 JavaScript 偵錯工具，以在適用的目標中進行 JavaScript 的偵測（需要重新開機偵錯工具）** 可以同時連接到瀏覽器和後端，讓您可以從編輯器中，直接對在用戶端和伺服器中執行的程式碼進行偵錯工具。
::: moniker-end

**載入 dll 匯出（僅限原生）**：載入 dll 匯出資料表。 若您使用 Windows 訊息、Windows 程序 (WindowProc)、COM 物件、封送處理或是任何您沒有其符號的 dll，則 dll 匯出資料表的符號資訊會很有幫助。 讀取 dll 匯出資訊會產生一些額外負荷。 因此，這項功能預設為關閉。

若您想知道 dll 匯出表中可使用的符號，請使用 `dumpbin /exports`。 這些符號適用於任何 32 位元系統 dll。 讀取 `dumpbin /exports` 輸出時，您可以看到確實的函式名稱，包含非英數字元。 這對設定函式的中斷點來說很有幫助。 dll 匯出表中的函式名稱在偵錯工具中的其他位置可能會顯示為已被截斷。 這些呼叫都按呼叫順序列出，目前的函式 (巢狀最深處) 列在頂端。 如需詳細資訊，請參閱 [dumpbin /exports](/cpp/build/reference/dash-exports)。

**顯示平行堆疊圖表底部**：控制堆疊在 [**平行堆疊**] 視窗中顯示的方向。

**如果寫入的資料未變更值，請忽略 GPU 記憶體存取例外**狀況：如果資料未變更，則忽略在進行偵錯工具期間偵測到的競爭條件。 如需詳細資訊，請參閱偵測[GPU 程式碼](../debugger/debugging-gpu-code.md)。

**使用 Managed 相容性模式**：以舊版取代預設的調試引擎，以啟用這些案例：

- 您使用 c #、Visual Basic 或 F # 以外的 .NET 語言，它會提供自己的運算式評估工具（這包括 c + +/CLI）。

- 您想要在混合模式的偵錯工具期間啟用 c + + 專案的 [編輯後繼續]。

> [!NOTE]
> 選擇 [Managed 相容性模式] 會停用某些僅在預設的偵錯工具中執行的功能。 舊版的偵錯工具引擎已取代為 Visual Studio 2012。

::: moniker range="vs-2017"
**使用舊版 c # 和 VB 運算式評估**工具：偵錯工具會使用 Visual Studio 2013 c # 或 Visual Basic 運算式評估工具，而不是 Visual Studio 2015 Roslyn 為基礎的運算式評估工具。
::: moniker-end

**對可能不安全的進程使用自訂偵錯工具視覺化檢視時發出警告（僅限 Managed）**： Visual Studio 當您使用的自訂偵錯工具視覺化檢視在已調試的進程中執行程式碼時警告您，因為它可能執行不安全的程式碼。

**啟用 windows debug 堆積配置器（僅限原生）**：啟用 windows debug 堆積來改善堆積診斷。 啟用此選項會影響偵錯效能。

**啟用 XAML 的 UI 偵錯工具**： [即時視覺化樹狀] 和 [即時屬性探索] 視窗將會在您開始偵錯工具（**F5**）支援的專案類型時出現。 如需詳細資訊，請參閱[在偵錯工具時檢查 XAML 屬性](../xaml-tools/inspect-xaml-properties-while-debugging.md)。

- **預覽 [即時視覺化樹狀結構] 中選取**的專案：在 [**即時視覺化樹狀**] 視窗中，也會選取其內容已選取的 XAML 元素。

- **在應用程式中顯示執行時間工具**：在正在進行調試之 XAML 應用程式的主視窗上，顯示工具列中的**即時視覺化樹狀**命令。 此選項是在 Visual Studio 2015 Update 2 中引進。

- **啟用 Xaml 熱重載**：當您的應用程式正在執行時，可讓您使用 Xaml 的熱重載功能搭配 xaml 程式碼。 （這項功能先前稱為「XAML 編輯後繼續」）

::: moniker range=">= vs-2019" 
- **僅啟用我的 XAML**：從 Visual Studio 2019 16.4 版開始，**即時視覺化樹狀結構**預設只會顯示分類為使用者程式碼的 XAML。 如果您停用此選項，則工具中會顯示所有產生的 XAML 程式碼。

- **選取元素時關閉選取模式**從 Visual Studio 2019 16.4 版開始，選取專案時，應用程式內工具列元素選取器按鈕（**啟用選取**）會關閉。 如果您停用此選項，元素選取會保持開啟，直到您再次按一下 [應用程式內] 工具列按鈕為止。

- **在檔儲存時套用 XAML 熱重載**從 Visual Studio 2019 16.6 版開始，當您儲存檔時，會套用 XAML 熱重載。

::: moniker-end

在**調試過程中啟用診斷工具**：當您要進行調試時，**診斷工具**視窗隨即出現。

執行**偵錯工具時顯示**已耗用的時間 PerfTip：程式碼視窗會在您進行偵錯工具時，顯示給定方法呼叫的經過時間。

**啟用 [編輯後繼續**]：在進行調試時啟用 [編輯後繼續] 功能。

- **啟用原生編輯後繼續**：您可以使用 [編輯後繼續] 功能，同時偵錯工具的原生 c + + 程式碼。 如需詳細資訊，請參閱[編輯後繼續（c + +）](../debugger/edit-and-continue-visual-cpp.md)。

- **繼續時套用變更（僅限原生）**： Visual Studio 會自動編譯，並套用您在從中斷狀態繼續處理時所做的任何未完成程式碼變更。 如果未選取此選項，您可以使用 [**調試**程式] 功能表下的 [套用程式**代碼變更**] 專案，選擇套用變更。

- **警告過時程式碼（僅限原生）**：取得過時程式碼的相關警告。

在**進行調試時顯示 [執行] 以在編輯器中按下按鈕**：選取這個選項時，會在進行調試時顯示 [[執行到按一下](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse)] 按鈕。

**停用調試時，自動關閉主控台**：告訴 Visual Studio 在調試會話結束時關閉主控台。

::: moniker range=">= vs-2019"
**啟用快速運算式評估（僅限 Managed）**：可讓偵錯工具藉由模擬簡單屬性和方法的執行，以嘗試更快速的評估。

**在外部進程中載入 debug 符號（僅限機器碼）** 在進行調試時啟用此[記憶體優化](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/)。

**中斷偵錯工具時，將 Visual Studio 帶入前景**當您在偵錯工具中暫停時，將 Visual Studio 切換為前景。
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>舊版 Visual Studio 中可用的選項

如果您使用較舊版本的 Visual Studio，可能會出現一些額外的選項。

**啟用適用于 Uwp JAVAscript 應用程式的 Edge 開發人員工具（實驗性）**：在 Microsoft Edge 中啟用適用于 uwp javascript 應用程式的開發人員工具。

**啟用適用于 ASP.NET 的舊版 Chrome javascript 偵錯工具**：啟用 ASP.NET 應用程式的舊版 chrome javascript 腳本偵錯工具。 第一次在 Chrome 中使用時，您可能需要登入瀏覽器，以啟用您已安裝的 Chrome 延伸模組。

**啟用 [例外狀況助理**]：針對 managed 程式碼，啟用 [例外狀況助理]。 從 Visual Studio 2017 開始，例外狀況協助程式取代了例外狀況小幫手。

**在未處理的例外狀況上回溯呼叫堆疊**：使 [**呼叫堆疊**] 視窗將呼叫堆疊復原到未處理的例外狀況發生之前的時間點。

**在以系統管理員身分執行 Visual Studio 時，使用實驗性的方式啟動 Chrome JavaScript 調試**：告訴 Visual Studio 在 JavaScript 調試過程中嘗試以新的方式啟動 chrome。

**如果啟動時沒有符號，就會發出警告（僅限機器碼）**：當您在偵錯工具沒有符號資訊時，會顯示警告對話方塊。

**如果啟動時停用腳本調試**程式，則發出警告：在啟動偵錯工具時顯示警告對話方塊，並停用腳本偵測。

**使用原生相容性模式**：當選取此選項時，偵錯工具會使用 Visual Studio 2010 原生偵錯工具，而不是新的原生偵錯工具。

- 當您要偵錯工具代碼時，請使用此選項，因為新的偵錯工具引擎不支援評估 .NET c + + 運算式。 然而，啟用 [原生相容性模式] 會停用許多相依於目前偵錯工具實作以進行運作的功能。 例如，舊版引擎缺少許多適用于內建類型的視覺化檢視，例如 `std::string` Visual Studio 2015 專案。   在這些情況下，請使用 Visual Studio 2013 專案來達到最佳的偵錯工具體驗。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)

---
title: 一般、除錯、選項對話框 :微軟文件
ms.date: 11/12/2019
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
ms.openlocfilehash: 98bbd65d11b26d9b35000e4acbe4d28a585f8ddc
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472693"
---
# <a name="general-debugging-options"></a>一般除錯選項

要設置 Visual Studio 除錯器選項,請選擇 **「工具** > **選項**」,並在 **「除錯」** 選擇或取消選擇 **「一般**」選項旁邊的框。 您可以使用**工具** > **匯入與匯出設定** > 回復所有預設設定**重設所有設定**。 要重置設定子集,請先使用 **「導入和匯出設置設置嚮導」** 保存設定,然後再進行要測試的更改,然後導入保存的設置。

您可以設定以下**一般**選項:

**刪除所有斷點之前,請詢問**:在完成 **「刪除所有斷點」** 命令之前,需要確認。

**當一個進程中斷時中斷所有進程**:當發生中斷時,同時中斷將調試器附加到的所有進程。

**當異常跨越 AppDomain 或託管/本機邊界時中斷**:在託管或混合模式調試中,通用語言運行時可以捕獲在以下條件為 true 時跨越應用程式域邊界或託管/本機邊界的異常:

1. 當機器碼使用 COM Interop 呼叫受控程式碼，且受控程式碼擲回例外狀況時。 請參閱 [COM Interop 簡介](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop)。

2. 當在應用程式定義域 1 中執行的受控程式碼呼叫應用程式定義域 2 中的受控程式碼，且應用程式定義域 2 中的程式碼擲回例外狀況時。 請參閱[使用應用程式定義域設計程式](/dotnet/articles/framework/app-domains/index)。

3. 當代碼使用反射調用函數時,該函數將引發異常。 請參閱[反射](/dotnet/framework/reflection-and-codedom/reflection)。

在條件 2 和 3 中,異常`mscorlib`有時被託管代碼捕獲,而不是由通用語言運行時捕獲。 這個選項不會影響被 `mscorlib` 攔截之例外狀況的中斷。

**啟用位址級除錯**:啟用用於在位址等級(**拆解**視窗、**寄存器**視窗和位址斷點)進行除錯的進階功能。

- **如果源不可用,請顯示拆解**:在除錯來源不可用的程式碼時,自動顯示 **「拆解**」視窗。

**開啟斷點篩選器**:使您能夠在斷點上設置篩選器,以便它們僅影響特定進程、線程或電腦。

**使用新的例外説明程式**:啟用替換異常助手的異常幫助程式。 ( 支援從 Visual Studio 2017 開始使用例外說明程式)

> [!NOTE]
> 對託管代碼,這個選項稱為**開啟異常助理**。

**僅啟用「我的代碼**」:除錯器僅顯示和步驟到使用者代碼(「我的代碼」),忽略系統代碼和其他經過最佳化或沒有除錯符號的代碼。

- **警告啟動時沒有用戶代碼(僅限託管):** 當除錯從啟用的「僅我的程式碼」開始時,此選項將警告您如果沒有使用者代碼("我的代碼")。

**啟用 .NET 框架源步長**:允許除錯器步進 .NET 框架來源。 啟用此選項會自動禁用"僅我的代碼」。 .NET 框架符號將下載到緩存位置。 使用 **「選項**」對話框「**除錯**類別 **」「 符號」** 頁更改快取位置。

**跨步執行屬性和運算符(僅限託管):** 防止除錯器步進託管代碼中的屬性和運算符號。

**啟用屬性計算和其他隱式函數調用**:打開變數視窗中的屬性和隱式函數調用的自動計算和隱式函數調用以及**QuickWatch**對話方塊。

- **在變數視窗(僅限 C# 和 JavaScript)中的物件上調用字串轉換函數**:在變數視窗中評估物件時執行隱式字串轉換調用。 結果顯示為字串而不是類型名稱。 只適用於偵錯 C# 程式碼時。 此設定可能被除錯器顯示屬性覆蓋(請參閱[使用除錯器顯示屬性](../debugger/using-the-debuggerdisplay-attribute.md))。

**啟用來源伺服器支援**:告訴 Visual Studio 除錯器從實現 SrcSrv ()`srcsrv.dll`協定的來源伺服器獲取來源檔案。 Team Foundation Server 和 Windows 偵錯工具這兩個來源伺服器會實作通訊協定。 有關 SrcSrv 設置的詳細資訊,請參閱[SrcSrv](/windows-hardware/drivers/debugger/srcsrv)文件。 此外,請參閱[指定符號 (.pdb) 和來源檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

> [!IMPORTANT]
> 因為讀取 *.pdb* 檔案可以執行檔案中的任意程式碼，請確定您信任伺服器。

- **將源伺服器診斷訊息列印到「輸出」視窗**:啟用源伺服器支援時,此設置將打開診斷顯示。

- **允許源伺服器用於部分信任程式集(僅限託管):** 啟用源伺服器支援時,此設置將覆蓋不檢索部分信任程式集的源的默認行為。

- **始終運行不受信任的源伺服器命令,而不提示**:啟用源伺服器支援時,此設置將覆蓋運行不受信任的命令時的預設提示行為。

**開啟來源連結支援**:告訴可視化工作室調試器下載包含源連結資訊的 *.pdb*檔案的源檔。 有關來源連結的詳細資訊,請參閱[源連結規範](/dotnet/standard/library-guidance/sourcelink)。

> [!IMPORTANT]
> 由於源連結將使用 http 或 Htcri 檔案,因此請確保信任 *.pdb*檔。

- **回退到所有源連結請求的 Git 認證認證**:啟用來源連結支援,並且源連結請求失敗身份驗證時,Visual Studio 調用 Git 認證分析。

**突出顯示斷點和當前語句的整行(僅限C++):** 當調試器突出顯示斷點或當前語句時,它會突出顯示整行。

**要求源檔與原始版本完全匹配**:告訴除錯器驗證源檔是否與用於生成正在調試的可執行檔的原始程式碼的版本匹配。 當版本不匹配時,系統會提示您尋找匹配來源。 如果找不到相符的原始程式檔，偵錯期間將不會顯示原始程式碼。

**將所有輸出視窗文字重定向到「立即」視窗**:將通常出現在 **「輸出」** 視窗中的所有除錯器訊息發送到 **「立即」** 視窗。

**在變數視窗中顯示物件的原始結構**:關閉所有物件結構檢視自定義項。 有關檢視自訂的詳細資訊,請參考[建立託管物件的自訂檢視](../debugger/create-custom-views-of-managed-objects.md)。

**在模組載入(僅限託管)上禁止 JIT 優化**:在載入模組時禁用託管代碼的 JIT 優化,並在連接除錯器時編譯 JIT。 停用最佳化可更容易偵錯一些問題，但消耗較多效能。 如果正在使用 Just My Code，隱藏 JIT 最佳化會使非使用者程式碼顯示為使用者程式碼 ("My Code")。 有關詳細資訊,請參閱[JIT 優化和除錯](../debugger/jit-optimization-and-debugging.md)。

**為ASP.NET(Chrome、微軟邊緣和 IE)啟用 JavaScript 調試:** 啟用ASP.NET應用的腳本調試器。 首次使用 Chrome 時,您可能需要登錄瀏覽器才能啟用您安裝的 Chrome 擴展名。 禁用此選項可還原為舊行為。

**為 UWP JavaScript 應用啟用邊緣開發人員工具(實驗):** 啟用 Microsoft Edge 中 UWP JavaScript 應用的開發人員工具。

**為ASP.NET啟用傳統的 Chrome JavaScript 調試器**:為ASP.NET應用啟用傳統的 Chrome JAvaScript 腳本調試器。 首次使用 Chrome 時,您可能需要登錄瀏覽器才能啟用您安裝的 Chrome 擴展名。

**使用實驗方法啟動 Chrome JavaScript 調試時運行 Visual Studio 作為管理員**: 告訴可視化工作室嘗試在 JavaScript 調試期間啟動 Chrome 的新方法。

**載入 dll 匯出(僅限本機):** 載入 dll 匯出表。 若您使用 Windows 訊息、Windows 程序 (WindowProc)、COM 物件、封送處理或是任何您沒有其符號的 dll，則 dll 匯出資料表的符號資訊會很有幫助。 讀取 dll 匯出資訊會產生一些額外負荷。 因此，這項功能預設為關閉。

若您想知道 dll 匯出表中可使用的符號，請使用 `dumpbin /exports`。 這些符號適用於任何 32 位元系統 dll。 讀取 `dumpbin /exports` 輸出時，您可以看到確實的函式名稱，包含非英數字元。 這對設定函式的中斷點來說很有幫助。 dll 匯出表中的函式名稱在偵錯工具中的其他位置可能會顯示為已被截斷。 這些呼叫都按呼叫順序列出，目前的函式 (巢狀最深處) 列在頂端。 如需詳細資訊，請參閱 [dumpbin /exports](/cpp/build/reference/dash-exports)。

**自下而上顯示並行堆疊圖**:控制堆疊在 **「並行堆疊**」視窗中顯示的方向。

**如果寫入的數據未更改值,請忽略 GPU 記憶體訪問異常**:如果資料未更改,則忽略在調試過程中檢測到的爭用條件。 有關詳細資訊,請參閱除錯[GPU 代碼](../debugger/debugging-gpu-code.md)。

**使用託管相容性模式**:將預設除錯引擎取代為舊版本以啟用這些方案:

- 您使用的是提供其自己的運算式賦值器(包括C++/CLI)以外的 .NET 語言。C#、可視基本或 F#。

- 您希望在混合模式調試期間為C++專案啟用"編輯並繼續」。

> [!NOTE]
> 選擇託管相容性模式會禁用僅在預設調試引擎中實現的某些功能。 舊版調試引擎在 Visual Studio 2012 中被替換。

**使用傳統的 C# 和 VB 運算式賦值器**:調試器將使用 Visual Studio 2013 C# 或可視化基本運算式賦值器,而不是基於 Roslyn 的 Visual Studio 2015 運算式賦值器。

**在針對潛在的不安全進程(僅限託管)使用自訂調試器可視化器時發出警告**:當您使用在調試過程中運行代碼的自定義調試器可視化器時,Visual Studio 會發出警告,因為它可能運行不安全的代碼。

**啟用 Windows 調試堆分配器(僅限本機):** 啟用 Windows 調試堆以改進堆診斷。 啟用此選項會影響偵錯效能。

**為 XAML 啟用 UI 除錯工具**:當您開始**除錯受支援**的專案類型時,將顯示即時可視化樹和即時屬性瀏覽視窗。 有關詳細資訊,請參閱[在除錯時檢查 XAML 屬性](../xaml-tools/inspect-xaml-properties-while-debugging.md)。

- **預覽即時可視化樹中的選定元素**:其上下文被選中的 XAML 元素也在 **「即時可視化樹」** 視窗中被選中。

- **在應用程式中顯示執行時工具**:在正在除錯的 XAML 應用程式的主視窗中的工具列中顯示**即時可視化樹**命令。 此選項在 Visual Studio 2015 更新 2 中引入。

- **啟用 XAML 熱重新載入**:允許您在應用程式執行時使用 XAML 熱重新載入功能與 XAML 代碼。 (此功能以前稱為"XAML 編輯並繼續")

::: moniker range=">= vs-2019" 
- **僅啟用我的 XAML**: 從 Visual Studio 2019 版本 16.4 開始,預設情況下**的即時可視化樹**僅顯示歸類為用戶代碼的 XAML。 如果關閉這個選項,該工具中將顯示所有生成的 XAML 程式碼。

- **選擇元素時關閉選擇模式**從 Visual Studio 2019 版本 16.4 開始,應用內工具列元素選擇器按鈕 (**啟用選擇**) 在選擇元素時關閉。 如果關閉這個選項,元素選擇將保持打開狀態,直到您再次按下應用內工具列按鈕。
::: moniker-end

**除錯時啟用診斷工具**:除錯時將顯示**診斷工具**視窗。

**在調試時顯示已用時間 PerfTip:** 代碼視窗顯示調試時給定方法調用的已用時間。

**啟用編輯並繼續**:在除錯時啟用編輯並繼續"功能。

- **啟用本機編輯並繼續**:您可以在除錯本機C++代碼時使用"編輯並繼續"功能。 有關詳細資訊,請參閱[編輯並繼續 (C++)](../debugger/edit-and-continue-visual-cpp.md)。

- **在繼續時應用更改(僅限本機):Visual**Studio 會自動編譯並應用從中斷狀態繼續進程時所做的任何未完成的代碼更改。 如果未選取,則可以選擇使用 **「除錯」** 選單下的 **「應用程式代碼變更」 的變更變更**。

- **警告過時代碼(僅限本機代碼):** 獲取有關過時代碼的警告。

**除錯時在編輯器中顯示「執行到按下」按鈕**:選擇此選項時,除錯時將顯示[「運行到按下」](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse)按鈕。

**除錯停止時自動關閉主控台**:告訴 Visual Studio 在調試工作階段結束時關閉主控台。

::: moniker range=">= vs-2019"
**啟用快速運算式計算(僅限託管):** 允許除錯器透過類比簡單屬性和方法的執行來嘗試更快的計算。
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>舊版本的 Visual Studio 提供選項

如果您使用的是舊版本的 Visual Studio,則可能存在一些其他選項。

**啟用異常助理**:對於託管代碼,啟用異常助理。 從 Visual Studio 2017 開始,異常幫助程式替換了異常助手。

**解除未處理異常上的調用堆疊**:導致**調用堆疊**視窗將調用堆疊回滾到未處理異常發生之前的點。

**警告啟動時沒有符號(僅限本機):** 在除錯除試器沒有符號資訊的程式時顯示警告對話方塊。

**警告在啟動時文本調試是否禁用**:在啟動除錯器時顯示一個警告對話框,禁用腳本調試。

**使用本機相容性模式**:選擇此選項后,除錯器使用 Visual Studio 2010 本機調試器,而不是新的本機調試器。

- 除錯 .NET C++ 代碼時使用此選項,因為新的除錯引擎不支援計算.NET C++運算式。 然而，啟用 [原生相容性模式] 會停用許多相依於目前偵錯工具實作以進行運作的功能。 例如,舊引擎缺少許多內置類型的可視化工具,如`std::string`Visual Studio 2015 專案中。   在這些情況下,使用 Visual Studio 2013 項目獲得最佳調試體驗。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
- [首先檢視除錯器](../debugger/debugger-feature-tour.md)

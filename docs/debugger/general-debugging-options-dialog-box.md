---
title: 一般、 偵錯、 選項對話方塊 |Microsoft Docs
ms.date: 11/09/2018
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
ms.openlocfilehash: 29b730bacd589e7b42b9f87086eda91d9e199622
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59504415"
---
# <a name="general-debugging-options"></a>一般偵錯選項

若要設定 Visual Studio 偵錯工具選項，請選取**工具** > **選項**，然後在**偵錯**選取或取消選取方塊旁**一般**選項。 您可以還原所有預設設定**工具** > **匯入和匯出設定** > **重設所有設定**。 若要重設設定的子集，請將儲存您的設定**匯入和匯出設定精靈**之前進行您想要測試的變更，然後匯入儲存的設定之後。

您可以設定下列**一般**選項：

**刪除所有中斷點時先詢問**：完成 [刪除所有中斷點] 命令之前需要確認。

**如果其中一個處理序中斷，就中斷所有處理序**：發生中斷時，同時中斷偵錯工具附加至的所有處理序。

**例外狀況為跨 AppDomain 或受控/機器碼界限時中斷**：在 Managed 或混合模式偵錯中，當符合下列條件，Common Language Runtime 就可以攔截跨應用程式定義域界限或 Managed/原生界限的例外狀況：

1. 當機器碼使用 COM Interop 呼叫受控程式碼，且受控程式碼擲回例外狀況時。 請參閱 [COM Interop 簡介](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop)。

2. 當在應用程式定義域 1 中執行的受控程式碼呼叫應用程式定義域 2 中的受控程式碼，且應用程式定義域 2 中的程式碼擲回例外狀況時。 請參閱[使用應用程式定義域設計程式](/dotnet/articles/framework/app-domains/index)。

3. 當程式碼呼叫的函式使用反映，，和該函式會擲回的例外狀況。 請參閱[反映](/dotnet/framework/reflection-and-codedom/reflection)。

在 條件 2 和 3，攔截的例外狀況是有時在 managed 程式碼`mscorlib`而不是由通用語言執行平台。 這個選項不會影響被 `mscorlib` 攔截之例外狀況的中斷。

**啟用位址層級偵錯**：在位址層級啟用進階偵錯功能 ([反組譯碼] 視窗、[暫存器] 視窗和位址中斷點)。

- **找不到原始碼時則顯示反組譯碼**： 會自動顯示**反組譯碼**時的來源是無法使用的程式碼偵錯 視窗。

**啟用中斷點篩選條件**：可讓您設定中斷點的篩選條件，讓中斷點只會影響特定處理序、執行緒或電腦。

**使用新的例外狀況協助程式**：可讓取代例外狀況助理的例外狀況協助程式。 （例外狀況協助程式支援從 Visual Studio 2017 開始）

> [!NOTE]
> Managed 程式碼，這個選項先前已呼叫**啟用例外狀況助理**。

**啟用 Just My Code**：偵錯工具會隨即顯示且僅逐步執行使用者程式碼 ("My Code")，並忽略系統程式碼和其他已最佳化或沒有偵錯符號的程式碼。

- **如果啟動時沒有使用者程式碼則警告 (僅限受控)**： 在啟用 Just My Code 的狀態下開始偵錯時，如果沒有使用者程式碼 ("My Code")，這個選項會警告您。

**啟用 .NET Framework 原始碼逐步偵錯**：允許偵錯工具逐步執行 .NET Framework 原始檔。 自動啟用此選項會停用 Just My Code。 .NET framework 符號將會下載至快取位置。 變更快取位置**選項** 對話方塊中，**偵錯**類別**符號**頁面。

**不進入屬性和運算子 (僅限受控)**：讓偵錯工具無法逐步執行 Managed 程式碼中的屬性和運算子。

**啟用屬性評估及其他隱含函式呼叫**：開啟變數視窗和 [快速監看式] 對話方塊中的屬性自動評估與隱含函式呼叫。

- **在變數視窗中呼叫物件上的字串轉換函式 (僅限 C# 和 JavaScript)**：在評估變數視窗中的物件時，執行隱含的字串轉換呼叫。 結果會顯示為字串，而不是類型名稱。 只適用於偵錯 C# 程式碼時。 DebuggerDisplay 屬性可能會覆寫此設定 (請參閱[使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md))。

**啟用來源伺服器支援**：告知 Visual Studio Debugger 從實作 SrcSrv (`srcsrv.dll`) 通訊協定的來源伺服器取得來源檔。 Team Foundation Server 和 Windows 偵錯工具這兩個來源伺服器會實作通訊協定。 如需 SrcSrv 設定的詳細資訊，請參閱[SrcSrv](/windows-hardware/drivers/debugger/srcsrv)文件。 此外，請參閱 <<c0> [ 指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

> [!IMPORTANT]
> 因為讀取 *.pdb* 檔案可以執行檔案中的任意程式碼，請確定您信任伺服器。

- **將來源伺服器診斷訊息列印到輸出視窗**： 啟用來源伺服器支援時，這個設定會開啟診斷顯示畫面。

- **允許部分信任組件的來源伺服器 (僅限受控)**： 當來源伺服器支援啟用時，這個設定會覆寫不擷取部分信任組件之來源的預設行為。

- **永遠執行未受信任的來源伺服器命令而不須提示**： 啟用來源伺服器支援時，此設定會覆寫提示執行不受信任的命令時的預設的行為。

**啟用來源連結支援**：會告知 Visual Studio 偵錯工具下載來源檔案 *.pdb*包含來源連結資訊的檔案。 如需有關來源連結的詳細資訊，請參閱[來源連結規格](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md)。

> [!IMPORTANT]
>  因為來源連結將會下載使用 http 或 https 的檔案，請確定您信任 *.pdb*檔案。

- **改為對所有來源連結要求使用 Git 認證管理員驗證**： 當已啟用來源連結支援，並驗證失敗的來源連結要求時，Visual Studio 接著會呼叫 Git 認證管理員。

**反白顯示中斷點和目前的陳述式的整行 (C++只)**:當偵錯工具反白顯示中斷點或目前的陳述式時，它會反白顯示整行。

**原始程式檔必須完全符合原始版本**：告知偵錯工具驗證原始程式檔是否符合用來建置正在偵錯之可執行檔的原始程式碼版本。 當版本不符時，系統會提示您尋找相符的來源。 如果找不到相符的原始程式檔，偵錯期間將不會顯示原始程式碼。

**將所有輸出視窗文字重新導向到即時運算視窗**：將通常會出現在 [輸出] 視窗的所有偵錯工具訊息，改成傳送到 [即時運算] 視窗。

**在變數視窗中顯示物件的原始結構**：關閉所有物件結構檢視自訂。 如需有關檢視自訂的詳細資訊，請參閱[建立受管理物件的自訂檢視](../debugger/create-custom-views-of-dot-managed-objects.md)。

**模組載入時隱藏 JIT 最佳化 (僅限受控)**：在附加偵錯工具時若已載入模組且已編譯 JIT，便停用 Managed 程式碼的 JIT 最佳化。 停用最佳化可更容易偵錯一些問題，但消耗較多效能。 如果正在使用 Just My Code，隱藏 JIT 最佳化會使非使用者程式碼顯示為使用者程式碼 ("My Code")。 如需詳細資訊，請參閱 < [JIT 最佳化和偵錯](../debugger/jit-optimization-and-debugging.md)。

**為 ASP.NET 啟用 JavaScript 偵錯 (Chrome、Edge 及 IE)**：可讓 ASP.NET 應用程式的指令碼偵錯工具。 在 Chrome 中的第一次使用，您可能需要登入瀏覽器，以啟用您已安裝的 Chrome 擴充功能。 停用此選項可還原為舊版的行為。

**啟用適用於 UWP JavaScript 應用程式的 Edge 開發人員工具 (實驗性)**：可讓開發人員工具，在 Edge 中的 UWP JavaScript 應用程式。

**為 ASP.NET 啟用舊版 Chrome JavaScript 偵錯工具**：啟用舊版 Chrome JavaScript 指令碼偵錯工具的 ASP.NET 應用程式。 在 Chrome 中的第一次使用，您可能需要登入瀏覽器，以啟用您已安裝的 Chrome 擴充功能。

**以系統管理員身分執行 Visual Studio 時，請以實驗方式啟動 Chrome JavaScript 偵錯**：會告訴 Visual Studio 嘗試啟動 Chrome JavaScript 偵錯期間的新方式。

**載入 dll 匯出 (僅限機器碼)**：載入 dll 匯出資料表。 若您使用 Windows 訊息、Windows 程序 (WindowProc)、COM 物件、封送處理或是任何您沒有其符號的 dll，則 dll 匯出資料表的符號資訊會很有幫助。 讀取 dll 匯出資訊會產生一些額外負荷。 因此，這項功能預設為關閉。

若您想知道 dll 匯出表中可使用的符號，請使用 `dumpbin /exports`。 這些符號適用於任何 32 位元系統 dll。 讀取 `dumpbin /exports` 輸出時，您可以看到確實的函式名稱，包含非英數字元。 這對設定函式的中斷點來說很有幫助。 dll 匯出表中的函式名稱在偵錯工具中的其他位置可能會顯示為已被截斷。 這些呼叫都按呼叫順序列出，目前的函式 (巢狀最深處) 列在頂端。 如需詳細資訊，請參閱 [dumpbin /exports](/cpp/build/reference/dash-exports)。

**由下而上顯示平行堆疊圖表**：控制堆疊在 [平行堆疊] 視窗中顯示的方向。

**如果寫入的資料未變更值，請忽略 GPU 記憶體存取例外狀況**：如果資料沒有變更，請忽略偵錯期間偵測到的競爭條件。 如需詳細資訊，請參閱 <<c0> [ 偵錯 GPU 程式碼](../debugger/debugging-gpu-code.md)。

**使用受控相容性模式**：將預設偵錯引擎取代為舊版偵錯引擎，以啟用這些案例：

- 您要使用.NET Framework 語言以外的其他C#，Visual Basic 或F#，提供它自己的運算式評估工具 (這包括C++/CLI)。

- 您想要啟用編輯後繼續C++在混合的模式偵錯期間的專案。

> [!NOTE]
> 選擇 Managed 相容性模式會停用只在預設偵錯引擎中實作某些功能。 Visual Studio 2012 中，已取代舊版的偵錯引擎。

**使用舊版 C# 和 VB 運算式評估工具**：偵錯工具會使用 Visual Studio 2013C#或 Visual Basic 運算式評估工具，而非 Visual Studio 2015 roslyn 運算式評估工具。

**對可能不安全的處理序使用自訂偵錯工具視覺化檢視時發出警告 (僅限受控)**：當您使用的自訂偵錯工具視覺化檢視在偵錯項目處理序中執行程式碼時，Visual Studio 會發出警告，原因是它可能會執行到不安全的程式碼。

**啟用 Windows 偵錯堆積配置器 (僅限機器碼)**：啟用 Windows 偵錯堆積，以改善堆積診斷。 啟用此選項會影響偵錯效能。

**啟用 XAML 的 UI 偵錯工具**：當您開始為支援的專案類型進行偵錯 (**F5**) 時，即時視覺化樹狀和即時屬性瀏覽視窗會隨即出現。 如需詳細資訊，請參閱 <<c0> [ 偵錯時檢查 XAML 屬性](../debugger/inspect-xaml-properties-while-debugging.md)。

- **在即時視覺化樹狀中預覽選取的元素**： 在 [即時視覺化樹狀] 視窗中，也會選取其內容已被選取的 XAML 元素。

- **在應用程式中顯示執行階段工具**：顯示**即時視覺化樹狀結構**在主視窗的 XAML 應用程式進行偵錯工具列中的命令。 在 Visual Studio 2015 Update 2 中引進了此選項。

- **啟用 XAML 編輯後繼續**： 可讓您使用 編輯後繼續使用 XAML 程式碼的功能。

**偵錯時啟用診斷工具**：[診斷工具] 視窗會在偵錯期間出現。

**偵錯時顯示經歷時間 PerfTip**：在您偵錯時，[程式碼] 視窗中會顯示指定之方法呼叫的已耗用時間。

**啟用編輯後繼續**：偵錯時啟用編輯後繼續功能。

- **啟用原生編輯後繼續**：在偵錯原生 C++ 程式碼時，您可以使用 [編輯後繼續] 功能。 如需詳細資訊，請參閱 <<c0> [ 編輯後繼續 (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)。</c0>

- **繼續時套用變更 (僅限機器碼)**：當從中斷狀態繼續處理序時，Visual Studio 會自動編譯和套用任何未完成的程式碼變更。 若未選取，您可以選擇使用 [偵錯] 功能表下的 [套用程式碼變更] 項目套用變更。

- **警告出現過時的程式碼 (僅限機器碼)**： 取得過時程式碼的警告。

**顯示 [執行]，請按一下以在偵錯時的編輯器中的按鈕**:選取此選項時，[執行至點選處](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse)按鈕將會顯示在偵錯時。

**偵錯停止時，自動關閉主控台**：會告知 Visual Studio 在偵錯工作階段結束時關閉主控台。

## <a name="options-available-in-older-versions-of-visual-studio"></a>在舊版的 Visual Studio 中可用的選項

如果您使用較舊版本的 Visual Studio，則可能會存在一些其他選項。

**啟用例外狀況助理**：Managed 程式碼，可讓例外狀況助理。 從 Visual Studio 2017 中，例外狀況協助程式取代例外狀況助理。

**發生未處理的例外狀況時回溯呼叫堆疊**：導致 [呼叫堆疊] 視窗將呼叫堆疊復原到無法處理的例外狀況發生之前。

**如果啟動時沒有符號，就提出警告 (僅限機器碼)**：當您偵錯一個偵錯工具沒有符號資訊這程式時，會顯示警告對話方塊。

**如果啟動時指令碼偵錯處於停用狀態則警告**：在啟動偵錯工具卻停用指令碼偵錯時，顯示警告對話方塊。

**使用原生相容性模式**：選取此選項時，偵錯工具會使用 Visual Studio 2010 原生偵錯工具，而不是新的原生偵錯工具。

- 使用此選項，當您偵錯.NETC++程式碼，因為新的偵錯引擎不支援評估.NETC++運算式。 然而，啟用 [原生相容性模式] 會停用許多相依於目前偵錯工具實作以進行運作的功能。 比方說，舊版引擎缺乏許多視覺化檢視內建型別之類的`std::string`Visual Studio 2015 專案中。   使用 Visual Studio 2013 專案，以在這些情況下獲得最佳的偵錯體驗。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
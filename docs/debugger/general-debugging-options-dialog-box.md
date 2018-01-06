---
title: "選項對話方塊、 一般、 偵錯，|Microsoft 文件"
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
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
helpviewer_keywords: Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: "46"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bf693d7a5339e57edeaed82c25ed552901e1ea51
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="general-debugging-options-dialog-box"></a>選項對話方塊、偵錯、一般
**工具 > 選項 > 偵錯 > 一般**頁面可讓您設定下列選項：  
  
**刪除所有中斷點時先詢問**  
完成之前需要確認**刪除所有中斷點**命令。  
  
**如果其中一個處理序中斷，就，中斷所有處理序**  
發生中斷時，同時中斷偵錯工具附加至的所有處理序。  
  
**例外狀況為跨 AppDomain 或 managed/原生界限時中斷**  
在 Managed 或混合模式偵錯中，當符合下列條件，Common Language Runtime 就可以攔截跨應用程式定義域界限或 Managed/原生界限的例外狀況：  
  
1\)當機器碼使用 COM Interop 呼叫 managed 程式碼，且 managed 程式碼擲回例外狀況。 請參閱[COM Interop 簡介](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop)。  
  
2\)當應用程式定義域 1 中執行的 managed 程式碼呼叫應用程式定義域 2 中的 managed 程式碼，且應用程式定義域 2 中的程式碼擲回例外狀況。 請參閱[Programming with Application Domains](/dotnet/articles/framework/app-domains/index)。  

3\)當程式碼使用反映，呼叫的函式，且函式擲回例外狀況。 請參閱[反映](/dotnet/framework/reflection-and-codedom/reflection)。  
  
在 條件 2 和 3 會攔截例外狀況有時的 managed 程式碼中`mscorlib`而不是 common language runtime。 這個選項不會影響被 `mscorlib` 攔截之例外狀況的中斷。  
  
**啟用位址層級偵錯**  
 啟用位址層級偵錯的進階功能 (**反組譯碼**視窗中，**註冊**視窗和位址中斷點)。  
  
- **如果來源不可以使用 顯示反組譯碼**  
    會自動顯示**反組譯碼**視窗，當您嘗試偵錯原始程式碼是無法使用。  
  
**啟用中斷點篩選條件**  
可讓您設定中斷點的篩選條件，讓中斷點只會影響特定處理序、執行緒或電腦。  
 
**使用新的例外狀況協助程式**  
可讓例外狀況協助程式 (Visual Studio 2017)，以取代例外狀況助理。
  
> [!NOTE]
> Managed 程式碼，此選項之前已呼叫**啟用例外狀況助理**。 
  
**啟用 Just My Code**  
偵錯工具會隨即顯示且僅逐步執行使用者程式碼 ("My Code")，並忽略系統程式碼和其他已最佳化或沒有偵錯符號的程式碼。

- **如果啟動 (僅限 Managed) 沒有使用者程式碼，即發出警告**  
    在啟用 Just My Code 的狀態下開始偵錯時，如果沒有使用者程式碼 ("My Code")，這個選項會警告您。 

**啟用.NET Framework 來源逐步執行**  
允許偵錯工具逐步執行 .NET Framework 原始檔。 啟用此選項會自動停用 Just My Code.NET Framework 符號會下載到快取位置。 您可以變更快取中的位置**選項**對話方塊中，**偵錯**類別，**符號**頁面。  
  
**不進入屬性和運算子 (僅限 Managed)**  
讓偵錯工具無法逐步執行 Managed 程式碼中的屬性和運算子。  
  
**啟用屬性評估及其他隱含函式呼叫**  
在變數視窗中呼叫的自動評估屬性和隱含函式可開啟和**快速監看式** 對話方塊。  
  
- **在變數視窗 （C# 和 JavaScript 只有） 中的物件上呼叫字串轉換函式**  
    在評估變數視窗中的物件時，執行隱含的字串轉換呼叫。 因此，該結果會顯示為字串，而非類型名稱。 只適用於偵錯 C# 程式碼時。 DebuggerDisplay 屬性可能會覆寫這項設定 (請參閱[使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md))。  
  
**啟用來源伺服器支援**  
告知 Visual Studio Debugger 從實作 SrcSrv (`srcsrv.dll`) 通訊協定的來源伺服器取得來源檔。 Team Foundation Server 和 Windows 偵錯工具這兩個來源伺服器會實作通訊協定。 如需 SrcSrv 設定的詳細資訊，請參閱[SrcSrv](hhttps://msdn.microsoft.com/en-us/library/windows/hardware/ff558791(v=vs.85).aspx)文件。 此外，請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  
> [!IMPORTANT]
>  因為讀取 .pdb 檔案可以執行檔案中的任意程式碼，請確定您信任伺服器。  
  
- **來源伺服器診斷訊息列印到輸出視窗**  
    啟用來源伺服器支援時，這個設定會開啟診斷顯示畫面。  
  
- **允許部分信任組件 (僅限 Managed) 的來源伺服器**  
    當來源伺服器支援啟用時，這個設定會覆寫不擷取部分信任組件之來源的預設行為。  

- **啟用來源連結支援**  
    告知 Visual Studio debugger 下載來源檔案包含來源連結資訊的.pdb 檔。 如需來源連結的詳細資訊，請參閱[來源連結規格](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md)。

    > [!IMPORTANT]
    >  因為來源連結會下載檔案，使用 http 或 https，請確定您信任的.pdb 檔案。  
  
**反白顯示整行中斷點和目前的陳述式 （只有 c + +）**  
當偵錯工具反白顯示中斷點或目前的陳述式時，它會反白顯示整行。  
  
**程式檔必須完全符合原始版本**  
告知偵錯工具驗證原始程式檔是否符合用來建置正在偵錯之可執行檔的原始程式碼版本。 如果版本不符，系統會提示您找不到相符的來源。 如果找不到相符的原始程式檔，偵錯期間將不會顯示原始程式碼。 
  
**將所有輸出 視窗文字重新都導向至即時運算視窗**  
傳送所有偵錯工具通常會出現在訊息**輸出**視窗**即時運算**視窗改為。  
  
**變數視窗中顯示物件的原始結構**  
關閉所有物件結構檢視自訂。 如需檢視自訂的詳細資訊，請參閱[建立.managed 物件的自訂檢視](../debugger/create-custom-views-of-dot-managed-objects.md)。  
  
**隱藏 JIT 最佳化，在模組載入 (僅限 Managed)**  
在附加偵錯工具時若已載入模組且已編譯 JIT，便停用 Managed 程式碼的 JIT 最佳化。 停用最佳化可更容易偵錯一些問題，但消耗較多效能。 如果正在使用 Just My Code，隱藏 JIT 最佳化會使非使用者程式碼顯示為使用者程式碼 ("My Code")。

**啟用 ASP.NET （Chrome 和 IE） 的偵錯 JavaScript**可讓 ASP.NET 應用程式的指令碼偵錯工具。 在 Chrome 中的第一次使用，您可能需要登入第一次使用啟用已安裝的 Chrome 擴充功能上的瀏覽器。 停用此選項以還原到舊版的行為。    

**載入 dll 匯出**  
載入 dll 匯出資料表。 若您使用 Windows 訊息、Windows 程序 (WindowProc)、COM 物件、封送處理或是任何您沒有其符號的 dll，則 dll 匯出資料表的符號資訊會很有幫助。 讀取 dll 匯出資訊會產生一些額外負荷。 因此，這項功能預設為關閉。  
  
若要查看哪些符號的 dll 匯出表中可用，請使用`dumpbin /exports`。 這些符號適用於任何 32 位元系統 dll。 讀取 `dumpbin /exports` 輸出時，您可以看到確實的函式名稱，包含非英數字元。 這對設定函式的中斷點來說很有幫助。 dll 匯出表中的函式名稱在偵錯工具中的其他位置可能會顯示為已被截斷。 這些呼叫都按呼叫順序列出，目前的函式 (巢狀最深處) 列在頂端。 如需詳細資訊，請參閱 [dumpbin /exports](/cpp/build/reference/dash-exports)。  
  
**顯示平行堆疊圖表的由下往上**  
控制堆疊中的顯示方向**平行堆疊**視窗。  
  
**如果寫入的資料未變更值，請忽略 GPU 記憶體存取例外狀況**  
會忽略 如果資料未變更，偵錯期間偵測到的競爭條件。 如需詳細資訊，請參閱[偵錯 GPU 程式碼](../debugger/debugging-gpu-code.md)。  
  
**使用 Managed 相容性模式**  
將預設偵錯引擎取代為舊版偵錯引擎，以啟用這些案例：  
  
- 您要使用 C#、VB 或 F# 以外的 .NET Framework 語言 (包括 C++/CLI)，以提供其自己的運算式評估工具。  
  
- 您要在混合模式偵錯時啟用 C++ 專案的 [編輯後繼續]。  
  
請注意，選擇 Managed 相容性模式會停用只在預設偵錯引擎中實作的一些功能。 

**使用傳統的 C# 和 VB 運算式評估工具**  
偵錯工具會使用 Visual Studio 2013 C# /VB 運算式評估工具，而不是 Visual Studio 2015 Roslyn 運算式評估工具。    
  
**使用自訂偵錯工具視覺化檢視，針對可能不安全的程序 (僅限 Managed) 時，即發出警告**  
當您使用的自訂偵錯工具視覺化檢視在偵錯項目處理序中執行程式碼時，Visual Studio 會發出警告，原因是它可能會執行到不安全的程式碼。  
  
**啟用 Windows 偵錯堆積配置器 （僅限原生）**  
啟用 Windows 偵錯堆積，以改善堆積診斷。 啟用此選項會影響偵錯效能。  
  
**啟用 XAML 的偵錯工具 UI**  
當您開始偵錯 (F5) 支援的專案類型時，即時視覺化樹狀和即時屬性瀏覽視窗會隨即出現。 如需詳細資訊，請參閱[偵錯時檢查 XAML 屬性](../debugger/inspect-xaml-properties-while-debugging.md)。  
  
- **預覽選取的元素，在 即時視覺化樹狀結構中**  
    選取其內容的 XAML 項目也會選取在**即時視覺化樹狀結構**視窗。  
  
- **在應用程式中顯示執行階段工具**  
    顯示**即時視覺化樹狀結構**上進行偵錯 XAML 應用程式的主視窗的工具列中的命令。 此選項已引入 Visual Studio 2015 Update 2。 

- **啟用 XAML 編輯後繼續**可讓您使用編輯後繼續的 XAML 程式碼的功能。 
  
**偵錯時啟用診斷工具**  
**診斷工具**您偵錯時，視窗隨即出現。
  
**偵錯時顯示經歷時間 PerfTip**  
在您偵錯時，[程式碼] 視窗中會顯示指定之方法呼叫的已耗用時間。  
  
**啟用編輯後繼續**  
在偵錯時，您可以使用 [編輯後繼續] 功能。  
  
- **啟用原生編輯後繼續**  
    在偵錯原生 C++ 程式碼時，您可以使用 [編輯後繼續] 功能。 如需詳細資訊，請參閱[編輯後繼續 （Visual c + +）](../debugger/edit-and-continue-visual-cpp.md)。  
  
- **將變更套用在繼續 （僅限原生）**  
    當從中斷狀態繼續處理序時，Visual Studio 會自動編譯和套用任何未完成的程式碼變更。 如果未選取，您可以選擇使用 [偵錯] 功能表底下的 [套用程式碼變更] 項目套用變更。  
  
- **警告出現過時的程式碼 （僅限原生）**  
    取得過時程式碼的警告。    

**顯示執行偵錯時按一下編輯器中的按鈕**選取此選項時，[執行按一下](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse)按鈕將會顯示偵錯時。

## <a name="options-supported-in-older-versions-of-visual-studio"></a>在舊版的 Visual Studio 中支援的選項

如果您使用較舊版本的 Visual Studio，可能會存在一些其他選項。

**啟用例外狀況助理**  
Managed 程式碼中啟用例外狀況助理。 在 Visual Studio 2017，例外狀況協助程式取代為例外狀況助理。

**回溯呼叫堆疊上未處理例外狀況**  
會導致**呼叫堆疊**視窗呼叫堆疊復原點之前，發生未處理的例外狀況。 

**如果沒有啟動 （僅限原生） 符號，即發出警告**  
在您嘗試偵錯一個偵錯工具中沒有符號資訊的程式時，顯示警告對話方塊。 

**如果指令碼偵錯已停用啟動，即發出警告**  
在啟動偵錯工具卻停用指令碼偵錯時，顯示警告對話方塊。

**使用原生相容性模式**  
選取此選項時，偵錯工具會使用 Visual Studio 2010 原生偵錯工具，而不是新的原生偵錯工具。  
  
您應在偵錯 .NET C++ 程式碼時使用此選項，原因是新的偵錯引擎不支援評估 .NET C++ 運算式。 然而，啟用 [原生相容性模式] 會停用許多相依於目前偵錯工具實作以進行運作的功能。 例如，舊版引擎缺乏許多視覺化檢視針對內建型別類似`std::string`Visual Studio 2015 的專案中。   請在這些案例中使用 Visual Studio 2013 專案，以獲得最佳的偵錯體驗。
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 偵錯](../debugger/index.md)  
 [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)
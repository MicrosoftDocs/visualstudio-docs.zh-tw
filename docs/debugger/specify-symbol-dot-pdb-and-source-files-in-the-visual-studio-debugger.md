---
title: 在偵錯工具中設定符號 ( .pdb) 和原始程式檔
description: 瞭解如何在 Visual Studio 中設定和管理符號和原始檔
ms.custom: ''
ms.date: 10/31/2019
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78440c6da86d49364f7fd9006779166e8c2fb7d3
ms.sourcegitcommit: 686aa3516594ab951d48b192fc60b102eedaf9b7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2021
ms.locfileid: "99628002"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>在 Visual Studio 偵錯工具中指定符號 ( .pdb) 和原始程式檔 (c #、c + +、Visual Basic、F # ) 

程式資料庫 (*.pdb*) 檔案（也稱為符號檔）、將專案原始程式碼中的識別碼和語句對應至已編譯之應用程式中的對應識別碼和指示。 這些對應檔會將偵錯工具連結至您的原始程式碼，以啟用偵錯工具。

當您使用標準 Debug 組建設定從 Visual Studio IDE 建立專案時，編譯器會建立適當的符號檔。 本文說明如何在 IDE 中管理符號檔，例如如何 [在偵錯工具選項中指定符號的位置](#BKMK_Specify_symbol_locations_and_loading_behavior)、如何在偵錯工具時 [檢查符號載入狀態](#work-with-symbols-in-the-modules-window) ，以及如何 [在程式碼中設定符號選項](#compiler-symbol-options)。

如需符號檔的詳細說明，請參閱下列檔：

- [瞭解符號檔和 Visual Studio 符號設定](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [為什麼 Visual Studio 要求偵錯工具符號檔與建立它們的二進位檔案完全相符？](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>符號檔的運作方式

*.Pdb* 檔案包含偵錯工具和專案狀態資訊，可讓您應用程式的偵錯工具的累加式連結。 Visual Studio 偵錯工具在進行偵錯工具時，會使用 *.pdb* 檔案來判斷兩個重要的資訊片段：

* 要在 Visual Studio IDE 中顯示的原始程式檔名稱和行號。
* 應用程式停止中斷點的位置。

符號檔也會顯示來源檔案的位置，並選擇性地顯示從中抓取來源檔案的位置。

偵錯工具只會載入與建立應用程式時所建立之 *.pdb* 檔案完全相符的 *.pdb* 檔 (也就是原始 *.pdb* 檔案或複製) 。 這 [完全](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) 是必要的，因為即使程式碼本身未變更，應用程式的配置也可能會變更。

> [!TIP]
> 若要在專案原始程式碼之外（例如，您的專案呼叫的 Windows 程式碼或協力廠商程式碼）進行程式碼的偵錯工具，您必須指定外部程式碼 *.pdb* 檔案的位置 (並選擇性地指定原始程式檔) ，其必須完全符合您應用程式中的組建。

## <a name="symbol-file-locations-and-loading-behavior"></a>符號檔位置和載入行為

當您在 Visual Studio IDE 中對專案進行偵錯工具時，偵錯工具會自動載入位於專案資料夾中的符號檔。

> [!NOTE]
> 在遠端裝置上對 managed 程式碼進行偵錯工具時，所有的符號檔都必須位於本機電腦上，或位於 [偵錯工具選項中指定](#BKMK_Specify_symbol_locations_and_loading_behavior)的位置。

偵錯工具也會在下列位置中搜尋符號檔：

1. 在 DLL 或可執行檔 (*.exe* 中指定的位置) 檔。

   根據預設，如果您的電腦上已建立 DLL 或 *.exe* 檔，連結器會將相關聯之 *.pdb* 檔案的完整路徑和檔案名放入 dll 或 *.exe* 檔案中。 偵錯工具會檢查符號檔是否存在於該位置中。

2. 與 DLL 或 *.exe* 檔案相同的資料夾。

3. 符號檔的偵錯工具選項中指定的任何位置。 若要加入和啟用符號位置，請參閱 [設定符號位置和載入選項](#BKMK_Specify_symbol_locations_and_loading_behavior)。

   - 任何本機符號快取資料夾。

   - 指定的網路、網際網路或本機符號伺服器和位置，例如 Microsoft 符號伺服器（若已選取）。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可以從執行通訊協定的符號伺服器下載偵錯工具符號檔 `symsrv` 。 [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) 和 [適用于 Windows 的調試](/windows-hardware/drivers/debugger/index) 程式都是可使用符號伺服器的兩個工具。

     您可能使用的符號伺服器包括：

     **公用 Microsoft 符號伺服器**：若要在呼叫系統 DLL 或協力廠商程式庫時，偵測發生的損毀，您通常需要系統 *.pdb* 檔。 系統 *.pdb* 檔案包含 Windows dll、 *.exe* 檔和設備磁碟機的符號。 您可以從公用 Microsoft 符號伺服器取得 Windows 作業系統、MDAC、IIS、ISA 和 .NET 的符號。

     **內部網路或本機電腦上的符號伺服器**：您的小組或公司可以為自己的產品建立符號伺服器，並為外部來源的符號快取。 您的電腦上可能有符號伺服器。

     **協力廠商符號伺服器**： Windows 應用程式和程式庫的協力廠商提供者可以存取網際網路上的符號伺服器。

     > [!WARNING]
     > 如果您使用的符號伺服器不是公用 Microsoft 符號伺服器，請確認符號伺服器及其路徑是否值得信任。 由於符號檔可以包含任意可執行檔程式碼，因此您可能會面臨安全性威脅。

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>設定符號位置和載入選項

在 [**工具**  >  **選項**  >  **調試**  >  **符號**] 頁面上，您可以：

- 指定並選取 Microsoft、Windows 或協力廠商元件的搜尋路徑和符號伺服器。
- 指定您要或不希望偵錯工具自動載入符號的模組。
- 當您主動進行調試時，請變更這些設定。 請參閱 [在調試過程中管理符號](#manage-symbols-while-debugging)。

**若要指定符號位置和載入選項：**

1. 在 Visual Studio 中，開啟 [**工具**  >  **選項**]  >  (**調試**  >  **符號** 或) 的 **調試**  >  **選項**  >  **符號**。

2. 在 **符號檔 ( .pdb) 位置**，
   - 若要使用 **Microsoft 符號伺服器** 或 **NuGet.org 符號伺服器**，請選取核取方塊。

   - 若要加入新的符號伺服器位置，
     1. 選取 **+** 工具列中的符號。
     1. 在 [文字] 欄位中輸入 (HTTP) 、網路共用或符號伺服器的本機路徑或符號位置的 URL。 陳述式完成可幫助您找出正確的格式。

     ![工具 &#45; 選項 &#45; &#45; 符號頁面的調試](media/dbg-options-symbols.gif "工具 &#45; 選項 &#45; &#45; 符號頁面的調試")

     >[!NOTE]
     >只搜尋指定的資料夾。 您必須為想要搜尋的任何子資料夾新增專案。

   - 若要加入新的 VSTS 符號伺服器位置，
     1. 在工具列中選取 [ ![工具]&#47; 選項&#47;&#47;符號新增伺服器圖示](media/dbg_tools_options_foldersicon.png "工具 &#45; 選項 &#45; 調試 &#45; 符號新伺服器圖示") ] 圖示。
     1. 在 [ **連接到 VSTS 符號伺服器** ] 對話方塊中，選擇其中一個可用的符號伺服器，然後選取 [ **連接]**。

   - 若要變更符號位置的載入順序，請使用 **ctrl** + **向上** 和向 + **下** ctrl，或 **向上** 鍵和 **向下** 箭號圖示。
   - 若要編輯 URL 或路徑，請按兩下該專案，或是選取它，然後按 **F2**。
   - 若要移除專案，請選取專案，然後選取 **-** 圖示。

3.  (選擇性) 若要改善符號載入效能，請在 [ **在此目錄中** 的快取符號] 下，輸入符號伺服器可以複製符號的本機資料夾路徑。

   > [!NOTE]
   > 請勿將本機符號快取放在受保護的資料夾中，例如 C：\Windows 或子資料夾。 請改用可讀寫的資料夾。

   > [!NOTE]
   > 針對 c + + 專案，如果您已 `_NT_SYMBOL_PATH` 設定環境變數，它會覆寫 **此目錄中** 的 [快取符號] 下設定的值。

4. 指定要讓偵錯工具從符號檔載入的模組， **( .pdb** 在啟動時) 位置。

   - 除非已排除 (預設) ，否則請選取 [ **載入所有模組** ]，以載入符號檔位置中所有模組的所有符號，除了您明確排除的模組以外。 若要排除某些模組，請選取 [ **指定排除的模組**]、選取 **+** 圖示、輸入要排除的模組名稱，然後選取 **[確定]**。

   - 若只要載入您從符號檔位置指定的模組，請選取 [ **僅載入指定的模組**]。 選取 [ **指定包含的模組**]、選取 **+** 圖示、輸入要包含的模組名稱，然後選取 **[確定]**。 未載入其他模組的符號檔。

5. 選取 [確定]。

## <a name="other-symbol-options-for-debugging"></a>用於偵錯工具的其他符號選項

您可以在 [**工具**  >  **選項**] 的  >    >  **[一般**] (或  >    >  **[一般**) 的 Debug 選項中選取其他符號選項：

- **載入 dll 匯出 (僅限原生)**

  載入適用于 C/c + + 的 DLL 匯出資料表。 如需詳細資訊，請參閱 [DLL 匯出資料表](#use-dumpbin-exports)。 讀取 DLL 匯出資訊需要一些額外負荷，因此預設會關閉載入匯出資料表。 您也可以 `dumpbin /exports` 在 C/c + + 組建命令列中使用。

- **啟用位址層級的調試**，並 **在來源無法使用時顯示** 反組解碼

  在找不到來源或符號檔時，一律顯示反組解碼。

  ![&#47; 一般反組解碼選項 &#47; 調試的選項](../debugger/media/dbg_options_general_disassembly_checkbox.png "&#47; 一般反組解碼選項 &#47; 調試的選項")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **啟用來源伺服器支援**

  當本機電腦上沒有任何原始程式碼，或 *.pdb* 檔案不符合原始程式碼時，會使用來源伺服器來協助您進行應用程式的偵錯工具。 來源伺服器會取得檔案的要求，並從原始檔控制傳回實際的檔案。 來源伺服器使用名為 *srcsrv.dll* 的 DLL 來執行，以讀取應用程式的 *.pdb* 檔。 *.Pdb* 檔案包含原始程式碼存放庫的指標，以及用來從存放庫取出原始程式碼的命令。

  您可以在名為 *srcsrv.ini* 的檔案中列出允許的命令，以限制 *srcsrv.dll* 可從應用程式的 *.pdb* 檔執行的命令。 將 *srcsrv.ini* 檔案放在與 *srcsrv.dll* 和 *devenv.exe* 相同的資料夾中。

  >[!IMPORTANT]
  >任意命令都可以內嵌在應用程式的 *.pdb* 檔中，因此請務必只將您想要執行的命令放入 *srcsrv.ini* 檔案中。 嘗試執行 *srcsvr.ini* 檔案中未包含的任何命令，會讓確認對話方塊出現。 如需詳細資訊，請參閱 [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md)。
  >
  >由於不會對命令參數進行任何驗證，因此請謹慎使用受信任的命令。 例如，如果您在 *srcsrv.ini* 中列出 *cmd.exe* ，惡意使用者可能會在 *cmd.exe* 上指定參數，使其成為危險。

  選取此專案和您想要的子專案。 **允許部分信任元件的來源伺服器僅 (受控)** ，而且 **一律執行不受信任的來源伺服器命令而不提示** ，可能會增加安全性風險。

  ![啟用來源伺服器選項](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>編譯器符號選項

當您使用標準 **Debug** 組建設定從 Visual Studio IDE 建立專案時，c + + 和 managed 編譯器會為您的程式碼建立適當的符號檔。 您也可以在程式碼中設定編譯器選項。

### <a name="net-options"></a>.NET 選項

使用 **/debug** 建立，以建立 *.pdb* 檔。 您可以使用 **/debug:full** 或 **/debug:pdbonly** 建置應用程式。 使用 **/debug:full** 建置會產生可偵錯的程式碼。 使用 **/debug:pdbonly** 進行建置則會產生 *.pdb* 檔案，但是不會產生用於通知 JIT 編譯器有可用偵錯資訊的 `DebuggableAttribute`。 如果您要為發行組建 (Release Build) 產生 *.pdb* 檔案，但不希望為可偵錯，則請使用 **/debug:pdbonly**。 如需詳細資訊，請參閱 [/debug (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) 或 [/debug (Visual Basic) ](/dotnet/visual-basic/reference/command-line-compiler/debug)。

### <a name="cc-options"></a>C/C++ 選項

- *VC \<x> .pdb* 和 *\<project> .pdb* 檔案

  當您使用 [/zi 或/zi](/cpp/build/reference/z7-zi-zi-debug-information-format)建立時，會建立 C/c + + 的 *.pdb* 檔。 在中 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] ， [/fd](/cpp/build/reference/fd-program-database-file-name)選項會為編譯器所建立的 .pdb 檔命名 *。* 當您使用 IDE 在中建立專案時 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，會將 **/fd** 選項設定為建立副檔名為 *\<project> .pdb* 的 *.pdb* 檔。

  如果您使用 makefile 來建立 C/c + + 應用程式，並在不使用 **/fd** 的情況下指定 **/zi** 或 **/zi** ，則編譯器會建立兩個 *.pdb* 檔案：

  - *VC \<x>*，其中 *\<x>* 代表 Microsoft c + + 編譯器的版本，例如 *vc11.pdb .pdb*

    *VC \<x> .pdb* 檔會儲存個別物件檔案的所有偵錯工具資訊，並且位於與專案 makefile 相同的目錄中。 每次建立物件檔案時，C/c + + 編譯器都會將 debug 資訊合併為 *VC \<x> .pdb*。 因此，即使每個原始檔都包含一般標頭檔（例如 *\<windows.h>* ），這些標頭中的 typedef 都只會儲存一次，而不會儲存在每個物件檔案中。 插入的資訊包括類型資訊，但是不包括符號資訊 (例如函式定義)。

  - *\<project>.pdb*

    *\<project> .Pdb* 檔案會儲存專案的 *.exe* 檔案的所有偵錯工具資訊，並且位於 *\debug* 子目錄中。 *\<project> .Pdb* 檔案包含完整的 debug 資訊，包括函式原型，而不只是在 VC 中 *找到 \<x>* 的類型資訊。

  *VC \<x> .pdb* 和 *\<project> .pdb* 檔案都允許累加式更新。 連結器也會將 *.pdb* 檔案的路徑嵌入其所建立的 *.exe* 或 *.dll* 檔案中。

- <a name="use-dumpbin-exports"></a>DLL 匯出資料表

  使用 `dumpbin /exports` 可查看 DLL 匯出資料表中的可用符號。 DLL 匯出資料表的符號資訊適用于處理 Windows 訊息、Windows 程式 (Windowproc) 、COM 物件、封送處理，或您沒有符號的任何 DLL。 這些符號適用於任何 32 位元系統 DLL。 這些呼叫都按呼叫順序列出，目前的函式 (巢狀最深處) 列在頂端。

  藉由讀取 `dumpbin /exports` 輸出，您可以看到確切的函式名稱，包括非英數位元。 看到確切的函式名稱對於在函式上設定中斷點很有用，因為函式名稱可以在偵錯工具中的其他地方截斷。 如需詳細資訊，請參閱 [dumpbin /exports](/cpp/build/reference/dash-exports)。

### <a name="web-applications"></a>Web 應用程式

將 ASP.NET 應用程式的 *web.config* 檔案設定為 debug 模式。 偵錯模式會導致 ASP.NET 產生動態產生之檔案的符號，並使偵錯工具附加到 ASP.NET 應用程式。 如果您已從 Web 專案範本建立專案，Visual Studio 會在您開始 debug 時自動設定此專案。

## <a name="manage-symbols-while-debugging"></a>在調試過程中管理符號

您可以使用 [**模組**]、[**呼叫堆疊**]、[區域變數]、[自動 **變數**] 或任何 **[監看** 式]**視窗，在** 偵測時載入符號或變更符號選項 如需詳細資訊，請參閱 [深入瞭解偵錯工具附加至您應用程式的方式](../debugger/debugger-tips-and-tricks.md#modules_window)。

### <a name="work-with-symbols-in-the-modules-window"></a>在 [模組] 視窗中使用符號

在偵錯工具期間，[ **模組** ] 視窗會顯示偵錯工具視為使用者程式碼或 My Code 的程式碼模組，以及其符號載入狀態。 您也可以在 [ **模組** ] 視窗中監視符號載入狀態、載入符號，以及變更符號選項。

**若要在進行調試時監視或變更符號位置或選項：**

1. 若要開啟 [**模組**] 視窗，請在調試過程中選取 [ **Debug**  >  **Windows**  >  **模組**] (或按下 **Ctrl**  +  **Alt**  +  **U**) 。
1. 在 [ **模組** ] 視窗中，以滑鼠右鍵按一下 **符號狀態** 或 **符號** 檔標頭，或任何模組。
1. 在快顯功能表中，選取下列其中一個選項︰

|選項|Description|
|------------|-----------------|
|**載入符號**|顯示已略過、找不到或未載入符號的模組。 嘗試從 [**選項**  >  **調試**  >  **符號**] 頁面上指定的位置載入符號。 如果找不到或未載入符號檔，則會啟動 **檔案總管** ，讓您可以指定要搜尋的新位置。|
|**符號載入資訊**|顯示載入的符號檔的位置，或如果偵錯工具找不到檔案時所搜尋的位置。|
|**符號設定**|開啟 [**選項**  >  **調試**  >  **符號**] 頁面，您可以在其中編輯和新增符號位置。|
|**永遠自動載入**|將選取的符號檔加入至偵錯工具自動載入的檔案清單。|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>使用未載入的符號/沒有來源載入的頁面

有幾種方式可讓偵錯工具中斷程式碼，而不含符號或原始程式檔：

- 逐步執行程式碼。
- 從中斷點或例外狀況中斷程式碼。
- 切換至不同的執行緒。
- 按兩下 [ **呼叫堆疊** ] 視窗中的框架，以變更堆疊框架。

發生這種情況時，偵錯工具會顯示 [ **未載入符號** ] 或 [ **未載入來源** ] 頁面，協助您尋找和載入必要的符號或來源。

 ![未載入符號頁面](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**若要使用 [未載入符號] 檔頁面，以協助尋找及載入遺漏的符號：**

- 若要變更搜尋路徑，請選取未選取的路徑，或選取 [ **新增路徑** ] 或 [ **新增 VSTS 路徑** ]，然後輸入或選取新的路徑。 選取 [ **載入** ] 以再次搜尋路徑，並載入符號檔（如果找到的話）。
- 若要覆寫任何符號選項並重試搜尋路徑，請選取 **[ \<executable-name> 流覽並尋找]**。 如果找到符號檔，則會載入符號檔，或 **檔案總管** 開啟，讓您可以手動選取符號檔。
- 若要開啟 [**選項**  >  **調試**  >  **符號**] 頁面，請選取 [**變更符號設定**]。
- 若要在新視窗中一次顯示反組解碼，請選取 [ **視圖** 反組解碼]，或選取 [ **選項] 對話方塊** ，將選項設定為 [當找不到來源或符號檔時一律顯示反組解碼]。
- 若要顯示搜尋的位置和結果，請展開 [ **符號載入資訊**]。

如果偵錯工具在您執行其中一個選項之後找到 *.pdb* 檔案，而且可以使用 *.pdb* 檔案中的資訊來抓取原始程式檔，則會顯示來源。 否則，它會顯示 [ **未載入來源** ] 頁面來描述問題，並連結至可能會解決問題的動作。

**若要將原始檔搜尋路徑加入至方案：**

您可以指定偵錯工具搜尋原始程式檔的位置，以及從搜尋中排除特定檔案。

1. 在 [**方案總管** 中選取方案，然後選取 [**屬性**] 圖示，按下 **Alt** + **enter**，或按一下滑鼠右鍵並選取 [**屬性**]。

1. 選取 [ **Debug Source Files**]。

1. 在 [ **包含原始程式碼的目錄**] 下，輸入或選取要搜尋的原始程式碼位置。 使用 **新行** 圖示來新增更多位置、 **向上** 箭號和 **向下** 箭號圖示來重新排序它們，或使用 **X** 圖示來刪除它們。

   >[!NOTE]
   >偵錯工具只會搜尋指定的目錄。 您必須自行加入要搜尋的所有子目錄項目。

1. 在 [不 **尋找這些原始程式** 檔] 底下，輸入要從搜尋中排除的原始程式檔名稱。

1. 選取 **[確定]** **或**[套用]。

## <a name="see-also"></a>另請參閱
- [瞭解符號檔和 Visual Studio 符號設定](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Visual Studio 2012 和2013中的 .NET 遠端符號載入變更](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
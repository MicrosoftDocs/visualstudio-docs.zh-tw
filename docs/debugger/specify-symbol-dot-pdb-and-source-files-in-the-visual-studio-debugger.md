---
title: 設定偵錯工具中的符號 (.pdb) 和原始程式檔
ms.custom: seodec18
ms.date: 10/08/2018
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d970d2b761b2987bc74e94eb5bfefa8f0ffc78ec
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "53892442"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>在 Visual Studio debugger 中指定符號 (.pdb) 和原始程式檔 (C#，c + +、 Visual Basic 中， F#)

程式資料庫 (*.pdb*) 檔案，也稱為符號檔將識別項對應，並在對應的識別項專案的原始程式碼中的陳述式中及指示編譯應用程式。 

當您從偵錯組建組態的標準 Visual Studio IDE 建置專案時，則編譯器會建立適當的符號檔。 您也可以[程式碼中設定符號選項](#compiler-symbol-options)。 

*.Pdb*檔會保留偵錯和專案狀態資訊，可讓您的應用程式的偵錯組態的累加連結。 Visual Studio 偵錯工具會使用 *.pdb*檔案，以判斷兩個關鍵偵錯時的資訊：

* 原始程式檔名和行號以顯示 Visual Studio IDE 中。
* 在中斷點停止應用程式中的位置。

符號檔也會顯示原始程式檔中，並選擇性地擷取它們從伺服器的位置。
  
偵錯工具只會載入 *.pdb*完全符合的檔案 *.pdb*建置應用程式時建立的檔案 (也就是原始 *.pdb*檔案或複本)。 完全重複項目是必要的因為應用程式的配置可以變更，即使未變更程式碼本身。 如需詳細資訊，請參閱 [Why does Visual Studio require debugger symbol files to exactly match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/) (Visual Studio 為何要求偵錯工具符號檔案必須完全符合當初建置這些符號檔案時所使用的二進位檔案？)

> [!TIP]
> 偵錯專案程式碼中，外部程式碼，例如 Windows 程式碼或協力廠商程式碼專案呼叫，您必須指定外部程式碼的位置 *.pdb*檔案 （以及 （選擇性） 原始程式檔），這必須完全符合在您的應用程式的組建。 

## <a name="symbol-file-locations-and-loading-behavior"></a>符號檔位置和載入行為

> [!NOTE]
> 當偵錯 managed 程式碼，在遠端裝置上的，所有的符號檔必須位於本機電腦，或是在位置[偵錯工具選項中指定](#BKMK_Specify_symbol_locations_and_loading_behavior)。  
  
當您偵錯 Visual Studio IDE 中的專案時，偵錯工具會自動載入位於專案資料夾中的符號檔。 

偵錯工具也會搜尋下列位置中的符號檔：

1. 指定 DLL 或可執行檔內部的位置 (*.exe*) 檔案。  
   
   根據預設，如果您已建置的 DLL 或 *.exe*的完整路徑和檔案名稱相關聯的您在電腦上，連結器的檔案會放 *.pdb*在 DLL 中的檔案或 *.exe*檔案。 偵錯工具會檢查是否在該位置已有符號檔。  
   
2. 與 DLL 相同的資料夾或 *.exe*檔案。
   
3. 指定符號檔的偵錯工具選項中的任何位置。 若要新增並啟用符號位置，請參閱[設定符號位置和載入選項](#BKMK_Specify_symbol_locations_and_loading_behavior)。 
   
   - 任何本機符號快取資料夾。  
  
   - 如果選取，請指定網路、 網際網路或本機符號伺服器和位置，例如 Microsoft 符號伺服器。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可以從實作符號伺服器下載偵錯符號檔`symsrv`通訊協定。 [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols)而[的 Windows 偵錯工具](/windows-hardware/drivers/debugger/index)是兩項工具，可以使用符號伺服器。
      
     您可以使用的符號伺服器包括：  
      
     **公用 Microsoft 符號伺服器**:若要偵錯發生在系統 DLL 或協力廠商程式庫呼叫期間當機，因此您通常需要系統 *.pdb*檔案。 系統 *.pdb*檔案包含 Windows Dll 符號 *.exe*檔案和裝置驅動程式。 您可以取得 Windows 作業系統、 MDAC、 IIS、 ISA、 符號和[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]從公用 Microsoft 符號伺服器。 
      
     **內部網路或本機電腦上的符號伺服器**：您的小組或公司可以為自己的產品建立符號伺服器，以及作為外部來源符號的快取。 您的電腦上可能有符號伺服器。 
      
     **協力廠商符號伺服器**：Windows 應用程式和程式庫的協力廠商提供者可提供對網際網路上符號伺服器的存取。 
    
     > [!WARNING]
     > 如果您使用公用 Microsoft 符號伺服器以外的符號伺服器，請確定符號伺服器和它的路徑是值得信任。 由於符號檔可能包含任意可執行程式碼，您可以公開安全性威脅。  

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>設定符號位置和載入選項

在 **工具** > **選項** > **偵錯** > **符號**頁面上，您可以：

- 指定並選取 為 Microsoft、 Windows 或第三方元件的 搜尋路徑和符號伺服器。
- 指定您執行或不想偵錯工具自動載入符號的模組。
- 您正在偵錯時，請變更這些設定。 請參閱[偵錯時管理符號](#manage-symbols-while-debugging)。 
  
**若要指定符號位置和載入選項：**

1. 在 Visual Studio 中開啟**工具** > **選項** > **偵錯** > **符號**（或**偵錯** > **選項** > **符號**)。  
   
   ![工具&#45;選項&#45;偵錯&#45;[符號] 頁面](media/dbg-options-symbols.png "工具&#45;選項&#45;偵錯&#45;[符號] 頁面")  
   
2. 底下**符號檔 (.pdb) 位置**，
   - 若要使用**Microsoft 符號伺服器**，選取核取方塊。  
   
   - 若要新增新的符號伺服器位置
     1. 選取  **+** 工具列中的符號。 
     1. 在文字欄位中輸入符號伺服器或符號位置的 URL 或資料夾的路徑。 陳述式完成可幫助您找出正確的格式。
     
     >[!NOTE]
     >搜尋指定的資料夾。 您必須新增您想要搜尋的任何子資料夾的項目。  
   
   - 若要新增 VSTS 符號伺服器位置， 
     1. 選取 ![工具&#47;選項&#47;偵錯&#47;符號新伺服器 圖示](media/dbg_tools_options_foldersicon.png "工具&#45;選項&#45;偵錯&#45;符號新的伺服器圖示")工具列中的圖示。 
     1. 在 [**連線至 VSTS 符號伺服器**] 對話方塊中，選擇其中一個可用的符號伺服器，然後選取**Connect**。  
   
   - 若要變更符號位置的載入順序，請使用**Ctrl**+**向上**並**Ctrl**+**向下**，或**向上**並**向下**箭號圖示。 
   - 若要編輯 URL 或路徑，請按兩下項目，或選取它然後按**F2**。  
   - 若要移除的項目，選取它，然後按**-** 圖示。
  
3. （選擇性）若要改善符號載入效能，底下**快取此目錄中的符號**，型別至符號的符號伺服器可以將複製的本機資料夾路徑。  
  
   > [!NOTE]
   > 請勿將本機符號快取放在受保護的資料夾中，例如 C:\Windows 或子資料夾。 請改用可讀寫的資料夾。  
  
   > [!NOTE]
   > C + + 專案，如果您有`_NT_SYMBOL_PATH`環境變數的集合，則會覆寫下設定的值**快取此目錄中的符號**。
  
4. 指定您想要偵錯工具從載入的模組**符號檔 (.pdb) 位置**當它啟動。  
  
   -  選取 **載入所有模組，除非已排除**（預設） 載入所有符號，符號檔案位置，除非您特別排除的模組中的所有模組。 若要排除特定的模組，請選取**指定排除的模組**，選取**+** 圖示，輸入要排除，然後選取的模組名稱**確定**。  
  
   -  若要載入符號檔位置從指定的模組，請選取**負載只指定了模組**。 選取 **指定包含的模組**，選取**+** 圖示，輸入要包含此項目，然後選取 模組名稱**確定**。 不會載入其他模組的符號檔。  
  
5. 選取 [確定]。

## <a name="other-symbol-options-for-debugging"></a>偵錯的其他符號選項
  
您可以選取中的其他符號選項**工具** > **選項** > **偵錯** > **一般**(或**偵錯** > **選項** > **一般**):  

- **載入 DLL 匯出 (僅限原生)**  
  
  載入 DLL 匯出表 C/c + +。 如需詳細資訊，請參閱 < [DLL 匯出表](#use-dumpbin-exports)。 讀取 DLL 匯出資訊會涉及一些額外負荷，因此載入匯出資料表預設關閉。 您也可以使用`dumpbin /exports`C/c + + 建置命令列中。  
  
- **啟用位址層級偵錯**和**顯示反組譯如果來源無法使用**  
  
  找不到來源或符號檔時，一律顯示反組譯碼。  
  
  ![選項&#47;偵錯&#47;一般反組譯碼選項](../debugger/media/dbg_options_general_disassembly_checkbox.png "選項&#47;偵錯&#47;一般反組譯碼選項")  
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **啟用來源伺服器支援**  
  
  若要協助偵錯應用程式，在本機電腦上沒有原始程式碼時使用來源伺服器或 *.pdb*檔案不相符的原始碼。 來源伺服器會接受要求的檔案，並傳回實際的檔案從原始檔控制。 來源伺服器執行，會使用名為的 DLL *srcsrv.dll*讀取應用程式的 *.pdb*檔案。 *.Pdb*檔案包含指向原始程式碼存放庫，以及用來從儲存機制擷取原始程式碼的命令。 
  
  您可以限制命令的*srcsrv.dll*可以從應用程式的執行 *.pdb*列出允許的命令，在名為的檔案*srcsrv.ini*。 地方*srcsrv.ini*相同的資料夾中的檔案*srcsrv.dll*並*devenv.exe*。  
  
  >[!IMPORTANT]
  >在應用程式的可內嵌任意命令 *.pdb*檔案中，因此請務必將只有您想要執行的命令*srcsrv.ini*檔案。 嘗試執行 *srcsvr.ini* 檔案中未包含的任何命令，會讓確認對話方塊出現。 如需詳細資訊，請參閱[安全性警告：偵錯工具必須執行未受信任的命令](../debugger/security-warning-debugger-must-execute-untrusted-command.md)。 
  >
  >由於不會對命令參數進行任何驗證，因此請謹慎使用受信任的命令。 例如，如果您列出*cmd.exe*中您*srcsrv.ini*，惡意使用者可能在上指定參數*cmd.exe*這會讓它危險。  
  
  選取此項目，而且您想要的子系項目。 **允許部分信任組件 （僅限受控） 的來源伺服器**並**永遠執行未受信任的來源伺服器命令而不提示**可能提高安全性風險。  
  
  ![啟用來源伺服器選項](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")  

## <a name="compiler-symbol-options"></a>編譯器符號選項  

當您從 Visual Studio IDE 與標準，會在建置專案時**偵錯**組建組態時，c + + 和 managed 的編譯器建立您的程式碼的適當的符號檔。 您也可以在程式碼中設定編譯器選項。 

### <a name="cc-options"></a>C/C++ 選項 

- *VC\<x >.pdb*並*\<專案 >.pdb*檔案
  
  A *.pdb*檔案，當您使用建置時，會建立 C/c + + [/ZI 或 /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)。 在  [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]，則[/Fd](/cpp/build/reference/fd-program-database-file-name)選項名稱 *.pdb*編譯器會建立的檔案。 當您建立的專案中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用 IDE **/Fd**選項設定為建立 *.pdb*檔案命名為*\<專案 >.pdb*。  
  
  如果您建置 C/c + + 應用程式使用 makefile，且您指定 **/ZI**或是 **/Zi**不用 **/Fd**，編譯器會建立兩個 *.pdb*檔案：  
  
  - *VC\<x>.pdb*，其中 *\<x>* 代表 Visual C++ 的版本，例如 *VC11.pdb* 
    
    *VC\<x >.pdb*檔案會儲存個別物件檔案的所有偵錯資訊，並且位在與專案 makefile 相同的目錄中。 每次建立物件檔時，C/c + + 編譯器會將合併到偵錯資訊*VC\<x >.pdb*。 因此，即使每個原始程式檔包含了常見的標頭檔這類 *\<windows.h >*，這些標頭檔的 typedef 也會儲存一次，而非每個目的檔中。 插入的資訊包括類型資訊，但是不包括符號資訊 (例如函式定義)。  
  
  - *\<project>.pdb* 
    
    *\<專案 >.pdb*檔案會儲存專案的所有偵錯資訊 *.exe*檔案，並位於*\debug*子目錄。 這個 *\<project>.pdb* 包含完整的偵錯資訊，包括函式原型，而不僅是在 *VC\<x>.pdb* 找到的類型資訊。 
  
  這兩個*VC\<x >.pdb*並*\<專案 >.pdb*檔案允許累加式更新。 連結器也會將路徑嵌入 *.pdb*中的檔案 *.exe*或是 *.dll*它所建立的檔案。  
  
- <a name="use-dumpbin-exports"></a>DLL 匯出表
  
  使用`dumpbin /exports`若要查看可用的 dll 匯出表中的符號。 DLL 匯出表中的符號資訊可用於處理 Windows 訊息、 Windows 程序 (Windowproc)、 COM 物件、 封送處理，或您沒有符號的任何 DLL。 這些符號適用於任何 32 位元系統 DLL。 這些呼叫都按呼叫順序列出，目前的函式 (巢狀最深處) 列在頂端。 
  
  藉由讀取`dumpbin /exports`輸出，您可以看到的確切的函式的名稱，包括非英數字元。 因為可以在其他地方截斷函式名稱，在偵錯工具中，查看確切的函式名稱可用於函式上設定中斷點。 如需詳細資訊，請參閱 [dumpbin /exports](/cpp/build/reference/dash-exports)。  
  
### <a name="net-framework-options"></a>.NET Framework 選項 
  
使用建置 **/debug**來建立 *.pdb*檔案。 您可以使用 **/debug:full** 或 **/debug:pdbonly**建置應用程式。 使用 **/debug:full** 建置會產生可偵錯的程式碼。 使用 **/debug:pdbonly** 進行建置則會產生 *.pdb* 檔案，但是不會產生用於通知 JIT 編譯器有可用偵錯資訊的 `DebuggableAttribute`。 如果您要為發行組建 (Release Build) 產生 *.pdb* 檔案，但不希望為可偵錯，則請使用 **/debug:pdbonly**。 如需詳細資訊，請參閱 [/debug (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) 或 [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug)。  
  
### <a name="web-applications"></a>Web 應用程式  
  
設定*web.config* ASP.NET 應用程式偵錯模式的檔案。 偵錯模式會導致 ASP.NET 產生動態產生之檔案的符號，並使偵錯工具附加到 ASP.NET 應用程式。 Visual Studio 時自動設定這個在開始偵錯，如果您的 web 專案範本建立您的專案。  

##  <a name="manage-symbols-while-debugging"></a>管理偵錯時的符號 

您可以使用**模組**，**呼叫堆疊**，**區域變數**，**自動變數**，或有任何**監看式**載入視窗符號或偵錯時變更符號選項。 如需詳細資訊，請參閱 <<c0> [ 更熟悉的偵錯工具附加至您的應用程式的方式](../debugger/debugger-tips-and-tricks.md#modules_window)。

### <a name="use-the-modules-window"></a>使用模組視窗

偵錯時，**模組**視窗會顯示偵錯工具會視為使用者程式碼，或我的程式碼，以及其符號載入作業狀態的程式碼模組。 您可以也監視符號載入狀態、 載入符號，以及變更符號選項，在**模組**視窗。

**若要監視或變更符號的位置或在偵錯時的選項：**

1. 若要開啟 **模組**視窗中的，偵錯時，選取**偵錯** > **Windows** > **模組**。 
1. 在 [**模組**] 視窗中，以滑鼠右鍵按一下**符號狀態**或**符號檔**標頭或任何模組。 
1. 在操作功能表中，選取下列選項之一：  
  
|選項|說明|  
|------------|-----------------|  
|**載入符號**|會出現以略過、 找不到或未載入符號的模組。 嘗試從指定的位置載入符號**選項** > **偵錯** > **符號**頁面。 如果找不到或未載入符號檔，會啟動**檔案總管**以便您可以指定要搜尋的新位置。|  
|**符號載入資訊**|顯示檔案的位置載入的符號或偵錯工具找不到檔案時所搜尋的位置。|  
|**符號設定**|會開啟**選項** > **偵錯** > **符號** 頁面上，您可以在其中編輯和新增符號位置。|  
|**永遠自動載入**|將偵錯工具會自動載入的檔案清單中選取的符號檔。|  

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>使用未 Loaded/No 來源載入符號頁面

有幾種方式偵錯工具沒有可用的符號或原始程式檔的程式碼：  

-  逐步執行程式碼。  
-  從中斷點或例外狀況的程式碼會中斷。  
-  切換至不同的執行緒。  
-  連按兩下中的框架，以變更堆疊框架**呼叫堆疊**視窗。  
   
當發生這種情況時，偵錯工具會顯示**未載入符號**或是**未載入來源**頁面，以協助您尋找和載入必要的符號或來源。  
  
 ![未載入符號頁面](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")  
  
**若要使用未載入符號 文件頁面，以協助尋找並載入符號遺失：**  
  
-   若要變更搜尋路徑，請選取 未選取的路徑，或選取**新的路徑**或是**新增 VSTS 路徑**然後輸入或選取新的路徑。 選取 **載入**再次搜尋路徑，並載入符號檔，並在找到。  
-   若要覆寫任何符號選項並重試搜尋路徑，請選取**瀏覽並尋找\<可執行檔名稱 >**。 如果找到，載入符號檔或**檔案總管**會開啟，讓您可以手動選取符號檔。  
-   若要開啟 **選項** > **偵錯** > **符號**頁面上，選取**變更符號設定**。  
-   若要在新視窗一次顯示反組譯碼，請選取**檢視反組譯碼**，或選取 **[選項] 對話方塊**選項設定為找不到來源或符號檔時，一律顯示反組譯碼。 
-   若要搜尋的位置與結果顯示，展開**符號載入資訊**。 

如果偵錯工具會尋找 *.pdb*檔案在您執行其中一個選項，並可以擷取原始程式檔中的資訊之後 *.pdb*檔案，它會顯示來源。 否則，它會顯示**未載入來源**描述問題，可能會解決此問題的動作連結的頁面。

**將原始程式檔搜尋路徑加入至方案：**
  
您可以指定偵錯工具搜尋原始程式檔的位置，並從搜尋結果中排除特定檔案。

1. 選取中的解決方案**方案總管**，然後選取**屬性**圖示，並按下**Alt**+**Enter**，或以滑鼠右鍵按一下並選取**屬性**。
   
1. 選取 **偵錯原始程式檔**。
   
1. 底下**包含原始程式碼的目錄**，輸入或選取要搜尋的來源的程式碼位置。 使用**新的一行**圖示以新增更多的位置，**向上**並**向下**箭號圖示，以重新排列它們，或**X**圖示即可刪除它們。
   
   >[!NOTE]
   >偵錯工具會搜尋指定的目錄。 您必須自行加入要搜尋的所有子目錄項目。
   
1. 底下**不會尋找這些原始程式檔**，輸入要排除搜尋原始程式檔的名稱。 
   
1. 選取  **確定**或是**套用**。


## <a name="see-also"></a>另請參閱  
[了解符號檔和 Visual Studio 符號設定](https://blogs.msdn.microsoft.com/devops/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/)

[Visual Studio 2012 和 2013 中的 .NET 遠端符號載入變更](https://blogs.msdn.microsoft.com/devops/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)

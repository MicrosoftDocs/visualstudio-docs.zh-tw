---
title: Link 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab3e3238e78062bc1193a6d81b3f74749a263968
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897715"
---
# <a name="link-task"></a>Link 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
包裝 Visual C++ 連結器工具 link.exe。 連結器工具會連結通用物件檔案格式 (COFF) 目的檔及程式庫，以建立可執行檔 (.exe) 或動態連結程式庫 (DLL)。 如需詳細資訊，請參閱[連結器選項](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129)。  
  
## <a name="parameters"></a>參數  
 下表說明 **Link** 工作的參數。 大部分的工作參數以及數組參數會對應到命令列選項。  
  
- **AdditionalDependencies**  
  
   選擇性的 **String[]** 參數。  
  
   指定要加入命令的輸入檔清單。  
  
   如需詳細資訊，請參閱 [LINK 輸入檔](http://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412)。  
  
- **AdditionalLibraryDirectories**  
  
   選擇性的 **String[]** 參數。  
  
   覆寫環境程式庫路徑。 指定目錄名稱。  
  
   如需詳細資訊，請參閱 [/LIBPATH (其他 Libpath)](http://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba)。  
  
- **AdditionalManifestDependencies**  
  
   選擇性的 **String[]** 參數。  
  
   指定將放入資訊清單檔案的 `dependency` 區段的屬性。  
  
   如需詳細資訊，請參閱 [/MANIFESTDEPENDENCY (指定資訊清單相依性)](http://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73)。 另請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上的＜發行者組態檔＞。  
  
- **AdditionalOptions**  
  
   選擇性的 **String** 參數。  
  
   指定於命令列上的連結器選項清單。 例如 **"**_/option1 /option2 /option#_"。 使用此參數，來指定任何其他 **Link** 工作參數未表示的連結器選項。  
  
   如需詳細資訊，請參閱[連結器選項](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129)。  
  
- **AddModuleNamesToAssembly**  
  
   選擇性的 **String[]** 參數。  
  
   將模組參考加入組件。  
  
   如需詳細資訊，請參閱 [/ASSEMBLYMODULE (將 MSIL 模組加入組件)](http://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143)。  
  
- **AllowIsolation**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會導致作業系統查閱和載入資訊清單。 如果是 `false`，則表示會載入 Dll，如同沒有任何資訊清單。  
  
   如需詳細資訊，請參閱 [/ALLOWISOLATION (資訊清單查閱)](http://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f)。  
  
- **AssemblyDebug**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會發出帶有偵錯資訊追蹤的 **DebuggableAttribute** 屬性，並停用 JIT 最佳化。 如果是 `false`，即會發出 **DebuggableAttribute** 屬性，但會停用偵錯資訊追蹤，並啟用 JIT 最佳化。  
  
   如需詳細資訊，請參閱 [/ASSEMBLYDEBUG (加入 DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)。  
  
- **AssemblyLinkResource**  
  
   選擇性的 **String[]** 參數。  
  
   在輸出檔中建立 .NET Framework 資源的連結；不要將資源檔放置於輸出檔中。 指定資源的名稱。  
  
   如需詳細資訊，請參閱 [/ASSEMBLYLINKRESOURCE (連結到 .NET Framework 資源)](http://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64)。  
  
- **AttributeFileTracking**  
  
   隱含的 **Boolean** 參數。  
  
   啟用更深入的檔案追蹤，來擷取累加式連結的行為。 一律傳回 `true`。  
  
- **BaseAddress**  
  
   選擇性的 **String** 參數。  
  
   設定要建置之程式或 DLL 的基底位址。 請指定 `{address[,size] | @filename,key}`。  
  
   如需詳細資訊，請參閱 [/BASE (基底位址)](http://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069)。  
  
- **BuildingInIDE**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 true，即表示會從 IDE 叫用 MSBuild。 否則，即表示會從命令列叫用 MSBuild。  
  
   此參數沒有對等的連結器選項。  
  
- **CLRImageType**  
  
   選擇性的 **String** 參數。  
  
   設定 Common Language Runtime (CLR) 映像的類型。  
  
   指定下列其中一個值；每個值會分別對應至一個連結器選項。  
  
  - **Default** - *\<none>*  
  
  - **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
  - **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
  - **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**  
  
    如需詳細資訊，請參閱 [/CLRIMAGETYPE (指定 CLR 映像類型)](http://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116)。  
  
- **CLRSupportLastError**  
  
   選擇性的 **String** 參數。  
  
   保留透過 P/Invoke 機制呼叫之函式的最後一個錯誤碼。  
  
   指定下列其中一個值；每個值會分別對應至一個連結器選項。  
  
  - **Enabled** - **/CLRSupportLastError**  
  
  - **Disabled** - **/CLRSupportLastError:NO**  
  
  - **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
    如需詳細資訊，請參閱 [/CLRSUPPORTLASTERROR (保留 PInvoke 呼叫的最後一個錯誤碼)](http://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575)。  
  
- **CLRThreadAttribute**  
  
   選擇性的 **String** 參數。  
  
   明確指定 CLR 程式進入點的執行緒屬性。  
  
   指定下列其中一個值；每個值會分別對應至一個連結器選項。  
  
  - **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**  
  
  - **MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**  
  
  - **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
    如需詳細資訊，請參閱 [/CLRTHREADATTRIBUTE (設定 CLR 執行緒屬性)](http://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8)。  
  
- **CLRUnmanagedCodeCheck**  
  
   選擇性的 **Boolean** 參數。  
  
   指定連結器是否會將 **SuppressUnmanagedCodeSecurityAttribute** 套用至連結器產生的 P/Invoke 呼叫 (由 Managed 程式碼至原生 DLL)。  
  
   如需詳細資訊，請參閱 [/CLRUNMANAGEDCODECHECK (加入 SupressUnmanagedCodeSecurityAttribute)](http://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2)。  
  
- **CreateHotPatchableImage**  
  
   選擇性的 **String** 參數。  
  
   準備映像進行 Hotpatch。  
  
   指定下列其中一個值，每個值會分別對應至一個連結器選項。  
  
  - **Enabled** - **/FUNCTIONPADMIN**  
  
  - **X86Image** - **/FUNCTIONPADMIN:5**  
  
  - **X64Image** - **/FUNCTIONPADMIN:6**  
  
  - **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
    如需詳細資訊，請參閱 [/FUNCTIONPADMIN (建立可進行 Hotpatch 的映像)](http://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7)。  
  
- **DataExecutionPrevention**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即表示可執行檔已經過測試，可與 Windows 資料執行防止功能相容。  
  
   如需詳細資訊，請參閱 [/NXCOMPAT (與資料執行防止相容)](http://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b)。  
  
- **DelayLoadDLLs**  
  
   選擇性的 **String[]** 參數。  
  
   此參數會導致 DLL「延遲載入」。 指定要延遲載入的 DLL 名稱。  
  
   如需詳細資訊，請參閱 [/DELAYLOAD (延遲載入匯入)](http://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28)。  
  
- **DelaySign**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會部分簽署組件。 預設值為 `false`。  
  
   如需詳細資訊，請參閱 [/DELAYSIGN (部分簽署組件)](http://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20)。  
  
- **驅動程式**  
  
   選擇性的 **String** 參數。  
  
   指定此參數來建置 Windows NT 核心模式驅動程式。  
  
   指定下列其中一個值；每個值會分別對應至一個連結器選項。  
  
  - **NotSet** - *\<none>*  
  
  - **Driver** - **/Driver**  
  
  - **UpOnly** - **/DRIVER:UPONLY**  
  
  - **WDM** - **/DRIVER:WDM**  
  
    如需詳細資訊，請參閱 [/DRIVER (Windows NT 核心模式驅動程式)](http://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8)。  
  
- **EmbedManagedResourceFile**  
  
   選擇性的 **String[]** 參數。  
  
   在組件中內嵌資源檔。 指定所需的資源檔名稱。 選擇性地指定邏輯名稱 (用來載入資源) 及 **PRIVATE** 選項 (表示在組件資訊清單中資源檔為私用的)。  
  
   如需詳細資訊，請參閱 [/ASSEMBLYRESOURCE (內嵌 Managed 資源)](http://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2)。  
  
- **EnableCOMDATFolding**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會啟用完全相同的 COMDAT 摺疊。  
  
   如需詳細資訊，請參閱 [/OPT (最佳化)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac) 的 `ICF[= iterations]` 引數。  
  
- **EnableUAC**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會指定要在程式資訊清單中內嵌使用者帳戶控制 (UAC) 資訊。  
  
   如需詳細資訊，請參閱 [/MANIFESTUAC (在資訊清單中內嵌 UAC 資訊)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a)。  
  
- **EntryPointSymbol**  
  
   選擇性的 **String** 參數。  
  
   指定進入點函式做為 .exe 檔或 DLL 的開始位址。 指定函式名稱做為參數值。  
  
   如需詳細資訊，請參閱 [/ENTRY (進入點符號)](http://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445)。  
  
- **FixedBaseAddress**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會建立僅可在其慣用基底位址載入的程式或 DLL。  
  
   如需詳細資訊，請參閱 [/FIXED (固定基底位址)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5)。  
  
- **ForceFileOutput**  
  
   選擇性的 **String** 參數。  
  
   告訴連結器即使參考到未定義或多次定義的符號，也要建立有效的 .exe 檔或 DLL。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Enabled** - **/FORCE**  
  
  - **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
  - **UndefinedSymbolOnly** - **/FORCE:UNRESOLVED**  
  
    如需詳細資訊，請參閱 [/FORCE (強制檔案輸出)](http://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da)。  
  
- **ForceSymbolReferences**  
  
   選擇性的 **String[]** 參數。  
  
   此參數會告訴連結器，將指定的符號加入符號表。  
  
   如需詳細資訊，請參閱 [/INCLUDE (強制符號參考)](http://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c)。  
  
- **FunctionOrder**  
  
   選擇性的 **String** 參數。  
  
   此參數會以預先定義的順序將指定的封裝函式 (COMDAT) 放入映像中，來最佳化您的程式。  
  
   如需詳細資訊，請參閱 [/ORDER (依順序置放函式)](http://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a)。  
  
- **GenerateDebugInformation**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會建立 .exe 檔或 DLL 的偵錯資訊。  
  
   如需詳細資訊，請參閱 [/DEBUG (產生偵錯資訊)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103)。  
  
- **GenerateManifest**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會建立並存資訊清單檔。  
  
   如需詳細資訊，請參閱 [/MANIFEST (建立並存組件資訊清單)](http://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600)。  
  
- **GenerateMapFile**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會建立「對應檔」。 對應檔的副檔名是 .map。  
  
   如需詳細資訊，請參閱 [/MAP (產生對應檔)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)。  
  
- **HeapCommitSize**  
  
   選擇性的 **String** 參數。  
  
   指定一次要配置的實體記憶體數量。  
  
   如需詳細資訊，請參閱 [/HEAP (設定堆積大小)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da) 中的 `commit` 引數。 另請參閱 **HeapReserveSize** 參數。  
  
- **HeapReserveSize**  
  
   選擇性的 **String** 參數。  
  
   指定虛擬記憶體中的堆積配置總和。  
  
   如需詳細資訊，請參閱 [/HEAP (設定堆積大小)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da) 中的 `reserve` 引數。 另請參閱此表格中的 **HeapCommitSize** 參數。  
  
- **IgnoreAllDefaultLibraries**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會告訴連結器在解析外部參考時，從它搜尋的程式庫清單中移除一或多個預設程式庫。  
  
   如需詳細資訊，請參閱 [/NODEFAULTLIB (忽略程式庫)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e)。  
  
- **IgnoreEmbeddedIDL**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會指定不應將原始程式碼中的任何 IDL 屬性處理到 .idl 檔中。  
  
   如需詳細資訊，請參閱 [/IGNOREIDL (不要將屬性處理至 MIDL 中)](http://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780)。  
  
- **IgnoreImportLibrary**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會指定不要將此組態所產生的程式庫匯入相依專案。  
  
   此參數並未對應至連結器選項。  
  
- **IgnoreSpecificDefaultLibraries**  
  
   選擇性的 **String[]** 參數。  
  
   指定要忽略的一或多個預設程式庫名稱。 使用分號分隔多個程式庫。  
  
   如需詳細資訊，請參閱 [/NODEFAULTLIB (忽略程式庫)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e)。  
  
- **ImageHasSafeExceptionHandlers**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，連結器只有在它也可以產生映像的安全例外狀況處理常式表格時，才會產生該映像。  
  
   如需詳細資訊，請參閱 [/SAFESEH (映像有安全例外狀況處理常式)](http://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7)。  
  
- **ImportLibrary**  
  
   使用者指定的匯入程式庫名稱，可取代預設的程式庫名稱。  
  
   如需詳細資訊，請參閱 [/IMPLIB (名稱匯入程式庫)](http://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432)。  
  
- **KeyContainer**  
  
   選擇性的 **String** 參數。  
  
   包含已簽署組件之金鑰的容器。  
  
   如需詳細資訊，請參閱 [/KEYCONTAINER (指定要簽署組件的金鑰容器)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e)。 另請參閱此表格中的 **KeyFile** 參數。  
  
- **KeyFile**  
  
   選擇性的 **String** 參數。  
  
   指定包含已簽署組件之金鑰的容器。  
  
   如需詳細資訊，請參閱 [/KEYFILE (指定要簽署組件的金鑰或金鑰組)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06)。 另請參閱 **KeyContainer** 參數。  
  
- **LargeAddressAware**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，應用程式就能處理大於 2 GB 的位址。  
  
   如需詳細資訊，請參閱 [/LARGEADDRESSAWARE (處理大型記憶體)](http://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385)。  
  
- **LinkDLL**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會建置 DLL 做為主要輸出檔。  
  
   如需詳細資訊，請參閱 [/DLL (建置 DLL)](http://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609)。  
  
- **LinkErrorReporting**  
  
   選擇性的 **String** 參數。  
  
   讓您可將內部編譯器錯誤 (ICE) 資訊直接提供給 Microsoft。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **NoErrorReport** - **/ERRORREPORT:NONE**  
  
  - **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
  - **SendErrorReport** - **/ERRORREPORT:SEND**  
  
    如需詳細資訊，請參閱 [/ERRORREPORT (回報內部連結器錯誤)](http://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28)。  
  
- **LinkIncremental**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會啟用累加連結。  
  
   如需詳細資訊，請參閱 [/INCREMENTAL (以累加方式連結)](http://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b)。  
  
- **LinkLibraryDependencies**  
  
   選擇性的 **Boolean** 參數。  
  
   若為 `true`，會指定要自動連結專案相依性的程式庫輸出。  
  
   此參數並未對應至連結器選項。  
  
- **LinkStatus**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會指定連結器要顯示進度指示器，以顯示連結完成的百分比。  
  
   如需詳細資訊，請參閱 [/LTCG (連結時產生程式碼)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) 的 `STATUS` 引數。  
  
- **LinkTimeCodeGeneration**  
  
   選擇性的 **String** 參數。  
  
   指定特性指引最佳化的選項。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Default** - *\<none>*  
  
  - **UseLinkTimeCodeGeneration** - **/LTCG**  
  
  - **PGInstrument** - **/LTCG:PGInstrument**  
  
  - **PGOptimization** - **/LTCG:PGOptimize**  
  
  - **PGUpdate**  
  
     \- **/LTCG:PGUpdate**  
  
    如需詳細資訊，請參閱 [/LTCG (連結時產生程式碼)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2)。  
  
- **ManifestFile**  
  
   選擇性的 **String** 參數。  
  
   將預設的資訊清單檔案名稱變更為指定的檔案名稱。  
  
   如需詳細資訊，請參閱 [/MANIFESTFILE (為資訊清單檔案命名)](http://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d)。  
  
- **MapExports**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會告訴連結器在對應檔中包含匯出的函式。  
  
   如需詳細資訊，請參閱 [/MAPINFO (在對應檔中包含資訊)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b) 中的`EXPORTS` 引數。  
  
- **MapFileName**  
  
   選擇性的 **String** 參數。  
  
   將預設的對應檔名稱變更為指定的檔案名稱。  
  
- **MergedIDLBaseFileName**  
  
   選擇性的 **String** 參數。  
  
   指定 .idl 檔的檔名和副檔名。  
  
   如需詳細資訊，請參閱 [/IDLOUT (為 MIDL 輸出檔命名)](http://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509)。  
  
- **MergeSections**  
  
   選擇性的 **String** 參數。  
  
   結合映像中的區段。 請指定 `from-section=to-section`。  
  
   如需詳細資訊，請參閱 [/MERGE (結合區段)](http://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52)。  
  
- **MidlCommandFile**  
  
   選擇性的 **String** 參數。  
  
   指定包含 MIDL 命令列選項的檔案名稱。  
  
   如需詳細資訊，請參閱 [/MIDL (指定 MIDL 命令列引數選項)](http://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1)。  
  
- **MinimumRequiredVersion**  
  
   選擇性的 **String** 參數。  
  
   指定子系統的最小必要版本。 引數為範圍從 0 到 65535 的十進位數字。  
  
- **ModuleDefinitionFile**  
  
   選擇性的 **String** 參數。  
  
   指定[模組定義檔](http://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8)的名稱。  
  
   如需詳細資訊，請參閱 [/DEF (指定模組定義檔)](http://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a)。  
  
- **MSDOSStubFileName**  
  
   選擇性的 **String** 參數。  
  
   將指定的 MS-DOS Stub 程式附加至 Win32 程式。  
  
   如需詳細資訊，請參閱 [/STUB (MS-DOS Stub 檔名)](http://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f)。  
  
- **NoEntryPoint**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會指定僅含資源的 DLL。  
  
   如需詳細資訊，請參閱 [/NOENTRY (沒有進入點)](http://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a)。  
  
- **ObjectFiles**  
  
   隱含的 **String []** 參數。  
  
   指定連結的目的檔。  
  
- **OptimizeReferences**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會排除從未參考的函式和/或資料。  
  
   如需詳細資訊，請參閱 [/OPT (最佳化)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac) 中的 `REF` 引數。  
  
- **OutputFile**  
  
   選擇性的 **String** 參數。  
  
   覆寫連結器所建立程式的預設名稱和位置。  
  
   如需詳細資訊，請參閱 [/OUT (輸出檔名稱)](http://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834)。  
  
- **PerUserRedirection**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true` 且已啟用登錄輸出，即會強制將登錄寫入 **HKEY_CLASSES_ROOT**，使其重新導向到 **HKEY_CURRENT_USER**。  
  
- **PreprocessOutput**  
  
   選擇性的 `ITaskItem[]` 參數。  
  
   定義工作可以耗用和發出的前置處理器輸出項目的陣列。  
  
- **PreventDllBinding**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會指示 Bind.exe 不應該繫結連結的映像。  
  
   如需詳細資訊，請參閱 [/ALLOWBIND (防止 DLL 繫結)](http://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598)。  
  
- **Profile**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會產生可與**效能工具**分析工具搭配使用的輸出檔。  
  
   如需詳細資訊，請參閱 [/PROFILE (效能工具分析工具)](http://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699)。  
  
- **ProfileGuidedDatabase**  
  
   選擇性的 **String** 參數。  
  
   指定將用來保存執行中程式相關資訊的 .pgd 檔案名稱  
  
   如需詳細資訊，請參閱 [/PGD (指定特性指引最佳化的資料庫)](http://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443)。  
  
- **ProgramDatabaseFile**  
  
   選擇性的 **String** 參數。  
  
   指定連結器建立的程式資料庫 (PDB) 名稱。  
  
   如需詳細資訊，請參閱 [/PDB (使用程式資料庫)](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d)。  
  
- **RandomizedBaseAddress**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會產生可執行映像檔，其可使用 Windows 的「位址空間配置隨機載入」(ASLR) 功能，於載入時隨機重定基底。  
  
   如需詳細資訊，請參閱 [/DYNAMICBASE (使用位址空間配置隨機載入)](http://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2)。  
  
- **RegisterOutput**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會登錄此組建的主要輸出。  
  
- **SectionAlignment**  
  
   選擇性的 **Integer** 參數。  
  
   指定程式線性位址空間內每個區段的對應儲存方式。 參數值是一個單位數的位元組且為 2 的次方。  
  
   如需詳細資訊，請參閱 [/ALIGN (區段對應儲存)](http://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740)。  
  
- **SetChecksum**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會在 .exe 檔的標頭中設定總和檢查碼。  
  
   如需詳細資訊，請參閱 [/RELEASE (設定總和檢查碼)](http://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22)。  
  
- **ShowProgress**  
  
   選擇性的 **String** 參數。  
  
   指定連結作業的進度報表詳細資訊。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **NotSet** - *\<none>*  
  
  - **LinkVerbose** - **/VERBOSE**  
  
  - **LinkVerboseLib** - **/VERBOSE:Lib**  
  
  - **LinkVerboseICF** - **/VERBOSE:ICF**  
  
  - **LinkVerboseREF** - **/VERBOSE:REF**  
  
  - **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
  - **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
    如需詳細資訊，請參閱 [/VERBOSE (列印進度訊息)](http://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab)。  
  
- **Sources**  
  
   必要的 `ITaskItem[]` 參數。  
  
   定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。  
  
- **SpecifySectionAttributes**  
  
   選擇性的 **String** 參數。  
  
   指定區段的屬性。 這會覆寫在編譯區段的 .obj 檔案時所設定的屬性。  
  
   如需詳細資訊，請參閱 [/SECTION (指定區段屬性)](http://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16)。  
  
- **StackCommitSize**  
  
   選擇性的 **String** 參數。  
  
   指定在配置額外的記憶體時，每個配置中的實體記憶體數量。  
  
   如需詳細資訊，請參閱 [/STACK (堆疊配置)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c) 的 `commit` 引數。  
  
- **StackReserveSize**  
  
   選擇性的 **String** 參數。  
  
   指定虛擬記憶體中的堆疊配置大小總和。  
  
   如需詳細資訊，請參閱 [/STACK (堆疊配置)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c) 的 `reserve` 引數。  
  
- **StripPrivateSymbols**  
  
   選擇性的 **String** 參數。  
  
   建立第二個程式資料庫 (PDB) 檔，以省略您不要散發給客戶的符號。 指定第二個 PDB 檔的名稱。  
  
   如需詳細資訊，請參閱 [/PDBSTRIPPED (移除專用符號)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55)。  
  
- **SubSystem**  
  
   選擇性的 **String** 參數。  
  
   指定可執行檔的環境。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **NotSet** - *\<none>*  
  
  - **Console** - **/SUBSYSTEM:CONSOLE**  
  
  - **Windows** - **/SUBSYSTEM:WINDOWS**  
  
  - **Native** - **/SUBSYSTEM:NATIVE**  
  
  - **EFI Application** - **/SUBSYSTEM:EFI_APPLICATION**  
  
  - **EFI Boot Service Driver** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
  - **EFI ROM** - **/SUBSYSTEM:EFI_ROM**  
  
  - **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
  - **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
  - **POSIX** - **/SUBSYSTEM:POSIX**  
  
    如需詳細資訊，請參閱 [/SUBSYSTEM (指定子系統)](http://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b)。  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會告知連結器不要在最終映像中包含可繫結的匯入位址表 (IAT)。  
  
   如需詳細資訊，請參閱 [/DELAY (延遲載入匯入設定)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c) 的 `NOBIND` 引數。  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會告知延遲載入 Helper 函式，支援明確卸載 DLL。  
  
   如需詳細資訊，請參閱 [/DELAY (延遲載入匯入設定)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c) 的 `UNLOAD` 引數。  
  
- **SuppressStartupBanner**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。  
  
   如需詳細資訊，請參閱 [/NOLOGO (隱藏程式啟始資訊) (連結器)](http://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197)。  
  
- **SwapRunFromCD**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會告知作業系統要先將連結器輸出複製到交換檔，然後從該處執行映像。  
  
   如需詳細資訊，請參閱 [/SWAPRUN (將連結器輸出載入至交換檔)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683) 的 `CD` 引數。 另請參閱 **SwapRunFromNET** 參數。  
  
- **SwapRunFromNET**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會告知作業系統要先將連結器輸出複製到交換檔，然後從該處執行映像。  
  
   如需詳細資訊，請參閱 [/SWAPRUN (將連結器輸出載入至交換檔)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683) 的 `NET` 引數。 另請參閱此表格中的 **SwapRunFromCD** 參數。  
  
- **TargetMachine**  
  
   選擇性的 **String** 參數。  
  
   指定程式或 DLL 的目標平台。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **NotSet** - *\<none>*  
  
  - **MachineARM** - **/MACHINE:ARM**  
  
  - **MachineEBC** - **/MACHINE:EBC**  
  
  - **MachineIA64** - **/MACHINE:IA64**  
  
  - **MachineMIPS** - **/MACHINE:MIPS**  
  
  - **MachineMIPS16** - **/MACHINE:MIPS16**  
  
  - **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
  - **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
  - **MachineSH4** - **/MACHINE:SH4**  
  
  - **MachineTHUMB** - **/MACHINE:THUMB**  
  
  - **MachineX64** - **/MACHINE:X64**  
  
  - **MachineX86** - **/MACHINE:X86**  
  
    如需詳細資訊，請參閱 [/MACHINE (指定目標平台)](http://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2)。  
  
- **TerminalServerAware**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會在程式映像的選擇性標頭內 IMAGE_OPTIONAL_HEADER DllCharacteristics 欄位中設定旗標。 設定此旗標時，終端機伺服器將不會對應用程式進行某些變更。  
  
   如需詳細資訊，請參閱 [/TSAWARE (建立終端伺服器感知應用程式)](http://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29)。  
  
- **TrackerLogDirectory**  
  
   選擇性的 **String** 參數。  
  
   指定追蹤器記錄檔的目錄。  
  
- **TreatLinkerWarningAsErrors**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，導致在連結器產生警告時，不會產生任何輸出檔。  
  
   如需詳細資訊，請參閱 [/WX (將連結器警告視為錯誤)](http://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9)。  
  
- **TurnOffAssemblyGeneration**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，即會為目前的輸出檔建立不含 .NET Framework 組件的映像。  
  
   如需詳細資訊，請參閱 [/NOASSEMBLY (建立 MSIL 模組)](http://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe)。  
  
- **TypeLibraryFile**  
  
   選擇性的 **String** 參數。  
  
   指定 .tlb 檔的檔名和副檔名。 指定檔案名稱，或路徑和檔案名稱。  
  
   如需詳細資訊，請參閱 [/TLBOUT (為 .TLB 檔命名)](http://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8)。  
  
- **TypeLibraryResourceID**  
  
   選擇性的 **Integer** 參數。  
  
   為連結器建立的類型程式庫指定使用者指定的值。 指定範圍從 1 到 65535 的值。  
  
   如需詳細資訊，請參閱 [/TLBID (指定 TypeLib 的資源識別碼)](http://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2)。  
  
- **UACExecutionLevel**  
  
   選擇性的 **String** 參數。  
  
   指定在啟用使用者帳戶控制的情況下執行時，應用程式要求的執行層級。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **AsInvoker** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **RequireAdministrator** - `level='requireAdministrator'`  
  
    如需詳細資訊，請參閱 [/MANIFESTUAC (在資訊清單中內嵌 UAC 資訊)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a) 的 `level` 引數。  
  
- **UACUIAccess**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，應用程式即會略過使用者介面保護層級，並將輸入放到桌面上更高權限的視窗；否則為 `false`。  
  
   如需詳細資訊，請參閱 [/MANIFESTUAC (在資訊清單中內嵌 UAC 資訊)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a) 的 `uiAccess` 引數。  
  
- **UseLibraryDependencyInputs**  
  
   選擇性的 **Boolean** 參數。  
  
   如果是 `true`，連結專案相依性的程式庫輸出時，會使用管理員工具的輸入而非程式庫檔案本身。  
  
- **版本**  
  
   選擇性的 **String** 參數。  
  
   將版本號碼放入 .exe 或 .dll 檔的標頭。 請指定 "`major[.minor]`"。 `major` 和 `minor` 引數都是範圍從 0 到 65535 的十進位數字。  
  
   如需詳細資訊，請參閱 [/VERSION (版本資訊)](http://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223)。  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)




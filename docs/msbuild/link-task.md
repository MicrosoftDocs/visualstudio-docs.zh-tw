---
title: Link 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用連結工作包裝 Microsoft c + + 連結器工具 link.exe，其會連結 COFF 物件檔案和程式庫。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
- MSBuild (C++), Link task
- Link task (MSBuild (C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99e545cc4ae6a037816fd727d63fce16d3626484
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966314"
---
# <a name="link-task"></a>Link 工作

包裝 Microsoft c + + 連結器工具， *link.exe*。 連結器工具會連結通用物件檔案格式 (COFF) 目的檔及程式庫，以建立可執行檔 (*.exe*) 或動態連結程式庫 (DLL)。 如需詳細資訊，請參閱 [連結器選項](/cpp/build/reference/linker-options) 和 [從命令列使用 MSBuild](/cpp/build/msbuild-visual-cpp) ，然後 [從命令列使用 Microsoft c + + 工具](/cpp/build/building-on-the-command-line)組。

## <a name="parameters"></a>參數

 以下描述 **Link** 工作的參數。 大部分的工作參數以及數組參數會對應到命令列選項。

- **AdditionalDependencies**

  選擇性的 **String []** 參數。

  指定要加入命令的輸入檔清單。

  如需詳細資訊，請參閱 [LINK 輸入檔](/cpp/build/reference/link-input-files)。

- **AdditionalLibraryDirectories**

  選擇性的 **String []** 參數。

  覆寫環境程式庫路徑。 指定目錄名稱。

  如需詳細資訊，請參閱 [/LIBPATH (其他 Libpath)](/cpp/build/reference/libpath-additional-libpath)。

- **AdditionalManifestDependencies**

  選擇性的 **String []** 參數。

  指定將放入資訊清單檔案的 `dependency` 區段的屬性。

  如需詳細資訊，請參閱 [/MANIFESTDEPENDENCY (指定資訊清單相依性)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies)。 另請參閱[發行者組態檔](/windows/desktop/SbsCs/publisher-configuration-files)。

- **AdditionalOptions**

  選擇性的 **字串** 參數。

  指定於命令列上的連結器選項清單。 例如，/ \<option1>  / \<option2>  / \<option#> 。 使用此參數，來指定任何其他 **Link** 工作參數未表示的連結器選項。

  如需詳細資訊，請參閱[連結器選項](/cpp/build/reference/linker-options)。

- **AddModuleNamesToAssembly**

  選擇性的 **String []** 參數。

  將模組參考加入組件。

  如需詳細資訊，請參閱 [/ASSEMBLYMODULE (將 MSIL 模組新增至組件)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly)。

- **AllowIsolation**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會導致作業系統查閱和載入資訊清單。 如果是 `false`，則表示會載入 Dll，如同沒有任何資訊清單。

  如需詳細資訊，請參閱 [/ALLOWISOLATION (資訊清單查閱) ](/cpp/build/reference/allowisolation-manifest-lookup)。

- **AssemblyDebug**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會發出帶有偵錯資訊追蹤的 **DebuggableAttribute** 屬性，並停用 JIT 最佳化。 如果是 `false`，即會發出 **DebuggableAttribute** 屬性，但會停用偵錯資訊追蹤，並啟用 JIT 最佳化。

  如需詳細資訊，請參閱 [/ASSEMBLYDEBUG (加入 DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)。

- **AssemblyLinkResource**

  選擇性的 **String []** 參數。

  在輸出檔中建立 .NET Framework 資源的連結；不要將資源檔放置於輸出檔中。 指定資源的名稱。

  如需詳細資訊，請參閱 [/ASSEMBLYLINKRESOURCE (連結至 .NET Framework 資源) ](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource)。

- **AttributeFileTracking**

  隱含的 **Boolean** 參數。

  啟用更深入的檔案追蹤，來擷取累加式連結的行為。 一律傳回 `true`。

- **BaseAddress**

  選擇性的 **字串** 參數。

  設定要建置之程式或 DLL 的基底位址。 請指定 `{address[,size] | @filename,key}`。

  如需詳細資訊，請參閱 [/base (基底位址) ](/cpp/build/reference/base-base-address)。

- **BuildingInIDE**

  選擇性的 **布林值** 參數。

  如果是 true，即表示會從 IDE 叫用 MSBuild。 否則，即表示會從命令列叫用 MSBuild。

  此參數沒有對等的連結器選項。

- **CLRImageType**

  選擇性的 **字串** 參數。

  設定 Common Language Runtime (CLR) 映像的類型。

  指定下列其中一個值；每個值會分別對應至一個連結器選項。

  - **預設** - *\<none>*

  - **ForceIJWImage**  - **/CLRIMAGETYPE： IJW**

  - **ForcePureILImage**  - **/CLRIMAGETYPE：純**

  - **ForceSafeILImage**  - **/CLRIMAGETYPE： SAFE**

  如需詳細資訊，請參閱 [/CLRIMAGETYPE (指定 CLR 映射類型) ](/cpp/build/reference/clrimagetype-specify-type-of-clr-image)。

- **CLRSupportLastError**

  選擇性的 **字串** 參數。

  保留透過 P/Invoke 機制呼叫之函式的最後一個錯誤碼。

  指定下列其中一個值；每個值會分別對應至一個連結器選項。

  - **已啟用**  - **/CLRSupportLastError**

  - **已停用**  - **/CLRSupportLastError：否**

  - **SystemDlls**  - **/CLRSupportLastError： SYSTEMDLL**

  如需詳細資訊，請參閱 [/CLRSUPPORTLASTERROR (針對 PInvoke 呼叫保留最後的錯誤碼) ](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls)。

- **CLRThreadAttribute**

  選擇性的 **字串** 參數。

  明確指定 CLR 程式進入點的執行緒屬性。

  指定下列其中一個值；每個值會分別對應至一個連結器選項。

  - **DefaultThreadingAttribute**  - **/CLRTHREADATTRIBUTE：無**

  - **MTAThreadingAttribute**  - **/CLRTHREADATTRIBUTE： MTA**

  - **STAThreadingAttribute**  - **/CLRTHREADATTRIBUTE： STA**

  如需詳細資訊，請參閱 [/CLRTHREADATTRIBUTE (設定 CLR 執行緒屬性) ](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute)。

- **CLRUnmanagedCodeCheck**

  選擇性的 **布林值** 參數。

  指定連結器是否會將 **SuppressUnmanagedCodeSecurityAttribute** 套用至連結器產生的 P/Invoke 呼叫 (由 Managed 程式碼至原生 DLL)。

  如需詳細資訊，請參閱 [/CLRUNMANAGEDCODECHECK (新增 SuppressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute)。

- **CreateHotPatchableImage**

  選擇性的 **字串** 參數。

  準備映像進行 Hotpatch。

  指定下列其中一個值，每個值會分別對應至一個連結器選項。

  - **已啟用**  - **/FUNCTIONPADMIN**

  - **X86Image**  - **/FUNCTIONPADMIN： 5**

  - **X64Image**  - **/FUNCTIONPADMIN： 6**

  - **ItaniumImage**  - **/FUNCTIONPADMIN： 16**

  如需詳細資訊，請參閱 [/FUNCTIONPADMIN (建立可線上修補映射) ](/cpp/build/reference/functionpadmin-create-hotpatchable-image)。

- **DataExecutionPrevention**

  選擇性的 **布林值** 參數。

  如果是 `true`，即表示可執行檔已經過測試，可與 Windows 資料執行防止功能相容。

  如需詳細資訊，請參閱 [/NXCOMPAT (與資料執行防止相容)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention)。

- **DelayLoadDLLs**

  選擇性的 **String []** 參數。

  此參數會導致 DLL「延遲載入」。 指定要延遲載入的 DLL 名稱。

  如需詳細資訊，請參閱 [/DELAYLOAD (延遲載入匯入)](/cpp/build/reference/delayload-delay-load-import)。

- **DelaySign**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會部分簽署組件。 根據預設，此值是 `false`。

  如需詳細資訊，請參閱 [/DELAYSIGN (部分簽署組件)](/cpp/build/reference/delaysign-partially-sign-an-assembly)。

- **驅動程式**

  選擇性的 **字串** 參數。

  指定此參數來建置 Windows NT 核心模式驅動程式。

  指定下列其中一個值；每個值會分別對應至一個連結器選項。

  - **NotSet** - *\<none>*

  - **驅動程式**  - **/Driver**

  - **UpOnly**  - **/DRIVER： UPONLY**

  - **WDM**  - **/DRIVER： WDM**

  如需詳細資訊，請參閱 [/DRIVER (Windows NT 核心模式驅動程式) ](/cpp/build/reference/driver-windows-nt-kernel-mode-driver)。

- **EmbedManagedResourceFile**

  選擇性的 **String []** 參數。

  在組件中內嵌資源檔。 指定所需的資源檔名稱。 選擇性地指定邏輯名稱 (用來載入資源) 及 **PRIVATE** 選項 (表示在組件資訊清單中資源檔為私用的)。

  如需詳細資訊，請參閱 [/ASSEMBLYRESOURCE (內嵌 managed 資源) ](/cpp/build/reference/assemblyresource-embed-a-managed-resource)。

- **EnableCOMDATFolding**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會啟用完全相同的 COMDAT 摺疊。

  如需詳細資訊，請參閱 [/OPT (最佳化)](/cpp/build/reference/opt-optimizations) 的 `ICF[= iterations]` 引數。

- **EnableUAC**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會指定要在程式資訊清單中內嵌使用者帳戶控制 (UAC) 資訊。

  如需詳細資訊，請參閱 [/MANIFESTUAC (在資訊清單中內嵌 UAC 資訊)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)。

- **EntryPointSymbol**

  選擇性的 **字串** 參數。

  指定進入點函式作為 *.exe* 檔案或 DLL 的開始位址。 指定函式名稱做為參數值。

  如需詳細資訊，請參閱 [/ENTRY (進入點符號) ](/cpp/build/reference/entry-entry-point-symbol)。

- **FixedBaseAddress**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會建立僅可在其慣用基底位址載入的程式或 DLL。

  如需詳細資訊，請參閱 [/FIXED (固定基底位址) ](/cpp/build/reference/fixed-fixed-base-address)。

- **ForceFileOutput**

  選擇性的 **字串** 參數。

  告訴連結器即使參考到未定義或多次定義的符號，也要建立有效的 *.exe* 檔案或 DLL。

  指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **已啟用**  - **/Force**

  - **MultiplyDefinedSymbolOnly**  - **/FORCE：多重**

  - **UndefinedSymbolOnly**  - **/FORCE：無法解析**

  如需詳細資訊，請參閱 [/FORCE (強制檔案輸出)](/cpp/build/reference/force-force-file-output)。

- **ForceSymbolReferences**

  選擇性的 **String []** 參數。

  此參數會告訴連結器，將指定的符號加入符號表。

  如需詳細資訊，請參閱 [/INCLUDE (強制符號參考)](/cpp/build/reference/include-force-symbol-references)。

- **FunctionOrder**

  選擇性的 **字串** 參數。

  此參數會以預先定義的順序將指定的封裝函式 (COMDAT) 放入映像中，來最佳化您的程式。

  如需詳細資訊，請參閱依 [序) 的/order (Put 函數 ](/cpp/build/reference/order-put-functions-in-order)。

- **GenerateDebugInformation**

  選擇性的 **布林值** 參數。

  若為 `true`，即會建立 *.exe* 檔或 DLL 的偵錯資訊。

  如需詳細資訊，請參閱 [/debug (產生) 的 DEBUG 資訊 ](/cpp/build/reference/debug-generate-debug-info)。

- **GenerateManifest**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會建立並存資訊清單檔。

  如需詳細資訊，請參閱 [/MANIFEST (建立並存組件資訊清單)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest)。

- **GenerateMapFile**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會建立「對應檔」。 對應檔的副檔名為 *. map*。

  如需詳細資訊，請參閱 [/MAP (產生 ](/cpp/build/reference/map-generate-mapfile)對應檔) 。

- **HeapCommitSize**

  選擇性的 **字串** 參數。

  指定一次要配置的實體記憶體數量。

  如需詳細資訊，請參閱 [/HEAP (設定堆積大小)](/cpp/build/reference/heap-set-heap-size) 中的 `commit` 引數。 另請參閱 **HeapReserveSize** 參數。

- **HeapReserveSize**

  選擇性的 **字串** 參數。

  指定虛擬記憶體中的堆積配置總和。

  如需詳細資訊，請參閱 [/HEAP (設定堆積大小)](/cpp/build/reference/heap-set-heap-size) 中的 `reserve` 引數。 另請參閱此表格中的 **HeapCommitSize** 參數。

- **IgnoreAllDefaultLibraries**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會告訴連結器在解析外部參考時，從它搜尋的程式庫清單中移除一或多個預設程式庫。

  如需詳細資訊，請參閱 [/NODEFAULTLIB (忽略程式庫)](/cpp/build/reference/nodefaultlib-ignore-libraries)。

- **IgnoreEmbeddedIDL**

  選擇性的 **布林值** 參數。

  若為 `true`，即會指定不應將原始程式碼中的任何 IDL 屬性處理到 *.idl* 檔案中。

  如需詳細資訊，請參閱 [/IGNOREIDL (不要將屬性處理至 MIDL 中)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl)。

- **IgnoreImportLibrary**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會指定不要將此組態所產生的程式庫匯入相依專案。

  此參數並未對應至連結器選項。

- **IgnoreSpecificDefaultLibraries**

  選擇性的 **String []** 參數。

  指定要忽略的一或多個預設程式庫名稱。 使用分號分隔多個程式庫。

  如需詳細資訊，請參閱 [/NODEFAULTLIB (忽略程式庫)](/cpp/build/reference/nodefaultlib-ignore-libraries)。

- **ImageHasSafeExceptionHandlers**

  選擇性的 **布林值** 參數。

  如果是 `true`，連結器只有在它也可以產生映像的安全例外狀況處理常式表格時，才會產生該映像。

  如需詳細資訊，請參閱 [/SAFESEH (映射有安全的例外狀況處理常式) ](/cpp/build/reference/safeseh-image-has-safe-exception-handlers)。

- **ImportLibrary**

  使用者指定的匯入程式庫名稱，可取代預設的程式庫名稱。

  如需詳細資訊，請參閱 [/IMPLIB (名稱匯入程式庫) ](/cpp/build/reference/implib-name-import-library)。

- **KeyContainer**

  選擇性的 **字串** 參數。

  包含已簽署組件之金鑰的容器。

  如需詳細資訊，請參閱 [/KEYCONTAINER (指定要簽署元件) 的金鑰容器 ](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly)。 另請參閱此表格中的 **KeyFile** 參數。

- **KeyFile**

  選擇性的 **字串** 參數。

  指定包含已簽署組件之金鑰的容器。

  如需詳細資訊，請參閱 [/KEYFILE (指定) 簽署元件的金鑰或金鑰 ](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly)組。 另請參閱 **KeyContainer** 參數。

- **LargeAddressAware**

  選擇性的 **布林值** 參數。

  如果是 `true`，應用程式就能處理大於 2 GB 的位址。

  如需詳細資訊，請參閱 [/LARGEADDRESSAWARE (處理大型記憶體位址)](/cpp/build/reference/largeaddressaware-handle-large-addresses)。

- **LinkDLL**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會建置 DLL 做為主要輸出檔。

  如需詳細資訊，請參閱 [/DLL (建置 DLL)](/cpp/build/reference/dll-build-a-dll)。

- **LinkErrorReporting**

  選擇性的 **字串** 參數。

  讓您可將內部編譯器錯誤 (ICE) 資訊直接提供給 Microsoft。

  指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **NoErrorReport** - **/ERRORREPORT:NONE**

  - **PromptImmediately** - **/ERRORREPORT:PROMPT**

  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**

  - **SendErrorReport** - **/ERRORREPORT:SEND**

  如需詳細資訊，請參閱 [/ERRORREPORT (回報內部連結器錯誤)](/cpp/build/reference/errorreport-report-internal-linker-errors)。

- **LinkIncremental**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會啟用累加連結。

  如需詳細資訊，請參閱 [/INCREMENTAL (以累加方式連結)](/cpp/build/reference/incremental-link-incrementally)。

- **LinkLibraryDependencies**

  選擇性的 **布林值** 參數。

  若為 `true`，會指定要自動連結專案相依性的程式庫輸出。

  此參數並未對應至連結器選項。

- **LinkStatus**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會指定連結器要顯示進度指示器，以顯示連結完成的百分比。

  如需詳細資訊，請參閱 `STATUS` [/Ltcg (連結時產生程式碼) ](/cpp/build/reference/ltcg-link-time-code-generation)的引數。

- **LinkTimeCodeGeneration**

  選擇性的 **字串** 參數。

  指定特性指引最佳化的選項。

  指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **預設** - *\<none>*

  - **UseLinkTimeCodeGeneration**  - **/Ltcg**

  - **PGInstrument**  - **/Ltcg： PGInstrument**

  - **PGOptimization**  - **/Ltcg： PGOptimize**

  - **PGUpdate**

    \- **/LTCG:PGUpdate**

  如需詳細資訊，請參閱 [/LTCG (連結時產生程式碼)](/cpp/build/reference/ltcg-link-time-code-generation)。

- **ManifestFile**

  選擇性的 **字串** 參數。

  將預設的資訊清單檔案名稱變更為指定的檔案名稱。

  如需詳細資訊，請參閱 [/MANIFESTFILE (命名資訊清單檔) ](/cpp/build/reference/manifestfile-name-manifest-file)。

- **MapExports**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會告訴連結器在對應檔中包含匯出的函式。

  如需詳細資訊，請參閱 `EXPORTS` /MAPINFO (的引數包含對應檔 [中的資訊) ](/cpp/build/reference/mapinfo-include-information-in-mapfile)。

- **MapFileName**

  選擇性的 **字串** 參數。

  將預設的對應檔名稱變更為指定的檔案名稱。

- **MergedIDLBaseFileName**

  選擇性的 **字串** 參數。

  指定 .idl 檔案的檔名和副檔名。

  如需詳細資訊，請參閱 [/IDLOUT (將 MIDL 輸出檔命名) ](/cpp/build/reference/idlout-name-midl-output-files)。

- **MergeSections**

  選擇性的 **字串** 參數。

  結合映像中的區段。 請指定 `from-section=to-section`。

  如需詳細資訊，請參閱 [/merge (將區段合併) ](/cpp/build/reference/merge-combine-sections)。

- **MidlCommandFile**

  選擇性的 **字串** 參數。

  指定包含 MIDL 命令列選項的檔案名稱。

  如需詳細資訊，請參閱 [/MIDL (指定 MIDL 命令列選項) ](/cpp/build/reference/midl-specify-midl-command-line-options)。

- **MinimumRequiredVersion**

  選擇性的 **字串** 參數。

  指定子系統的最小必要版本。 引數為範圍從 0 到 65535 的十進位數字。

- **ModuleDefinitionFile**

  選擇性的 **字串** 參數。

  指定[模組定義檔](/cpp/build/reference/module-definition-dot-def-files)的名稱。

  如需詳細資訊，請參閱 [/DEF (指定模組定義檔) ](/cpp/build/reference/def-specify-module-definition-file)。

- **MSDOSStubFileName**

  選擇性的 **字串** 參數。

  將指定的 MS-DOS Stub 程式附加至 Win32 程式。

  如需詳細資訊，請參閱 [/STUB (MS-DOS 存根檔案名) ](/cpp/build/reference/stub-ms-dos-stub-file-name)。

- **NoEntryPoint**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會指定僅含資源的 DLL。

  如需詳細資訊，請參閱 [/NOENTRY (沒有進入點) ](/cpp/build/reference/noentry-no-entry-point)。

- **ObjectFiles**

  隱含的 **String []** 參數。

  指定連結的目的檔。

- **OptimizeReferences**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會排除從未參考的函式和/或資料。

  如需詳細資訊，請參閱 [/OPT (最佳化)](/cpp/build/reference/opt-optimizations) 中的 `REF` 引數。

- **OutputFile**

  選擇性的 **字串** 參數。

  覆寫連結器所建立程式的預設名稱和位置。

  如需詳細資訊，請參閱 [/out (輸出檔名稱) ](/cpp/build/reference/out-output-file-name)。

- **PerUserRedirection**

  選擇性的 **布林值** 參數。

  如果是 `true` 且已啟用登錄輸出，即會強制將登錄寫入 **HKEY_CLASSES_ROOT**，使其重新導向到 **HKEY_CURRENT_USER**。

- **PreprocessOutput**

  選擇性的 `ITaskItem[]` 參數。

  定義工作可以耗用和發出的前置處理器輸出項目的陣列。

- **PreventDllBinding**

  選擇性的 **布林值** 參數。

  若為 `true`，即會指示 *Bind.exe* 不應該繫結連結的映像。

  如需詳細資訊，請參閱 [/ALLOWBIND (防止 DLL ](/cpp/build/reference/allowbind-prevent-dll-binding)系結) 。

- **設定檔**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會產生可與 **效能工具** 分析工具搭配使用的輸出檔。

  如需詳細資訊，請參閱 [/PROFILE (效能工具分析工具)](/cpp/build/reference/profile-performance-tools-profiler)。

- **ProfileGuidedDatabase**

  選擇性的 **字串** 參數。

  指定將用來保存執行中程式相關資訊的 *.pgd 檔案名。*

  如需詳細資訊，請參閱 [/PGD (指定特性指引最佳化資料庫)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations)。

- **ProgramDatabaseFile**

  選擇性的 **字串** 參數。

  指定連結器建立的程式資料庫 (PDB) 名稱。

  如需詳細資訊，請參閱 [/PDB (使用程式資料庫)](/cpp/build/reference/pdb-use-program-database)。

- **RandomizedBaseAddress**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會產生可執行映像檔，其可使用 Windows 的「位址空間配置隨機載入」(ASLR) 功能，於載入時隨機重定基底。

  如需詳細資訊，請參閱 [/DYNAMICBASE (使用位址空間配置隨機載入)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization)。

- **RegisterOutput**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會登錄此組建的主要輸出。

- **SectionAlignment**

  選擇性的 **Integer** 參數。

  指定程式線性位址空間內每個區段的對應儲存方式。 參數值是一個單位數的位元組且為 2 的次方。

  如需詳細資訊，請參閱 [/ALIGN (區段對齊)](/cpp/build/reference/align-section-alignment)。

- **SetChecksum**

  選擇性的 **布林值** 參數。

  若為 `true`，即會在 *.exe* 檔案的標頭中設定總和檢查碼。

  如需詳細資訊，請參閱 [/RELEASE (設定總和檢查碼) ](/cpp/build/reference/release-set-the-checksum)。

- **ShowProgress**

  選擇性的 **字串** 參數。

  指定連結作業的進度報表詳細資訊。

  指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **NotSet** - *\<none>*

  - **LinkVerbose**  - **/Verbose**

  - **LinkVerboseLib**  - **/Verbose： Lib**

  - **LinkVerboseICF**  - **/VERBOSE： ICF**

  - **LinkVerboseREF**  - **/VERBOSE： REF**

  - **LinkVerboseSAFESEH**  - **/VERBOSE： SAFESEH**

  - **LinkVerboseCLR**  - **/VERBOSE： CLR**

  如需詳細資訊，請參閱 [/VERBOSE (列印進度訊息)](/cpp/build/reference/verbose-print-progress-messages)。

- **來源**

  必要的 `ITaskItem[]` 參數。

  定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。

- **SpecifySectionAttributes**

  選擇性的 **字串** 參數。

  指定區段的屬性。 這會覆寫在編譯區段的 *.obj* 檔案時所設定的屬性。

  如需詳細資訊，請參閱 [/SECTION (指定區段屬性) ](/cpp/build/reference/section-specify-section-attributes)。

- **StackCommitSize**

  選擇性的 **字串** 參數。

  指定在配置額外的記憶體時，每個配置中的實體記憶體數量。

  如需詳細資訊，請參閱 [/STACK (堆疊配置)](/cpp/build/reference/stack-stack-allocations) 的 `commit` 引數。

- **StackReserveSize**

  選擇性的 **字串** 參數。

  指定虛擬記憶體中的堆疊配置大小總和。

  如需詳細資訊，請參閱 [/STACK (堆疊配置)](/cpp/build/reference/stack-stack-allocations) 的 `reserve` 引數。

- **StripPrivateSymbols**

  選擇性的 **字串** 參數。

  建立第二個程式資料庫 (PDB) 檔，以省略您不要散發給客戶的符號。 指定第二個 PDB 檔的名稱。

  如需詳細資訊，請參閱 [/PDBSTRIPPED (去除私用符號) ](/cpp/build/reference/pdbstripped-strip-private-symbols)。

- **子系統**

  選擇性的 **字串** 參數。

  指定可執行檔的環境。

  指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **NotSet** - *\<none>*

  - **主控台** - **/SUBSYSTEM:CONSOLE**

  - **Windows** - **/SUBSYSTEM:WINDOWS**

  - **原生** - **/SUBSYSTEM:NATIVE**

  - **EFI 應用程式** - **/SUBSYSTEM:EFI_APPLICATION**

  - **EFI 開機服務驅動程式** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**

  - **EFI ROM** - **/SUBSYSTEM:EFI_ROM**

  - **EFI 執行階段** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**

  - **WindowsCE**  - **/SUBSYSTEM： WINDOWSCE**

  - **POSIX** - **/SUBSYSTEM:POSIX**

  如需詳細資訊，請參閱 [/SUBSYSTEM (指定子系統)](/cpp/build/reference/subsystem-specify-subsystem)。

- **SupportNobindOfDelayLoadedDLL**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會告知連結器不要在最終映像中包含可繫結的匯入位址表 (IAT)。

  如需詳細資訊，請參閱 `NOBIND` [/DELAY (延遲載入匯入設定) ](/cpp/build/reference/delay-delay-load-import-settings)的引數。

- **SupportUnloadOfDelayLoadedDLL**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會告知延遲載入 Helper 函式，支援明確卸載 DLL。

  如需詳細資訊，請參閱 `UNLOAD` [/DELAY (延遲載入匯入設定) ](/cpp/build/reference/delay-delay-load-import-settings)的引數。

- **SuppressStartupBanner**

  選擇性的 **布林值** 參數。

  如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。

  如需詳細資訊，請參閱 [/NOLOGO (隱藏程式啟始資訊) (連結器)](/cpp/build/reference/nologo-suppress-startup-banner-linker)。

- **SwapRunFromCD**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會告知作業系統要先將連結器輸出複製到交換檔，然後從該處執行映像。

  如需詳細資訊，請參閱 `CD` [/SWAPRUN (將連結器輸出載入至交換檔) ](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)的引數。 另請參閱 **SwapRunFromNET** 參數。

- **SwapRunFromNET**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會告知作業系統要先將連結器輸出複製到交換檔，然後從該處執行映像。

  如需詳細資訊，請參閱 `NET` [/SWAPRUN (將連結器輸出載入至交換檔) ](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)的引數。 另請參閱此表格中的 **SwapRunFromCD** 參數。

- **TargetMachine**

  選擇性的 **字串** 參數。

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

  如需詳細資訊，請參閱 [/MACHINE (指定目標平臺) ](/cpp/build/reference/machine-specify-target-platform)。

- **TerminalServerAware**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會在程式映像的選擇性標頭內 IMAGE_OPTIONAL_HEADER DllCharacteristics 欄位中設定旗標。 設定此旗標時，終端機伺服器將不會對應用程式進行某些變更。

  如需詳細資訊，請參閱 [/TSAWARE (建立終端伺服器感知應用程式) ](/cpp/build/reference/tsaware-create-terminal-server-aware-application)。

- **TrackerLogDirectory**

  選擇性的 **字串** 參數。

  指定追蹤器記錄檔的目錄。

- **TreatLinkerWarningAsErrors**

  選擇性的 **布林值** 參數。

  如果是 `true`，導致在連結器產生警告時，不會產生任何輸出檔。

  如需詳細資訊，請參閱 [/WX (將連結器警告視為錯誤)](/cpp/build/reference/wx-treat-linker-warnings-as-errors)。

- **TurnOffAssemblyGeneration**

  選擇性的 **布林值** 參數。

  如果是 `true`，即會為目前的輸出檔建立不含 .NET Framework 組件的映像。

  如需詳細資訊，請參閱 [/NOASSEMBLY (建立 MSIL 模組) ](/cpp/build/reference/noassembly-create-a-msil-module)。

- **TypeLibraryFile**

  選擇性的 **字串** 參數。

  指定 *.tlb* 檔案的檔案名和副檔名。 指定檔案名稱，或路徑和檔案名稱。

  如需詳細資訊，請參閱 [/TLBOUT (命名 .tlb 檔)](/cpp/build/reference/tlbout-name-dot-tlb-file)。

- **TypeLibraryResourceID**

  選擇性的 **Integer** 參數。

  為連結器建立的類型程式庫指定使用者指定的值。 指定範圍從 1 到 65535 的值。

  如需詳細資訊，請參閱 [/TLBID (指定 TypeLib 的資源識別碼) ](/cpp/build/reference/tlbid-specify-resource-id-for-typelib)。

- **UACExecutionLevel**

  選擇性的 **字串** 參數。

  指定在啟用使用者帳戶控制的情況下執行時，應用程式要求的執行層級。

  指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **AsInvoker** - `level='asInvoker'`

  - **HighestAvailable** - `level='highestAvailable'`

  - **RequireAdministrator** - `level='requireAdministrator'`

  如需詳細資訊，請參閱 [/MANIFESTUAC (在資訊清單中內嵌 UAC 資訊)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest) 的 `level` 引數。

- **UACUIAccess**

  選擇性的 **布林值** 參數。

  如果是 `true`，應用程式即會略過使用者介面保護層級，並將輸入放到桌面上更高權限的視窗；否則為 `false`。

  如需詳細資訊，請參閱 [/MANIFESTUAC (在資訊清單中內嵌 UAC 資訊)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest) 的 `uiAccess` 引數。

- **UseLibraryDependencyInputs**

  選擇性的 **布林值** 參數。

  如果是 `true`，連結專案相依性的程式庫輸出時，會使用管理員工具的輸入而非程式庫檔案本身。

- **版本**

  選擇性的 **字串** 參數。

  將版本號碼放入 *.exe* 或 *.dll* 檔案的標頭。 請指定 "`major[.minor]`"。 `major` 和 `minor` 引數都是範圍從 0 到 65535 的十進位數字。

  如需詳細資訊，請參閱 [/VERSION (版本資訊) ](/cpp/build/reference/version-version-information)。

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)

---
title: CL 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cea2e191c5a85b8aac592e4e438eaa3b93bcd4f7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912765"
---
# <a name="cl-task"></a>CL 工作
包裝 Visual C++ 編譯器工具 *cl.exe*。 編譯器會產生可執行檔 (*.exe*)、動態連結程式庫 (*.dll*) 檔案或程式碼模組 (*.netmodule*) 檔案。 如需詳細資訊，請參閱[編譯器選項](/cpp/build/reference/compiler-options)。  
  
## <a name="parameters"></a>參數  
 下列清單描述 **CL** 工作的參數。 大部分的工作參數以及數組參數會對應到命令列選項。  
  
- **AdditionalIncludeDirectories**  
  
   選擇性的 String[] 參數。  
  
   將目錄加入至要搜尋 include 檔案的目錄清單。  
  
   如需詳細資訊，請參閱 [/I (其他 Include 目錄)](/cpp/build/reference/i-additional-include-directories)。  
  
- **AdditionalOptions**  
  
   選擇性的 String 參數。  
  
   命令列選項清單。 例如，"/\<option1> /\<option2> /\<option#>"。 使用此參數，來指定任何其他工作參數未表示的命令列選項。  
  
   如需詳細資訊，請參閱[編譯器選項](/cpp/build/reference/compiler-options)。  
  
- **AdditionalUsingDirectories**

   選擇性的 String[] 參數。  
  
   指定編譯器要搜尋的目錄，以解析傳遞給 **#using** 指示詞的檔案參考。  
  
   如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](/cpp/build/reference/ai-specify-metadata-directories)。  
  
- **AlwaysAppend**  
  
   選擇性的 String 參數。  
  
   一律會在命令列上發出的字串。 其預設值為 "**/c**"。  
  
- **AssemblerListingLocation**  
  
   建立包含組譯碼的清單檔案。  
  
   如需詳細資訊，請參閱 [/FA、/Fa (清單檔)](/cpp/build/reference/fa-fa-listing-file) 中的 **/Fa** 選項。  
  
- **AssemblerOutput**  
  
   選擇性的 String 參數。  
  
   建立包含組譯碼的清單檔案。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **NoListing** - *\<none>*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** - **/FAc**  
  
  - **AssemblyAndSourceCode** - **/FAs**  
  
  - **All** - **/FAcs**  
  
    如需詳細資訊，請參閱 [/FA、/Fa (清單檔)](/cpp/build/reference/fa-fa-listing-file) 中的 **/FA**、**/FAc**、**/FAs** 及 **/FAcs** 選項。  
  
- **BasicRuntimeChecks**  
  
   選擇性的 String 參數。  
  
   搭配 [runtime_checks](/cpp/preprocessor/runtime-checks) pragma 來啟用和停用執行階段錯誤檢查功能。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Default** -                          *\<none>*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **/RTCu**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    如需詳細資訊，請參閱 [/RTC (執行階段錯誤檢查)](/cpp/build/reference/rtc-run-time-error-checks)。  
  
- **BrowseInformation**  
  
   選擇性的 Boolean 參數。  
  
   如果是 `true`，即會建立瀏覽資訊檔。  
  
   如需詳細資訊，請參閱 [/FR、/Fr (建立 .sbr 檔案)](/cpp/build/reference/fr-fr-create-dot-sbr-file) 中的 **/FR** 選項。  
  
- **BrowseInformationFile**  
  
   選擇性的 String 參數。  
  
   指定瀏覽資訊檔的檔案名稱。  
  
   如需詳細資訊，請參閱此表格中的 **BrowseInformation** 參數，另請參閱 [/FR、/Fr (建立 .sbr 檔案)](/cpp/build/reference/fr-fr-create-dot-sbr-file)。  
  
- **BufferSecurityCheck**  
  
   選擇性的 Boolean 參數。  
  
   如果是 `true`，即會偵測某些會覆寫傳回位址的緩衝區滿溢，此為用來惡意探索不會強制執行緩衝區大小限制之程式碼的常用技巧。  
  
   如需詳細資訊，請參閱 [/GS (緩衝區安全性檢查)](/cpp/build/reference/gs-buffer-security-check)。  
  
- **BuildingInIDE**  
  
   選擇性的 Boolean 參數。  
  
   如果是 `true`，即表示 IDE 會叫用 **MSBuild**。 否則，會在命令列上叫用 **MSBuild**。  
  
- **CallingConvention**  
  
   選擇性的 String 參數。  
  
   指定呼叫慣例，決定將函式引數推入堆疊的順序、呼叫端函式或呼叫的函式是否會在呼叫結尾從堆疊中移除引數，以及編譯器用來識別個別函式的名稱裝飾慣例。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Cdecl** - **/Gd**  
  
  - **FastCall** -                          **/Gr**  
  
  - **StdCall** -                          **/Gz**  
  
    如需詳細資訊，請參閱 [/Gd、/Gr、/Gv、/Gz (呼叫慣例)](/cpp/build/reference/gd-gr-gv-gz-calling-convention)。  
  
- **CompileAs**  
  
   選擇性的 String 參數。  
  
   指定是否要將輸入檔案編譯為 C 或 C++ 原始程式檔。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Default** - *\<none>*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    如需詳細資訊，請參閱 [/Tc、/Tp、/TC、/TP (指定原始程式檔類型)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type)。  
  
- **CompileAsManaged**  
  
   選擇性的 String 參數。  
  
   可讓應用程式和元件使用 Common Language Runtime (CLR) 中的功能。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **false** - *\<none>*  
  
  - **true** - **/clr**  
  
  - **Pure** - **/clr:pure**  
  
  - **Safe** - **/clr:safe**  
  
  - **OldSyntax** - **/clr:oldSyntax**  
  
    如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](/cpp/build/reference/clr-common-language-runtime-compilation)。  
  
- **CreateHotpatchableImage**  
  
   選擇性的 Boolean 參數。  
  
   如果是 `true`，則會告知編譯器來準備「Hotpatch 功能」所需的映像。 此參數會確認每個函式的第一個指令都是兩個位元組，這是 Hotpatch 功能所需要的。  
  
   如需詳細資訊，請參閱 [/hotpatch (建立可進行 Hotpatch 的映像)](/cpp/build/reference/hotpatch-create-hotpatchable-image)。  
  
- **DebugInformationFormat**  
  
   選擇性的 String 參數。  
  
   選取為程式所建立的偵錯資訊類型，以及此資訊要保留於目的檔 (.obj) 還是程式資料庫 (PDB) 中。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **OldStyle** - **/Z7**  
  
  - **ProgramDatabase** - **/Zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    如需詳細資訊，請參閱 [/Z7、/Zi、/ZI (偵錯資訊格式)](/cpp/build/reference/z7-zi-zi-debug-information-format)。  
  
- **DisableLanguageExtensions**  
  
   選擇性的 Boolean 參數。  
  
   如果是 **true**，即會告訴編譯器，針對與 ANSI C 或 ANSI C++ 不相容的語言建構發出錯誤。  
  
   如需詳細資訊，請參閱 [/Za、/Ze (停用語言延伸模組)](/cpp/build/reference/za-ze-disable-language-extensions) 中的 **/Za** 選項。  
  
- **DisableSpecificWarnings**  
  
   選擇性的 String[] 參數。  
  
   停用以分號分隔的清單中所指定的警告編號。  
  
   如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](/cpp/build/reference/compiler-option-warning-level) 中的 `/wd` 選項。  
  
- **EnableEnhancedInstructionSet**  
  
   選擇性的 String 參數。  
  
   指定產生程式碼的架構，來使用 Streaming SIMD Extensions (SSE) 和 Streaming SIMD Extensions 2 (SSE2) 指令。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
    如需詳細資訊，請參閱 [/arch (x86)](/cpp/build/reference/arch-x86)。  
  
- **EnableFiberSafeOptimizations**  
  
   選擇性的 Boolean 參數。  
  
   如果是 `true`，即會對使用靜態執行緒區域儲存區配置的資料 (也就是使用 `__declspec(thread)` 配置的資料) 支援 Fiber 安全。  
  
   如需詳細資訊，請參閱 [/GT (支援 Fiber-Safe 執行緒區域儲存區)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage)。  
  
- **EnablePREfast**  
  
   選擇性的 Boolean 參數。  
  
   如果是 `true`，即會啟用程式碼分析。  
  
   如需詳細資訊，請參閱 [/analyze (程式碼分析)](/cpp/build/reference/analyze-code-analysis)。  
  
- **ErrorReporting**  
  
   選擇性的 String 參數。  
  
   讓您可將內部編譯器錯誤 (ICE) 資訊直接提供給 Microsoft。 根據預設，IDE 組建中的設定是 **Prompt**，而命令列組建中的設定是 **Queue**。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **None** - **/errorReport:none**  
  
  - **Prompt** - **/errorReport:prompt**  
  
  - **Queue** - **/errorReport:queue**  
  
  - **Send** - **/errorReport:send**  
  
    如需詳細資訊，請參閱 [/errorReport (回報編譯器內部錯誤)](/cpp/build/reference/errorreport-report-internal-compiler-errors)。  
  
- **ExceptionHandling**  
  
   選擇性的 String 參數。  
  
   指定編譯器所使用的例外狀況處理模型。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **false** - *\<none>*  
  
  - **Async** - **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    如需詳細資訊，請參閱 [/EH (例外狀況處理模型)](/cpp/build/reference/eh-exception-handling-model)。  
  
- **ExpandAttributedSource**  
  
   選擇性的 Boolean 參數。  
  
   如果是 `true`，即會建立清單檔案，並展開已加入原始程式碼的屬性。  
  
   如需詳細資訊，請參閱 [/Fx (合併插入的程式碼)](/cpp/build/reference/fx-merge-injected-code)。  
  
- **FavorSizeOrSpeed**  
  
   選擇性的 String 參數。  
  
   指定偏好程式碼大小，還是程式碼的速度。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Neither** - *\<none>*  
  
  - **Size** - **/Os**  
  
  - **Speed** - **/Ot**  
  
    如需詳細資訊，請參閱 [/Os、/Ot (偏好小的程式碼、偏好快的程式碼)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code)。  
  
- **FloatingPointExceptions**  
  
   選擇性的 Boolean 參數。  
  
   如果是 `true`，即會啟用可靠的浮點例外狀況模型。 觸發例外狀況之後，將會立即引發例外狀況。  
  
   如需詳細資訊，請參閱 [/fp (指定浮點行為)](/cpp/build/reference/fp-specify-floating-point-behavior) 中的 /**fp:except** 選項。  
  
- **FloatingPointModel**  
  
   選擇性的 String 參數。  
  
   設定浮點模型。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Precise** - **/fp:precise**  
  
  - **Strict** - **/fp:strict**  
  
  - **Fast** - **/fp:fast**  
  
    如需詳細資訊，請參閱 [/fp (指定浮點行為)](/cpp/build/reference/fp-specify-floating-point-behavior)。  
  
- **ForceConformanceInForLoopScope**  
  
   選擇性的 Boolean 參數。  
  
   如果是 `true`，即會在使用 Microsoft 擴充功能 ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)) 的 [for](/cpp/cpp/for-statement-cpp) 迴圈中實作標準的 C++ 行為。  
  
   如需詳細資訊，請參閱 [/Zc:forScope (強制 for 迴圈範圍中的一致性)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope)。  
  
- **ForcedIncludeFiles**  
  
   選擇性的 `String[]` 參數。  
  
   導致前置處理器要處理一或多個指定的標頭檔。  
  
   如需詳細資訊，請參閱 [/FI (指定強制的包含檔)](/cpp/build/reference/fi-name-forced-include-file)。  
  
- **ForcedUsingFiles**  
  
   選擇性的 **String[]** 參數。  
  
   導致前置處理器要一或多個指定的 **#using** 檔案。  
  
   如需詳細資訊，請參閱 [/FU (命名強制的 #using 檔案)](/cpp/build/reference/fu-name-forced-hash-using-file)。  
  
- **FunctionLevelLinking**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會讓編譯器以封裝函式 (COMDAT) 的格式封裝個別的函式。  
  
   如需詳細資訊，請參閱 [/Gy (啟用函式階層連結)](/cpp/build/reference/gy-enable-function-level-linking)。  
  
- **GenerateXMLDocumentationFiles**  
  
   選擇性的 `Boolean` 參數。  
  
   若為 `true`，即會導致編譯器處理原始程式碼檔案中的文件註解，並針對每個具有文件註解的原始程式碼檔案建立 *.xdc* 檔案。  
  
   如需詳細資訊，請參閱 [/doc (處理文件註解) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp)。 另請參閱此表格中的 **XMLDocumentationFileName** 參數。  
  
- **IgnoreStandardIncludePath**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會防止編譯器在 PATH 和 INCLUDE 環境變數中指定的目錄內搜尋 Include 檔。  
  
   如需詳細資訊，請參閱 [/X (忽略標準 Include 路徑)](/cpp/build/reference/x-ignore-standard-include-paths)。  
  
- **InlineFunctionExpansion**  
  
   選擇性的 **String** 參數。  
  
   選取組建的內嵌函式展開等級。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Default** - *\<none>*  
  
  - **Disabled** - **/Ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** - **/Ob2**  
  
    如需詳細資訊，請參閱 [/Ob (內嵌函式展開)](/cpp/build/reference/ob-inline-function-expansion)。  
  
- **IntrinsicFunctions**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會使用內建函式或特殊形式的函式來取代某些函式呼叫，以協助讓您的應用程式執行得更快。  
  
   如需詳細資訊，請參閱 [/Oi (產生內建函式)](/cpp/build/reference/oi-generate-intrinsic-functions)。  
  
- **MinimalRebuild**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會啟用最少重建，其可判定是否必須重新編譯包含已變更 C++ 類別定義 (儲存於標頭檔 (.h)) 的 C++ 原始程式檔。  
  
   如需詳細資訊，請參閱 [/Gm (啟用最少重建)](/cpp/build/reference/gm-enable-minimal-rebuild) 。  
  
- **MultiProcessorCompilation**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會使用多個處理器來編譯。 這個參數會針對電腦上每個有效的處理器建立處理序。  
  
   如需詳細資訊，請參閱 [/MP (使用多處理序建置)](/cpp/build/reference/mp-build-with-multiple-processes)。 另請參閱此表格中的 **ProcessorNumber** 參數。  
  
- **ObjectFileName**  
  
   選擇性的 **String** 參數。  
  
   指定要使用的目的檔 (.obj) 名稱或目錄，而不使用預設值。  
  
   如需詳細資訊，請參閱 [/Fo (目的檔名稱)](/cpp/build/reference/fo-object-file-name)。  
  
- **ObjectFiles**  
  
   選擇性的 **String[]** 參數。  
  
   目的檔清單。  
  
- **OmitDefaultLibName**  
  
   選擇性的 `Boolean` 參數。  
  
   若為 `true`，即會在目的檔 (*.obj*) 中省略預設的 C 執行階段程式庫名稱。 根據預設，編譯器會將程式庫名稱置入 .obj 檔案中，以將連結器導向至正確的程式庫。  
  
   如需詳細資訊，請參閱 [/Zl (省略預設程式庫名稱)](/cpp/build/reference/zl-omit-default-library-name)。  
  
- **OmitFramePointers**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會在呼叫堆疊上隱藏框架指標的建立。  
  
   如需詳細資訊，請參閱 [/Oy (框架指標省略)](/cpp/build/reference/oy-frame-pointer-omission)。  
  
- **OpenMPSupport**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會導致編譯器處理 OpenMP 子句和指示詞。  
  
   如需詳細資訊，請參閱 [/openmp (啟用 OpenMP 2.0 支援)](/cpp/build/reference/openmp-enable-openmp-2-0-support)。  
  
- **Optimization**  
  
   選擇性的 **String** 參數。  
  
   指定各種適用於速度和規模的程式碼最佳化。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Disabled** - **/Od**  
  
  - **MinSpace** - **/O1**  
  
  - **MaxSpeed** - **/O2**  
  
  - **Full** - **/Ox**  
  
    如需詳細資訊，請參閱 [/O 選項 (最佳化程式碼)](/cpp/build/reference/o-options-optimize-code)。  
  
- **PrecompiledHeader**  
  
   選擇性的 **String** 參數。  
  
   在建置期間建立或使用先行編譯標頭檔 (.pch)。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **NotUsing** - *\<none>*  
  
  - **Create** - **/Yc**  
  
  - **Use** - **/Yu**  
  
    如需詳細資訊，請參閱 [/Yc (建立先行編譯標頭檔)](/cpp/build/reference/yc-create-precompiled-header-file) 和 [/Yu (使用先行編譯標頭檔)](/cpp/build/reference/yu-use-precompiled-header-file)。 另請參閱此表格中的 **PrecompiledHeaderFile** 和 **PrecompiledHeaderOutputFile** 參數。  
  
- **PrecompiledHeaderFile**  
  
   選擇性的 **String** 參數。  
  
   指定要建立或使用的先行編譯標頭檔名稱。  
  
   如需詳細資訊，請參閱 [/Yc (建立先行編譯標頭檔)](/cpp/build/reference/yc-create-precompiled-header-file) 和 [/Yu (使用先行編譯標頭檔)](/cpp/build/reference/yu-use-precompiled-header-file)。  
  
- **PrecompiledHeaderOutputFile**  
  
   選擇性的 **String** 參數。  
  
   指定先行編譯標頭檔的路徑名稱，而不使用預設的路徑名稱。  
  
   如需詳細資訊，請參閱 [/Fp (命名 .pch 檔案)](/cpp/build/reference/fp-name-dot-pch-file)。  
  
- **PreprocessKeepComments**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會在前置處理期間保留註解。  
  
   如需詳細資訊，請參閱 [/C (前置處理時保留註解)](/cpp/build/reference/c-preserve-comments-during-preprocessing)。  
  
- **PreprocessorDefinitions**  
  
   選擇性的 `String[]` 參數。  
  
   為原始程式檔定義前置處理符號。  
  
   如需詳細資訊，請參閱 [/D (前置處理器定義)](/cpp/build/reference/d-preprocessor-definitions)。  
  
- **PreprocessOutput**  
  
   選擇性的 `ITaskItem[]` 參數。  
  
   定義工作可以耗用和發出的前置處理器輸出項目的陣列。  
  
- **PreprocessOutputPath**  
  
   選擇性的 `String` 參數。  
  
   指定 **PreprocessToFile** 參數要將前置處理過的輸出寫入其中的輸出檔名稱。  
  
   如需詳細資訊，請參閱 [/Fi (前置處理輸出檔案名稱)](/cpp/build/reference/fi-preprocess-output-file-name)。  
  
- **PreprocessSuppressLineNumbers**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會前置處理 C 和 C++ 原始程式檔，並將前置處理過的檔案複製到標準輸出裝置。  
  
   如需詳細資訊，請參閱 [/EP (前置處理至 stdout 不加 #line 指示詞)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives)。  
  
- **PreprocessToFile**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會前置處理 C 和 C++ 原始程式檔，並將前置處理過的輸出寫入檔案。  
  
   如需詳細資訊，請參閱 [/P (前置處理至檔案)](/cpp/build/reference/p-preprocess-to-a-file)。  
  
- **ProcessorNumber**  
  
   選擇性的 `Integer` 參數。  
  
   指定要在多處理器的編譯中使用的處理器數目上限。 使用此參數搭配 **MultiProcessorCompilation** 參數。  
  
- **ProgramDataBaseFileName**  
  
   選擇性的 `String` 參數。  
  
   指定程式資料庫 (PDB) 檔案的檔案名稱。  
  
   如需詳細資訊，請參閱 [/Fd (程式資料庫檔名)](/cpp/build/reference/fd-program-database-file-name)。  
  
- **RuntimeLibrary**  
  
   選擇性的 `String` 參數。  
  
   指出多執行緒模組是否為 DLL，並選取執行階段程式庫的正式版本或偵錯版本。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **MultiThreaded** - **/MT**  
  
  - **MultiThreadedDebug** - **/MTd**  
  
  - **MultiThreadedDLL** - **/MD**  
  
  - **MultiThreadedDebugDLL** - **/MDd**  
  
    如需詳細資訊，請參閱 [/MD、/MT、/LD (使用執行階段程式庫)](/cpp/build/reference/md-mt-ld-use-run-time-library)。  
  
- **RuntimeTypeInfo**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會加入程式碼，以便在執行階段檢查 C++ 物件類型 (執行階段類型資訊)。  
  
   如需詳細資訊，請參閱 [/GR (啟用執行階段類型資訊)](/cpp/build/reference/gr-enable-run-time-type-information)。  
  
- **ShowIncludes**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會導致編譯器輸出 include 檔案清單。  
  
   如需詳細資訊，請參閱 [/showIncludes (列示包含檔)](/cpp/build/reference/showincludes-list-include-files)。  
  
- **SmallerTypeCheck**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，若將某個值指派給較小的資料類型，就會報告執行階段錯誤，並造成資料遺失。  
  
   如需詳細資訊，請參閱 [/RTC (執行階段錯誤檢查)](/cpp/build/reference/rtc-run-time-error-checks) 中的 **/RTCc** 選項。  
  
- **Sources**  
  
   必要的 `ITaskItem[]` 參數。  
  
   指定以空格分隔的原始程式檔清單。  
  
- **StringPooling**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，就能讓編譯器在程式映像中建立一份完全相同的字串。  
  
   如需詳細資訊，請參閱 [/GF (消除重複字串)](/cpp/build/reference/gf-eliminate-duplicate-strings)。  
  
- **StructMemberAlignment**  
  
   選擇性的 `String` 參數。  
  
   指定結構中所有成員的位元組對應儲存。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **Default** - **/Zp1**  
  
  - **1Byte** - **/Zp1**  
  
  - **2Bytes** - **/Zp2**  
  
  - **4Bytes** - **/Zp4**  
  
  - **8Bytes** - **/Zp8**  
  
  - **16Bytes** - **/Zp16**  
  
    如需詳細資訊，請參閱 [/Zp (結構成員對齊)](/cpp/build/reference/zp-struct-member-alignment)。  
  
- **SuppressStartupBanner**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。  
  
   如需詳細資訊，請參閱 [/nologo (隱藏程式啟始資訊) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp)。  
  
- **TrackerLogDirectory**  
  
   選擇性的 `String` 參數。  
  
   指定儲存此工作之追蹤記錄檔的中繼目錄。  
  
   如需詳細資訊，請參閱此表格中的 **TLogReadFiles** 和 **TLogWriteFiles** 參數。  
  
- **TreatSpecificWarningsAsErrors**  
  
   選擇性的 **String[]** 參數。  
  
   將指定的編譯器警告清單視為錯誤。  
  
   如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](/cpp/build/reference/compiler-option-warning-level) 中的 **/we**`n` 選項。  
  
- **TreatWarningAsError**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會將所有的編譯器警告視為錯誤。  
  
   如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](/cpp/build/reference/compiler-option-warning-level) 中的 **/WX** 選項。  
  
- **TreatWChar_tAsBuiltInType**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會將 `wchar_t` 類型視為原生類型。  
  
   如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type)。  
  
- **UndefineAllPreprocessorDefinitions**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會取消定義編譯器所定義的 Microsoft 特定符號。  
  
   如需詳細資訊，請參閱 [/U、/u (取消定義符號)](/cpp/build/reference/u-u-undefine-symbols) 中的 **/u** 選項。  
  
- **UndefinePreprocessorDefinitions**  
  
   選擇性的 `String[]` 參數。  
  
   指定要取消定義的一或多個前置處理器符號清單。  
  
   如需詳細資訊，請參閱 [/U、/u (取消定義符號)](/cpp/build/reference/u-u-undefine-symbols) 中的 **/U** 選項。  
  
- **UseFullPaths**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會顯示在診斷中傳遞給編譯器的原始程式檔完整路徑。  
  
   如需詳細資訊，請參閱 [/FC (診斷中原始程式碼檔的完整路徑)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics)。  
  
- **UseUnicodeForAssemblerListing**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，就會以 UTF-8 格式建立輸出檔。  
  
   如需詳細資訊，請參閱 [/FA、/Fa (清單檔)](/cpp/build/reference/fa-fa-listing-file) 中的 **/FAu** 選項。  
  
- **WarningLevel**  
  
   選擇性的 `String` 參數。  
  
   指定編譯器要產生的最高警告層級。  
  
   指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
  - **TurnOffAllWarnings** - **/W0**  
  
  - **Level1** - **/W1**  
  
  - **Level2** - **/W2**  
  
  - **Level3** - **/W3**  
  
  - **Level4** - **/W4**  
  
  - **EnableAllWarnings** - **/Wall**  
  
    如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](/cpp/build/reference/compiler-option-warning-level) 中的 **/W**_n_ 選項。  
  
- **WholeProgramOptimization**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會啟用整個程式最佳化。  
  
   如需詳細資訊，請參閱 [/GL (整個程式最佳化)](/cpp/build/reference/gl-whole-program-optimization)。  
  
- **XMLDocumentationFileName**  
  
   選擇性的 `String` 參數。  
  
   指定所產生的 XML 文件檔名稱。 這個參數可以是檔案或目錄的名稱。  
  
   如需詳細資訊，請參閱 [/doc (處理文件註解) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp) 中的 `name` 引數。 另請參閱此表格中的 **GenerateXMLDocumentationFiles** 參數。  
  
- **MinimalRebuildFromTracking**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會執行追蹤的累加建置；如果是 `false`，則會執行重建。  
  
- **TLogReadFiles**  
  
   選擇性的 `ITaskItem[]` 參數。  
  
   指定代表「讀取檔案追蹤記錄檔」的項目陣列。  
  
   讀取檔案追蹤記錄檔 (*.tlog*) 包含工作所讀取的輸入檔名稱，並由專案組建系統用來支援累加建置。 如需詳細資訊，請參閱此表格中的 **TrackerLogDirectory** 和 **TrackFileAccess** 參數。  
  
- **TLogWriteFiles**  
  
   選擇性的 `ITaskItem[]` 參數。  
  
   指定代表「寫入檔案追蹤記錄檔」的項目陣列。  
  
   寫入檔案追蹤記錄檔 (*.tlog*) 包含工作所寫入的輸出檔案名稱，並由專案組建系統用來支援累加建置。 如需詳細資訊，請參閱此表格中的 **TrackerLogDirectory** 和 **TrackFileAccess** 參數。  
  
- **TrackFileAccess**  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，即會追蹤檔案存取模式。  
  
   如需詳細資訊，請參閱此表格中的 **TLogReadFiles** 和 **TLogWriteFiles** 參數。  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)
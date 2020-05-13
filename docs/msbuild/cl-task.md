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
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb0e1feee1f7e1d271dd436a1879731354cbd8bb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865332"
---
# <a name="cl-task"></a>CL 工作

包裝微軟C++編譯器工具 *，cl.exe*。 編譯器生成可執行檔 *（.exe）* 檔、動態連結程式庫 *（.dll*） 檔或代碼模組 *（.netmodule）* 檔。 有關詳細資訊，請參閱[編譯器選項](/cpp/build/reference/compiler-options)，[並從命令列使用 MSBuild，](/cpp/build/msbuild-visual-cpp)並使用[命令列中的 Microsoft C++工具集](/cpp/build/building-on-the-command-line)。

## <a name="parameters"></a>參數

 下列清單描述 **CL** 工作的參數。 大部分的工作參數以及數組參數會對應到命令列選項。

- **AdditionalIncludeDirectories**

   選擇性的 String[] 參數。

   將目錄加入至要搜尋 include 檔案的目錄清單。

   有關詳細資訊，請參閱[/I（其他包含目錄）](/cpp/build/reference/i-additional-include-directories)。

- **AdditionalOptions**

   選擇性的 String 參數。

   命令列選項清單。 例如，"/\<option1> /\<option2> /\<option#>"。 使用此參數，來指定任何其他工作參數未表示的命令列選項。

   有關詳細資訊，請參閱[編譯器選項](/cpp/build/reference/compiler-options)。

- **AdditionalUsingDirectories**

   選擇性的 String[] 參數。

   指定編譯器要搜尋的目錄，以解析傳遞給 **#using** 指示詞的檔案參考。

   有關詳細資訊，請參閱[/AI（指定中繼資料目錄）](/cpp/build/reference/ai-specify-metadata-directories)。

- **AlwaysAppend**

   選擇性的 String 參數。

   一律會在命令列上發出的字串。 其預設值為 "**/c**"。

- **AssemblerListingLocation**

   建立包含組譯碼的清單檔案。

   有關詳細資訊，請參閱 **/FA**中的 /Fa 選項[/Fa（清單檔）](/cpp/build/reference/fa-fa-listing-file)。

- **AssemblerOutput**

   選擇性的 String 參數。

   建立包含組譯碼的清單檔案。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **無** - *清單\<無>*

  - **裝配代碼** - **/FA**

  - **裝配和機器代碼** - **/FAc**

  - **程式集和原始程式碼** - **/法**

  - **所有** - **/FAc**

    有關詳細資訊，請參閱 **/FA** **、/FAc** **、/FA**和 **/FAc**選項[/FA、/Fa（清單檔）](/cpp/build/reference/fa-fa-listing-file)中的選項。

- **BasicRuntimeChecks**

   選擇性的 String 參數。

   搭配 [runtime_checks](/cpp/preprocessor/runtime-checks) pragma 來啟用和停用執行階段錯誤檢查功能。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **Default**  -                          *預設\<無>*

  - **堆疊幀運行時檢查** - **/RTC**

  - **未初始化的本地用法檢查** - **/RTCu**

  - **啟用快速檢查** -                          **/RTC1**

    有關詳細資訊，請參閱[/RTC（執行階段錯誤檢查）。](/cpp/build/reference/rtc-run-time-error-checks)

- **BrowseInformation**

   選擇性的 Boolean 參數。

   如果是 `true`，即會建立瀏覽資訊檔。

   有關詳細資訊，請參閱 /FR 中的 **/FR**選項[/Fr（創建 .sbr 檔）](/cpp/build/reference/fr-fr-create-dot-sbr-file)

- **BrowseInformationFile**

   選擇性的 String 參數。

   指定瀏覽資訊檔的檔案名稱。

   有關詳細資訊，請參閱此表中的 **"流覽資訊"** 參數，並另請參閱[/FR、/Fr（創建 .sbr 檔）。](/cpp/build/reference/fr-fr-create-dot-sbr-file)

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

  - **克德克爾** - **/Gd**

  - **快速呼叫** -                          **/Gr**

  - **斯特呼叫** -                          **/Gz**

    有關詳細資訊，請參閱[/Gd、/Gr、/Gv、/Gz（呼叫約定）。](/cpp/build/reference/gd-gr-gv-gz-calling-convention)

- **CompileAs**

   選擇性的 String 參數。

   指定是否要將輸入檔案編譯為 C 或 C++ 原始程式檔。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **Default**  - *預設\<無>*

  - **編譯AsC/TC**  -  ** **

  - **編譯為** - **Cpp/TP**

    有關詳細資訊，請參閱[/Tc、/Tp、/TC、/TP（指定源檔案類型）](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type)。

- **CompileAsManaged**

   選擇性的 String 參數。

   可讓應用程式和元件使用 Common Language Runtime (CLR) 中的功能。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **false**  - *假\<無>*

  - **真** - **/clr**

  - **純** - **/克拉：純**

  - **安全** - **/克拉：安全**

  - **舊語法** - **/clr：舊語法**

    如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](/cpp/build/reference/clr-common-language-runtime-compilation)。

- **CreateHotpatchableImage**

   選擇性的 Boolean 參數。

   如果是 `true`，則會告知編譯器來準備「Hotpatch 功能」** 所需的映像。 此參數會確認每個函式的第一個指令都是兩個位元組，這是 Hotpatch 功能所需要的。

   有關詳細資訊，請參閱[/熱補丁（創建可熱圖像）](/cpp/build/reference/hotpatch-create-hotpatchable-image)。

- **DebugInformationFormat**

   選擇性的 String 參數。

   選擇為程式創建的調試資訊的類型，以及此資訊是保存在物件 *（.obj*） 檔中還是程式資料庫 （PDB）。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **舊樣式** - **/Z7**

  - **程式資料庫** - **/子**

  - **編輯並繼續** - **/ZI**

    有關詳細資訊，請參閱[/Z7、/Zi、/ZI（調試資訊格式）。](/cpp/build/reference/z7-zi-zi-debug-information-format)

- **DisableLanguageExtensions**

   選擇性的 Boolean 參數。

   如果是 **true**，即會告訴編譯器，針對與 ANSI C 或 ANSI C++ 不相容的語言建構發出錯誤。

   有關詳細資訊，請參閱 /Za 中的 **/Za**選項[/Ze（禁用語言擴展）。](/cpp/build/reference/za-ze-disable-language-extensions)

- **DisableSpecificWarnings**

   選擇性的 String[] 參數。

   停用以分號分隔的清單中所指定的警告編號。

   有關詳細資訊，請參閱`/wd` [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/Wv、/WX（警告級別）的選項](/cpp/build/reference/compiler-option-warning-level)。

- **EnableEnhancedInstructionSet**

   選擇性的 String 參數。

   指定產生程式碼的架構，來使用 Streaming SIMD Extensions (SSE) 和 Streaming SIMD Extensions 2 (SSE2) 指令。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **流式 SIMD 擴展** - **/arch：SSE**

  - **流式 SIMD 擴展2** - **/arch：SSE2**

    如需詳細資訊，請參閱 [/arch (x86)](/cpp/build/reference/arch-x86)。

- **EnableFiberSafeOptimizations**

   選擇性的 Boolean 參數。

   如果是 `true`，即會對使用靜態執行緒區域儲存區配置的資料 (也就是使用 `__declspec(thread)` 配置的資料) 支援 Fiber 安全。

   有關詳細資訊，請參閱[/GT（支援光纖安全線程本機存放區）。](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage)

- **EnablePREfast**

   選擇性的 Boolean 參數。

   如果是 `true`，即會啟用程式碼分析。

   有關詳細資訊，請參閱[/分析（代碼分析）。](/cpp/build/reference/analyze-code-analysis)

- **錯誤報表**

   選擇性的 String 參數。

   讓您可將內部編譯器錯誤 (ICE) 資訊直接提供給 Microsoft。 根據預設，IDE 組建中的設定是 **Prompt**，而命令列組建中的設定是 **Queue**。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **無** - **/錯誤報表：無**

  - **提示** - **/錯誤報表：提示**

  - **佇列** - **/錯誤報表：佇列**

  - **發送** - **/錯誤報表：發送**

    有關詳細資訊，請參閱[/錯誤報表（報告內部編譯器錯誤）](/cpp/build/reference/errorreport-report-internal-compiler-errors)。

- **ExceptionHandling**

   選擇性的 String 參數。

   指定編譯器所使用的例外狀況處理模型。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **false**  - *假\<無>*

  - **非同步** - **/EHa**

  - **同步** - **/EHsc**

  - **同步投擲** - **/EHs**

    有關詳細資訊，請參閱[/EH（異常處理模型）。](/cpp/build/reference/eh-exception-handling-model)

- **ExpandAttributedSource**

   選擇性的 Boolean 參數。

   如果是 `true`，即會建立清單檔案，並展開已加入原始程式碼的屬性。

   有關詳細資訊，請參閱[/Fx（合併注入的代碼）](/cpp/build/reference/fx-merge-injected-code)。

- **FavorSizeOrSpeed**

   選擇性的 String 參數。

   指定偏好程式碼大小，還是程式碼的速度。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **兩者都沒有** - *\<>*

  - **大小** - **/O**

  - **速度** - **/Ot**

    有關詳細資訊，請參閱[/O、/Ot（贊成小代碼，喜歡快速代碼）](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code)。

- **FloatingPointExceptions**

   選擇性的 Boolean 參數。

   如果是 `true`，即會啟用可靠的浮點例外狀況模型。 觸發例外狀況之後，將會立即引發例外狀況。

   有關詳細資訊，請參閱 **/fp：/fp**中的選項[（指定浮點行為）。](/cpp/build/reference/fp-specify-floating-point-behavior)

- **FloatingPointModel**

   選擇性的 String 參數。

   設定浮點模型。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **精確** - **/fp：精確**

  - **嚴格** - **/fp：嚴格**

  - **快速** - **/fp：快速**

    有關詳細資訊，請參閱[/fp（指定浮點行為）](/cpp/build/reference/fp-specify-floating-point-behavior)。

- **ForceConformanceInForLoopScope**

   選擇性的 Boolean 參數。

   如果是 `true`，即會在使用 Microsoft 擴充功能 ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)) 的 [for](/cpp/cpp/for-statement-cpp) 迴圈中實作標準的 C++ 行為。

   有關詳細資訊，請參閱[/Zc：forScope（迴圈作用域中的強制一致性）](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope)。

- **ForcedIncludeFiles**

   選擇性的 `String[]` 參數。

   導致前置處理器要處理一或多個指定的標頭檔。

   有關詳細資訊，請參閱[/FI（名稱強制包含檔）](/cpp/build/reference/fi-name-forced-include-file)。

- **ForcedUsingFiles**

   可選**字串*** 參數。

   導致前置處理器要一或多個指定的 **#using** 檔案。

   有關詳細資訊，請參閱[/FU（名稱強制#using檔）](/cpp/build/reference/fu-name-forced-hash-using-file)。

- **FunctionLevelLinking**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會讓編譯器以封裝函式 (COMDAT) 的格式封裝個別的函式。

   有關詳細資訊，請參閱[/Gy（啟用函數級連結）](/cpp/build/reference/gy-enable-function-level-linking)。

- **GenerateXMLDocumentationFiles**

   選擇性的 `Boolean` 參數。

   如果`true`，導致編譯器處理原始程式碼檔中的文檔注釋，並為具有文檔注釋的每個原始程式碼檔創建 *.xdc*檔。

   有關詳細資訊，請參閱[/doc（流程文檔注釋）（C/C++）。](/cpp/build/reference/doc-process-documentation-comments-c-cpp) 另請參閱此表格中的 **XMLDocumentationFileName** 參數。

- **IgnoreStandardIncludePath**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會防止編譯器在 PATH 和 INCLUDE 環境變數中指定的目錄內搜尋 Include 檔。

   有關詳細資訊，請參閱[/X（忽略標準包含路徑）](/cpp/build/reference/x-ignore-standard-include-paths)。

- **InlineFunctionExpansion**

   可選**字串**參數。

   選取組建的內嵌函式展開等級。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **Default**  - *預設\<無>*

  - **禁用** - **/Ob0**

  - **僅顯式內聯** - **/Ob1**

  - **任何合適的** - **/Ob2**

    有關詳細資訊，請參閱[/Ob（內聯函數擴展）。](/cpp/build/reference/ob-inline-function-expansion)

- **IntrinsicFunctions**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會使用內建函式或特殊形式的函式來取代某些函式呼叫，以協助讓您的應用程式執行得更快。

   有關詳細資訊，請參閱[/Oi（生成內建函式）](/cpp/build/reference/oi-generate-intrinsic-functions)。

- **MinimalRebuild**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會啟用最少重建，其可判定是否必須重新編譯包含已變更 C++ 類別定義 (儲存於標頭檔 (.h)) 的 C++ 原始程式檔。

   有關詳細資訊，請參閱[/Gm（啟用最少的重建）](/cpp/build/reference/gm-enable-minimal-rebuild)。

- **MultiProcessorCompilation**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會使用多個處理器來編譯。 這個參數會針對電腦上每個有效的處理器建立處理序。

   有關詳細資訊，請參閱[/MP（使用多個進程構建）](/cpp/build/reference/mp-build-with-multiple-processes)。 另請參閱此表格中的 **ProcessorNumber** 參數。

- **ObjectFileName**

   可選**字串**參數。

   指定要使用的目的檔 (.obj) 名稱或目錄，而不使用預設值。

   如需詳細資訊，請參閱 [/Fo (目的檔名稱)](/cpp/build/reference/fo-object-file-name)。

- **ObjectFiles**

   可選**字串*** 參數。

   目的檔清單。

- **OmitDefaultLibName**

   選擇性的 `Boolean` 參數。

   如果`true`從 物件 *（.obj*） 檔中省略預設的 C 運行時庫名稱。 預設情況下，編譯器將庫的名稱放入 *.obj*檔中，以將連結器定向到正確的庫。

   有關詳細資訊，請參閱[/Zl（Omit 預設庫名稱）。](/cpp/build/reference/zl-omit-default-library-name)

- **OmitFramePointers**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會在呼叫堆疊上隱藏框架指標的建立。

   有關詳細資訊，請參閱[/Oy（幀指標省略）。](/cpp/build/reference/oy-frame-pointer-omission)

- **OpenMPSupport**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會導致編譯器處理 OpenMP 子句和指示詞。

   有關詳細資訊，請參閱[/openmp（啟用 OpenMP 2.0 支援）。](/cpp/build/reference/openmp-enable-openmp-2-0-support)

- **Optimization**

   可選**字串**參數。

   指定各種適用於速度和規模的程式碼最佳化。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **禁用** - **/Od**

  - **最小空間** - **/O1**

  - **最大速度** - **/O2**

  - **全** - **/牛**

    如需詳細資訊，請參閱 [/O 選項 (最佳化程式碼)](/cpp/build/reference/o-options-optimize-code)。

- **PrecompiledHeader**

   可選**字串**參數。

   在生成期間創建或使用預編譯的標頭 （*.pch*） 檔。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **不使用** - *無>\<*

  - **創建** - **/Yc**

  - **使用** - **/宇**

    有關詳細資訊，請參閱[/Yc（創建預編譯的標標頭檔）](/cpp/build/reference/yc-create-precompiled-header-file)和[/Yu（使用預編譯的標標頭檔）。](/cpp/build/reference/yu-use-precompiled-header-file) 另請參閱此表格中的 **PrecompiledHeaderFile** 和 **PrecompiledHeaderOutputFile** 參數。

- **PrecompiledHeaderFile**

   可選**字串**參數。

   指定要建立或使用的先行編譯標頭檔名稱。

   有關詳細資訊，請參閱[/Yc（創建預編譯的標標頭檔）](/cpp/build/reference/yc-create-precompiled-header-file)和[/Yu（使用預編譯的標標頭檔）。](/cpp/build/reference/yu-use-precompiled-header-file)

- **PrecompiledHeaderOutputFile**

   可選**字串**參數。

   指定先行編譯標頭檔的路徑名稱，而不使用預設的路徑名稱。

   有關詳細資訊，請參閱[/Fp（Name .pch 檔）](/cpp/build/reference/fp-name-dot-pch-file)。

- **PreprocessKeepComments**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會在前置處理期間保留註解。

   有關詳細資訊，請參閱[/C（在預處理期間保留注釋）](/cpp/build/reference/c-preserve-comments-during-preprocessing)。

- **PreprocessorDefinitions**

   選擇性的 `String[]` 參數。

   為原始程式檔定義前置處理符號。

   有關詳細資訊，請參閱[/D（預處理器定義）](/cpp/build/reference/d-preprocessor-definitions)。

- **PreprocessOutput**

   選擇性的 `ITaskItem[]` 參數。

   定義工作可以耗用和發出的前置處理器輸出項目的陣列。

- **PreprocessOutputPath**

   選擇性的 `String` 參數。

   指定 **PreprocessToFile** 參數要將前置處理過的輸出寫入其中的輸出檔名稱。

   有關詳細資訊，請參閱[/Fi（預處理輸出檔案名）。](/cpp/build/reference/fi-preprocess-output-file-name)

- **PreprocessSuppressLineNumbers**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會前置處理 C 和 C++ 原始程式檔，並將前置處理過的檔案複製到標準輸出裝置。

   有關詳細資訊，請參閱[/EP（預處理到不#line指令的停滯）](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives)。

- **PreprocessToFile**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會前置處理 C 和 C++ 原始程式檔，並將前置處理過的輸出寫入檔案。

   有關詳細資訊，請參閱[/P（對檔進行預處理）](/cpp/build/reference/p-preprocess-to-a-file)。

- **ProcessorNumber**

   選擇性的 `Integer` 參數。

   指定要在多處理器的編譯中使用的處理器數目上限。 使用此參數搭配 **MultiProcessorCompilation** 參數。

- **ProgramDataBaseFileName**

   選擇性的 `String` 參數。

   指定程式資料庫 (PDB) 檔案的檔案名稱。

   有關詳細資訊，請參閱[/Fd（程式資料庫檔案名）。](/cpp/build/reference/fd-program-database-file-name)

- **RuntimeLibrary**

   選擇性的 `String` 參數。

   指出多執行緒模組是否為 DLL，並選取執行階段程式庫的正式版本或偵錯版本。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **多執行緒** - **/MT**

  - **多執行緒調試** - **/MTd**

  - **多執行緒 DLL** - **/MD**

  - **多執行緒調試DLL** - **/MDd**

    有關詳細資訊，請參閱[/MD、/MT、/LD（使用運行時庫）。](/cpp/build/reference/md-mt-ld-use-run-time-library)

- **RuntimeTypeInfo**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會加入程式碼，以便在執行階段檢查 C++ 物件類型 (執行階段類型資訊)。

   有關詳細資訊，請參閱[/GR（啟用運行時類型資訊）。](/cpp/build/reference/gr-enable-run-time-type-information)

- **ShowIncludes**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會導致編譯器輸出 include 檔案清單。

   有關詳細資訊，請參閱[/show 包括（清單包含檔）](/cpp/build/reference/showincludes-list-include-files)。

- **SmallerTypeCheck**

   選擇性的 `Boolean` 參數。

   如果是 `true`，若將某個值指派給較小的資料類型，就會報告執行階段錯誤，並造成資料遺失。

   有關詳細資訊，請參閱 **/RTC 中的 /RTCc**選項[（執行階段錯誤檢查）。](/cpp/build/reference/rtc-run-time-error-checks)

- **來源**

   必要的 `ITaskItem[]` 參數。

   指定以空格分隔的原始程式檔清單。

- **StringPooling**

   選擇性的 `Boolean` 參數。

   如果是 `true`，就能讓編譯器在程式映像中建立一份完全相同的字串。

   有關詳細資訊，請參閱[/GF（消除重複字串）。](/cpp/build/reference/gf-eliminate-duplicate-strings)

- **StructMemberAlignment**

   選擇性的 `String` 參數。

   指定結構中所有成員的位元組對應儲存。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **預設值** - **/Zp1**

  - **1位元組** - **/Zp1**

  - **2 位元組** - **/Zp2**

  - **4 位元組** - **/Zp4**

  - **8 位元組** - **/Zp8**

  - **16位元組** - **/Zp16**

    有關詳細資訊，請參閱[/Zp（結構成員對齊）](/cpp/build/reference/zp-struct-member-alignment)。

- **SuppressStartupBanner**

   選擇性的 `Boolean` 參數。

   如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。

   有關詳細資訊，請參閱[/nologo（抑制啟動橫幅）（C/C++）](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp)。

- **TrackerLogDirectory**

   選擇性的 `String` 參數。

   指定儲存此工作之追蹤記錄檔的中繼目錄。

   如需詳細資訊，請參閱此表格中的 **TLogReadFiles** 和 **TLogWriteFiles** 參數。

- **TreatSpecificWarningsAsErrors**

   可選**字串*** 參數。

   將指定的編譯器警告清單視為錯誤。

   有關詳細資訊，請參閱[/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX（警告級別）中的](/cpp/build/reference/compiler-option-warning-level)**/我們**`n`選項。

- **TreatWarningAsError**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會將所有的編譯器警告視為錯誤。

   有關詳細資訊，請參閱 **/WX**選項，包括[/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX（警告級別）。](/cpp/build/reference/compiler-option-warning-level)

- **TreatWChar_tAsBuiltInType**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會將 `wchar_t` 類型視為原生類型。

   有關詳細資訊，請參閱[/Zc：wchar_t（wchar_t是本機類型）。](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type)

- **UndefineAllPreprocessorDefinitions**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會取消定義編譯器所定義的 Microsoft 特定符號。

   有關詳細資訊，請參閱[/U、/u 中的 /u 選項（取消定義符號）。](/cpp/build/reference/u-u-undefine-symbols) **/u**

- **UndefinePreprocessorDefinitions**

   選擇性的 `String[]` 參數。

   指定要取消定義的一或多個前置處理器符號清單。

   有關詳細資訊，請參閱 /U 中的 **/U**選項[/u（取消定義符號）](/cpp/build/reference/u-u-undefine-symbols)。

- **UseFullPaths**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會顯示在診斷中傳遞給編譯器的原始程式檔完整路徑。

   有關詳細資訊，請參閱[/FC（診斷中原始程式碼檔的完整路徑）](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics)。

- **UseUnicodeForAssemblerListing**

   選擇性的 `Boolean` 參數。

   如果是 `true`，就會以 UTF-8 格式建立輸出檔。

   有關詳細資訊，請參閱[/FA、/Fa（清單檔）](/cpp/build/reference/fa-fa-listing-file)中的 **/FA**選項。

- **WarningLevel**

   選擇性的 `String` 參數。

   指定編譯器要產生的最高警告層級。

   指定下列其中一個值；每個值會分別對應至一個命令列選項。

  - **關閉所有警告** - **/W0**

  - **級別1** - **/W1**

  - **級別2** - **/W2**

  - **級別3** - **/W3**

  - **級別4** - **/W4**

  - **啟用所有警告** - **/牆**

    有關詳細資訊，請參閱[/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX（警告級別）中的](/cpp/build/reference/compiler-option-warning-level) **/W**_n_選項。

- **WholeProgramOptimization**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會啟用整個程式最佳化。

   有關詳細資訊，請參閱[/GL（整個程式優化）。](/cpp/build/reference/gl-whole-program-optimization)

- **XMLDocumentationFileName**

   選擇性的 `String` 參數。

   指定所產生的 XML 文件檔名稱。 這個參數可以是檔案或目錄的名稱。

   有關詳細資訊，請參閱`name`[/doc（進程文檔注釋）（C/C++）中的](/cpp/build/reference/doc-process-documentation-comments-c-cpp)參數。 另請參閱此表格中的 **GenerateXMLDocumentationFiles** 參數。

- **MinimalRebuildFromTracking**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會執行追蹤的累加建置；如果是 `false`，則會執行重建。

- **TLogReadFiles**

   選擇性的 `ITaskItem[]` 參數。

   指定代表「讀取檔案追蹤記錄檔」** 的項目陣列。

   讀取檔跟蹤日誌 *（.tlog*） 包含任務讀取的輸入檔的名稱，並且專案生成系統用於支援增量生成。 如需詳細資訊，請參閱此表格中的 **TrackerLogDirectory** 和 **TrackFileAccess** 參數。

- **TLogWriteFiles**

   選擇性的 `ITaskItem[]` 參數。

   指定代表「寫入檔案追蹤記錄檔」** 的項目陣列。

   寫入檔跟蹤日誌 *（.tlog*） 包含由任務編寫的輸出檔案的名稱，並且專案生成系統用於支援增量生成。 如需詳細資訊，請參閱此表格中的 **TrackerLogDirectory** 和 **TrackFileAccess** 參數。

- **TrackFileAccess**

   選擇性的 `Boolean` 參數。

   如果是 `true`，即會追蹤檔案存取模式。

   如需詳細資訊，請參閱此表格中的 **TLogReadFiles** 和 **TLogWriteFiles** 參數。

## <a name="see-also"></a>另請參閱

- [任務引用](../msbuild/msbuild-task-reference.md)

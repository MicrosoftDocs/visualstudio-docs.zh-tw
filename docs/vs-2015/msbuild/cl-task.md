---
title: CL 工作 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e10c5d6ed0e4b992f5b573cd46bd1248d8d24d90
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "47588752"
---
# <a name="cl-task"></a>CL 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CL 工作](https://docs.microsoft.com/visualstudio/msbuild/cl-task)。  
  
  
包裝 Visual C++ 編譯器工具 cl.exe。 編譯器會產生可執行檔 (.exe)、動態連結程式庫 (.dll) 檔案或程式碼模組 (.netmodule) 檔案。 如需詳細資訊，請參閱[編譯器選項](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c)。  
  
## <a name="parameters"></a>參數  
 下表說明 **CL** 工作的參數。 大部分的工作參數以及數組參數會對應到命令列選項。  
  
-   **AdditionalIncludeDirectories**  
  
     選擇性的 String[] 參數。  
  
     將目錄加入至要搜尋 include 檔案的目錄清單。  
  
     如需詳細資訊，請參閱 [/I (其他 Include 目錄)](http://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49)。  
  
-   **AdditionalOptions**  
  
     選擇性的 String 參數。  
  
     命令列選項清單。 例如，"/*option1* /*option2* /*option#*"。 使用此參數，來指定任何其他工作參數未表示的命令列選項。  
  
     如需詳細資訊，請參閱[編譯器選項](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c)。  
  
-   **AdditionalUsingDirectories**選擇性的 String[] 參數。  
  
     指定編譯器要搜尋的目錄，以解析傳遞給 **#using** 指示詞的檔案參考。  
  
     如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](http://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f)。  
  
-   **AlwaysAppend**  
  
     選擇性的 String 參數。  
  
     一律會在命令列上發出的字串。 其預設值為 "**/c**"。  
  
-   **AssemblerListingLocation**  
  
     建立包含組譯碼的清單檔案。  
  
     如需詳細資訊，請參閱 [/FA、/Fa (清單檔)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402) 中的 **/Fa** 選項。  
  
-   **AssemblerOutput**  
  
     選擇性的 String 參數。  
  
     建立包含組譯碼的清單檔案。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **NoListing** - *\<none>*  
  
    -   **AssemblyCode** - **/FA**  
  
    -   **AssemblyAndMachineCode** - **/FAc**  
  
    -   **AssemblyAndSourceCode** - **/FAs**  
  
    -   **All** - **/FAcs**  
  
     如需詳細資訊，請參閱 [/FA、/Fa (清單檔)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402) 中的 **/FA**、**/FAc**、**/FAs** 及 **/FAcs** 選項。  
  
-   **BasicRuntimeChecks**  
  
     選擇性的 String 參數。  
  
     搭配 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) pragma 來啟用和停用執行階段錯誤檢查功能。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **Default** -                          *\<none>*  
  
    -   **StackFrameRuntimeCheck** - **/RTCs**  
  
    -   **UninitializedLocalUsageCheck** - **/RTCu**  
  
    -   **EnableFastChecks** -                          **/RTC1**  
  
     如需詳細資訊，請參閱 [/RTC (執行階段錯誤檢查)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368)。  
  
-   **BrowseInformation**  
  
     選擇性的 Boolean 參數。  
  
     如果是 `true`，即會建立瀏覽資訊檔。  
  
     如需詳細資訊，請參閱 [/FR、/Fr (建立 .Sbr 檔案)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896) 中的 **/FR** 選項。  
  
-   **BrowseInformationFile**  
  
     選擇性的 String 參數。  
  
     指定瀏覽資訊檔的檔案名稱。  
  
     如需詳細資訊，請參閱此表格中的 **BrowseInformation** 參數，另請參閱 [/FR、/Fr (建立 .Sbr 檔案)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896)。  
  
-   **BufferSecurityCheck**  
  
     選擇性的 Boolean 參數。  
  
     如果是 `true`，即會偵測某些會覆寫傳回位址的緩衝區滿溢，此為用來惡意探索不會強制執行緩衝區大小限制之程式碼的常用技巧。  
  
     如需詳細資訊，請參閱 [/GS (緩衝區安全性檢查)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e)。  
  
-   **BuildingInIDE**  
  
     選擇性的 Boolean 參數。  
  
     如果是 `true`，即表示 IDE 會叫用 **MSBuild**。 否則，會在命令列上叫用 **MSBuild**。  
  
-   **CallingConvention**  
  
     選擇性的 String 參數。  
  
     指定呼叫慣例，決定將函式引數推入堆疊的順序、呼叫端函式或呼叫的函式是否會在呼叫結尾從堆疊中移除引數，以及編譯器用來識別個別函式的名稱裝飾慣例。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **Cdecl** - **/Gd**  
  
    -   **FastCall** -                          **/Gr**  
  
    -   **StdCall** -                          **/Gz**  
  
     如需詳細資訊，請參閱 [/Gd、/Gr、/Gv、/Gz (呼叫慣例)](http://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3)。  
  
-   **CompileAs**  
  
     選擇性的 String 參數。  
  
     指定是否要將輸入檔案編譯為 C 或 C++ 原始程式檔。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **Default** - *\<none>*  
  
    -   **CompileAsC** - **/TC**  
  
    -   **CompileAsCpp** - **/TP**  
  
     如需詳細資訊，請參閱 [/Tc、/Tp、/TC、/TP (指定原始程式檔類型)](http://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b)。  
  
-   **CompileAsManaged**  
  
     選擇性的 String 參數。  
  
     可讓應用程式和元件使用 Common Language Runtime (CLR) 中的功能。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **false** - *\<none>*  
  
    -   **true** - **/clr**  
  
    -   **Pure** - **/clr:pure**  
  
    -   **Safe** - **/clr:safe**  
  
    -   **OldSyntax** - **/clr:oldSyntax**  
  
     如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c)。  
  
-   **CreateHotpatchableImage**  
  
     選擇性的 Boolean 參數。  
  
     如果是 `true`，則會告知編譯器來準備「Hotpatch 功能」所需的映像。 此參數會確認每個函式的第一個指令都是兩個位元組，這是 Hotpatch 功能所需要的。  
  
     如需詳細資訊，請參閱 [/hotpatch (建立可進行 Hotpatch 的映像)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798)。  
  
-   **DebugInformationFormat**  
  
     選擇性的 String 參數。  
  
     選取為程式所建立的偵錯資訊類型，以及此資訊要保留於目的檔 (.obj) 還是程式資料庫 (PDB) 中。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **OldStyle** - **/Z7**  
  
    -   **ProgramDatabase** - **/Zi**  
  
    -   **EditAndContinue** - **/ZI**  
  
     如需詳細資訊，請參閱 [/Z7、/Zi、/ZI (偵錯資訊格式)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)。  
  
-   **DisableLanguageExtensions**  
  
     選擇性的 Boolean 參數。  
  
     如果是 **true**，即會告訴編譯器，針對與 ANSI C 或 ANSI C++ 不相容的語言建構發出錯誤。  
  
     如需詳細資訊，請參閱 [/Za、/Ze (停用語言擴充功能)](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2) 中的 **/Za** 選項。  
  
-   **DisableSpecificWarnings**  
  
     選擇性的 String[] 參數。  
  
     停用以分號分隔的清單中所指定的警告編號。  
  
     如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f) 中的 `/wd` 選項。  
  
-   **EnableEnhancedInstructionSet**  
  
     選擇性的 String 參數。  
  
     指定產生程式碼的架構，來使用 Streaming SIMD Extensions (SSE) 和 Streaming SIMD Extensions 2 (SSE2) 指令。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **StreamingSIMDExtensions** - **/arch:SSE**  
  
    -   **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
     如需詳細資訊，請參閱 [/arch (x86)](http://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d)。  
  
-   **EnableFiberSafeOptimizations**  
  
     選擇性的 Boolean 參數。  
  
     如果是 `true`，即會對使用靜態執行緒區域儲存區配置的資料 (也就是使用 `__declspec(thread)` 配置的資料) 支援 Fiber 安全。  
  
     如需詳細資訊，請參閱 [/GT (支援 Fiber-Safe 執行緒區域儲存區)](http://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159)。  
  
-   **EnablePREfast**  
  
     選擇性的 Boolean 參數。  
  
     如果是 `true`，即會啟用程式碼分析。  
  
     如需詳細資訊，請參閱 [/analyze (程式碼分析)](http://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08)。  
  
-   **ErrorReporting**  
  
     選擇性的 String 參數。  
  
     讓您可將內部編譯器錯誤 (ICE) 資訊直接提供給 Microsoft。 根據預設，IDE 組建中的設定是 **Prompt**，而命令列組建中的設定是 **Queue**。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **None** - **/errorReport:none**  
  
    -   **Prompt** - **/errorReport:prompt**  
  
    -   **Queue** - **/errorReport:queue**  
  
    -   **Send** - **/errorReport:send**  
  
     如需詳細資訊，請參閱 [/errorReport (回報編譯器內部錯誤)](http://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667)。  
  
-   **ExceptionHandling**  
  
     選擇性的 String 參數。  
  
     指定編譯器所使用的例外狀況處理模型。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **false** - *\<none>*  
  
    -   **Async** - **/EHa**  
  
    -   **Sync** - **/EHsc**  
  
    -   **SyncCThrow** - **/EHs**  
  
     如需詳細資訊，請參閱 [/EH (例外狀況處理模型)](http://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d)。  
  
-   **ExpandAttributedSource**  
  
     選擇性的 Boolean 參數。  
  
     如果是 `true`，即會建立清單檔案，並展開已加入原始程式碼的屬性。  
  
     如需詳細資訊，請參閱[/Fx (合併加入的程式碼)](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560)。  
  
-   **FavorSizeOrSpeed**  
  
     選擇性的 String 參數。  
  
     指定偏好程式碼大小，還是程式碼的速度。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **Neither** - *\<none>*  
  
    -   **Size** - **/Os**  
  
    -   **Speed** - **/Ot**  
  
     如需詳細資訊，請參閱 [/Os、/Ot (偏好小的程式碼、偏好快的程式碼)](http://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2)。  
  
-   **FloatingPointExceptions**  
  
     選擇性的 Boolean 參數。  
  
     如果是 `true`，即會啟用可靠的浮點例外狀況模型。 觸發例外狀況之後，將會立即引發例外狀況。  
  
     如需詳細資訊，請參閱 [/fp (指定浮點行為)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e) 中的 /**fp:except** 選項。  
  
-   **FloatingPointModel**  
  
     選擇性的 String 參數。  
  
     設定浮點模型。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **Precise** - **/fp:precise**  
  
    -   **Strict** - **/fp:strict**  
  
    -   **Fast** - **/fp:fast**  
  
     如需詳細資訊，請參閱 [/fp (指定浮點行為)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e)。  
  
-   **ForceConformanceInForLoopScope**  
  
     選擇性的 Boolean 參數。  
  
     如果是 `true`，即會在使用 Microsoft 擴充功能 ([/Ze](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)) 的 [for](http://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) 迴圈中實作標準的 C++ 行為。  
  
     如需詳細資訊，請參閱 [/Zc:forScope (強制 for 迴圈範圍中的一致性)](http://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed)。  
  
-   **ForcedIncludeFiles**  
  
     選擇性的 `String[]` 參數。  
  
     導致前置處理器要處理一或多個指定的標頭檔。  
  
     如需詳細資訊，請參閱 [/FI (指定強制的 Include 檔)](http://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397)。  
  
-   **ForcedUsingFiles**  
  
     選擇性的 **String[]** 參數。  
  
     導致前置處理器要一或多個指定的 **#using** 檔案。  
  
     如需詳細資訊，請參閱 [/FU (指定強制的 #using 檔)](http://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1)。  
  
-   **FunctionLevelLinking**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會讓編譯器以封裝函式 (COMDAT) 的格式封裝個別的函式。  
  
     如需詳細資訊，請參閱 [/Gy (啟用函式階層連結)](http://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046)。  
  
-   **GenerateXMLDocumentationFiles**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會導致編譯器處理原始程式碼檔案中的文件註解，並針對每個具有文件註解的原始程式碼檔案建立 .xdc 檔案。  
  
     如需詳細資訊，請參閱 [/doc (處理文件註解) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63)。 另請參閱此表格中的 **XMLDocumentationFileName** 參數。  
  
-   **IgnoreStandardIncludePath**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會防止編譯器在 PATH 和 INCLUDE 環境變數中指定的目錄內搜尋 Include 檔。  
  
     如需詳細資訊，請參閱 [/X (忽略標準 Include 路徑)](http://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef)。  
  
-   **InlineFunctionExpansion**  
  
     選擇性的 **String** 參數。  
  
     選取組建的內嵌函式展開等級。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **Default** - *\<none>*  
  
    -   **Disabled** - **/Ob0**  
  
    -   **OnlyExplicitInline** - **/Ob1**  
  
    -   **AnySuitable** - **/Ob2**  
  
     如需詳細資訊，請參閱 [/Ob (內嵌函式展開)](http://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a)。  
  
-   **IntrinsicFunctions**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會使用內建函式或特殊形式的函式來取代某些函式呼叫，以協助讓您的應用程式執行得更快。  
  
     如需詳細資訊，請參閱 [/Oi (產生內建函式)](http://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4)。  
  
-   **MinimalRebuild**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會啟用最少重建，其可判定是否必須重新編譯包含已變更 C++ 類別定義 (儲存於標頭檔 (.h)) 的 C++ 原始程式檔。  
  
     如需詳細資訊，請參閱 [/Gm (啟用最少重建)](http://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59) 。  
  
-   **MultiProcessorCompilation**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會使用多個處理器來編譯。 這個參數會針對電腦上每個有效的處理器建立處理序。  
  
     如需詳細資訊，請參閱 [/MP (使用多處理序建置)](http://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07)。 另請參閱此表格中的 **ProcessorNumber** 參數。  
  
-   **ObjectFileName**  
  
     選擇性的 **String** 參數。  
  
     指定要使用的目的檔 (.obj) 名稱或目錄，而不使用預設值。  
  
     如需詳細資訊，請參閱 [/Fo (目的檔名稱)](http://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6)。  
  
-   **ObjectFiles**  
  
     選擇性的 **String[]** 參數。  
  
     目的檔清單。  
  
-   **OmitDefaultLibName**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會在目的檔 (.obj) 中省略預設的 C 執行階段程式庫名稱。 根據預設，編譯器會將程式庫名稱置入 .obj 檔案中，以將連結器導向至正確的程式庫。  
  
     如需詳細資訊，請參閱 [/Zl (省略預設程式庫名稱)](http://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59)。  
  
-   **OmitFramePointers**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會在呼叫堆疊上隱藏框架指標的建立。  
  
     如需詳細資訊，請參閱 [/Oy (框架指標省略)](http://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853)。  
  
-   **OpenMPSupport**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會導致編譯器處理 OpenMP 子句和指示詞。  
  
     如需詳細資訊，請參閱 [/openmp (啟用 OpenMP 2.0 支援)](http://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13)。  
  
-   **Optimization**  
  
     選擇性的 **String** 參數。  
  
     指定各種適用於速度和規模的程式碼最佳化。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **Disabled** - **/Od**  
  
    -   **MinSpace** - **/O1**  
  
    -   **MaxSpeed** - **/O2**  
  
    -   **Full** - **/Ox**  
  
     如需詳細資訊，請參閱 [/O 選項 (最佳化程式碼)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d)。  
  
-   **PrecompiledHeader**  
  
     選擇性的 **String** 參數。  
  
     在建置期間建立或使用先行編譯標頭檔 (.pch)。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **NotUsing** - *\<none>*  
  
    -   **Create** - **/Yc**  
  
    -   **Use** - **/Yu**  
  
     如需詳細資訊，請參閱 [/Yc (建立先行編譯標頭檔)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) 和 [/Yu (使用先行編譯標頭檔)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f)。 另請參閱此表格中的 **PrecompiledHeaderFile** 和 **PrecompiledHeaderOutputFile** 參數。  
  
-   **PrecompiledHeaderFile**  
  
     選擇性的 **String** 參數。  
  
     指定要建立或使用的先行編譯標頭檔名稱。  
  
     如需詳細資訊，請參閱 [/Yc (建立先行編譯標頭檔)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) 和 [/Yu (使用先行編譯標頭檔)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f)。  
  
-   **PrecompiledHeaderOutputFile**  
  
     選擇性的 **String** 參數。  
  
     指定先行編譯標頭檔的路徑名稱，而不使用預設的路徑名稱。  
  
     如需詳細資訊，請參閱 [/Fp (指定 .PCH 檔)](http://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2)。  
  
-   **PreprocessKeepComments**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會在前置處理期間保留註解。  
  
     如需詳細資訊，請參閱 [/C (在前置處理期間保留註解)](http://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26)。  
  
-   **PreprocessorDefinitions**  
  
     選擇性的 `String[]` 參數。  
  
     為原始程式檔定義前置處理符號。  
  
     如需詳細資訊，請參閱 [/D (前置處理器定義)](http://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba)。  
  
-   **PreprocessOutput**  
  
     選擇性的 `ITaskItem[]` 參數。  
  
     定義工作可以耗用和發出的前置處理器輸出項目的陣列。  
  
-   **PreprocessOutputPath**  
  
     選擇性的 `String` 參數。  
  
     指定 **PreprocessToFile** 參數要將前置處理過的輸出寫入其中的輸出檔名稱。  
  
     如需詳細資訊，請參閱 [/Fi (前置處理輸出檔名稱)](http://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee)。  
  
-   **PreprocessSuppressLineNumbers**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會前置處理 C 和 C++ 原始程式檔，並將前置處理過的檔案複製到標準輸出裝置。  
  
     如需詳細資訊，請參閱 [/EP (前置處理至 stdout 不加 #line 指示詞)](http://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea)。  
  
-   **PreprocessToFile**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會前置處理 C 和 C++ 原始程式檔，並將前置處理過的輸出寫入檔案。  
  
     如需詳細資訊，請參閱 [/P (前置處理至檔案)](http://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc)。  
  
-   **ProcessorNumber**  
  
     選擇性的 `Integer` 參數。  
  
     指定要在多處理器的編譯中使用的處理器數目上限。 使用此參數搭配 **MultiProcessorCompilation** 參數。  
  
-   **ProgramDataBaseFileName**  
  
     選擇性的 `String` 參數。  
  
     指定程式資料庫 (PDB) 檔案的檔案名稱。  
  
     如需詳細資訊，請參閱 [/Fd (程式資料庫檔名)](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a)。  
  
-   **RuntimeLibrary**  
  
     選擇性的 `String` 參數。  
  
     指出多執行緒模組是否為 DLL，並選取執行階段程式庫的正式版本或偵錯版本。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **MultiThreaded** - **/MT**  
  
    -   **MultiThreadedDebug** - **/MTd**  
  
    -   **MultiThreadedDLL** - **/MD**  
  
    -   **MultiThreadedDebugDLL** - **/MDd**  
  
     如需詳細資訊，請參閱 [/MD、/MT、/LD (使用執行階段程式庫)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)。  
  
-   **RuntimeTypeInfo**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會加入程式碼，以便在執行階段檢查 C++ 物件類型 (執行階段類型資訊)。  
  
     如需詳細資訊，請參閱 [/GR (啟用執行階段類型資訊)](http://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906)。  
  
-   **ShowIncludes**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會導致編譯器輸出 include 檔案清單。  
  
     如需詳細資訊，請參閱 [/showIncludes (列示 Include 檔案)](http://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d)。  
  
-   **SmallerTypeCheck**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，若將某個值指派給較小的資料類型，就會報告執行階段錯誤，並造成資料遺失。  
  
     如需詳細資訊，請參閱 [/RTC (執行階段錯誤檢查)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368) 中的 **/RTCc** 選項。  
  
-   **Sources**  
  
     必要的 `ITaskItem[]` 參數。  
  
     指定以空格分隔的原始程式檔清單。  
  
-   **StringPooling**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，就能讓編譯器在程式映像中建立一份完全相同的字串。  
  
     如需詳細資訊，請參閱 [/GF (消除重複字串)](http://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c)。  
  
-   **StructMemberAlignment**  
  
     選擇性的 `String` 參數。  
  
     指定結構中所有成員的位元組對應儲存。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **Default** - **/Zp1**  
  
    -   **1Byte** - **/Zp1**  
  
    -   **2Bytes** - **/Zp2**  
  
    -   **4Bytes** - **/Zp4**  
  
    -   **8Bytes** - **/Zp8**  
  
    -   **16Bytes** - **/Zp16**  
  
     如需詳細資訊，請參閱 [/Zp (結構成員對應儲存)](http://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f)。  
  
-   **SuppressStartupBanner**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。  
  
     如需詳細資訊，請參閱 [/nologo (隱藏程式啟始資訊) (C/C++)](http://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693)。  
  
-   **TrackerLogDirectory**  
  
     選擇性的 `String` 參數。  
  
     指定儲存此工作之追蹤記錄檔的中繼目錄。  
  
     如需詳細資訊，請參閱此表格中的 **TLogReadFiles** 和 **TLogWriteFiles** 參數。  
  
-   **TreatSpecificWarningsAsErrors**  
  
     選擇性的 **String[]** 參數。  
  
     將指定的編譯器警告清單視為錯誤。  
  
     如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f) 中的 **/we**`n` 選項。  
  
-   **TreatWarningAsError**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會將所有的編譯器警告視為錯誤。  
  
     如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f) 中的 **/WX** 選項。  
  
-   **TreatWChar_tAsBuiltInType**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會將 `wchar_t` 類型視為原生類型。  
  
     如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](http://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0)。  
  
-   **UndefineAllPreprocessorDefinitions**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會取消定義編譯器所定義的 Microsoft 特定符號。  
  
     如需詳細資訊，請參閱 [/U、/u (取消定義符號)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a) 中的 **/u** 選項。  
  
-   **UndefinePreprocessorDefinitions**  
  
     選擇性的 `String[]` 參數。  
  
     指定要取消定義的一或多個前置處理器符號清單。  
  
     如需詳細資訊，請參閱 [/U、/u (取消定義符號)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a) 中的 **/U** 選項。  
  
-   **UseFullPaths**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會顯示在診斷中傳遞給編譯器的原始程式檔完整路徑。  
  
     如需詳細資訊，請參閱 [/FC (診斷中原始程式碼檔的完整路徑)](http://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b)。  
  
-   **UseUnicodeForAssemblerListing**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，就會以 UTF-8 格式建立輸出檔。  
  
     如需詳細資訊，請參閱 [/FA、/Fa (清單檔)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402) 中的 **/FAu** 選項。  
  
-   **WarningLevel**  
  
     選擇性的 `String` 參數。  
  
     指定編譯器要產生的最高警告層級。  
  
     指定下列其中一個值；每個值會分別對應至一個命令列選項。  
  
    -   **TurnOffAllWarnings** - **/W0**  
  
    -   **Level1** - **/W1**  
  
    -   **Level2** - **/W2**  
  
    -   **Level3** - **/W3**  
  
    -   **Level4** - **/W4**  
  
    -   **EnableAllWarnings** - **/Wall**  
  
     如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f) 中的 **/W**_n_ 選項。  
  
-   **WholeProgramOptimization**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會啟用整個程式最佳化。  
  
     如需詳細資訊，請參閱 [/GL (整個程式最佳化)](http://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1)。  
  
-   **XMLDocumentationFileName**  
  
     選擇性的 `String` 參數。  
  
     指定所產生的 XML 文件檔名稱。 這個參數可以是檔案或目錄的名稱。  
  
     如需詳細資訊，請參閱 [/doc (處理文件註解) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) 中的 `name` 引數。 另請參閱此表格中的 **GenerateXMLDocumentationFiles** 參數。  
  
-   **MinimalRebuildFromTracking**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會執行追蹤的累加建置；如果是 `false`，則會執行重建。  
  
-   **TLogReadFiles**  
  
     選擇性的 `ITaskItem[]` 參數。  
  
     指定代表「讀取檔案追蹤記錄檔」的項目陣列。  
  
     讀取檔案追蹤記錄檔 (.tlog) 包含工作所讀取的輸入檔名稱，並由專案組建系統用來支援累加建置。 如需詳細資訊，請參閱此表格中的 **TrackerLogDirectory** 和 **TrackFileAccess** 參數。  
  
-   **TLogWriteFiles**  
  
     選擇性的 `ITaskItem[]` 參數。  
  
     指定代表「寫入檔案追蹤記錄檔」的項目陣列。  
  
     寫入檔案追蹤記錄檔 (.tlog) 包含工作所寫入的輸出檔名稱，並由專案組建系統用來支援累加建置。 如需詳細資訊，請參閱此表格中的 **TrackerLogDirectory** 和 **TrackFileAccess** 參數。  
  
-   **TrackFileAccess**  
  
     選擇性的 `Boolean` 參數。  
  
     如果是 `true`，即會追蹤檔案存取模式。  
  
     如需詳細資訊，請參閱此表格中的 **TLogReadFiles** 和 **TLogWriteFiles** 參數。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)




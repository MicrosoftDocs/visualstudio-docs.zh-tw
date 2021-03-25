---
title: MIDL 工作 | Microsoft Docs
description: 深入瞭解 MSBuild MIDL 工作，這項工作會包裝 Microsoft 介面定義語言 (MIDL) 編譯器工具 midl.exe。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), MIDL task
- MIDL task (MSBuild (C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eadec17e7c5221f0b169d38b15b9601cec746fa4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094974"
---
# <a name="midl-task"></a>MIDL 工作

包裝 Microsoft 介面定義語言 (MIDL) 編譯器工具 (midl.exe)。 如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考)。

## <a name="parameters"></a>參數

 下列描述 **MIDL** 工作的參數。 大部分的工作參數以及數組參數會對應到命令列選項。

- **AdditionalIncludeDirectories**

     選擇性的 **String []** 參數。

     將目錄加入要在其中搜尋匯入的 IDL 檔案、包含的標頭檔及應用程式組態檔 (ACF) 的目錄清單。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/I** 選項。

- **AdditionalOptions**

     選擇性的 **字串** 參數。

     命令列選項清單。 例如，/ \<option1>  / \<option2>  / \<option#> 。 使用此參數，來指定任何其他 MIDL 工作參數未表示的命令列選項。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考)。

- **ApplicationConfigurationMode**

     選擇性的 **布林值** 參數。

     如果是 `true`，可讓您在 IDL 檔案中使用某些 ACF 關鍵字。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/app_config** 選項。

- **ClientStubFile**

     選擇性的 **字串** 參數。

     指定 RPC 介面的用戶端 Stub 檔案名稱。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/cstub** 選項。 另請參閱此表格中的 **ServerStubFile** 參數。

- **CPreprocessOptions**

     選擇性的 **字串** 參數。

     指定要傳遞至 C/C++ 前置處理器的選項。 指定以空格分隔的前置處理器選項清單。 必須包含 `/E` 選項。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/cpp_opt** 選項。

- **DefaultCharType**

     選擇性的 **字串** 參數。

     指定預設的字元類型，C 編譯器將使用此類型來編譯產生的程式碼。

     指定下列其中一個值；每個值會分別對應至一個命令列選項。

    |值|命令列選項|
    |-----------|--------------------------|
    |**簽署**|**/char signed**|
    |**符號**|**/char unsigned**|
    |**Ascii**|**/char ascii7**|

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/char** 選項。

- **DllDataFileName**

     選擇性的 **字串** 參數。

     指定針對 Proxy DLL 所產生之 *dlldata* 檔案的檔名。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/dlldata** 選項。

- **EnableErrorChecks**

     選擇性的 **字串** 參數。

     指定錯誤檢查的類型，產生的 Stub 將會在執行階段加以執行。

     指定下列其中一個值；每個值會分別對應至一個命令列選項。

    |值|命令列選項|
    |-----------|--------------------------|
    |**None**|**/error none**|
    |**EnableCustom**|**/error**|
    |**全部**|**/error all**|

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/error** 選項。

- **ErrorCheckAllocations**

     選擇性的 **布林值** 參數。

     如果是 `true`，即會檢查有無記憶體不足的錯誤。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/error allocation** 選項。

- **ErrorCheckBounds**

     選擇性的 **布林值** 參數。

     如果是 `true`，即會根據傳輸長度規格來檢查不一致的各種陣列大小。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/error bounds_check** 選項。

- **ErrorCheckEnumRange**

     選擇性的 **布林值** 參數。

     如果是 `true`，即會檢查列舉值位於允許的範圍內。

     如需詳細資訊，請參閱 midl.exe 的命令列說明 (**/?**) 中的 **/error enum** 選項。

- **ErrorCheckRefPointers**

     選擇性的 **布林值** 參數。

     如果是 `true`，即會檢查未將任何 Null 參考指標傳遞到用戶端 Stub。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/error ref** 選項。

- **ErrorCheckStubData**

     選擇性的 **布林值** 參數。

     如果是 `true`，即會產生 Stub，來攔截伺服器端的解除封送處理例外狀況，並將它們傳播回用戶端。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/error stub_data** 選項。

- **GenerateClientFiles**

     選擇性的 **字串** 參數。

     指定編譯器是否要針對 RPC 介面產生用戶端的 C 原始程式檔。

     指定下列其中一個值；每個值會分別對應至一個命令列選項。

    |值|命令列選項|
    |-----------|--------------------------|
    |**None**|**/client none**|
    |**存根**|**/client stub**|

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/client** 選項。

- **GenerateServerFiles**

     選擇性的 **字串** 參數。

     指定編譯器是否要針對 RPC 介面產生伺服器端的 C 原始程式檔。

     指定下列其中一個值；每個值會分別對應至一個命令列選項。

    |值|命令列選項|
    |-----------|--------------------------|
    |**None**|**/server none**|
    |**存根**|**/server stub**|

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/server** 選項。

- **GenerateStublessProxies**

     選擇性的 **布林值** 參數。

     如果是 `true`，即會透過物件介面的 Stubless Proxies 一併產生完全解譯的 Stub。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/Oicf** 選項。

- **GenerateTypeLibrary**

     選擇性的 **布林值** 參數。

     若為 `true`，就不會產生類型程式庫 (*.tlb*) 檔案。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/notlb** 選項。

- **HeaderFileName**

     選擇性的 **字串** 參數。

     指定所產生的標頭檔名稱。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/h** 或 **/header** 選項。

- **IgnoreStandardIncludePath**

     選擇性的 **布林值** 參數。

     如果是 `true`，則 MIDL 工作只會搜尋使用 **AdditionalIncludeDirectories** 參數指定的目錄，並忽略目前的目錄以及 INCLUDE 環境變數所指定的目錄。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/no_def_idir** 選項。

- **InterfaceIdentifierFileName**

     選擇性的 **字串** 參數。

     針對 COM 介面指定「介面識別項檔」的名稱。 這會覆寫透過在 IDL 檔名中加入 "_i.c" 而取得的預設名稱。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/iid** 選項。

- **LocaleID**

     選擇性的 **int** 參數。

     指定「地區設定識別項」，讓您能夠在輸入檔、檔案名稱和目錄路徑中使用國際字元。 指定十進位的地區設定識別項。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/lcid** 選項。 另請參閱[地區設定識別碼](/windows/desktop/intl/locale-identifiers)。

- **MkTypLibCompatible**

     選擇性的 **布林值** 參數。

     若為 `true`，則輸入檔的格式必須與 mktyplib.exe 2.03 版相容。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/mktyplib203** 選項。 另請參閱 MSDN 網站上的 [ODL 檔案語法](/previous-versions/windows/desktop/automat/odl-file-syntax)。

- **OutputDirectory**

     選擇性的 **字串** 參數。

     指定 MIDL 工作寫入輸出檔的預設目錄。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/out** 選項。

- **PreprocessorDefinitions**

     選擇性的 **String []** 參數。

     指定一或多個「定義」；也就是要傳遞到 C 前置處理器的名稱和選擇性的值，如同透過 `#define` 指示詞。 每個定義的格式是 *name[=value]*。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/D** 選項。 另請參閱此表格中的 **UndefinePreprocessorDefinitions** 參數。

- **ProxyFileName**

     選擇性的 **字串** 參數。

     針對 COM 介面指定介面 Proxy 檔案的名稱。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/proxy** 選項。

- **RedirectOutputAndErrors**

     選擇性的 **字串** 參數。

     將輸出 (例如錯誤訊息和警告) 從標準輸出重新導向到指定的檔案。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/o** 選項。

- **ServerStubFile**

     選擇性的 **字串** 參數。

     指定 RPC 介面的伺服器 Stub 檔案名稱。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/sstub** 選項。 另請參閱此表格中的 **ClientStubFile** 參數。

- **來源**

     必要的 `ITaskItem[]` 參數。

     指定以空格分隔的原始程式檔清單。

- **StructMemberAlignment**

     選擇性的 **字串** 參數。

     指定目標系統中結構的對應儲存 (「封裝層級」)。

     指定下列其中一個值；每個值會分別對應至一個命令列選項。

    |值|命令列選項|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**1**|**/Zp1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/Zp8**|

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/Zp** 選項。 **/Zp** 選項相當於 **/pack** 選項和較舊的 **/align** 選項。

- **SuppressCompilerWarnings**

     選擇性的 **布林值** 參數。

     如果是 `true`，即會隱藏來自 MIDL 工作的警告訊息。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/no_warn** 選項。

- **SuppressStartupBanner**

     選擇性的 `Boolean` 參數。

     如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/nologo** 選項。

- **TargetEnvironment**

     選擇性的 **字串** 參數。

     指定執行應用程式的環境。

     指定下列其中一個值；每個值會分別對應至一個命令列選項。

    |值|命令列選項|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**Win32**|**/env win32**|
    |**Itanium**|**/env ia64**|
    |**64**|**/env x64**|

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/env** 選項。

- **TrackerLogDirectory**

     選擇性的 `String` 參數。

     指定儲存此工作之追蹤記錄檔的中繼目錄。

- **TypeLibFormat**

     選擇性的 **字串** 參數。

     指定類型程式庫檔案的格式。

     指定下列其中一個值；每個值會分別對應至一個命令列選項。

    |值|命令列選項|
    |-----------|--------------------------|
    |**NewFormat**|**/newtlb**|
    |**OldFormat**|**/oldtlb**|

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/newtlb** 和 **/oldtlb** 選項。

- **TypeLibraryName**

     選擇性的 **字串** 參數。

     指定類型程式庫檔案的名稱。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/tlb** 選項。

- **UndefinePreprocessorDefinitions**

     選擇性的 **String []** 參數。

     將名稱傳遞到 C 前置處理器 (如同透過 `#undefine` 指示詞)，藉以移除名稱所有先前的定義。 指定一或多個先前定義的名稱。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/U** 選項。 另請參閱此表格中的 **PreprocessorDefinitions** 參數。

- **ValidateAllParameters**

     選擇性的 `Boolean` 參數。

     如果是 `true`，即會產生其他錯誤檢查資訊，以便在執行階段用來執行完整性檢查。 如果是 `false`，則不會產生錯誤檢查資訊。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/robust** 和 **/no_robust** 選項。

- **WarnAsError**

     選擇性的 `Boolean` 參數。

     如果是 `true`，即會將所有警告視為錯誤。

     如果未指定 **WarningLevel** MIDL 工作參數，就會將預設層級 (層級 1) 上的警告視為錯誤。

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/WX** 選項。 另請參閱此表格中的 **WarningLevel** 參數。

- **WarningLevel**

     選擇性的 **字串** 參數。

     指定要發出的警告嚴重性 (「警告層級」)。 值為 0，就會不發出任何警告。 否則，如果其警告層級是小於或等於指定值的數字，就會發出警告。

     指定下列其中一個值；每個值會分別對應至一個命令列選項。

    |值|命令列選項|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     如需詳細資訊，請參閱 [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference) (MIDL 命令列參考) 中的 **/W** 選項。 另請參閱此表格中的 **WarnAsError** 參數。

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)

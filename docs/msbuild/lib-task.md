---
title: LIB 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 LIB 工作包裝 Microsoft 32 位程式庫管理員工具 lib.exe，此工具會建立和管理 COFF 物件檔的程式庫。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), LIB task
- LIB task (MSBuild (C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2141818c13a187b8afddf337aa11677097940f23
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913734"
---
# <a name="lib-task"></a>LIB 工作

包裝 Microsoft 32 位程式庫管理員工具 *lib.exe*。 程式庫管理員會建立並管理通用物件檔案格式 (COFF) 物件檔的程式庫。 程式庫管理員也可以建立匯出檔和匯入程式庫，以參考匯出的定義。 如需詳細資訊，請參閱 [lib 參考](/cpp/build/reference/lib-reference) 和執行 [lib](/cpp/build/reference/running-lib)。

## <a name="parameters"></a>參數

 下表描述 **LIB** 工作的參數。 大部分的工作參數會對應至命令列選項。

|參數|Description|
|---------------|-----------------|
|**AdditionalDependencies**|選擇性的 **String []** 參數。<br /><br /> 指定要加入至命令列的其他項目。|
|**AdditionalLibraryDirectories**|選擇性的 **String []** 參數。<br /><br /> 覆寫環境程式庫路徑。 指定目錄名稱。<br /><br /> 如需詳細資訊，請參閱 [/LIBPATH (其他 Libpath)](/cpp/build/reference/libpath-additional-libpath)。|
|**AdditionalOptions**|選擇性的 **字串** 參數。<br /><br /> 命令列上指定的 *lib.exe* 選項清單。 例如，/ \<option1>  / \<option2>  / \<option#> 。 使用這個參數來指定任何其他 **LIB** 工作參數未表示的 *lib.exe* 選項。<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib)。|
|**DisplayLibrary**|選擇性的 **字串** 參數。<br /><br /> 顯示輸出程式庫的相關資訊。 指定檔案名稱，可將資訊重新導向至該檔案。 指定 "CON" 或不指定任何項目，可將資訊重新導向至主控台。<br /><br /> 此參數對應于 *lib.exe* 的 **/list** 選項。|
|**ErrorReporting**|選擇性的 **字串** 參數。<br /><br /> 指定當 *lib.exe* 在執行時間失敗時，如何將內部錯誤資訊傳送給 Microsoft。<br /><br /> 指定下列其中一個值；每個值會分別對應至一個命令列選項。<br /><br /> -   **NoErrorReport**  - **/ERRORREPORT：無**<br />-   **PromptImmediately**  - **/ERRORREPORT： PROMPT**<br />-   **QueueForNextLogin**  - **/ERRORREPORT： QUEUE**<br />-   **SendErrorReport**  - **/ERRORREPORT：傳送**<br /><br /> 如需詳細資訊，請參閱 [執行 LIB](/cpp/build/reference/running-lib) 中的 **/ERRORREPORT** 命令列選項。|
|**ExportNamedFunctions**|選擇性的 **String []** 參數。<br /><br /> 指定一或多個要匯出的函式。<br /><br /> 此參數對應于 *lib.exe* 的 **/export：** 選項。|
|**ForceSymbolReferences**|選擇性的 **字串** 參數。<br /><br /> 強制 *lib.exe* 包含指定符號的參考。<br /><br /> 此參數對應于 *lib.exe* 的 **/INCLUDE：** 選項。|
|**IgnoreAllDefaultLibraries**|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true` 為，則會在解析外部參考時，從 *lib.exe* 搜尋的程式庫清單中移除所有預設的程式庫。<br /><br /> 此參數對應于 *lib.exe* 之 **/NODEFAULTLIB** 選項的無參數形式。|
|**IgnoreSpecificDefaultLibraries**|選擇性的 **String []** 參數。<br /><br /> 在解析外部參考時，從 *lib.exe* 搜尋的程式庫清單中移除指定的程式庫。<br /><br /> 此參數會對應至採用引數之 *lib.exe* 的 **/NODEFAULTLIB** 選項 `library` 。|
|**LinkLibraryDependencies**|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，會指定要自動連結專案相依性的程式庫輸出。|
|**LinkTimeCodeGeneration**|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，會指定在連結時產生程式碼。<br /><br /> 此參數對應于 *lib.exe* 的 **/LCTG** 選項。|
|**MinimumRequiredVersion**|選擇性的 **字串** 參數。<br /><br /> 指定子系統的最小必要版本。 在 0 到 65535 的範圍中指定以逗號分隔的十進位數字清單。|
|**ModuleDefinitionFile**|選擇性的 **字串** 參數。<br /><br /> 指定模組定義檔 (*.def*) 的名稱。<br /><br /> 此參數會對應至採用引數之 *lib.exe* 的 **/DEF** 選項 `filename` 。|
|**名稱**|選擇性的 **字串** 參數。<br /><br /> 在建置匯入程式庫時，指定正在建置之匯入程式庫的 DLL 名稱。<br /><br /> 此參數會對應至採用引數之 *lib.exe* 的 **/NAME** 選項 `filename` 。|
|**OutputFile**|選擇性的 **字串** 參數。<br /><br /> 覆寫 *lib.exe* 建立之程式的預設名稱和位置。<br /><br /> 此參數會對應至採用引數之 *lib.exe* 的 **/out** 選項 `filename` 。|
|**RemoveObjects**|選擇性的 **String []** 參數。<br /><br /> 省略輸出程式庫中的指定物件。 *Lib.exe* 建立輸出程式庫，方法是將所有物件 () 的物件檔案或程式庫中，然後刪除此選項所指定的任何物件。<br /><br /> 此參數會對應至採用引數之 *lib.exe* 的 **/remove** 選項 `membername` 。|
|**來源**|必要的 `ITaskItem[]` 參數。<br /><br /> 指定以空格分隔的原始程式檔清單。|
|**子系統**|選擇性的 **字串** 參數。<br /><br /> 指定可執行檔的環境。 子系統的選擇會影響進入點符號或進入點函式。<br /><br /> 指定下列其中一個值；每個值會分別對應至一個命令列選項。<br /><br /> -   **主控台**  - **/SUBSYSTEM：主控台**<br />-   **Windows**  - **/SUBSYSTEM： WINDOWS**<br />-   **原生**  - **/SUBSYSTEM： NATIVE**<br />-   **EFI 應用程式**  - **/SUBSYSTEM： EFI_APPLICATION**<br />-   **EFI 開機服務驅動程式**  - **/SUBSYSTEM： EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM**  - **/SUBSYSTEM： EFI_ROM**<br />-   **EFI 運行**  -  時間 **/SUBSYSTEM： EFI_RUNTIME_DRIVER**<br />-   **WindowsCE**  - **/SUBSYSTEM： WINDOWSCE**<br />-   **POSIX**  - **/SUBSYSTEM： POSIX**<br /><br /> 如需詳細資訊，請參閱 [/SUBSYSTEM (指定子系統)](/cpp/build/reference/subsystem-specify-subsystem)。|
|**SuppressStartupBanner**|選擇性的 **布林值** 參數。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請參閱 [執行 LIB](/cpp/build/reference/running-lib) 中的 **/NOLOGO** 選項。|
|**TargetMachine**|選擇性的 **字串** 參數。<br /><br /> 指定程式或 DLL 的目標平台。<br /><br /> 指定下列其中一個值；每個值會分別對應至一個命令列選項。<br /><br /> -   **MachineARM**  - **/MACHINE： ARM**<br />-   **MachineEBC**  - **/MACHINE： EBC**<br />-   **MachineIA64**  - **/MACHINE： IA64**<br />-   **MachineMIPS**  - **/MACHINE： MIPS**<br />-   **MachineMIPS16**  - **/MACHINE： MIPS16**<br />-   **MachineMIPSFPU**  -**/MACHINE： MIPSFPU**<br />-   **MachineMIPSFPU16**  - **/MACHINE： MIPSFPU16**<br />-   **MachineSH4**  - **/MACHINE： SH4**<br />-   **MachineTHUMB**  - **/MACHINE： THUMB**<br />-   **MachineX64**  - **/MACHINE： X64**<br />-   **MachineX86**  - **/MACHINE： X86**<br /><br /> 如需詳細資訊，請參閱 [/MACHINE (指定目標平臺) ](/cpp/build/reference/machine-specify-target-platform)。|
|**TrackerLogDirectory**|選擇性的 **字串** 參數。<br /><br /> 指定追蹤器記錄檔的目錄。|
|**TreatLibWarningAsErrors**|選擇性的 **布林值** 參數。<br /><br /> 如果 `true` 為，則當 *lib.exe* 產生警告時，會導致 **LIB** 工作不產生輸出檔。 如果是 `false`，則會產生輸出檔。<br /><br /> 如需詳細資訊，請參閱 [執行 LIB](/cpp/build/reference/running-lib) 中的 **/WX** 選項。|
|**UseUnicodeResponseFiles**|選擇性的 **布林值** 參數。<br /><br /> 如果是 `true`，會指示專案系統在管理員繁衍時產生 UNICODE 回應檔。 在專案中的檔案具有 UNICODE 路徑時指定 `true`。|
|**詳細資訊**|選擇性的 **布林值** 參數。<br /><br /> 如果 `true` 為，則會顯示會話進度的詳細資料，這包括所加入之 *.obj* 檔案的名稱。 資訊會傳送至標準輸出，並且可重新導向至檔案。<br /><br /> 如需詳細資訊，請參閱 [執行 LIB](/cpp/build/reference/running-lib) 中的 **/VERBOSE** 選項。|

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
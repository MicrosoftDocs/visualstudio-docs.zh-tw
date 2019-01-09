---
title: LIB 工作 | Microsoft Docs
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
- MSBuild (Visual C++), LIB task
- LIB task (MSBuild (Visual C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54a9fc4a75d49699087f7fb2ca80c3b8c17ddc8f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922016"
---
# <a name="lib-task"></a>LIB 工作
包裝 Microsoft 32 位元程式庫管理員工具 *lib.exe*。 程式庫管理員會建立並管理通用物件檔案格式 (COFF) 物件檔的程式庫。 程式庫管理員也可以建立匯出檔和匯入程式庫，以參考匯出的定義。 如需詳細資訊，請參閱 [LIB 參考](/cpp/build/reference/lib-reference)和[執行 LIB](/cpp/build/reference/running-lib)。  
  
## <a name="parameters"></a>參數  
 下表描述 **LIB** 工作的參數。 大部分的工作參數會對應至命令列選項。  
  
|參數|說明|  
|---------------|-----------------|  
|**AdditionalDependencies**|選擇性的 **String[]** 參數。<br /><br /> 指定要加入至命令列的其他項目。|  
|**AdditionalLibraryDirectories**|選擇性的 **String[]** 參數。<br /><br /> 覆寫環境程式庫路徑。 指定目錄名稱。<br /><br /> 如需詳細資訊，請參閱 [/LIBPATH (其他 Libpath)](/cpp/build/reference/libpath-additional-libpath)。|  
|**AdditionalOptions**|選擇性的 **String** 參數。<br /><br /> 指定於命令列上的 *lib.exe* 選項清單。 例如，/\<option1> /\<option2> /\<option#>。 使用此參數可指定任何其他 **LIB** 工作參數未表示的 *lib.exe* 選項。<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib)。|  
|**DisplayLibrary**|選擇性的 **String** 參數。<br /><br /> 顯示輸出程式庫的相關資訊。 指定檔案名稱，可將資訊重新導向至該檔案。 指定 "CON" 或不指定任何項目，可將資訊重新導向至主控台。<br /><br /> 此參數對應於 *lib.exe* 的 **/LIST** 選項。|  
|**ErrorReporting**|選擇性的 **String** 參數。<br /><br /> 指定 *lib.exe* 在執行階段失敗時如何將內部錯誤資訊傳送至 Microsoft。<br /><br /> 指定下列其中一個值；每個值會分別對應至一個命令列選項。<br /><br /> -   **NoErrorReport** - **/ERRORREPORT:NONE**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **/ERRORREPORT:SEND**<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib) 中的 **/ERRORREPORT** 命令列選項。|  
|**ExportNamedFunctions**|選擇性的 **String[]** 參數。<br /><br /> 指定一或多個要匯出的函式。<br /><br /> 此參數對應於 *lib.exe* 的 **/EXPORT:** 選項。|  
|**ForceSymbolReferences**|選擇性的 **String** 參數。<br /><br /> 強制 *lib.exe* 包含指定符號的參考。<br /><br /> 此參數對應於 *lib.exe* 的 **/INCLUDE:** 選項。|  
|**IgnoreAllDefaultLibraries**|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，則會在 lib.exe 解析外部參考時，從 *lib.exe* 所搜尋的程式庫清單中移除所有的預設程式庫。<br /><br /> 此參數對應於 *lib.exe* 的無參數形式 **/NODEFAULTLIB** 選項。|  
|**IgnoreSpecificDefaultLibraries**|選擇性的 **String[]** 參數。<br /><br /> 在 lib.exe 解析外部參考時，從 *lib.exe* 所搜尋的程式庫清單中移除指定的程式庫。<br /><br /> 此參數對應於 *lib.exe* 使用 `library` 引數的 **/NODEFAULTLIB** 選項。|  
|**LinkLibraryDependencies**|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，會指定要自動連結專案相依性的程式庫輸出。|  
|**LinkTimeCodeGeneration**|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，會指定在連結時產生程式碼。<br /><br /> 此參數對應於 *lib.exe* 的 **/LCTG** 選項。|  
|**MinimumRequiredVersion**|選擇性的 **String** 參數。<br /><br /> 指定子系統的最小必要版本。 在 0 到 65535 的範圍中指定以逗號分隔的十進位數字清單。|  
|**ModuleDefinitionFile**|選擇性的 **String** 參數。<br /><br /> 指定模組定義檔 (*.def*) 的名稱。<br /><br /> 此參數對應於 *lib.exe* 使用 `filename` 引數的 **/DEF** 選項。|  
|**名稱**|選擇性的 **String** 參數。<br /><br /> 在建置匯入程式庫時，指定正在建置之匯入程式庫的 DLL 名稱。<br /><br /> 此參數對應於 *lib.exe* 使用 `filename` 引數的 **/NAME** 選項。|  
|**OutputFile**|選擇性的 **String** 參數。<br /><br /> 覆寫 *lib.exe* 所建立之程式的預設名稱和位置。<br /><br /> 此參數對應於 *lib.exe* 使用 `filename` 引數的 **/OUT** 選項。|  
|**RemoveObjects**|選擇性的 **String[]** 參數。<br /><br /> 省略輸出程式庫中的指定物件。 *Lib.exe* 會合併所有的物件 (不論位於目的檔或程式庫中) 以建立輸出程式庫，然後刪除任何由此選項指定的物件。<br /><br /> 此參數對應於 *lib.exe* 使用 `membername` 引數的 **/REMOVE** 選項。|  
|**Sources**|必要的 `ITaskItem[]` 參數。<br /><br /> 指定以空格分隔的原始程式檔清單。|  
|**SubSystem**|選擇性的 **String** 參數。<br /><br /> 指定可執行檔的環境。 子系統的選擇會影響進入點符號或進入點函式。<br /><br /> 指定下列其中一個值；每個值會分別對應至一個命令列選項。<br /><br /> -   **主控台** - **/SUBSYSTEM:CONSOLE**<br />-   **Windows** - **/SUBSYSTEM:WINDOWS**<br />-   **原生** - **/SUBSYSTEM:NATIVE**<br />-   **EFI 應用程式** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **EFI 開機服務驅動程式** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **EFI 執行階段** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX** - **/SUBSYSTEM:POSIX**<br /><br /> 如需詳細資訊，請參閱 [/SUBSYSTEM (指定子系統)](/cpp/build/reference/subsystem-specify-subsystem)。|  
|**SuppressStartupBanner**|選擇性的 **Boolean** 參數。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib) 中的 **/NOLOGO** 選項。|  
|**TargetMachine**|選擇性的 **String** 參數。<br /><br /> 指定程式或 DLL 的目標平台。<br /><br /> 指定下列其中一個值；每個值會分別對應至一個命令列選項。<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X64**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> 如需詳細資訊，請參閱 [/MACHINE (指定目標平台)](/cpp/build/reference/machine-specify-target-platform)。|  
|**TrackerLogDirectory**|選擇性的 **String** 參數。<br /><br /> 指定追蹤器記錄檔的目錄。|  
|**TreatLibWarningAsErrors**|選擇性的 **Boolean** 參數。<br /><br /> 如果是 `true`，會使 **LIB** 工作在 *lib.exe* 產生警告時不產生輸出檔。 如果是 `false`，則會產生輸出檔。<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib) 中的 **/WX** 選項。|  
|**UseUnicodeResponseFiles**|選擇性的 **Boolean** 參數。<br /><br /> 如果是 `true`，會指示專案系統在管理員繁衍時產生 UNICODE 回應檔。 在專案中的檔案具有 UNICODE 路徑時指定 `true`。|  
|**Verbose**|選擇性的 **Boolean** 參數。<br /><br /> 如果是 `true`，會顯示工作階段進度的詳細資料，其中包括所新增之 *.obj* 檔的名稱。 資訊會傳送至標準輸出，並且可重新導向至檔案。<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib) 中的 **/VERBOSE** 選項。|  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)
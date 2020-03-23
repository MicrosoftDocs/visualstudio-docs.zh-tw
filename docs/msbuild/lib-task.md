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
- MSBuild (C++), LIB task
- LIB task (MSBuild (C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5794d059a17f39531a7788895b604ae0e9590ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633586"
---
# <a name="lib-task"></a>LIB 工作

包裝微軟32位庫管理器工具 *，lib.exe*。 程式庫管理員會建立並管理通用物件檔案格式 (COFF) 物件檔的程式庫。 程式庫管理員也可以建立匯出檔和匯入程式庫，以參考匯出的定義。 有關詳細資訊，請參閱[LIB 引用](/cpp/build/reference/lib-reference)和[運行 LIB](/cpp/build/reference/running-lib)。

## <a name="parameters"></a>參數

 下表描述 **LIB** 工作的參數。 大部分的工作參數會對應至命令列選項。

|參數|描述|
|---------------|-----------------|
|**AdditionalDependencies**|可選**字串*** 參數。<br /><br /> 指定要加入至命令列的其他項目。|
|**AdditionalLibraryDirectories**|可選**字串*** 參數。<br /><br /> 覆寫環境程式庫路徑。 指定目錄名稱。<br /><br /> 如需詳細資訊，請參閱 [/LIBPATH (其他 Libpath)](/cpp/build/reference/libpath-additional-libpath)。|
|**AdditionalOptions**|可選**字串**參數。<br /><br /> 命令列上指定的*lib.exe*選項的清單。 例如，/\<option1> /\<option2> /\<option#>。 使用此參數可以指定不由任何其他**LIB**任務參數表示的*lib.exe*選項。<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib)。|
|**DisplayLibrary**|可選**字串**參數。<br /><br /> 顯示輸出程式庫的相關資訊。 指定檔案名稱，可將資訊重新導向至該檔案。 指定 "CON" 或不指定任何項目，可將資訊重新導向至主控台。<br /><br /> 此參數對應于*lib.exe*的 **/LIST**選項。|
|**錯誤報表**|可選**字串**參數。<br /><br /> 指定在*lib.exe*運行時發生故障時如何向 Microsoft 發送內部錯誤資訊。<br /><br /> 指定下列其中一個值；每個值會分別對應至一個命令列選項。<br /><br /> -   **無錯誤報表** - **/錯誤報表：無**<br />-   **立即提示/** - **錯誤報表：提示**<br />-   **佇列為下一個登錄** - **/錯誤報表：QUEUE**<br />-   **發送錯誤報表** - **/錯誤報表：發送**<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib) 中的 **/ERRORREPORT** 命令列選項。|
|**ExportNamedFunctions**|可選**字串*** 參數。<br /><br /> 指定一或多個要匯出的函式。<br /><br /> 此參數對應于 **/EXPORT：** *選項的 lib.exe*。|
|**ForceSymbolReferences**|可選**字串**參數。<br /><br /> 強制*lib.exe*以包含對指定符號的引用。<br /><br /> 此參數對應于 **/INCLUDE：** *自由.exe*的選項。|
|**IgnoreAllDefaultLibraries**|選擇性的 `Boolean` 參數。<br /><br /> 如果`true`中刪除*lib.exe*在解決外部引用時搜索的所有預設庫。<br /><br /> 此參數對應于*lib.exe*的 **/NODEFAULTLIB**選項的無參數形式。|
|**IgnoreSpecificDefaultLibraries**|可選**字串*** 參數。<br /><br /> 從*lib.exe*解析外部引用時搜索的庫清單中刪除指定的庫。<br /><br /> 此參數對應于取`library`參數的*lib.exe*的 **/NODEFAULTLIB**選項。|
|**LinkLibraryDependencies**|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，會指定要自動連結專案相依性的程式庫輸出。|
|**LinkTimeCodeGeneration**|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，會指定在連結時產生程式碼。<br /><br /> 此參數對應于*lib.exe*的 **/LCTG**選項。|
|**MinimumRequiredVersion**|可選**字串**參數。<br /><br /> 指定子系統的最小必要版本。 在 0 到 65535 的範圍中指定以逗號分隔的十進位數字清單。|
|**ModuleDefinitionFile**|可選**字串**參數。<br /><br /> 指定模組定義檔 *（.def）* 的名稱。<br /><br /> 此參數對應于取`filename`參數的*lib.exe*的 **/DEF**選項。|
|**名稱**|可選**字串**參數。<br /><br /> 在建置匯入程式庫時，指定正在建置之匯入程式庫的 DLL 名稱。<br /><br /> 此參數對應于取`filename`參數的*lib.exe*的 **/NAME**選項。|
|**輸出檔案**|可選**字串**參數。<br /><br /> 覆蓋*lib.exe*創建的程式的預設名稱和位置。<br /><br /> 此參數對應于取`filename`參數的*lib.exe*的 **/OUT**選項。|
|**RemoveObjects**|可選**字串*** 參數。<br /><br /> 省略輸出程式庫中的指定物件。 *Lib.exe*通過合併所有物件（無論是在目的檔還是庫中），然後刪除此選項指定的任何物件，創建輸出庫。<br /><br /> 此參數對應于取`membername`參數的*lib.exe*的 **/REMOVE**選項。|
|**來源**|必要的 `ITaskItem[]` 參數。<br /><br /> 指定以空格分隔的原始程式檔清單。|
|**子系統**|可選**字串**參數。<br /><br /> 指定可執行檔的環境。 子系統的選擇會影響進入點符號或進入點函式。<br /><br /> 指定下列其中一個值；每個值會分別對應至一個命令列選項。<br /><br /> -   **主控台** - **/子系統：主控台**<br />-   **視窗** - **/子系統：視窗**<br />-   **本機** - **/子系統：本機**<br />-   **EFI 應用程式** - **/子系統：EFI_APPLICATION**<br />-   **EFI 啟動服務驅動程式** - **/SUBSYSTEM：EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM：EFI_ROM**<br />-   **EFI 運行時** - **/子系統：EFI_RUNTIME_DRIVER**<br />-   **視窗****/子系統：視窗** - <br />-   **POSIX/** - **子系統：PO6**<br /><br /> 如需詳細資訊，請參閱 [/SUBSYSTEM (指定子系統)](/cpp/build/reference/subsystem-specify-subsystem)。|
|**SuppressStartupBanner**|可選**布林參數**。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib) 中的 **/NOLOGO** 選項。|
|**TargetMachine**|可選**字串**參數。<br /><br /> 指定程式或 DLL 的目標平台。<br /><br /> 指定下列其中一個值；每個值會分別對應至一個命令列選項。<br /><br /> -   **機器/** - **機器：ARM**<br />-   **機機/** - **機：EBC**<br />-   **機器64** - **/MACHINE：IA64**<br />-   **機器MIPS/** - **機器：MIPS**<br />-   **機器MIPS16** - **/機器：MIPS16**<br />-   **機器MIPSFPU/** -**機器：MIPSFPU**<br />-   **機器MIPSFPU16/MACHINE：MIPSFPU16**  -  ** **<br />-   **機器SH4** - **/機器：SH4**<br />-   **機器：** - **拇指/機器：拇指**<br />-   **機器X64** - **/MACHINE：X64**<br />-   **機器X86** - **/MACHINE：X86**<br /><br /> 有關詳細資訊，請參閱[/MACHINE（指定目標平臺）](/cpp/build/reference/machine-specify-target-platform)。|
|**TrackerLogDirectory**|可選**字串**參數。<br /><br /> 指定追蹤器記錄檔的目錄。|
|**TreatLibWarningAsErrors**|可選**布林參數**。<br /><br /> 如果`true`， 如果 ， 如果**LIB**任務不生成輸出檔案，如果*lib.exe*生成警告。 如果是 `false`，則會產生輸出檔。<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib) 中的 **/WX** 選項。|
|**UseUnicodeResponseFiles**|可選**布林參數**。<br /><br /> 如果是 `true`，會指示專案系統在管理員繁衍時產生 UNICODE 回應檔。 在專案中的檔案具有 UNICODE 路徑時指定 `true`。|
|**詳細**|可選**布林參數**。<br /><br /> 如果`true`顯示有關會話進度的詳細資訊;如果 ，請顯示有關會話進度的詳細資訊。這包括要添加的 *.obj*檔的名稱。 資訊會傳送至標準輸出，並且可重新導向至檔案。<br /><br /> 如需詳細資訊，請參閱[執行 LIB](/cpp/build/reference/running-lib) 中的 **/VERBOSE** 選項。|

## <a name="see-also"></a>另請參閱

- [任務引用](../msbuild/msbuild-task-reference.md)
---
title: MSBuild 命令列參考 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb95da599e6362ad32c0ef94dcf9c184269ddedf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633404"
---
# <a name="msbuild-command-line-reference"></a>MSBuild 命令列參考

在使用 *MSBuild.exe* 來建置專案或方案檔時，您可以包含數個參數來指定程序的各個層面。

每個參數都以兩種形式提供：-switch 和 /switch。 本文件僅示範 -switch 形式。 參數不區分大小寫。 如果從 Windows 命令提示符以外的 shell 運行 MSBuild，則交換器的參數清單（由分號或逗號分隔）可能需要單引號或雙引號，以確保清單傳遞給 MSBuild，而不是由 shell 解釋。

## <a name="syntax"></a>語法

```cmd
MSBuild.exe [Switches] [ProjectFile]
```

## <a name="arguments"></a>引數

|引數|描述|
|--------------|-----------------|
|`ProjectFile`|在所指定的專案檔中建置目標。 如果您未指定專案檔，MSBuild 會搜尋目前工作目錄中結尾為 *proj* 的檔案名稱副檔名，並使用該檔案。 您也可以為這個引數指定 Visual Studio 方案檔。|

## <a name="switches"></a>交換器

|Switch|簡短形式|描述|
|------------|----------------|-----------------|
|-詳細摘要|-ds|在組建記錄檔結尾顯示關於所建置組態及其如何排程至節點的詳細資訊。|
|-圖形生成*：`True` `False`或 ||-圖：`True`或`False`*|使 MSBuild 構造和生成專案圖。 構造圖形涉及標識專案引用以形成依賴關係。 構建該圖形涉及嘗試在引用專案之前生成專案引用，這不同于傳統的 MSBuild 計畫。|
|-help|/? 或 -h|顯示使用資訊。 下列命令是範例：<br /><br /> `msbuild.exe -?`|
|-忽略專案擴展：`extensions`|-ignore: `extensions`|決定要建置哪個專案檔後，請忽略指定的副檔名。 使用分號或逗號分隔多個副檔名，如下列範例所示：<br /><br /> `-ignoreprojectextensions:.vcproj,.sln`|
|-互動*：`True` `False`或 ||-|指示允許生成中的操作與使用者交互。  在不需要交互的自動方案中，請勿使用此參數。 指定 -互動式與指定 -互動式：true 相同。  使用 參數重寫來自回應檔的值。
|-隔離專案*：`True` `False`或 ||-隔離*：`True` `False`或 ||使 MSBuild 孤立地生成每個專案。 這是一種更加嚴格的 MSBuild 模式，因為它要求專案圖在評估時可靜態發現，但在構建大型專案集時可以改進計畫並減少記憶體開銷。|
|-maxCpuCount*：`number`||-m[:`number`]|指定要在建置時使用的並行處理最大數目。 如果您未包含此參數，預設值為 1。 如果您包含此參數但未指定值，MSBuild 將會使用電腦上的處理器最大數目。 如需詳細資訊，請參閱[同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。<br /><br /> 下列範例會指示 MSBuild 使用三個 MSBuild 處理程序來建置，這可在同一時間建置三個專案：<br /><br /> `msbuild myproject.proj -maxcpucount:3`|
|-無自動回應|-noautorsp|不要自動包含任何 *MSBuild.rsp* 檔案。|
|-nodeReuse:`value`|-nr:`value`|啟用或停用 MSBuild 節點的重複使用功能。 您可以指定下列值：<br /><br /> -   **確實如此**。 組建完成後保留節點，以便後續組建可以加以使用 (預設值)。<br />-   **假**。 在組建完成後不保留節點。<br /><br /> 節點對應至執行中專案。 如果您包含 **-maxcpucount** 參數，就能同時執行多個節點。|
|-nologo||不要顯示程式啟始資訊或著作權訊息。|
|<a name="preprocess"></a>-預處理*：`filepath`||-pp[:`filepath`]|由內嵌在組建期間匯入的所有檔案，並標上其界限標記，藉此建立單一彙總的專案檔。 您可以使用此參數更輕鬆地判斷正在匯入哪些檔案、從哪裡匯入檔案，以及哪些檔案形成組建。 使用這個參數時，並不會建置專案。<br /><br /> 如果您指定 `filepath`，則彙總的專案檔會是檔案的輸出。 否則，輸出會顯示在主控台視窗中。<br /><br /> 如需如何使用 `Import` 項目來將專案檔插入另一個專案檔的資訊，請參閱 [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md) 和[如何：在多個專案檔中使用相同的目標](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)。|
|-輸出結果緩存[：快取檔案]|-orc_：快取檔案*|輸出快取檔案，其中 MSBuild 將在生成結束時寫入其生成結果緩存的內容。 設置此功能也會打開隔離生成（隔離）。|
|-簡介評價：`<file>`|-|設定檔 MSBuild 計算並將結果寫入指定的檔。 如果指定檔的副檔名為".md"，則結果以標記格式生成。 否則，將生成與選項卡分隔的檔。|
|-property:`name`=`value`|-p:`name`=`value`|設定或覆寫所指定的專案層級屬性，其中 `name` 是屬性名稱，而 `value` 是屬性值。 分別指定每個屬性，或使用分號或逗號分隔多個屬性，如下列範例所示：<br /><br /> `-property:WarningLevel=2;OutDir=bin\Debug`|
|-restore|-r|在建置實際目標前執行 `Restore` 目標。|
|-恢復財產：`name=value`|-rp：`name=value`|僅在還原期間設置或重寫這些專案級屬性，並且不使用與 -property 參數一起指定的屬性。 `name`是屬性名稱，`value`是屬性值。 使用分號或逗號分隔多個屬性，或分別指定每個屬性。|
|-target:`targets`|-t:`targets`|在專案中建置指定的目標。 分別指定每個目標，或使用分號或逗號分隔多個目標，如下列範例所示：<br /><br /> `-target:PrepareResources;Compile`<br /><br /> 如果您使用這個參數指定任何目標，便會執行這些目標，而不是專案檔中 `DefaultTargets` 屬性的任何目標。 如需詳細資訊，請參閱[目標建置順序](../msbuild/target-build-order.md)和[如何：指定要優先建置的目標](../msbuild/how-to-specify-which-target-to-build-first.md)。<br /><br /> 目標是一組工作。 如需詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。|
|-工具版本：`version`|-tv:`version`|指定用來建置專案的工具組版本，如下列範例所示：`-toolsversion:3.5`<br /><br /> 使用此參數，即可建置專案，並指定有別於 [Project 項目 (MSBuild)](../msbuild/project-element-msbuild.md) 中所指定的版本。 如需詳細資訊，請參閱[覆寫 ToolsVersion 設定](../msbuild/overriding-toolsversion-settings.md)。<br /><br /> 若是 MSBuild 4.5，您可以為 `version` 指定下列值：2.0、3.5 和 4.0。 如果您指定 4.0，則 `VisualStudioVersion` 組建屬性會指定要使用哪個子工具組。 如需詳細資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) 的＜子工具組＞一節。<br /><br /> 工具組包含用於建置應用程式的工作、目標和工具。 工具包括編譯器，例如 *csc.exe* 和 vbc.exe**。 如需工具組的詳細資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)、[標準和自訂工具組的組態](../msbuild/standard-and-custom-toolset-configurations.md)及[多目標](../msbuild/msbuild-multitargeting-overview.md)。 **注意：** 工具組版本與目標 Framework 的版本不同，目標 Framework 版本是建置專案以在其上方執行的目標 .NET Framework 版本。 如需詳細資訊，請參閱[目標 Framework 和目標平台](../msbuild/msbuild-target-framework-and-target-platform.md)。|
|-validate:[`schema`]|-val[`schema`]|驗證專案檔，如果驗證成功，則會建置專案。<br /><br /> 如果您沒有指定 `schema`，專案會針對預設結構描述進行驗證。<br /><br /> 如果您指定 `schema`，專案會針對您指定的結構描述進行驗證。<br /><br /> 下列設定為範例：`-validate:MyExtendedBuildSchema.xsd`|
|-verbosity:`level`|-v:`level`|指定要在組建記錄檔中顯示的資訊量。 每個記錄器都會顯示根據您為該記錄器所設詳細資訊層級的事件。<br /><br /> 您可以`q[uiet]`指定以下詳細級別： 、 `m[inimal]`、（`n[ormal]`預設）、`d[etailed]`和`diag[nostic]`。<br /><br /> 下列設定為範例：`-verbosity:quiet`
|-version|-ver|只顯示版本資訊。 不會建置專案。|
|@`file`||從文字檔中插入命令列參數。 如果您有多個檔案，請個別指定。 如需詳細資訊，請參閱[回應檔](../msbuild/msbuild-response-files.md)。|
|-警告錯誤*：`code`|`;code2`|-錯誤`:code`]`;code2`||要視為錯誤的警告代碼清單。  使用分號或逗號分隔多個警告代碼。 要將所有警告視為錯誤，請使用沒有值的開關。 當警告被視為錯誤時，目標將繼續執行，就好像它是警告，但整個生成失敗。<br/><br/>範例： `-err:MSB4130`|
|-警告訊息*：`code`|`;code2`|-不警告*`code`|`;code2`|要視為低重要性消息的警告代碼清單。  使用分號或逗號分隔多個警告代碼。<br/><br/>範例： `-noWarn:MSB3026`|

### <a name="switches-for-loggers"></a>記錄器的參數

|Switch|簡短形式|描述|
|------------|----------------|-----------------|
|-二進位記錄器：[日誌檔]`output.binlog`<br/>[;專案導入[無，嵌入，ZipFile]]|-bl|將所有建置事件序列化為壓縮的二進位檔案。 根據預設，檔案位於目前目錄中，並命名為 *msbuild.binlog*。 二進位記錄是建置程序的詳細描述，稍後可用來重構文字記錄並供其他分析工具所使用。 二進位記錄通常是 10-20x 小於最詳細的文字診斷層級記錄，但包含詳細資訊。<br /><br />二進位記錄器預設會收集專案檔的來源文字，包含在建置期間發生的所有已匯入的專案和目標檔案。 選擇性 `ProjectImports` 參數控制此行為：<br /><br /> -   **ProjectImports=None**. 不收集專案匯入。<br /> -   **ProjectImports=Embed**. 在記錄檔中內嵌專案匯入 (預設值)。<br /> -   **ProjectImports=ZipFile**. 將專案檔案保存到*\<輸出>.projectimports.zip，* 其中\<輸出>與二進位日誌檔案名稱同名。<br /><br />ProjectImports 的預設設定為 Embed。<br />**注意**：記錄器不會收集非 MSBuild 原始程式檔，例如 *.cs*、*.cpp* 等。<br />「播放」*.binlog* 檔案的方式是將它傳遞至 *msbuild.exe* 作為引數，而不是專案/方案。 其他記錄器將會收到記錄檔中所包含的資訊，就像發生原始組建一樣。 您可以閱讀更多有關二進位記錄檔及其使用方式，　網址為：https://github.com/Microsoft/msbuild/wiki/Binary-Log <br /><br />**範例**：<br /> -   `-bl`<br /> -    `-bl:output.binlog`<br /> -   `-bl:output.binlog;ProjectImports=None`<br /> -   `-bl:output.binlog;ProjectImports=ZipFile`<br /> -   `-bl:..\..\custom.binlog`<br /> -   `-binaryLogger`|
|-主控台記錄器參數：<br /><br /> `parameters`|-clp:`parameters`|將您所指定的參數傳遞至主控台記錄器，其會在主控台視窗中顯示組建資訊。 您可以指定下列參數︰<br /><br /> -   **PerformanceSummary**。 顯示工作、目標及專案所花費的時間。<br />-   **摘要**. 在結尾顯示錯誤和警告摘要。<br />-   **NoSummary**。 不要在結尾顯示錯誤和警告摘要。<br />-   **ErrorsOnly**。 僅顯示錯誤。<br />-   **WarningsOnly**。 僅顯示警告。<br />-   **NoItemAndPropertyList**。 如果詳細資訊層級設為 `diagnostic`，不要在每個專案組件開頭顯示項目和屬性的清單。<br />-   **ShowCommandLine**。 顯示 `TaskCommandLineEvent` 訊息。<br />-   **ShowTimestamp**。 顯示時間戳記做為任何訊息的前置詞。<br />-   **ShowEventId**。 顯示每個已啟動事件、已完成事件及訊息的事件識別碼。<br />-   **ForceNoAlign**。 不要讓文字對齊主控台緩衝區的大小。<br />-   **DisableConsoleColor**。 對所有記錄訊息使用預設的主控台色彩。<br />-   **DisableMPLogging**。 在非多處理器模式中執行時，停用多處理器的輸出記錄樣式。<br />-   **EnableMPLogging**。 即使在非多處理器模式中執行時也啟用多記錄器記錄樣式。 這個記錄樣式預設為開啟。<br />-   **詳細性**。 覆寫此記錄器的 **-verbosity** 設定。<br /><br /> 使用分號分隔多個參數，如以下示例所示：<br /><br /> `-consoleloggerparameters:PerformanceSummary;NoSummary -verbosity:minimal`<br/><br/> 預設主控台記錄器處於正常詳細狀態，包括 。 `Summary`|
|-distributedFileLogger|-dfl|將每個 MSBuild 節點的組建輸出記錄到自己的檔案。 這些檔案的初始位置是目前的目錄。 根據預設，系統會將檔案命名為 *MSBuild\<NodeId>.log*。 您可以使用 **-fileLoggerParameters** 參數，指定檔案位置及 fileLogger 的其他參數。<br /><br /> 如果使用 **-filelogger 參數**開關命名日誌檔，則分散式記錄器將該名稱用作範本，並在為每個節點創建日誌檔時將節點 ID 追加到該名稱。|
|-分散式記錄器：<br /><br /> `central logger`*<br /><br /> `forwarding logger`|-dl:`central logger`*`forwarding logger`|從 MSBuild 記錄事件，將不同的記錄器執行個體附加至每個節點。 若要指定多個記錄器，請分別指定每個記錄器。<br /><br /> 您可以使用記錄器語法來指定記錄器。 有關記錄器語法，請參閱下面的 **-記錄器**開關。<br /><br /> 下列範例顯示如何使用此參數：<br /><br /> `-dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|
|-fileLogger<br /><br /> *[數位]*|-fl[`number`]|在目前目錄中將組建輸出記錄至單一檔案。 如果您未指定 `number`，輸出檔案就會命名為 *msbuild.log*。 如果您指定 `number`，則輸出檔案會命名為 *msbuild\<n>.log*，其中 \<n> 是 `number`。 `Number` 可以是從 1 到 9 的數字。<br /><br /> 您可以使用 **-fileLogger 參數**開關來指定檔的位置以及檔記錄器的其他參數。|
|-檔記錄器參數：[數量]<br /><br /> `parameters`|-flp:[ `number`] `parameters`|指定檔案記錄器和分散式檔案記錄器的任何額外參數。 此開關的存在意味著存在相應的 -**檔記錄器 ***`number`**=** 開關。 `Number` 可以是從 1 到 9 的數字。<br /><br /> 您可以使用**為 -consolelogger 參數**列出的所有參數。 您也可以使用一個或多個下列參數：<br /><br /> -   **日誌檔**。 要寫入組建記錄檔的記錄檔路徑。 分散式檔案記錄器會在這個路徑放上其記錄檔名稱做為前置詞。<br />-   **追加 。** 決定是否要將組建記錄檔附加到記錄檔，或者加以覆寫。 在設定這個參數時，會將組建記錄檔附加至記錄檔。 若這個參數不存在，則會覆寫現有記錄檔的內容。<br />     如果您包含該附加參數，則無論是否設定為 True 或 False，都會附加記錄。 如果您沒有包含該附加參數，則會覆寫記錄。<br />     在此情況下會覆寫檔案：`msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log`<br />     在此情況下會附加檔案：`msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=true`<br />     在此情況下會附加檔案：`msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=false`<br />-   **編碼**. 指定檔案的編碼 (例如，UTF-8、Unicode 或 ASCII)。<br /><br /> 下列範例會為警告與錯誤產生個別的記錄檔：<br /><br /> `-flp1:logfile=errors.txt;errorsonly -flp2:logfile=warnings.txt;warningsonly`<br /><br /> 下列範例會顯示其他可能性：<br /><br /> `-fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `-flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `-flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `-flp2:errorsonly;logfile=msbuild.err`|
|-logger:<br /><br /> `logger`|-l:`logger`|從 MSBuild 指定要用於記錄事件的記錄器。 若要指定多個記錄器，請分別指定每個記錄器。<br /><br /> 針對 `logger` 使用下列語法：`[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> 針對 `LoggerClass` 使用下列語法：`[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> 如果組件恰好包含一個記錄器，就不必指定記錄器類別。<br /><br /> 針對 `LoggerAssembly` 使用下列語法：`{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> 記錄器參數是選擇性，只有在輸入時才會傳遞至記錄器。<br /><br /> 以下示例使用 **-logger**開關。<br /><br /> `-logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|
|-不控制台記錄器|-noconlog|停用預設主控台記錄器，而且不將事件記錄至主控台。|

## <a name="example"></a>範例

 下列範例會建置 `rebuild` 專案的 *MyProject.proj* 目標。

```cmd
MSBuild.exe MyProject.proj -t:rebuild
```

## <a name="example"></a>範例

 您可以使用 *MSBuild.exe* 來執行更複雜的組建。 例如，您可以用來在方案中建置特定專案的特定目標。 下列範例會重建 `NotInSolutionFolder` 專案並清除 `InSolutionFolder` 專案，這會位於 *NewFolder* 方案資料夾中。

```cmd
msbuild SlnFolders.sln -t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="see-also"></a>另請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [常見 MSBuild 專案屬性](../msbuild/common-msbuild-project-properties.md)

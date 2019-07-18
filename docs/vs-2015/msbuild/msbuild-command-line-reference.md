---
title: MSBuild 命令列參考 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 61
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d40bfefb1f89496b538612dfa1819cc6d65c76c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181064"
---
# <a name="msbuild-command-line-reference"></a>MSBuild 命令列參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在使用 MSBuild.exe 來建置專案或方案檔時，您可以包含數個參數來指定處理程序的各個層面。  
  
## <a name="syntax"></a>語法  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>引數  
  
|引數|描述|  
|--------------|-----------------|  
|`ProjectFile`|在所指定的專案檔中建置目標。 如果您未指定專案檔，MSBuild 會搜尋目前工作目錄中結尾為 "proj" 的檔案名稱副檔名，並使用該檔案。 您也可以為這個引數指定 Visual Studio 方案檔。|  
  
## <a name="switches"></a>參數  
  
|參數|簡短形式|說明|  
|------------|----------------|-----------------|  
|/help|/? 或 /h|顯示使用資訊。 下列命令是範例：<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/ds|在組建記錄檔結尾顯示關於所建置組態及其如何排程至節點的詳細資訊。|  
|/ignoreprojectextensions: `extensions`|/ignore: `extensions`|決定要建置哪個專案檔後，請忽略指定的副檔名。 使用分號或逗號分隔多個副檔名，如下列範例所示：<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/maxcpucount[:`number`]|/m[:`number`]|指定要在建置時使用的並行處理最大數目。 如果您未包含此參數，預設值為 1。 如果您包含此參數但未指定值，MSBuild 將會使用電腦上的處理器最大數目。 如需詳細資訊，請參閱[同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。<br /><br /> 下列範例會指示 MSBuild 使用三個 MSBuild 處理程序來建置，這可在同一時間建置三個專案：<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/noautoresponse|/noautorsp|不要自動包含任何 MSBuild.rsp 檔案。|  
|/nodeReuse:`value`|/nr:`value`|啟用或停用 MSBuild 節點的重複使用功能。 您可以指定下列值：<br /><br /> -   **True**。 組建完成後保留節點，以便後續組建可以加以使用 (預設值)。<br />-   **False**。 在組建完成後不保留節點。<br /><br /> 對應至執行中專案的節點。 如果您包含 **/maxcpucount** 參數，就能同時執行多個節點。|  
|/nologo||不要顯示程式啟始資訊或著作權訊息。|  
|/preprocess[:`filepath`]|/pp[:`filepath`]|由內嵌在組建期間匯入的所有檔案，並標上其界限標記，藉此建立單一彙總的專案檔。 您可以使用此參數更輕鬆地判斷正在匯入哪些檔案、從哪裡匯入檔案，以及哪些檔案形成組建。 使用這個參數時，並不會建置專案。<br /><br /> 如果您指定 `filepath`，則彙總的專案檔會是檔案的輸出。 否則，輸出會顯示在主控台視窗中。<br /><br /> 如需有關如何使用資訊`Import`項目將專案檔插入另一個專案檔，請參閱[匯入項目 (MSBuild)](../msbuild/import-element-msbuild.md)和[How to:在多個專案檔中使用相同的目標](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)。|  
|/property:`name`=`value`|/p:`name`=`value`|設定或覆寫所指定的專案層級屬性，其中 `name` 是屬性名稱，而 `value` 是屬性值。 分別指定每個屬性，或使用分號或逗號分隔多個屬性，如下列範例所示：<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/target:`targets`|/t:`targets`|在專案中建置指定的目標。 分別指定每個目標，或使用分號或逗號分隔多個目標，如下列範例所示：<br /><br /> `/target:Resources;Compile`<br /><br /> 如果您使用這個參數指定任何目標，便會執行這些目標，而不是專案檔中 `DefaultTargets` 屬性的任何目標。 如需詳細資訊，請參閱 <<c0> [ 目標建置順序](../msbuild/target-build-order.md)和[How to:指定要建置的目標先](../msbuild/how-to-specify-which-target-to-build-first.md)。<br /><br /> 目標是一組工作。 如需詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。|  
|/toolsversion:`version`|/tv:`version`|指定用來建置專案的工具組版本，如下列範例所示：`/toolsversion:3.5`<br /><br /> 藉由使用這個參數，您可以建置專案，並指定有別於 [Project 項目 (MSBuild)](../msbuild/project-element-msbuild.md) 中所指定的版本。 如需詳細資訊，請參閱[覆寫 ToolsVersion 設定](../msbuild/overriding-toolsversion-settings.md)。<br /><br /> 針對 MSBuild 4.5，您可以為 `version` 指定下列值：2.0、3.5 和 4.0。 如果您指定 4.0，則 `VisualStudioVersion` 組建屬性會指定要使用哪個子工具組。 如需詳細資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) 的＜子工具組＞一節。<br /><br /> 工具組包含用於建置應用程式的工作、目標和工具。 工具包括編譯器，例如 csc.exe 和 vbc.exe。 如需工具組的詳細資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)、[標準和自訂工具組的組態](../msbuild/standard-and-custom-toolset-configurations.md)及[多目標](../msbuild/msbuild-multitargeting-overview.md)。 **注意：** 工具組版本與目標架構的版本不同，它是在其上建置專案來執行的 .NET Framework 版本。 如需詳細資訊，請參閱[目標 Framework 和目標平台](../msbuild/msbuild-target-framework-and-target-platform.md)。|  
|/validate:[`schema`]|/val[`schema`]|驗證專案檔，如果驗證成功，則會建置專案。<br /><br /> 如果您沒有指定 `schema`，專案會針對預設結構描述進行驗證。<br /><br /> 如果您指定 `schema`，專案會針對您指定的結構描述進行驗證。<br /><br /> 下列設定為範例：`/validate:MyExtendedBuildSchema.xsd`|  
|/verbosity:`level`|/v:`level`|指定要在組建記錄檔中顯示的資訊量。 每個記錄器都會顯示根據您為該記錄器所設詳細資訊層級的事件。<br /><br /> 您可以指定下列詳細資訊層級：`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 及 `diag[nostic]`。<br /><br /> 下列設定為範例：`/verbosity:quiet`|  
|/version|/ver|只顯示版本資訊。 不會建置專案。|  
|@`file`||從文字檔中插入命令列參數。 如果您有多個檔案，請個別指定。 如需詳細資訊，請參閱[回應檔](../msbuild/msbuild-response-files.md)。|  
  
### <a name="switches-for-loggers"></a>記錄器的參數  
  
|參數|簡短形式|描述|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/clp:`parameters`|將您所指定的參數傳遞至主控台記錄器，其會在主控台視窗中顯示組建資訊。 您可以指定下列參數：<br /><br /> -   **PerformanceSummary**。 顯示工作、目標及專案所花費的時間。<br />-   **Summary**。 在結尾顯示錯誤和警告摘要。<br />-   **NoSummary**。 不要在結尾顯示錯誤和警告摘要。<br />-   **ErrorsOnly**。 僅顯示錯誤。<br />-   **WarningsOnly**。 僅顯示警告。<br />-   **NoItemAndPropertyList**。 如果詳細資訊層級設為 `diagnostic`，不要在每個專案組件開頭顯示項目和屬性的清單。<br />-   **ShowCommandLine**。 顯示 `TaskCommandLineEvent` 訊息。<br />-   **ShowTimestamp**。 顯示時間戳記做為任何訊息的前置詞。<br />-   **ShowEventId**。 顯示每個已啟動事件、已完成事件及訊息的事件識別碼。<br />-   **ForceNoAlign**。 不要讓文字對齊主控台緩衝區的大小。<br />-   **DisableConsoleColor**。 對所有記錄訊息使用預設的主控台色彩。<br />-   **DisableMPLogging**。 在非多處理器模式中執行時，停用多處理器的輸出記錄樣式。<br />-   **EnableMPLogging**。 即使在非多處理器模式中執行時也啟用多記錄器記錄樣式。 這個記錄樣式預設為開啟。<br />-   **Verbosity**。 覆寫此記錄器的 **/verbosity** 設定。<br /><br /> 使用分號或逗號分隔多個參數，如下列範例所示：<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/dfl|將每個 MSBuild 節點的組建輸出記錄到自己的檔案。 這些檔案的初始位置是目前的目錄。 根據預設，系統會將檔案命名為 "MSBuild*NodeId*.log"。 您可以使用 **/fileLoggerParameters** 參數，來指定檔案位置及 fileLogger 的其他參數。<br /><br /> 如果您使用 **/fileLoggerParameters** 參數來為記錄檔命名，分散式記錄器便會使用該名稱做為範本，並在為每個節點建立記錄檔時，將節點識別碼附加至該名稱。|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|/dl:`central logger`*`forwarding logger`|從 MSBuild 記錄事件，將不同的記錄器執行個體附加至每個節點。 若要指定多個記錄器，請分別指定每個記錄器。<br /><br /> 您可以使用記錄器語法來指定記錄器。 如需記錄器語法，請參閱下列 **/logger** 參數。<br /><br /> 下列範例顯示如何使用此參數：<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *[number]*|/fl[`number`]|在目前目錄中將組建輸出記錄至單一檔案。 如果您沒有指定 `number`，輸出檔案就會命名為 msbuild.log。 如果您指定 `number`，則輸出檔案會命名為 msbuild`n`.log，其中 n 是 `number`。 `Number` 可以是從 1 到 9 的數字。<br /><br /> 您可以使用 **/fileLoggerParameters** 參數，來指定檔案位置及 fileLogger 的其他參數。|  
|/fileloggerparameters:[number]<br /><br /> `parameters`|/flp:[ `number`] `parameters`|指定檔案記錄器和分散式檔案記錄器的任何額外參數。 這個參數的存在表示對應的 /**filelogger[** `number` **]** 參數已存在。 `Number` 可以是從 1 到 9 的數字。<br /><br /> 您可以使用針對 **/consoleloggerparameters** 列出的所有參數。 您也可以使用一個或多個下列參數：<br /><br /> -   **LogFile**。 要寫入組建記錄檔的記錄檔路徑。 分散式檔案記錄器會在這個路徑放上其記錄檔名稱做為前置詞。<br />-   **Append**。 決定是否要將組建記錄檔附加到記錄檔，或者加以覆寫。 在設定這個參數時，會將組建記錄檔附加至記錄檔。 若這個參數不存在，則會覆寫現有記錄檔的內容。<br />     如果您包含該附加參數，則無論是否設定為 True 或 False，都會附加記錄。 如果您沒有包含該附加參數，則會覆寫記錄。<br />     在此情況下會覆寫檔案：`msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     在此情況下會附加檔案：`msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     在此情況下會附加檔案：`msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Encoding**。 指定檔案的編碼 (例如，UTF-8、Unicode 或 ASCII)。<br /><br /> 下列範例會為警告與錯誤產生個別的記錄檔：<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> 下列範例會顯示其他可能性：<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|/logger:<br /><br /> `logger`|/l:`logger`|從 MSBuild 指定要用於記錄事件的記錄器。 若要指定多個記錄器，請分別指定每個記錄器。<br /><br /> 針對 `logger` 使用下列語法：`[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> 針對 `LoggerClass` 使用下列語法：`[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> 如果組件恰好包含一個記錄器，就不必指定記錄器類別。<br /><br /> 針對 `LoggerAssembly` 使用下列語法：`{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> 記錄器參數是選擇性，只有在輸入時才會傳遞至記錄器。<br /><br /> 下列範例會使用 **/logger** 參數。<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|停用預設主控台記錄器，而且不將事件記錄至主控台。|  
  
## <a name="example"></a>範例  
 下列範例會建置 `rebuild` 專案的 `MyProject.proj` 目標。  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>範例  
 您可以使用 MSBuild.exe 來執行更複雜的組建。 例如，您可以用來在方案中建置特定專案的特定目標。 下列範例會重建專案 `NotInSolutionFolder` 並清除專案 `InSolutionFolder`，這會位於 `NewFolder` 方案資料夾中。  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [通用的 MSBuild 專案屬性](../msbuild/common-msbuild-project-properties.md)

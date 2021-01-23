---
title: VSPerfReport | Microsoft Docs
description: 瞭解 VSPerfReport 命令列工具是用來建立使用 Visual Studio 分析工具程式碼剖析資料檔案的報表。
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ed3ba5453976e3f3976aba43bc296c040a86b7a5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719769"
---
# <a name="vsperfreport"></a>VSPerfReport
VSPerfReport 命令列工具可用來建立使用「[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具」分析資料檔案的報告。 預設報告格式為 .*csv* 檔案。

 VSPerfReport 會使用下列語法︰

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 請注意，`filename` 必須是有效的 .*vsp* 或 .*vsps* 檔案。

 VSPerfReport 命令列工具也可以用來比較 .*vsp* 或 .*vsps* 檔案。 若要產生差異 ("diff") 報告，請使用下列語法︰

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2` 必須是有效的 .*vsp* 或 .*vsps* 檔案。

## <a name="symbol-files"></a>符號檔
 若要顯示符號資訊 (例如函式名稱與行號)，VSPerfReport 需要存取已分析元件的符號 (.PDB) 檔與 Windows 符號檔。 如需詳細資訊，請參閱 [如何：從命令列指定符號檔位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)。

## <a name="general-report-options"></a>一般報告選項
 下表描述一般報告格式選項，以及選取要報告之資料的選項。

|選項。|描述|
|-------------|-----------------|
|**U**|報告輸出和重新導向的主控台輸出是以 Unicode 撰寫。 務必優先指定此選項。|
|**Summary:**[*types*]|建立一或多個類型的報告。<br /><br /> -   `All` - 產生所有報告類型。<br />-   `CallerCallee` - 函式之間的父/子關聯性。<br />-   `Function` - 已呼叫的函式。<br />-   `CallTree` - 已呼叫的函式階層。<br />-   `Counter` - 所有的標記，以及 Windows 效能計數器的值。<br />-   `Ip` - 已分析的指令。<br />-   `Life` - 已配置物件的存留期 (已收集配置資料時可以使用)。<br />-   `Line` 原始程式碼行設定檔資料。<br />-   `Header` - 報告包含檔案標頭資訊。<br />-   `Mark` 所有標記。<br />-   `Module` - 已分析的模組。<br />-   `Process` - 已分析的處理序。<br />-   `Thread` - 已分析的執行緒。<br />-   `Type` - 配置的類型。<br />-   `Contention` - 資源爭用。<br />-   `RuleWarnings` - 效能規則問題<br />-   `ETW` - 程式碼分析執行中所收集的所有 Windows 事件追蹤 (ETW) 事件。 .etl 資料檔案必須位於其原始位置，或位於包含 .vsp 或 .vsps 檔案的目錄。|
|**XML**|以 XML 格式輸出報告。|
|**CallTrace**|建立函式進入與離開、ETW 事件和標記的清單。|
|**ClearPackedSymbols**|從分析工具資料檔案移除先前內嵌的符號。 在第二次執行 PackSymbols 之前，執行此命令。|
|**SymbolPath：**`path`|指定包含分析工具資料檔案符號的一或多個搜尋路徑或符號伺服器。|
|**DebugSymPath**|列出搜尋符號以及是否找到符號的位置。 這個選項適合解決符號解析問題。|
|**PackSymbols**|將符號儲存到分析資料 (.vsp) 檔案中，這樣不需要符號 (.*pdb*) 檔案就能進行分析。|
|**Output:** *path*&#124;*filename*|指定產生之報告檔案的替代位置。 根據預設，會在目前的目錄中建立報告。|
|**SummaryFile**|分析並將已分析的資訊儲存於 .vsps 摘要檔中。|
|**PrintMarks**|在指定的報告檔案中顯示所有標記的名稱與時間戳記。|
|**?**|顯示使用資訊。|
|**NoLogo**|當執行報告時，隱藏版本資訊。|
|**UserRulesDirectory**|指定包含使用者定義之效能規則的目錄 [尚未實作]。|

## <a name="filter-options"></a>篩選選項
 下表描述用於篩選可用資料的選項。

|選項。|描述|
|-------------|-----------------|
|**JustMyCode**[**：**[ `caller` ] [， `callee` ]]|只顯示使用者應用程式函式呼叫；隱藏系統呼叫。<br /><br /> -   無參數 - 隱藏所有系統函式。<br />-   `caller` - 顯示呼叫應用程式函式的一個系統函式層級。<br />-   `callee` - 顯示使用者應用程式函式所呼叫的一個系統函式層級。|
|**StartTime：**[*值*]|只顯示值 (以毫秒為單位) 之後所收集的資料。|
|**EndTime：**[*值*]|只顯示值 (以毫秒為單位) 之前所收集的資料。|
|**FilterFile:** `VSPFFile`|指定從 [Visual Studio 效能報告] 視窗所產生之篩選器檔案的位置。|
|**MsFilter：**[*starttime，duration*]|只顯示從 `starttime` 直到 `duration` 長度(以毫秒為單位) 的資料。|
|**進程：**[*pid*]|只顯示來自所指定處理序的資料。|
|**Thread：**[*threadid*]|只顯示來自所指定執行緒的資料。|
|**Thread：**[*threadid，processid*]|只顯示來自與指定處理序相關聯之指定執行緒的資料。|

## <a name="difference-report-options"></a>差異報告選項
 下表描述用來比較報告檔案的選項。

|選項。|描述|
|-------------|-----------------|
|**Diff**  `vspfile1 vspfile2`|比較兩個報告檔案 (.*vsp* 或 .*vsps*)。 使用 diff 選項將會忽略摘要選項。|
|**Diff:**[*value*]|低於此臨界值將會略過兩個值之間的差異。 此外，將不會顯示包含值低於此臨界值的新資料。|
|**DiffTable：**[*tablename*]|使用此特定資料表來比較檔案。 預設為函式資料表。|
|**DiffColumn：**[*columnname*]|使用此特定資料行來比較值。 預設為專有樣本百分比資料行。|
|**QueryDiffTables**|列出提供之兩個報告檔案的有效資料表和資料行。|

## <a name="see-also"></a>另請參閱
- [效能報表檢視](../profiling/performance-report-views.md)

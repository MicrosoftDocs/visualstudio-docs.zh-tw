---
title: 從命令列建立分析工具報表 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7f28d7271fdf33822475a663debed269bb515959
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777773"
---
# <a name="create-profiler-reports-from-the-command-line"></a>從命令列建立分析工具報告
**VSPerfReport**命令列工具使您能夠創建 。*xml*或逗號分隔值 （。*csv*） 從分析資料 （中報告）*vsp*） 檔。 VSPerfReport 報表類型極符合 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之介面的資料表檢視。 您可以篩選報表只顯示您的程式碼，以及只顯示分析資料檔案的區段。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。

 您還可以通過在 中嵌入符號來簡化分析資料檔的共用。*vsp*檔和通過創建預分析的報告 （。*vsps*） 檔，是更小，更快的打開。

## <a name="common-tasks"></a>常見工作

|Task|相關內容|
|----------|---------------------|
|**創建基礎報表。** 建立所有 VSPerfReport 報表類型或其子集。|-   [建立基本報表](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**比較兩個分析資料檔案。** 建立 "diff" 報表，以比較兩個分析資料檔案中的效能資料。|-   [如何：從命令提示符創建探測器比較報告](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**檢視呼叫追蹤和 Windows 事件追蹤 (ETW) 資料。** 建立呼叫追蹤報表，以列出您應用程式函式每個進入點和結束點的計時資訊，以及您的函式對其他函式的每次呼叫。 或者，建立分析回合中所收集之所有 ETW 事件的詳細清單。|-   [如何：創建呼叫跟蹤報告](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**篩選報表。** 限制報表，只顯示程式碼中的函式或分析資料檔案中的特定時間。|-   [如何：篩選來自命令列的報告](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**建立可移植的分析資料檔案。** 為了更輕鬆地共用分析資料，可以將運行分析的符號嵌入到 中。*vsp*檔。 您還可以創建預分析的分析資料 （。*vsps*） 檔，是更小，更快的打開。|-   [創建可擕式分析資料檔](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|

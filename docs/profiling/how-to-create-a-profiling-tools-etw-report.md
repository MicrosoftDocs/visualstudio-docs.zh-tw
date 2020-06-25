---
title: 如何-建立分析工具 ETW 報表 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 622015ecbc2730c5b0a8cdf7b2ba92c4f5963886
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329819"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>如何：建立分析工具 ETW 報表
「Windows 事件追蹤」(ETW) 報告會列出「[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具」的效能工作階段中記錄的 ETW 事件。 ETW 資料會收集在二進位 (.*etl*) 檔案中。 如需這份報告的詳細資訊，請參閱[Windows 事件追蹤（ETW）報告](../profiling/event-tracing-for-windows-etw-report.md)。

> [!NOTE]
> 您無法在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的介面中顯示 ETW 報告。

- 如需如何使用的介面來收集 ETW 資料的詳細資訊 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，請參閱[如何：收集 Windows 事件追蹤（ETW）資料](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)。

- 如需有關如何從命令提示字元收集 ETW 資料的資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 和 [Events](../profiling/events-vsperfcmd.md)。

  您可以使用 **VSReport/summary:etw** 命令來產生 ETW 報告。 該.包含 ETW 資料的*etl*必須位於與程式碼剖析資料相同的目錄中（。*vsp*或。*.vsps*）文字檔. 根據預設，報表會以逗點分隔值（的形式產生。*csv*）檔案。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。

### <a name="to-generate-an-etw-report"></a>產生 ETW 報告

- 在 [命令提示字元]**** 視窗中，輸入下列命令行：

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |||
    |-|-|
    |*ToolsPath*|「分析工具」公用程式的路徑。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。|
    |*VSPFile*|程式碼剖析資料（。*vsp*或。*.vsps*）文字檔. 可接受完整和部分路徑。|
    |Xml|產生採用 XML 格式的報告。|

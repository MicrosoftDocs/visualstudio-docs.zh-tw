---
title: 從命令列測量效能
description: 從命令列測量應用程式中的 CPU 效能和受控記憶體使用量。
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: e1c8c20d350561eec520038dec521ab7bc5f5311
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570678"
---
# <a name="measure-application-performance-from-the-command-line"></a>從命令列測量應用程式的效能

您可以使用命令列工具來收集應用程式的效能資訊。

本文所述範例會收集 Microsoft [記事本] 的效能資訊，但您可以使用相同的方法來分析任何處理序。

## <a name="prerequisites"></a>必要條件

* Visual Studio 2019 或更新版本

* 熟悉命令列工具

* 若要在未安裝 Visual Studio 的遠端電腦上收集效能資訊，請在遠端電腦上安裝 [Visual Studio 遠端工具](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019) 。 這些工具的版本必須符合您的 Visual Studio 版本。

## <a name="collect-performance-data"></a>收集效能資料

使用 Visual Studio 診斷 CLI 工具進行分析時，其運作方式是將分析工具與其中一個收集器代理程式附加至處理序。 當您附加分析工具時，即會開始診斷工作階段以擷取並儲存分析資料，直到停止工具為止；此時會將這些資料匯出為 *.diagsession* 檔案。 接著，您即可在 Visual Studio 中開啟此檔案以分析結果。

1. 啟動 [記事本]，然後開啟 [工作管理員] 以取得其處理序識別碼 (PID)。 在 [工作管理員] 的 [詳細資料] 索引標籤中，尋找此 PID。

1. 開啟命令提示字元，然後使用集合代理程式可執行檔變更至目錄，通常是在 Visual Studio Enterprise) 的 (。

   ```<Visual Studio installation folder>\2019\Enterprise\Team Tools\DiagnosticsHub\Collector\```

1. 鍵入下列命令，開始 *VSDiagnostics.exe*。

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   必須包含的引數如下：

   * \<*id*> 識別收集會話。 識別碼必須是介於 1-255 之間的數字。
   * \<*pid*>，您想要分析之進程的 PID，在此案例中，您在步驟1中找到的 PID。
   * \<*configFile*>：您想要啟動之收集代理程式的設定檔。 如需詳細資訊，請參閱[代理程式的組態檔](#config_file)。

   例如，您可以將下列命令用於 CPUUsageBase 代理程式，如先前所述來取代 *pid* 。

   ```cmd
   VSDiagnostics.exe start 1 /attach:<pid> /loadConfig:AgentConfigs\CPUUsageLow.json
   ```

1. 調整 [記事本] 的大小，或在其中鍵入某些項目，以確保收集到一些可用的分析資訊。

1. 停止收集工作階段並鍵入下列命令，將輸出傳送至檔案。

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. 找出前一個命令的 *diagsession* 檔案輸出，並在 Visual Studio **中開啟它 (檔案**  >  **開啟**) 以檢查收集到的資訊。

   若要分析結果，請參閱對應效能工具的檔。 例如，這可能是 [ [CPU 使用量](../profiling/cpu-usage.md)]、[ [.net 物件配置] 工具](../profiling/dotnet-alloc-tool.md)或 [ [資料庫](../profiling/analyze-database.md) ] 工具。

## <a name="agent-configuration-files"></a><a name="config_file"></a> 代理程式組態檔

收集代理程式是一種可互換元件，其會依據您要嘗試測量的項目來收集不同類型資料。

為了方便起見，建議您將該資訊儲存在代理程式設定檔中。 組態檔是一種 *.json* 檔案，其中至少包含 *.dll* 的名稱和其 COM CLSID。 您可以在下列資料夾中找到的範例組態檔如下：

```<Visual Studio installation folder>Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

請參閱下列連結以下載和查看代理程式設定檔：

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow
- https://aka.ms/vs/diaghub/agentconfig/dotnetcountersbase

CpuUsage 設定 (基底/高/低) 對應至針對 [CPU 使用量](../profiling/cpu-usage.md) 分析工具所收集的資料。
DotNetObjectAlloc 設定 (Base/Low) 對應至針對 [.Net 物件組態工具](../profiling/dotnet-alloc-tool.md)所收集的資料。

組態的基底/高/低是指取樣率。 例如，低表示 100 個範例/秒，而高表示 4000 個範例/秒。

若要讓 *VSDiagnostics.exe* 工具使用集合代理程式，則需要適當的代理程式的 DLL 和 COM CLSID。 代理程式也可能會有其他的設定選項，這會是設定檔中指定的任何選項，格式正確的轉義 JSON。

## <a name="permissions"></a>權限

若要分析需要提高權限的應用程式，您必須從提升權限的命令提示字元執行此作業。

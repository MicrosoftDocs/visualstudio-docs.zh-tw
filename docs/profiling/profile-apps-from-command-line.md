---
title: 從命令列測量 CPU 使用量
description: 從命令列測量應用程式的 CPU 效能。
ms.custom: ''
ms.date: 02/19/2019
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: b2de537b17b68461c16f886c1eab706d2438ff6c
ms.sourcegitcommit: 62149c96de0811415e99bb1e0194e76c320e1a1e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "57007495"
---
# <a name="measure-application-performance-from-the-command-line"></a>從命令列測量應用程式的效能

您可以使用命令列工具來收集應用程式的效能資訊。

本文所述範例會收集 Microsoft [記事本] 的效能資訊，但您可以使用相同的方法來分析任何處理序。

## <a name="prerequisites"></a>必要條件

* Visual Studio 2019 Preview 3 或更新版本

* 熟悉命令列工具

## <a name="collect-performance-data"></a>收集效能資料

使用 Visual Studio 診斷 CLI 工具進行分析時，其運作方式是將分析工具與其中一個收集器代理程式附加至處理序。 當您附加分析工具時，即會開始診斷工作階段以擷取並儲存分析資料，直到停止工具為止；此時會將這些資料匯出為 *.diagsession* 檔案。 接著，您即可在 Visual Studio 中開啟此檔案以分析結果。

1. 啟動 [記事本]，然後開啟 [工作管理員] 以取得其處理序識別碼 (PID)。 在 [工作管理員] 的 [詳細資料] 索引標籤中，尋找此 PID。

1. 開啟命令提示字元，並變更為包含收集代理程式可執行檔的目錄，通常位於這裡。

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. 鍵入下列命令，開始 *VSDiagnostics.exe*。

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   必須包含的引數如下：

   * \<*id*> 可識別收集工作階段。 識別碼必須是介於 1-255 之間的數字。
   * \<*pid*>，您要分析的處理序 PID；在本例中為您在步驟 1 找到的 PID
   * \<*configFile*>，您要啟動的收集代理程式組態檔。 如需詳細資訊，請參閱[代理程式的組態檔](#config_file)。

1. 調整 [記事本] 的大小，或在其中鍵入某些項目，以確保收集到一些可用的分析資訊。

1. 停止收集工作階段並鍵入下列命令，將輸出傳送至檔案。

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. 移至上一個命令的檔案輸出，並在 Visual Studio 中開啟以檢查收集到的資訊。

## <a name="config_file"></a> 代理程式組態檔

收集代理程式是一種可互換元件，其會依據您要嘗試測量的項目來收集不同類型資料。

為了方便起見，您可以將該資訊儲存在代理程式組態檔中。 組態檔是一種 *.json* 檔案，其中至少包含 *.dll* 的名稱和其 COM CLSID。 您可以在下列資料夾中找到的範例組態檔如下：

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* CpuUsage 組態 (基底/高/低)，其會對應至 [CPU 使用量](../profiling/cpu-usage.md)分析工具收集到的資料。
* DotNetObjectAlloc 組態 (基底/低)，其會對應至 [.NET 物件配置工具](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-version-15-8-preview-3/#tooling)收集到的資料。

組態的基底/高/低是指取樣率。 例如，低表示 100 個範例/秒，而高表示 4000 個範例/秒。

若要搭配使用 *VSDiagnostics.exe* 工具和收集代理程式，您需要具備適當代理程式的 DLL 和 COM CLSID，且代理程式可能還有其他組態選項。 如果您要使用不含組態檔的代理程式，請使用下列命令的格式。

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>權限

若要分析需要提高權限的應用程式，您必須從提升權限的命令提示字元執行此作業。





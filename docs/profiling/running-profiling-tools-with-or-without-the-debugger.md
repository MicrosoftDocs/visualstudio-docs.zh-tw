---
title: 使用或不使用偵錯工具來執行分析工具 | Microsoft Docs
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45632967c39348e8dc78dc3e2fb95227dcd86d7d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285885"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>使用或不使用偵錯工具來執行分析工具

Visual Studio 提供各種效能測量和分析工具的選擇。 某些工具（例如 CPU 使用量和記憶體使用量）可以使用或不使用偵錯工具，以及發行或 debug 組建設定來執行。 效能分析工具（例如應用程式時間軸）可以在 debug 或 release 組建上執行。 偵錯工具整合的工具，像是診斷工具視窗和事件] 索引標籤，只會在偵測會話期間執行。

>[!NOTE]
>您可以在 Windows 7 和更新版本中使用非偵錯工具的效能工具。 若要執行偵錯工具整合的分析工具，需要 Windows 8 或更新版本。

非偵錯工具的 [效能分析工具] 和偵錯工具整合的 [診斷工具] 提供不同資訊與體驗。 偵錯工具整合的工具會顯示中斷點和變數值。 非偵錯工具之工具可為您提供更接近終端使用者體驗的結果。

若要協助決定要使用哪些工具和結果，請考慮下列事項：

- 外部效能問題 (例如檔案 I/O 或網路回應性問題) 在偵錯工具或非偵錯工具的工具中看起來沒有太大差異。
- 針對 CPU 密集呼叫所造成的問題，發行和偵錯工具組建之間可能會有相當大的效能差異。 查看發行組建中是否存在問題。
- 如果問題只是在 debug 組建期間發生，您可能不需要執行非偵錯工具工具。 針對發行組建問題，請決定偵錯工具工具是否能協助進行進一步的調查。
- [發行] 組建提供最佳化功能，例如內嵌函式呼叫和常數、清除未用的程式碼路徑，以及無法採用偵錯工具所使用的方式來儲存變數。 偵錯工具整合工具中的效能數位較不精確，因為 debug build 缺少這些優化。
- 偵錯工具本身會變更效能時間，因為它會執行必要的偵錯工具作業，例如攔截例外狀況和模組載入事件。
- [效能分析工具] 中的 [發行] 組建效能數字最精確且準確。 偵錯工具整合的工具結果最適合與其他偵錯相關的度量進行比較。

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a>偵錯時收集程式碼剖析資料

當您選取 [**調試**程式] [開始] [啟動]，或按 F5 在 Visual Studio 中啟動偵錯工具時，  >  **Start Debugging**預設會顯示 [ ** ****診斷工具**] 視窗。 若要手動開啟它，請選取 [ **Debug**  >  **Windows**  >  **Show 診斷工具**]。 [診斷工具]**** 視窗會顯示事件、處理序記憶體和 CPU 使用量的相關資訊。

![[診斷工具] 視窗的螢幕擷取畫面](../profiling/media/diagnostictoolswindow.png "[診斷工具] 視窗")

- 使用工具列上的**設定**圖示來選擇是否要檢視 [記憶體使用量]****、[UI 分析]****，以及 [CPU 使用量]****。

- 選取 [**設定**] 下拉式清單中的 [**設定**]，以使用更多選項開啟 [**診斷工具] 屬性頁**。

- 如果您正在執行 Visual Studio Enterprise，您可以前往 [**工具**] [選項] [  >  **Options**  >  **intellitrace**] 來啟用或停用 intellitrace。

在您停止偵錯時，診斷工作階段就會結束。

### <a name="the-events-tab"></a>[事件] 索引標籤

在偵錯工作階段期間，[診斷工具] 視窗的 [事件] 索引標籤會列出所發生診斷事件。 類別前置詞*中斷點*、檔案和其他專案，可讓您快速掃描*清單中的*類別，或略過不在意的類別。

您可以使用 [**篩選**] 下拉式清單，藉由選取或清除特定的事件類別，來篩選中的事件。

![診斷事件篩選器的螢幕擷取畫面](../profiling/media/diagnosticeventfilter.png "診斷事件篩選器")

請使用搜尋方塊來尋找事件清單中的特定字串。 以下是搜尋符合四個事件之字串*名稱*的結果：

![診斷事件搜尋的螢幕擷取畫面](../profiling/media/diagnosticseventsearch.png "診斷事件搜尋")

如需詳細資訊，請參閱 [搜尋和篩選診斷工具視窗的事件索引標籤](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)。

## <a name="collect-profiling-data-without-debugging"></a>收集程式碼剖析資料但不偵錯

若要收集效能資料而不進行偵錯，您可以執行 [效能分析工具]。

1. 在 Visual Studio 中開啟專案時，將解決方案設定設為 [ **發行**]，然後選取 [ **本機 Windows 偵錯工具**]   （或 [ **本機電腦**]）做為部署目標。

1. 選取 [ **Debug**  >  **Performance Profiler**]，或按**Alt** + **F2**。

1. 在 [診斷工具啟動] 頁面上，選取要執行的一或多個工具。 只有適用于專案類型、作業系統和程式設計語言的工具才會顯示。 選取 [顯示所有工具]**** 來另外查看針對這個診斷工作階段停用的工具。

   ![診斷工具的螢幕擷取畫面](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. 若要開始診斷工作階段，請選取 [開始]****。

   當會話正在執行時，某些工具會在 [診斷工具] 頁面上顯示即時資料的圖形，以及用來暫停和繼續資料收集的控制項。

    ![效能和診斷中樞上的資料收集螢幕擷取畫面](../profiling/media/diaghubcollectdata.png "中樞收集資料")

1. 若要結束診斷工作階段，請選取 [停止收集]****。

   分析的資料會出現在**報表**頁面上。

您可以儲存報表，並從 [診斷工具啟動] 頁面上 [**最近開啟的會話**] 清單中開啟它們。

![診斷工具最近開啟的會話清單的螢幕擷取畫面](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

## <a name="collect-profiling-data-from-the-command-line"></a>從命令列收集程式碼剖析資料

若要從命令列測量效能資料，您可以使用包含在 Visual Studio 或遠端工具中的 VSDiagnostics.exe。 這適用于在未安裝 Visual Studio 的系統上捕獲效能追蹤，或用來編寫效能追蹤集合的腳本。 當您使用 VSDiagnostics.exe 時，您會開始一個診斷會話，它會捕捉並儲存程式碼剖析資料，直到工具停止為止。 此時，該資料會匯出至 diagsession 檔案，而您可以在 Visual Studio 中開啟此檔案來分析結果。

### <a name="launch-an-application"></a>啟動應用程式

1. 開啟命令提示字元，然後使用 VSDiagnostics.exe 變更為目錄：

   ```
   <Visual Studio Install Folder>\Team Tools\DiagnosticsHub\Collector\
   ```

2. 使用下列命令啟動 VSDiagnostics.exe：

   ```
   VSDiagnostics.exe start <id> /launch:<appToLaunch> /loadConfig:<configFile>
   ```

   您必須包含下列引數：

   - \<id\>：識別收集會話。 識別碼必須是介於 1-255 之間的數字。
   - \<appToLaunch\>：要啟動和分析的可執行檔。
   - \<configFile\>：您要啟動之集合代理程式的設定檔。

3. 若要停止收集並查看結果，請依照本文稍後的「停止收集」一節中的步驟進行。

### <a name="attach-to-an-existing-application"></a>附加至現有的應用程式

1. 開啟應用程式（例如 [記事本]），然後開啟 [**工作管理員**] 以取得其處理序識別碼（PID）。 在 [工作管理員] 的 [ **詳細資料**] 索引標籤中，尋找 PID   。
2. 開啟命令提示字元，並將變更為具有集合代理程式可執行檔的目錄。 一般來說，它是：

   ```
   <Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\
   ```

3. 輸入下列命令來啟動 VSDiagnostics.exe 檔案。

   ```
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   您必須包含下列引數：

   - \<id\>：識別收集會話。 識別碼必須是介於 1-255 之間的數字。
   - \<pid\>：您要分析之進程的 PID，在此案例中是您在步驟1中找到的 PID。
   - \<configFile\>：您要啟動之集合代理程式的設定檔。 如需詳細資訊，請參閱 [代理程式的設定檔](../profiling/profile-apps-from-command-line.md)。

4. 若要停止收集並查看結果，請遵循下一節中的步驟。

### <a name="stop-collection"></a>停止收集

1. 停止收集會話，然後輸入下列命令，將輸出傳送至檔案。

   ```
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

2. 移至上一個命令的檔案輸出，並在 Visual Studio 中開啟以檢查收集到的資訊。

## <a name="agent-configuration-files"></a> 代理程式組態檔

集合代理程式是收集不同資料類型的可互換元件，視您嘗試測量的內容而定。
為了方便起見，您可以將該資訊儲存在代理程式組態檔中。 設定檔是一個 json 檔案，其中至少包含 .dll 檔案的名稱及其 COM CLSID。 您可以在下列資料夾中找到的範例組態檔如下：

```
<Visual Studio installation folder>\Team Tools\DiagnosticsHub\Collector\AgentConfigs\
```

請參閱下列連結，以下載並查看代理程式設定檔：

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow

CpuUsage 設定（基底/高/低）對應至針對 [CPU 使用量](../profiling/cpu-usage.md)分析工具所收集的資料。
DotNetObjectAlloc 設定（基底/低）對應至針對 [.Net 物件組態工具](../profiling/dotnet-alloc-tool.md)所收集的資料。

組態的基底/高/低是指取樣率。 例如，低表示 100 個範例/秒，而高表示 4000 個範例/秒。
為了讓 VSDiagnostics.exe 工具與集合代理程式搭配使用，它需要適當代理程式的 DLL 和 COM CLSID。 代理程式可能也會有其他設定選項。 如果您使用沒有設定檔的代理程式，請在下列命令中使用格式：

```
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

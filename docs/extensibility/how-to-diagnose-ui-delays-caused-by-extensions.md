---
title: 在 Visual Studio 中診斷延伸模組 UI 延遲 |Microsoft 文件
ms.custom: ''
ms.date: 01/26/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: douge
ms.workload: multiple
ms.openlocfilehash: b63f9538c916b74874031704a1f60d0646f8d032
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134331"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>如何： 診斷 UI 延伸模組所造成的延遲

UI 變得沒有回應，Visual Studio 會檢查分葉開始，並朝向基底，在 UI 執行緒呼叫堆疊。 如果 Visual Studio 會判斷呼叫堆疊框架屬於屬於已安裝且已啟用延伸模組，它會顯示通知。

![UI 延遲 （一堆） 通知](media/ui-delay-notification-in-vs.png)

通知會告知使用者 UI 延遲 （也就是在 UI 中一堆） 可能已從延伸模組的程式碼的結果。 它也會提供選項來停用擴充功能或未來的通知，該擴充功能的使用者。

本文件說明如何診斷延伸模組程式碼中造成 UI 延遲通知。 

> [!NOTE]
> 請勿使用 Visual Studio 的實驗執行個體診斷 UI 延遲。 使用實驗性執行個體，這表示可能不會顯示 UI 延遲通知時，會關閉 UI 延遲通知所需的呼叫堆疊分析的某些部分。

診斷程序的總覽如下所示：
1. 識別觸發程序案例。
2. 登入的活動並重新啟動 VS。
3. 啟動 ETW 追蹤。
4. 觸發程序才會出現一次通知。
5. 停止 ETW 追蹤。
6. 檢查活動記錄檔以取得延遲識別碼。
7. 分析使用延遲識別碼，從步驟 6 的 ETW 追蹤。

在下列章節中，我們將探討更多詳細資料中的這些步驟。

## <a name="identifying-the-trigger-scenario"></a>用來識別觸發程序案例

若要執行診斷 UI 延遲，您需要識別哪些 （序列執行） 會導致 Visual Studio 以顯示通知。 這是為了讓您能夠以開啟記錄之後觸發通知。

## <a name="restarting-vs-with-activity-logging-on"></a>重新啟動 VS 與登入活動

Visual Studio 可以產生 「 活動記錄檔 」 的問題進行偵錯時提供有用的資訊。 若要開啟 活動記錄在 Visual Studio 中，開始使用 Visual Studio`/log`命令列選項。 Visual Studio 會啟動之後，活動記錄檔會儲存在下列位置：

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

若要深入了解如何尋找您的 VS 執行個體識別碼，請參閱[來偵測及管理 Visual Studio 執行個體工具](../install/tools-for-managing-visual-studio-instances.md)。 我們稍後將使用此活動記錄檔以找出 UI 延遲和相關的通知的詳細資訊。

## <a name="starting-etw-tracing"></a>啟動 ETW 追蹤

您可以使用[PerfView](https://github.com/Microsoft/perfview/)收集 ETW 追蹤。 適用於收集 ETW 追蹤和分析它，PerfView 會提供方便使用介面。 您可以使用下列命令來收集追蹤：

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

這可讓 「 Microsoft visual Studio 「 提供者，是 Visual Studio 所使用的 UI 延遲通知相關的事件提供者。 它也會指定 PerfView 可以用來產生 「 執行緒時間堆疊 」 檢視核心提供者的關鍵字。

## <a name="triggering-the-notification-to-appear-again"></a>觸發一次出現的通知

啟動 PerfView 追蹤集合之後, 您可以使用通知 （來自步驟 1） 觸發程序動作順序出現一次。 通知會顯示後，您可以停止 PerfView 來處理和產生輸出追蹤檔追蹤集合。

## <a name="stopping-etw-tracing"></a>停止 ETW 追蹤

若要停止追蹤集合，請只使用`Stop collection`PerfView 視窗上的按鈕。 停止追蹤集合之後，PerfView 會自動處理 ETW 事件，並產生輸出追蹤檔。

## <a name="examining-the-activity-log-to-get-the-delay-id"></a>查看活動記錄檔中取得延遲識別碼

如先前所述，您可以找到活動記錄在`%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml`。 每次 Visual Studio 偵測到延伸模組 UI 延遲，它會將節點寫入活動記錄檔與`UIDelayNotifications`做為來源。 這個節點包含四項 UI 延遲的相關資訊：

- UI 延遲識別碼可唯一識別與工作階段中的 UI 延遲的序號
- 工作階段識別碼，可唯一識別您的 Visual Studio 工作階段從開始到關閉
- UI 延遲是否顯示通知
- 可能是 UI 延遲所造成的擴充功能

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> 並非所有 UI 延遲都導致通知。 因此，您應該一律檢查 「 通知顯示？ 」 值，以正確識別正確的 UI 會延遲。

活動記錄檔中尋找正確的 UI 延遲之後，記下指定的節點中的 UI 延遲識別碼。 您將使用識別碼來尋找下一個步驟中對應的 ETW 事件。

## <a name="analyzing-the-etw-trace"></a>分析 ETW 追蹤

接下來，開啟追蹤檔案。 您可以使用相同的執行個體 PerfView 或啟動的新執行個體，然後在左上角的視窗至追蹤檔案的位置中設定目前的資料夾路徑。

![在 Perfview 中設定的資料夾路徑](media/perfview-set-path.png)

然後，在左窗格中選取的追蹤檔案，並開啟以滑鼠右鍵按一下或內容功能表中選擇 開啟。

> [!NOTE]
> 根據預設 PerfView 會輸出 Zip 封存。 當您開啟 trace.zip 時，它會自動解壓縮的封存，並開啟追蹤。 您可以在追蹤收集期間 turn"Zip"方塊來跳過此設定。 不過，如果您打算傳送，並在不同電腦中使用追蹤，我們強烈建議針對"Zip"方塊取消選取。 沒有這個選項時，所需的 Pdb，Ngen 組件會隨附於追蹤，因此從 Ngen 組件的符號將不會解析目的地電腦上。 (請參閱[此部落格文章](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/)如需詳細資訊在 Pdb，Ngen 組件。) 

可能需要幾分鐘的時間來處理，以及開啟追蹤 PerfView。 一旦開啟追蹤，各種 「 檢視 」 清單隨即出現在其下。

![PerfView 追蹤的摘要檢視](media/perfview-summary-view-events-selected.png)

我們會先使用 「 事件 」 檢視，來取得 UI 延遲時間範圍：

1. 選取追蹤下的 事件 節點，然後以滑鼠右鍵按一下或內容功能表中選擇 開啟開啟 「 事件 」 檢視。
2. 選取 「`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`"的左窗格中。
3. 按 Enter 鍵

選取套用 」 和 「 全部`ExtensionUIUnresponsiveness`事件會顯示在右窗格中。

![在事件檢視中選取事件](media/perfview-event-selection.png)

在右窗格中的每個資料列對應到 UI 延遲。 事件包含 「 延遲識別碼 」 值應該與相符的活動記錄檔，從步驟 6 中的延遲識別碼。 因為`ExtensionUIUnresponsiveness`引發 UI 延遲，此事件的時間戳記的結尾 （大約） 標記的 UI 延遲的結束時間。 事件也包含延遲的持續時間。 我們可以減去 UI 延遲啟動時，取得的時間戳記的結束時間戳記的持續期間。

![計算 UI 延遲時間範圍](media/ui-delay-time-range.png)

在上一個螢幕擷取畫面，例如事件的時間戳記是 12,125.679 而延遲的持續時間 6,143.085 （毫秒）。 因此，
* 延遲啟動是 12,125.679 6,143.085 = 5,982.594。
* UI 的延遲時間範圍是以 12,125.679 5,982.594。

一旦時間範圍內，我們可以退出 事件檢視，開啟 「 執行緒時間 （以 StartStop 活動） 堆疊 」 檢視。 此檢視是特別有用，因為通常會封鎖 UI 執行緒的擴充功能只等候其他執行緒或 I/O 繫結作業。 因此，「 CPU 堆疊 」 檢視中，這是大部分的情況下的 移至選項，可能不會擷取封鎖，因為它不在該時間內使用 CPU 的執行緒花費的時間。 "執行緒時間堆疊 」 來解決這個問題，依正確顯示封鎖的時間。

![PerfView 摘要檢視中的執行緒 （具有 StartStop 活動） 的時間堆疊節點](media/perfview-thread-time-with-startstop-activities-stacks.png)

當開啟 「 執行緒時間堆疊 」 檢視中，選擇"devenv"處理序開始分析。

![執行緒 UI 延遲分析的時間堆疊檢視](media/ui-delay-thread-time-stacks.png)

在 「 執行緒時間堆疊 」 檢視中，在左上方的頁面上，您可以設定時間範圍來讓堆疊會調整至該時間範圍中的上一個步驟和按下 Enter 我們計算的值。

> [!NOTE]
> 判斷哪一個執行緒 UI （啟動） 執行緒可以自相矛盾，但是如果已開啟 Visual Studio 之後，追蹤集合已啟動。 不過，UI （啟動） 執行緒的堆疊上的第一個項目是最有可能永遠作業系統 Dll （ntdll.dll 和 kernel32.dll） 後面接著 devenv ！？ 然後 msenv ！？。 此順序有助於識別 UI 執行緒。

 ![識別啟動執行緒](media/ui-delay-startup-thread.png)

您可以也進一步篩選這個檢視只包含堆疊包含從您的封裝的模組。

* "GroupPats"設為空的文字，若要移除依預設，加入任何群組。
* 設定"IncPats 」 來包含部分除了現有的處理序篩選組件名稱。 在此情況下，它應該是"devenv;UIDelayR2"。

![GroupPath 和 IncPath 檢視 中設定執行緒的時間堆疊](media/perfview-tts-group-path-inc-path.png)

PerfView 詳述可用來找出效能瓶頸，您的程式碼中的 [說明] 功能表底下的指引。 此外，下列連結提供如何使用 Visual Studio 執行緒來最佳化您的程式碼的應用程式開發介面的詳細資訊：

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

您也可以使用新的 Visual Studio 靜態分析器，延伸模組 (NuGet 封裝[這裡](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers))，提供指引的最佳作法撰寫有效率的延伸模組。 看到一份[VS SDK 分析器](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md)和[執行緒分析器](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md)。

> [!NOTE]
> 如果無法解決由於相依性一堆您沒有控制項上 (例如： 如果您的擴充功能必須在 UI 執行緒上呼叫同步 VS 服務)，我們想要了解它。 如果您是我們的 Visual Studio 協力廠商程式的成員，您可以與我們連絡所提交的開發人員支援。 否則，請使用 '回報問題 工具來提交您的意見反應並包含`"Extension UI Delay Notifications"`標題中。 請也包含您的分析的詳細的描述。

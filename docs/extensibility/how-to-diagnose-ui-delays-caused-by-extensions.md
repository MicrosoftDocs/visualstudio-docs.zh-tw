---
title: 在 Visual Studio 中診斷延伸模組 UI 延遲 |Microsoft Docs
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: ac3d44734c868bdf57f76aec0572e6b7d3ea9f03
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719479"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>HOW TO：診斷延伸模組造成的 UI 延遲

UI 無回應時，Visual Studio 開始分葉，並朝向基底，就會檢查 UI 執行緒呼叫堆疊。 如果 Visual Studio 會判斷呼叫堆疊框架屬於已安裝並啟用延伸模組的模組，它會顯示通知。

![UI 延遲 （無回應） 通知](media/ui-delay-notification-in-vs.png)

通知會通知使用者 UI 延遲 （也就是在 UI 無回應） 可能已從擴充功能的程式碼的結果。 它也會提供選項來停用延伸模組或未來的通知，該延伸模組的使用者。

本文件說明如何診斷延伸模組程式碼中導致 UI 延遲通知。

> [!NOTE]
> 請勿使用 Visual Studio 的實驗執行個體來診斷 UI 延遲。 使用實驗的執行個體，這表示可能不會顯示 UI 延遲通知時，呼叫堆疊分析所需的 UI 延遲通知的某些部分為關閉狀態。

診斷的處理程序的概觀如下所示：
1. 識別觸發程序的案例。
2. 重新啟動 VS，登入的活動。
3. 啟動 ETW 追蹤。
4. 若要再次顯示通知觸發程序。
5. 停止 ETW 追蹤。
6. 查看活動記錄來取得延遲的識別碼。
7. 分析使用延遲的識別碼，來自步驟 6 的 ETW 追蹤。

在下列章節中，我們將探討更多詳細資料中的這些步驟。

## <a name="identify-the-trigger-scenario"></a>識別觸發程序的案例

若要執行診斷 UI 延遲，您首先要找出哪些 （順序的動作） 讓 Visual Studio 將顯示通知。 這是為了讓您能夠開啟記錄之後觸發通知。

## <a name="restart-vs-with-activity-logging-on"></a>登入的活動，並重新啟動 VS

Visual Studio 可以產生 「 活動記錄 」 的問題進行偵錯時提供有用的資訊。 若要開啟活動記錄在 Visual Studio 中，啟動 Visual Studio 中使用`/log`命令列選項。 Visual Studio 啟動之後，活動記錄檔會儲存在下列位置：

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

若要深入了解如何尋找您的 VS 執行個體識別碼，請參閱[工具，用於偵測及管理 Visual Studio 執行個體](../install/tools-for-managing-visual-studio-instances.md)。 我們稍後會使用此活動記錄檔以找出 UI 延遲和相關的通知的詳細資訊。

## <a name="starting-etw-tracing"></a>啟動 ETW 追蹤

您可以使用[PerfView](https://github.com/Microsoft/perfview/)收集 ETW 追蹤。 用來收集 ETW 追蹤並分析它，PerfView 會提供簡單易用介面。 您可以使用下列命令來收集追蹤：

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

這可讓 「 Microsoft VisualStudio 「 提供者，也就是 Visual Studio 所使用的 UI 延遲通知相關的事件提供者。 它也指定核心提供者 PerfView 可以用來產生關鍵字**執行緒時間堆疊**檢視。

## <a name="trigger-the-notification-to-appear-again"></a>觸發程序若要再次顯示通知

一旦啟動 PerfView 追蹤集合，您可以使用 通知 （來自步驟 1） 的觸發程序的動作順序出現一次。 通知顯示之後，您可以停止處理，並產生輸出追蹤檔 PerfView 追蹤集合。

## <a name="stop-etw-tracing"></a>停止 ETW 追蹤

若要停止追蹤集合，請只使用**停止收集**PerfView 視窗上的按鈕。 停止追蹤收集之後，PerfView 會自動處理的 ETW 事件，並產生輸出追蹤檔。

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>查看活動記錄來取得延遲識別碼

如先前所述，您可以找到在活動記錄 *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.xml*。 每次 Visual Studio 偵測到的延伸模組 UI 延遲時，它將節點寫入至活動記錄與`UIDelayNotifications`做為來源。 這個節點包含四個部分的 UI 延遲的相關資訊：

- UI 延遲識別碼可唯一識別與工作階段中的 UI 延遲的序號
- 工作階段識別碼，可唯一識別您的 Visual Studio 工作階段，從開始到關閉
- 通知是否顯示的 UI 延遲
- 擴充功能可能造成的 UI 延遲

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
> 並非所有的 UI 延遲發出通知。 因此，您應該一律檢查**所顯示的通知？** 值，才能正確地識別正確的 UI 延遲。

活動記錄檔中找到正確的 UI 延遲之後，記下  節點中所指定的 UI 延遲識別碼。 您將使用識別碼來尋找下一個步驟中對應的 ETW 事件。

## <a name="analyze-the-etw-trace"></a>分析 ETW 追蹤

接下來，開啟追蹤檔案。 您可以使用相同的執行個體 PerfView 或啟動新的執行個體，並在左上方視窗的追蹤檔案的位置來設定目前的資料夾路徑。

![在 Perfview 中設定的資料夾路徑](media/perfview-set-path.png)

然後，在左窗格中選取的追蹤檔案，並開啟該選擇**開啟**上按一下滑鼠右鍵功能表或操作功能表。

> [!NOTE]
> 根據預設 PerfView 會輸出 Zip 封存。 當您開啟*trace.zip*，它會自動解壓縮封存，並開啟追蹤。 您可以藉由取消核取 略過這個**Zip**追蹤收集期間的方塊。 不過，如果您打算傳送，並使用不同的機器的追蹤，我們強烈建議針對取消核取**Zip**  方塊中。 沒有這個選項時，所需的 Pdb，Ngen 組件會隨附於追蹤，並因此從 Ngen 組件的符號將不會解析目的地電腦上。 (請參閱[此部落格文章](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/)如需詳細資訊在 Pdb，Ngen 組件。)

可能需要幾分鐘的時間來處理，並開啟追蹤 PerfView。 一旦開啟追蹤，各種 「 檢視 」 清單會出現在其下。

![PerfView 追蹤摘要檢視](media/perfview-summary-view-events-selected.png)

我們會先使用**事件**檢視，以取得 UI 延遲時間範圍：

1. 開啟**事件**藉由選取的檢視`Events`節點下的追蹤，然後選擇**開啟**上按一下滑鼠右鍵功能表或操作功能表。
2. 選取 「`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`"的左窗格中。
3. 按下 enter 鍵

選取會套用所有`ExtensionUIUnresponsiveness`事件會顯示在右窗格中。

![在 [事件] 檢視中選取事件](media/perfview-event-selection.png)

在右窗格中的每個資料列會對應到 UI 延遲。 事件包含 「 延遲識別碼 」 值應該符合在步驟 6 中的活動記錄的延遲識別碼。 因為`ExtensionUIUnresponsiveness`引發 UI 延遲，而事件時間戳記的結尾 （大約） 標記的 UI 延遲的結束時間。 事件也包含延遲的持續時間。 我們可以減去從 UI 延遲啟動時取得的時間戳記的結束時間戳記的持續時間。

![計算 UI 延遲時間範圍](media/ui-delay-time-range.png)

在先前的螢幕擷取畫面，比方說，事件時間戳記 12,125.679 而延遲的持續時間 6,143.085 （毫秒）。 因此，
* 延遲啟動是 12,125.679 6,143.085 = 5,982.594。
* UI 延遲時間範圍是以 12,125.679 5,982.594。

一旦我們擁有的時間範圍，我們可以關閉共**事件**檢視，並開啟**執行緒的時間 （含 StartStop 活動） 堆疊**檢視。 此檢視是特別有用，因為通常會封鎖 UI 執行緒的延伸模組都只在等候其他執行緒或 I/O 繫結作業。 因此， **CPU 堆疊**檢視中，也就是在大部分情況下的 移至 」 選項，可能不會擷取該執行緒花費封鎖，因為它不在這段期間使用 CPU 的時間。 **執行緒時間堆疊**正確顯示封鎖時間解決這個問題。

![PerfView 摘要 檢視中的執行緒時間 （StartStop 活動） 堆疊節點](media/perfview-thread-time-with-startstop-activities-stacks.png)

在開啟時**執行緒時間堆疊**檢視中，選擇**devenv**程序，以開始分析。

![執行緒 UI 延遲分析的時間堆疊的檢視](media/ui-delay-thread-time-stacks.png)

在 **執行緒時間堆疊**檢視中，在頁面的左上方，您可以設定時間範圍內為我們計算的值上一個步驟，然後按下**Enter**讓堆疊會調整為該時間範圍。

> [!NOTE]
> 判斷哪一個執行緒 UI （啟動） 的執行緒可能違反直覺，如果已開啟 Visual Studio 之後，追蹤集合已啟動。 不過，在 UI （啟動） 執行緒的堆疊上的第一個項目最有可能一律會作業系統 Dll (*ntdll.dll*並*kernel32.dll*) 後面接著`devenv!?`，然後`msenv!?`. 這一系列可協助您識別 UI 執行緒。

 ![識別啟動執行緒](media/ui-delay-startup-thread.png)

您可以也進一步篩選此檢視只包含 包含來自您套件的模組堆疊。

* 設定**GroupPats**空的文字，若要移除依預設，加入任何群組。
* 設定**IncPats**來包含部分除了現有的處理序篩選組件名稱。 在此情況下，它應該是**devenv;UIDelayR2**。

![在執行緒時間堆疊檢視中設定 GroupPath 和 IncPath](media/perfview-tts-group-path-inc-path.png)

PerfView 有詳細的指導之下**協助**功能表可供您識別您的程式碼中的效能瓶頸。 此外，下列連結提供如何使用執行緒來最佳化您的程式碼的 Api 的 Visual Studio 的詳細資訊：

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

您也可以使用新的 Visual Studio 靜態分析器擴充功能 (NuGet 套件[此處](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers))，可提供最佳作法指引撰寫有效率的延伸模組。 看到一份[VS SDK 分析器](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md)並[執行緒分析器](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md)。

> [!NOTE]
> 如果您無法解決相依性由於一堆您沒有控制項上 （例如，如果您的延伸模組必須在 UI 執行緒上呼叫同步 VS 服務），我們想要了解它。 如果您是我們的 Visual Studio 合作夥伴計畫的成員，您可以與我們連絡提交開發人員的支援要求。 否則，請使用 '回報問題 工具來提交您的意見反應，並包含`"Extension UI Delay Notifications"`標題中。 請也包含您的分析的詳細的描述。

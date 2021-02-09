---
title: 診斷 Visual Studio 中的擴充功能 UI 延遲 |Microsoft Docs
description: 如果 UI 延遲可能是延伸模組造成的，Visual Studio 會通知您。 瞭解如何診斷延伸模組程式碼中造成 UI 延遲的情況。
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jmartens
ms.workload: multiple
ms.openlocfilehash: 508fdd44a1c73f66d88317b7ec304e810f5f12e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890795"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>如何：診斷延伸模組造成的 UI 延遲

當 UI 變得沒有回應時，Visual Studio 會檢查 UI 執行緒的呼叫堆疊，從分葉開始並朝基底處理。 如果 Visual Studio 判斷呼叫堆疊框架屬於已安裝並啟用之延伸模組的一部分，則會顯示通知。

![UI 延遲 (無回應) 通知](media/ui-delay-notification-in-vs.png)

通知會通知使用者 UI 延遲 (也就是說，UI 中的無回應) 可能是來自延伸模組的程式碼結果。 它也可讓使用者選擇停用擴充功能或未來的延伸模組通知。

本檔說明如何診斷延伸模組程式碼中會造成 UI 延遲通知的內容。

> [!NOTE]
> 請勿使用 Visual Studio 實驗性實例來診斷 UI 延遲。 使用實驗性實例時，會關閉 UI 延遲通知所需的呼叫堆疊分析部分，這表示可能不會顯示 UI 延遲通知。

診斷程式的總覽如下所示：
1. 識別觸發程式案例。
2. 重新開機 VS 活動記錄。
3. 開始 ETW 追蹤。
4. 觸發通知以再次出現。
5. 停止 ETW 追蹤。
6. 檢查活動記錄以取得延遲識別碼。
7. 使用步驟6中的延遲識別碼分析 ETW 追蹤。

在下列各節中，我們將更詳細地解說這些步驟。

## <a name="identify-the-trigger-scenario"></a>識別觸發程式案例

若要診斷 UI 延遲，您必須先找出哪些 (的動作順序) 導致 Visual Studio 顯示通知。 這是為了讓您可以在稍後開啟記錄時觸發通知。

## <a name="restart-vs-with-activity-logging-on"></a>重新開機 VS 活動記錄

Visual Studio 可以產生「活動記錄」，以提供在對問題進行偵錯工具時有用的資訊。 若要在 Visual Studio 中開啟活動記錄，請使用 `/log` 命令列選項開啟 Visual Studio。 Visual Studio 啟動之後，活動記錄會儲存在下列位置：

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

若要深入瞭解您可以如何尋找 VS 實例識別碼，請參閱偵測 [和管理 Visual Studio 實例的工具](../install/tools-for-managing-visual-studio-instances.md)。 我們稍後會使用此活動記錄來瞭解有關 UI 延遲和相關通知的詳細資訊。

## <a name="starting-etw-tracing"></a>開始 ETW 追蹤

您可以使用 [PerfView](https://github.com/Microsoft/perfview/) 來收集 ETW 追蹤。 PerfView 提供便於使用的介面，可用於收集 ETW 追蹤並進行分析。 使用下列命令來收集追蹤：

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

這會啟用「Microsoft VisualStudio」提供者，這是提供者 Visual Studio 使用於與 UI 延遲通知相關的事件。 它也會針對 PerfView 可用來產生 **執行緒時間堆疊** 視圖的核心提供者，指定關鍵字。

## <a name="trigger-the-notification-to-appear-again"></a>觸發通知以再次顯示

一旦 PerfView 啟動追蹤收集之後，您就可以使用步驟 1) 的觸發程式動作順序 (，讓通知再次出現。 一旦顯示通知，您就可以停止 PerfView 的追蹤收集來處理並產生輸出追蹤檔。

## <a name="stop-etw-tracing"></a>停止 ETW 追蹤

若要停止追蹤收集，只要使用 [PerfView] 視窗上的 [ **停止收集** ] 按鈕即可。 停止追蹤收集之後，PerfView 會自動處理 ETW 事件並產生輸出追蹤檔。

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>檢查活動記錄以取得延遲識別碼

如先前所述，您可以在 *%APPDATA%\Microsoft\VisualStudio \<vs_instance_id>\ActivityLog.xml* 找到活動記錄。 每次 Visual Studio 偵測到延伸模組 UI 延遲時，它就會將節點寫入至活動記錄以 `UIDelayNotifications` 做為來源。 此節點包含 UI 延遲的四項資訊：

- UI 延遲識別碼，這個序號可唯一識別 VS 會話中的 UI 延遲
- 會話識別碼，可唯一識別從開始到關閉的 Visual Studio 會話
- 是否顯示 UI 延遲的通知
- 可能造成 UI 延遲的延伸模組

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
> 並非所有的 UI 延遲都會產生通知。 因此，您應該一律檢查 **顯示的通知？** 值，以正確地識別正確的 UI 延遲。

當您在活動記錄中找到正確的 UI 延遲之後，請記下節點中指定的 UI 延遲識別碼。 您將在下一個步驟中使用此識別碼來尋找對應的 ETW 事件。

## <a name="analyze-the-etw-trace"></a>分析 ETW 追蹤

接下來，開啟追蹤檔案。 您可以使用相同的 PerfView 實例或啟動新的實例，並將視窗左上角的目前資料夾路徑設定為追蹤檔案的位置，來進行這項作業。

![在 Perfview 中設定資料夾路徑](media/perfview-set-path.png)

然後，選取左窗格中的追蹤檔案，並從按一下滑鼠右鍵或操作功能表中選擇 [ **開啟** ] 來開啟它。

> [!NOTE]
> 依預設，PerfView 會輸出 Zip 封存。 當您開啟 *trace.zip* 時，它會自動將封存解壓縮，並開啟追蹤。 您可以在追蹤收集期間取消核取 [ **Zip** ] 方塊，以略過這項工作。 但是，如果您打算在不同的電腦之間傳輸和使用追蹤，強烈建議您不要取消核取 [ **Zip** ] 方塊。 如果沒有這個選項，Ngen 元件的必要 Pdb 將不會伴隨追蹤，因此不會在目的地電腦上解析 Ngen 元件的符號。  (請參閱 [此 blog 文章](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) ，以取得 Ngen 元件之 pdb 的詳細資訊。 ) 

PerfView 可能需要幾分鐘的時間來處理並開啟追蹤。 開啟追蹤之後，會在其下顯示各種「views」清單。

![PerfView 追蹤摘要視圖](media/perfview-summary-view-events-selected.png)

我們會先使用 [ **事件** ] 視圖來取得 UI 延遲的時間範圍：

1. 選取追蹤底下的 `Events` 節點，然後從滑鼠右鍵功能表或操作功能表中選擇 [**開啟**]，以開啟 [事件] 視圖。
2. `Microsoft-VisualStudio/ExtensionUIUnresponsiveness`在左窗格中選取 []。
3. 按 Enter

此選項會套用，而且所有 `ExtensionUIUnresponsiveness` 事件都會顯示在右窗格中。

![在事件檢視中選取事件](media/perfview-event-selection.png)

右窗格中的每個資料列都會對應至 UI 延遲。 此事件包含「延遲識別碼」值，該值應符合步驟6中活動記錄檔的延遲識別碼。 由於 `ExtensionUIUnresponsiveness` 是在 ui 延遲結束時引發，事件的時間戳記大約 (大約) 標記 ui 延遲的結束時間。 此事件也會包含延遲的持續時間。 我們可以從結束時間戳記減去持續時間，以取得 UI 延遲啟動的時間戳記。

![計算 UI 延遲時間範圍](media/ui-delay-time-range.png)

例如，在上一個螢幕擷取畫面中，事件的時間戳記是12125.679，而延遲期間是 6143.085 (ms) 。 因此，
* 延遲開始時間為 12125.679-6143.085 = 5982.594。
* UI 延遲時間範圍是5982.594 到12125.679。

有了時間範圍之後，我們就可以關閉 [ **事件** ] 視圖，並 **使用 StartStop 活動) 堆疊視圖開啟執行緒時間 (** 。 此視圖特別方便，因為封鎖 UI 執行緒的延伸模組通常只會在等候其他執行緒或 i/o 系結作業。 因此，在大部分情況下，[ **CPU 堆疊** ] 的 [移至] 選項可能不會捕捉執行緒花費在封鎖的時間，因為它不會在這段時間內使用 CPU。 **執行緒時間堆疊** 會正確顯示封鎖的時間來解決此問題。

![在 PerfView 摘要視圖中使用 StartStop 活動) 堆疊節點的執行緒時間 (](media/perfview-thread-time-with-startstop-activities-stacks.png)

開啟 **執行緒時間堆疊** 視圖時，請選擇 **devenv** 進程以開始分析。

![UI 延遲分析的執行緒時間堆疊觀點](media/ui-delay-thread-time-stacks.png)

在 [ **執行緒時間堆疊** ] 中，您可以在頁面左上角，將時間範圍設定為我們在上一個步驟中計算的值，然後按 **enter** ，以便將堆疊調整為該時間範圍。

> [!NOTE]
> 如果在已開啟 Visual Studio 之後啟動追蹤收集，則判斷哪個執行緒是 UI (啟動) 執行緒可以違反直覺。 不過，UI 堆疊上的第一個元素 (啟動) 執行緒最可能一律是作業系統 Dll (*ntdll.dll* 和 *kernel32.dll*) 之後再接著 `devenv!?` `msenv!?` 。 此順序有助於識別 UI 執行緒。

 ![識別啟動執行緒](media/ui-delay-startup-thread.png)

您也可以進一步篩選此視圖，只包含套件中包含模組的堆疊。

* 將 **GroupPats** 設定為空白文字，以移除依預設新增的任何群組。
* 將 **IncPats** 設定為包含元件名稱的一部分，以及現有的進程篩選。 在此情況下，它應該是 **devenv;UIDelayR2**。

![線上程時間堆疊視圖中設定 GroupPath 和 IncPath](media/perfview-tts-group-path-inc-path.png)

PerfView 在 [說明] 功能表下有 **詳細的指引** ，可讓您用來識別程式碼中的效能瓶頸。 此外，下列連結提供有關如何利用 Visual Studio 執行緒 Api 來優化程式碼的詳細資訊：

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

您也可以使用新的 Visual Studio 靜態分析器 (NuGet [) 套件的](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers) 延伸模組），以提供撰寫有效率擴充功能的最佳作法指引。 查看 [VS SDK 分析器](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) 和 [執行緒分析器](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md)的清單。

> [!NOTE]
> 如果您因為相依性無法控制 (而無法處理無回應，例如，如果您的延伸模組必須呼叫 UI 執行緒上的同步 VS 服務) ，我們想要知道它的相關資訊。 如果您是 Visual Studio 合作夥伴方案的成員，您可以提交開發人員支援要求來洽詢我們。 否則，請使用「回報問題」工具來提交您的意見反應，並 `"Extension UI Delay Notifications"` 將其包含在標題中。 也請包含您分析的詳細描述。

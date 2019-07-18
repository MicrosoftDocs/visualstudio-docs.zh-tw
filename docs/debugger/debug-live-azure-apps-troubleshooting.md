---
title: 針對快照集偵錯進行疑難排解 | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3c66ba4a5031326ec288d3a5f2f3c4851d17ca6
ms.sourcegitcommit: 74c5360186731de07828764eb32ea1033a8c2275
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559743"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 中快照集偵錯的疑難排解和已知問題

如果這篇文章中所述的步驟無法解決您的問題，問題上搜尋[開發人員社群](https://developercommunity.visualstudio.com/spaces/8/index.html)或選擇回報新問題**協助** > **傳送意見反應**  > **回報問題**Visual Studio 中。

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>問題：「 附加快照偵錯工具 」 遇到 HTTP 狀態碼錯誤

如果您看到下列錯誤**輸出**期間嘗試附加的視窗，它可能是下面所列的已知的問題。 建議的解決方案，再如果問題持續發生，請連絡 「 上述的別名。

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) 未授權

此錯誤表示 REST 呼叫發給由 Visual Studio Azure 會使用該認證無效。 使用 Azure Active Directory 輕鬆 OAuth 模組的已知的 bug 可能會產生此錯誤。

請執行下列步驟：

* 請確定您的 Visual Studio 個人化帳戶具有 Azure 訂用帳戶與您要將附加至的資源的權限。 若要判斷這個快速的方法是檢查資源是否可用，在對話方塊中，從**偵錯** > **附加快照偵錯工具...**  >  **Azure 資源** > **選取現有**，或在 [雲端總管]。
* 如果此錯誤持續發生，請使用其中一種本文開頭所述的意見反應通道。

### <a name="403-forbidden"></a>(403) 禁止

此錯誤表示權限遭到拒絕。 這可能會因許多不同的問題。

請執行下列步驟：

* 請確認您的 Visual Studio 帳戶具有必要的角色型存取控制 (RBAC) 權限資源的有效 Azure 訂用帳戶。 AppService，請檢查您是否有權限[查詢](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get)App Service 方案裝載您的應用程式。
* 請確認您的用戶端電腦的時間戳記是正確和最新狀態。 伺服器關閉通常超過 15 分鐘的要求時間戳記的時間戳記會產生此錯誤。
* 如果此錯誤持續發生，請使用其中一種本文開頭所述的意見反應通道。

### <a name="404-not-found"></a>(404) 找不到

此錯誤表示，無法在伺服器上找到的網站。

請執行下列步驟：

* 請確認您已部署且會將附加至 App Service 資源上執行的網站。
* 確認站台位於 https://\<資源\>。 azurewebsites.net
* 如果此錯誤持續發生，請使用其中一種本文開頭所述的意見反應通道。

### <a name="406-not-acceptable"></a>(406) 無法接受

此錯誤表示伺服器無法回應要求的 Accept 標頭中所設定。

請執行下列步驟：

* 請確認您的網站位於 https://\<資源\>。 azurewebsites.net
* 請確認您的網站，尚未移轉成新的執行個體。 快照偵錯工具會使用要求路由傳送到特定的執行個體，這可能會產生此錯誤間歇性 ARRAffinity 的概念。
* 如果此錯誤持續發生，請使用其中一種本文開頭所述的意見反應通道。

### <a name="409-conflict"></a>(409) 衝突

此錯誤表示要求衝突與目前的伺服器狀態。

這是當使用者嘗試附加快照偵錯工具對已啟用 application Insights AppService 時會發生的已知的問題。 Application Insights 設定不同的大小寫比 Visual Studio 中，使用 AppSettings 造成此問題。

::: moniker range=">= vs-2019"
我們已在 Visual Studio 2019 來解決這個問題。
::: moniker-end

請執行下列步驟：

::: moniker range="vs-2017"

* 在 Azure 入口網站中確認 SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) 和 InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) AppSettings 是大寫。 如果沒有，更新的設定以手動的方式，可強制站台重新啟動。
::: moniker-end
* 如果此錯誤持續發生，請使用其中一種本文開頭所述的意見反應通道。

### <a name="500-internal-server-error"></a>(500) 的內部伺服器錯誤

此錯誤表示網站已完全關閉，或伺服器無法處理要求。 快照集偵錯工具執行應用程式的唯一函式。 [Application Insights 快照集偵錯工具](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger)提供的例外狀況的快照，且可能最適合的工具，針對您的需求。

### <a name="502-bad-gateway"></a>閘道不正確 (502)

此錯誤表示伺服器端網路連線問題，可能是暫時性。

請執行下列步驟：

* 請等候幾分鐘的時間之前再次附加快照偵錯工具。
* 如果此錯誤持續發生，請使用其中一種本文開頭所述的意見反應通道。

## <a name="issue-snappoint-does-not-turn-on"></a>問題：貼齊點不會開啟

如果看到快照點出現警告圖示![快照點警告圖示](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "快照點警告圖示")，而不是一般的快照點圖示，表示快照點未開啟。

![快照點未開啟](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "快照點未開啟")

請執行下列步驟：

1. 請確定您有相同版本的原始碼，用來建置及部署您的應用程式。 請確定您正在載入適用於部署的正確符號。 若要這樣做，請在進行快照集偵錯時檢視 [模組]  視窗，並確認 [符號檔案] 資料行顯示針對正在偵錯的組載入的 .pdb 檔案。 快照偵錯工具將嘗試自動為部署下載及使用符號。

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>問題：開啟 快照集時，未載入符號

如果您看到下列視窗中，表示未載入符號。

![未載入符號](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "未載入符號")

請執行下列步驟：

- 按一下此頁面上的 [變更符號設定...]  連結。 在 [偵錯] > [符號]  設定中，新增一個符號快取目錄。 在設定符號路徑之後，重新啟動快照集偵錯。

   專案中可用的符號或 .pdb 檔案都必須與您的 App Service 部署相符。 大部分的部署 (透過 Visual Studio、搭配 Azure Pipelines 或 Kudu 的 CI/CD 進行的部署) 將會和 App Service 一起發行您的符號檔案。 設定符號快取目錄讓 Visual Studio 能夠使用這些符號。

   ![符號設定](../debugger/media/snapshot-troubleshooting-symbol-settings.png "符號設定")

- 或者，如果您的組織使用符號伺服器，或是卸除另一個路徑中的符號，請使用符號設定為部署載入正確的符號。

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>問題：我看不到 [雲端總管] 中的 「 附加快照偵錯工具 」 選項

請執行下列步驟：

- 請確定已安裝的快照偵錯工具元件。 開啟 Visual Studio 安裝程式，並勾選 Azure 工作負載中的 [快照偵錯工具]  元件。
::: moniker range="< vs-2019"
- 確定您的應用程式受到支援。 目前僅支援部署至 Azure App Service 的 ASP.NET (4.6.1+) 和 ASP.NET Core (2.0 +) 應用程式。
::: moniker-end
::: moniker range=">= vs-2019"
- 確定您的應用程式受到支援：
  - Azure App Service - 在 .NET Framework 4.6.1 或更新版本中執行的 ASP.NET 應用程式。
  - Azure App Service - 在 Windows 上的 .NET Core 2.0 或更新版本中執行的 ASP.NET Core 應用程式。
  - Azure 虛擬機器 (與虛擬機器擴展集) - 在 .NET Framework 4.6.1 或更新版本中執行的 ASP.NET 應用程式。
  - Azure 虛擬機器 (與虛擬機器擴展集) - 在 Windows 上的 .NET Core 2.0 或更新版本中執行的 ASP.NET 應用程式。
  - Azure Kubernetes Service - 在 Debian 9 上的 .NET Core 2.2 或更新版本中執行的 ASP.NET Core 應用程式。
  - Azure Kubernetes Service - 在 Alpine 3.8 上的 .NET Core 2.2 或更新版本中執行的 ASP.NET Core 應用程式。
  - Azure Kubernetes Service - 在 Ubuntu 18.04 上的 .NET Core 2.2 或更新版本中執行的 ASP.NET Core 應用程式。
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>問題：我只會看到節流診斷工具中的快照集

![節流快照點](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "節流快照點")

請執行下列步驟：

- 快照集僅佔用少量記憶體，但需要付費。 如果快照偵錯工具偵測到您的伺服器處於大量記憶體負載狀態，將不會建立快照集。 您可以停止快照偵錯工具工作階段，以刪除已經擷取的快照集，然後再試一次。

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>問題：快照集偵錯多個版本的 Visual Studio 會顯示錯誤

Visual Studio 2019 需要較新版的 Azure App Service 上的快照集偵錯工具網站延伸模組。  此版本不相容於舊版的 Visual Studio 2017 所使用的快照集偵錯工具網站延伸模組。  如果您嘗試將 Visual Studio 2019 的快照集偵錯工具附加至先前偵錯快照集偵錯工具在 Visual Studio 2017 中的 Azure App Service，您會收到下列錯誤：

![不相容的快照集偵錯工具網站延伸 Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "網站延伸模組不相容的快照集偵錯工具 Visual Studio 2019")

相反地，如果您使用 Visual Studio 2017 來將快照集偵錯工具附加至先前偵錯快照集偵錯工具在 Visual Studio 2019 的 Azure App Service 時，您會得到下列錯誤：

![不相容的快照集偵錯工具網站擴充 Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "網站延伸模組不相容的快照集偵錯工具 Visual Studio 2017")

若要修正此問題，請在 Azure 入口網站中刪除下列應用程式設定並再次附加快照偵錯工具：

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>問題：我有快照集偵錯的問題，而且我需要啟用更多的記錄

### <a name="enable-agent-logs"></a>啟用代理程式記錄

若要啟用和停用代理程式記錄，請開啟的 Visual Studio，瀏覽至 [工具] > [選項] > [快照集偵錯工具] > [啟用代理程式記錄]  。 請注意，如果也已經啟用*在工作階段開始時刪除舊的代理程式記錄*，每個成功的 Visual Studio 附加都將會刪除先前的代理程式記錄。

您可以在下列位置找到代理程式記錄：

- App Service：
  - 瀏覽至您 App Service 的 Kudu 網站 (也就是 yourappservice.**scm**.azurewebsites.net)，並瀏覽至 [偵錯主控台]。
  - 代理程式記錄檔會儲存在下列目錄：D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS：
  - 登入您的 VM 代理程式記錄檔會儲存，如下所示：C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - 瀏覽至以下目錄：/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>啟用 Profiler/檢測記錄

您可以在下列位置找到檢測記錄：

- App Service：
  - 錯誤記錄會自動傳送給 D:\Home\LogFiles\eventlog.xml、 事件標記為`<Provider Name="Instrumentation Engine" />`或 「 實際執行中斷點 」
- VM/VMSS：
  - 登入您的 VM 並開啟事件檢視器。
  - 開啟下列檢視：*Windows 記錄檔 > 應用程式*。
  - 使用*生產中斷點*或*檢測引擎*，依據*事件來源* *篩選目前的記錄*。
- AKS
  - 檢測引擎記錄位於 /tmp/diag/log.txt (在DockerFile 中設定 MicrosoftInstrumentationEngine_FileLogPath)
  - ProductionBreakpoint logging at /tmp/diag/shLog.txt

## <a name="known-issues"></a>已知問題

- 目前不支援針對相同的 App Service 對多個 Visual Studio 用戶端使用快照集偵錯。
- ASP.NET Core 專案尚未完全支援 Roslyn IL 最佳化。 對於某些 ASP.NET Core 專案來說，您可能無法查看一些變數，或在條件陳述式中使用一些變數。
- 特殊變數，例如 *$FUNCTION* 或 *$CALLER*，無法在 ASP.NET Core 專案的條件陳述式或記錄點中評估。
- 快照集偵錯無法在已開啟[本機快取](/azure/app-service/app-service-local-cache)的 App Service 上運作。
- 目前不支援對 API 應用程式進行快照集偵錯。

## <a name="site-extension-upgrade"></a>網站延伸模組升級

快照集偵錯和 Application Insights 相依於 ICorProfiler，系統會將 ICorProfiler 載入至網站處理序，並在升級期間造成檔案鎖定的問題。 我們建議採用此程序，以確保您的生產網站不需要停機。

- 在您的 App Service 內建立[部署位置](/azure/app-service/web-sites-staged-publishing)，並將網站部署至位置。
- 從 Visual Studio 的 [Cloud Explorer] 或從 Azure 入口網站交換位置與生產環境。
- 停止位置網站。 這需要幾秒鐘來關閉所有執行個體中的網站 w3wp.exe 處理序。
- 從 Kudu 網站或 Azure 入口網站升級位置網站延伸模組 ([App Service 刀鋒視窗] > [開發工具] > [擴充功能] > [更新]  )。
- 啟動位置網站。 我們建議您造訪網站以再次使用它。
- 交換位置與生產環境。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.md)
- [使用快照集偵錯工具的即時 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)
- [偵錯即時 ASP.NET Azure 虛擬 Machines\Virtual 機器擴展集使用快照集偵錯工具](../debugger/debug-live-azure-virtual-machines.md)
- [偵錯即時 ASP.NET Azure Kubernetes 中使用快照集偵錯工具](../debugger/debug-live-azure-kubernetes.md)
- [快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)

---
title: 針對快照集偵錯進行疑難排解 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/07/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b7916cbd3a7faa633baf53a18686779dc2b386c
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857758"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 中快照集偵錯的疑難排解和已知問題

如果這篇文章中所述的步驟無法解決您的問題，請連絡snaphelp@microsoft.com。

## <a name="issue-snappoint-does-not-turn-on"></a>問題：快照點沒有開啟

如果看到快照點出現警告圖示![快照點警告圖示](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "快照點警告圖示")，而不是一般的快照點圖示，表示快照點未開啟。

![快照點未開啟](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "快照點未開啟")

請執行下列步驟：

1. 請確定您有用來建置及部署 app.isua1 的相同版本原始程式碼。 請確定您正在載入適用於部署的正確符號。 若要這樣做，請在進行快照集偵錯時檢視 [模組] 視窗，並確認 [符號檔案] 資料行顯示針對正在偵錯的組載入的 .pdb 檔案。 快照偵錯工具將嘗試自動為部署下載及使用符號。

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>問題：開啟快照集時沒有載入符號

如果您看到下列視窗中，表示未載入符號。

![未載入符號](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "未載入符號")

請執行下列步驟：

- 按一下此頁面上的 [變更符號設定...]  連結。 在 [偵錯] > [符號] 設定中，新增一個符號快取目錄。 在設定符號路徑之後，重新啟動快照集偵錯。

   專案中可用的符號或 .pdb 檔案都必須與您的 App Service 部署相符。 大部分的部署 (透過 Visual Studio、搭配 Azure Pipelines 或 Kudu 的 CI/CD 進行的部署) 將會和 App Service 一起發行您的符號檔案。 設定符號快取目錄讓 Visual Studio 能夠使用這些符號。

   ![符號設定](../debugger/media/snapshot-troubleshooting-symbol-settings.png "符號設定")

- 或者，如果您的組織使用符號伺服器，或是卸除另一個路徑中的符號，請使用符號設定為部署載入正確的符號。

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>問題：我在 [Cloud Explorer] 中看不到 [附加快照偵錯工具] 選項

請執行下列步驟：

- 請確定已安裝的快照偵錯工具元件。 開啟 Visual Studio 安裝程式，並勾選 Azure 工作負載中的 [快照偵錯工具] 元件。
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

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>問題：我在診斷工具中只看到節流快照集

![節流快照點](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "節流快照點")

請執行下列步驟：

- 快照集僅佔用少量記憶體，但需要付費。 如果快照偵錯工具偵測到您的伺服器處於大量記憶體負載狀態，將不會建立快照集。 您可以停止快照偵錯工具工作階段，以刪除已經擷取的快照集，然後再試一次。

## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>問題：針對多個版本的 Visual Studio 進行快照集偵錯時顯示錯誤

VS 2019 需要在 Azure App Service 中安裝較新版本的快照偵錯工具網站延伸模組。  此版本與 VS 2017 所使用的較舊版快照偵錯工具網站延伸模組不相容。  如果嘗試將 VS 2019 中的快照偵錯工具，附加至先前以 VS 2017 中的快照偵錯工具偵錯過的 Azure App Service，就會發生以下錯誤：

![不相容的快照偵錯工具網站延伸模組 VS 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "不相容的快照偵錯工具網站延伸模組 VS 2019")

相反的，如果使用 VS 2017，將快照偵錯工具附加至先前以 VS 2019 中的快照偵錯工具偵錯過的 Azure App Service，就會發生以下錯誤：

![不相容的快照偵錯工具網站延伸模組 VS 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "不相容的快照偵錯工具網站延伸模組 VS 2017")

若要修正此問題，請在 Azure 入口網站中刪除下列應用程式設定並再次附加快照偵錯工具：

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>問題：我在進行快照集偵錯時發生問題，而且需要啟用更多記錄功能

### <a name="enable-agent-logs"></a>啟用代理程式記錄

若要啟用和停用代理程式記錄，請開啟的 Visual Studio，瀏覽至 [工具] > [選項] > [快照集偵錯工具] > [啟用代理程式記錄]。 請注意，如果也已經啟用*在工作階段開始時刪除舊的代理程式記錄*，每個成功的 Visual Studio 附加都將會刪除先前的代理程式記錄。

您可以在下列位置找到代理程式記錄：

- App Service：
  - 瀏覽至您 App Service 的 Kudu 網站 (也就是 yourappservice.**scm**.azurewebsites.net)，並瀏覽至 [偵錯主控台]。
  - 代理程式記錄儲存在以下目錄：D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS：
  - 登入您的 VM，代理程式記錄儲存在以下目錄：C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - 瀏覽至以下目錄：/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>啟用 Profiler/檢測記錄

您可以在下列位置找到檢測記錄：

- App Service：
  - 錯誤記錄檔會自動傳送至 D:\Home\LogFiles\eventlog.xml，事件會標記 <<Provider Name="Instrumentation Engine" //>> 或 "Production Breakpoints"
- VM/VMSS：
  - 登入您的 VM 並開啟事件檢視器。
  - 開啟下列檢視：[Windows 記錄] > [應用程式]。
  - 使用*生產中斷點*或*檢測引擎*，依據*事件來源**篩選目前的記錄*。
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
- 從 Kudu 網站或 Azure 入口網站升級位置網站延伸模組 ([App Service 刀鋒視窗] > [開發工具] > [擴充功能] > [更新])。
- 啟動位置網站。 我們建議您造訪網站以再次使用它。
- 交換位置與生產環境。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.md)
- [使用快照偵錯工具針對即時 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)
- [使用快照偵錯工具針對即時 ASP.NET Azure 虛擬機器\虛擬機器擴展集進行偵錯](../debugger/debug-live-azure-virtual-machines.md)
- [使用快照偵錯工具針對即時 ASP.NET Azure Kubernetes 進行偵錯](../debugger/debug-live-azure-kubernetes.md)
- [快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)
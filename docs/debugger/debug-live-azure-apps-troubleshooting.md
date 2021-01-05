---
title: 針對快照集偵錯進行疑難排解 | Microsoft Docs
description: 瞭解 Visual Studio 中快照集偵錯工具的疑難排解和已知問題。 載入 ICorProfiler，而不會導致生產網站停機。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b5a76c1cae508acd08e5f077d466facf02e0211a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728640"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 中快照集偵錯的疑難排解和已知問題

如果本文中所述的步驟無法解決您的問題，請在 [開發人員社群](https://aka.ms/feedback/suggest?space=8)中搜尋問題，**或是選擇 [** 說明  >  **傳送意見** 反應回報  >  Visual Studio 中的 **問題**] 來回報新的問題。

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>問題：「附加快照偵錯工具」遇到 HTTP 狀態碼錯誤

如果您在嘗試附加時在 [ **輸出** ] 視窗中看到下列錯誤，則可能是下列已知問題。 試用建議的解決方案，如果問題持續存在，請洽詢先前的別名。

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a> (401) 未經授權

此錯誤表示 Visual Studio 至 Azure 發出的 REST 呼叫使用不正確認證。 

請執行下列步驟：

* 請確定您的 Visual Studio 個人化帳戶具有您要附加之 Azure 訂用帳戶和資源的許可權。 若要判斷這一點，快速的方法就是在對話方塊中檢查資源是否可從 **Debug**  >  **Attach 快照偵錯工具 ...**  > **Azure 資源**  > **選取 [現有**] 或 Cloud Explorer 中的。
* 如果此錯誤持續存在，請使用本文開頭所述的其中一個意見反應通道。

如果您已在 App Service 上啟用驗證/授權 (EasyAuth) ，您可能會在呼叫堆疊錯誤訊息中遇到 LaunchAgentAsync 的401錯誤。 請確定 **當要求未通過驗證時，所要採取的動作** 是設定為 **允許匿名要求， (在 Azure 入口網站中不) 動作** ，並改為在 D:\Home\sites\wwwroot 中提供下列內容的 authorization.js。 

```
{
  "routes": [
    {
      "path_prefix": "/",
      "policies": {
        "unauthenticated_action": "RedirectToLoginPage"
      }
    },
    {
      "http_methods": [ "POST" ],
      "path_prefix": "/41C07CED-2E08-4609-9D9F-882468261608/api/agent",
      "policies": {
        "unauthenticated_action": "AllowAnonymous"
      }
    }
  ]
}
```

第一個路由會有效地保護您的應用程式網域，類似于 **使用 [IdentityProvider] 登入**。 第二個路由會公開驗證以外的 SnapshotDebugger AgentLaunch 端點，只有在已為您的 app service 啟用 SnapshotDebugger 預先安裝的網站延伸模組時， *才* 會執行預先定義的動作來啟動 SnapshotDebugger 診斷代理程式。 如需有關設定 authorization.js的詳細資訊，請參閱 [URL 授權規則](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html)。

### <a name="403-forbidden"></a>(403) 禁止

此錯誤表示許可權遭到拒絕。 這可能是由許多不同的問題所引起。

請執行下列步驟：

* 確認您的 Visual Studio 帳戶具有有效的 Azure 訂用帳戶，且具有必要的 Role-Based 存取控制 (RBAC) 資源的許可權。 針對 AppService，請檢查您是否有許可權可 [查詢](/rest/api/appservice/appserviceplans/get) 裝載您應用程式的 App Service 方案。
* 確認用戶端電腦的時間戳記是否正確且為最新狀態。 時間戳記超過15分鐘要求時間戳記的伺服器通常會產生此錯誤。
* 如果此錯誤持續存在，請使用本文開頭所述的其中一個意見反應通道。

### <a name="404-not-found"></a>找不到 (404) 

此錯誤表示在伺服器上找不到網站。

請執行下列步驟：

* 確認您已在要附加的 App Service 資源上部署並執行網站。
* 確認網站可在 HTTPs:// \<resource\> azurewebsites.net。
* 確認在 HTTPs://存取時，您正確執行的自訂 web 應用程式不會傳回狀態碼 404 \<resource\> 。 azurewebsites.net
* 如果此錯誤持續存在，請使用本文開頭所述的其中一個意見反應通道。

### <a name="406-not-acceptable"></a> (406) 無法接受

此錯誤表示伺服器無法回應要求的 Accept 標頭中所設定的類型。

請執行下列步驟：

* 確認您的網站可在 HTTPs:// \<resource\> azurewebsites.net。
* 確認您的網站尚未遷移至新的實例。 快照偵錯工具使用 ARRAffinity 的概念將要求路由傳送至特定的實例，這些實例可能會間歇性地產生此錯誤。
* 如果此錯誤持續存在，請使用本文開頭所述的其中一個意見反應通道。

### <a name="409-conflict"></a> (409) 衝突

此錯誤表示要求與目前的伺服器狀態衝突。

這是當使用者嘗試針對已啟用 ApplicationInsights 的 AppService 附加快照偵錯工具時，所發生的已知問題。 ApplicationInsights 會使用不同的大小寫來設定 AppSettings，Visual Studio 而不會造成此問題。

::: moniker range=">= vs-2019"
我們已在 Visual Studio 2019 中解決此問題。
::: moniker-end

請執行下列步驟：

::: moniker range="vs-2017"

* 在 Azure 入口網站中確認 SnapshotDebugger 的 AppSettings (SNAPSHOTDEBUGGER_EXTENSION_VERSION) 和 InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) 為大寫。 如果沒有，請手動更新設定，這會強制網站重新開機。
::: moniker-end
* 如果此錯誤持續存在，請使用本文開頭所述的其中一個意見反應通道。

### <a name="500-internal-server-error"></a> (500) 內部伺服器錯誤

此錯誤表示網站已完全關閉，或伺服器無法處理要求。 快照偵錯工具只會執行應用程式的功能。 [Application Insights 快照偵錯工具](/azure/azure-monitor/app/snapshot-debugger) 會提供例外狀況的快照，而且可能是最適合您需求的工具。

### <a name="502-bad-gateway"></a> (502) 不正確的閘道

此錯誤表示伺服器端的網路問題，可能是暫時性的。

請執行下列步驟：

* 請稍候幾分鐘再附加快照偵錯工具。
* 如果此錯誤持續存在，請使用本文開頭所述的其中一個意見反應通道。

## <a name="issue-snappoint-does-not-turn-on"></a>問題：快照點沒有開啟

如果您在快照點中看到警告圖示 ![快照點警告圖示](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "快照點警告圖示") ，而不是使用一般快照點圖示，則快照點不會開啟。

![快照點不會開啟](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "快照點不會開啟")

請執行下列步驟：

1. 請確定您擁有用來建立和部署應用程式的相同版本原始程式碼。 請確定您正在載入適用於部署的正確符號。 若要這樣做，請在進行快照集偵錯時檢視 [模組] 視窗，並確認 [符號檔案] 資料行顯示針對正在偵錯的組載入的 .pdb 檔案。 快照偵錯工具將嘗試自動為部署下載及使用符號。

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>問題：開啟快照集時沒有載入符號

如果您看到下列視窗中，表示未載入符號。

![符號不會載入](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "符號不會載入")

請執行下列步驟：

- 按一下此頁面上的 [變更符號設定...] 連結。 在 [偵錯] > [符號] 設定中，新增一個符號快取目錄。 在設定符號路徑之後，重新啟動快照集偵錯。

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

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>問題：針對多個版本的 Visual Studio 進行快照集偵錯時顯示錯誤

Visual Studio 2019 需要您 Azure App Service 上的較新版本快照偵錯工具網站延伸模組。  此版本與 Visual Studio 2017 所使用快照偵錯工具網站延伸模組的舊版不相容。  如果您嘗試將 Visual Studio 2019 中的快照偵錯工具附加至先前由 Visual Studio 2017 中的快照偵錯工具所進行的 Azure App Service，您將會收到下列錯誤：

![快照偵錯工具網站擴充功能不相容 Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "快照偵錯工具網站擴充功能不相容 Visual Studio 2019")

相反地，如果您使用 Visual Studio 2017 將快照偵錯工具附加至先前由 Visual Studio 2019 中的快照偵錯工具所調試的 Azure App Service，您將會收到下列錯誤：

![快照偵錯工具網站擴充功能不相容 Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "快照偵錯工具網站擴充功能不相容 Visual Studio 2017")

若要修正此問題，請在 Azure 入口網站中刪除下列應用程式設定並再次附加快照偵錯工具：

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>問題：我在進行快照集偵錯時發生問題，而且需要啟用更多記錄功能

### <a name="enable-agent-logs"></a>啟用代理程式記錄

若要啟用和停用代理程式記錄，請開啟的 Visual Studio，瀏覽至 [工具] > [選項] > [快照集偵錯工具] > [啟用代理程式記錄]。 請注意，如果也已經啟用 *在工作階段開始時刪除舊的代理程式記錄*，每個成功的 Visual Studio 附加都將會刪除先前的代理程式記錄。

您可以在下列位置找到代理程式記錄：

- App Service：
  - 瀏覽至您 App Service 的 Kudu 網站 (也就是 yourappservice.**scm**.azurewebsites.net)，並瀏覽至 [偵錯主控台]。
  - 代理程式記錄儲存在以下目錄：D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS：
  - 登入您的 VM，代理程式記錄檔會儲存如下： C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics \<Version> \ SnapshotDebuggerAgent_ * .txt
- AKS
  - 瀏覽至以下目錄：/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>啟用 Profiler/檢測記錄

您可以在下列位置找到檢測記錄：

- App Service：
  - 錯誤記錄會自動傳送至 D:\Home\LogFiles\eventlog.xml，事件會標示為「 `<Provider Name="Instrumentation Engine" />` 生產中斷點」或「生產中斷點」
- VM/VMSS：
  - 登入您的 VM 並開啟事件檢視器。
  - 開啟下列檢視：[Windows 記錄] > [應用程式]。
  - 使用 *生產中斷點* 或 *檢測引擎*，依據 *事件來源**篩選目前的記錄*。
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

快照集偵錯和 Application Insights 相依於 ICorProfiler，系統會將 ICorProfiler 載入至網站處理序，並在升級期間造成檔案鎖定的問題。 我們建議採用此程序，以確保您的生產網站沒有停機時間。

- 在您的 App Service 內建立[部署位置](/azure/app-service/web-sites-staged-publishing)，並將網站部署至位置。
- 從 Visual Studio 的 [Cloud Explorer] 或從 Azure 入口網站交換位置與生產環境。
- 停止位置網站。 這需要幾秒鐘來關閉所有執行個體中的網站 w3wp.exe 處理序。
- 從 Kudu 網站或 Azure 入口網站升級位置網站延伸模組 ([App Service 刀鋒視窗] > [開發工具] > [擴充功能] > [更新])。
- 啟動位置網站。 我們建議您造訪網站以再次使用它。
- 交換位置與生產環境。

## <a name="see-also"></a>請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
- [使用快照偵錯工具針對即時 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)
- [使用快照偵錯工具針對即時 ASP.NET Azure 虛擬機器\虛擬機器擴展集進行偵錯](../debugger/debug-live-azure-virtual-machines.md)
- [使用快照偵錯工具針對即時 ASP.NET Azure Kubernetes 進行偵錯](../debugger/debug-live-azure-kubernetes.md)
- [快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)

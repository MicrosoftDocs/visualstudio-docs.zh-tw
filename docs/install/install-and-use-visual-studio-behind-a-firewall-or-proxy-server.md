---
title: 在防火牆或 Proxy 伺服器後方安裝及使用
description: 如果您的組織使用防火牆或 Proxy 伺服器，請檢閱建議新增至允許清單或開啟的網域 URL、連接埠及通訊協定
ms.date: 05/13/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c1a1fd706ce64b9b39954142664e0799b6251c56
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180437"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>在防火牆或 Proxy 伺服器後方安裝並使用 Visual Studio 和 Azure 服務

如果您或組織使用防火牆或 Proxy 伺服器等安全性措施，建議您將部分網域 URL 新增至「允許清單」，並開啟某些連接埠和通訊協定，以在安裝及使用 Visual Studio 及 Azure 服務時取得最佳體驗。

* **[安裝 Visual Studio](#install-visual-studio)**：這些資料表包含要新增至允許清單的網域 url，讓您可以存取所需的所有元件和工作負載。

* **[使用 Visual Studio 和 Azure 服務](#use-visual-studio-and-azure-services)**：此資料表包含要新增至允許清單的網域 url，以及要開啟的埠和通訊協定，讓您可以存取您想要的所有功能和服務。

> [!NOTE]
> 本文針對 Windows 上的 Visual Studio 撰寫，但特定資訊也適用於在防火牆或 Proxy 伺服器後方[安裝 Visual Studio for Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)。

## <a name="install-visual-studio"></a>安裝 Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>應新增至允許清單的 URL

由於 Visual Studio 安裝程式會從各種不同網域與這些網域的下載伺服器下載檔案，因此下列是建議您在 UI 或部署指令碼中作為受信任 URL 新增至允許清單的網域 URL。

#### <a name="microsoft-domains"></a>Microsoft 網域

| 網域 | 目的 |
| - | - |
| go.microsoft.com | 安裝 URL 解析 |
| aka.ms | 安裝 URL 解析 |
| download.visualstudio.microsoft.com | 安裝套件下載位置 |
| download.microsoft.com | 安裝套件下載位置 |
| download.visualstudio.com | 安裝套件下載位置 |
| dl.xamarin.com | 安裝套件下載位置 |
| xamarin-downloads.azureedge.net | Android SDK 套件下載清單位置 |
| marketplace.visualstudio.com | Visual Studio 延伸模組下載位置 |
| \*. gallerycdn.vsassets.io  | Visual Studio 延伸模組下載位置 |
| visualstudio.microsoft.com | 文件位置 |
| docs.microsoft.com | 文件位置 |
| msdn.microsoft.com | 文件位置 |
| www\.microsoft.com | 文件位置 |
| \*.windows.net | 登入位置 |
| \*.microsoftonline.com | 登入位置 |
| \*.live.com | 登入位置 |
| | |

#### <a name="non-microsoft-domains"></a>非 Microsoft 網域

| 網域 | 安裝這些工作負載 |
| - | - |
| archive.apache.org | 使用 JavaScript 進行行動開發 (Cordova) |
| cocos2d-x.org | 使用 C++ 進行遊戲開發 (Cocos) |
| download.epicgames.com | 使用 C++ 進行遊戲開發 (Unreal Engine) |
| download.oracle.com | 使用 JavaScript 進行行動開發 (Java SDK) <br /><br />使用 .NET 進行行動開發 (Java SDK) |
| download.unity3d.com | 使用 Unity 進行遊戲開發 (Unity) |
| netstorage.unity3d.com | 使用 Unity 進行遊戲開發 (Unity) |
| dl.google.com | 使用 JavaScript 進行行動開發 (Android SDK 及 NDK、模擬器) <br /><br />使用 .NET 進行行動開發 (Android SDK 及 NDK、模擬器) |
| www\.incredibuild.com | 使用 C++ 進行遊戲開發 (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | 使用 C++ 進行遊戲開發 (IncrediBuild) |
| www\.python.org | Python 開發 (Python) <br /><br />資料科學和分析應用程式 (Python) |
| developerservices2.apple.com | Xamarin iOS 布建 |
| developer.apple.com | Xamarin iOS 布建 |
| appstoreconnect.apple.com | Xamarin iOS 布建 |
| idmsa.apple.com | Xamarin iOS 布建 |
| | |

## <a name="use-visual-studio-and-azure-services"></a>使用 Visual Studio 和 Azure 服務

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>應新增至允許清單的 URL，以及應開啟的連接埠和通訊協定

為確保您可以在使用防火牆或 proxy 伺服器後方的 Visual Studio 或 Azure 服務時存取您想要的所有專案，以下是您應該新增至允許清單的 Url，以及您可能想要開啟的埠和通訊協定。

| 服務或案例 | DNS 端點 | 通訊協定<br/>/Port | 描述 |
| - | - | -: | - | - |
| URL<br>resolution | go.microsoft.com<br><br>aka.ms | | 用來縮短 URL，其將會進一步解析為較長的 URL |
| 起始頁 | vsstartpage.blob.core.windows.net | 443 | 用來顯示起始頁上的「開發人員新聞」(僅限 Visual Studio 2017) |
| 目標式<br> 通知 <br>服務 | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | 用來將通知全域清單篩選為僅適用於特定電腦/使用方式情節類型的清單 |
| 分機 <br>更新檢查 | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | 用來於已安裝的擴充功能有可用更新時提供通知 <br><br> 以登入位置的形式使用 |
| AI 專案 <br>整合 | az861674.vo.msecnd.net | 443<br> | 用來設定新專案以將使用方式資料傳送至您已註冊的 Application Insights 帳戶 |
| Code Lens | codelensprodscus1su0.app<br>codelens.visualstudio.com | 443 | 用來在編輯器中提供有關檔案上次更新的時間、變更的時間軸、與變更相關聯的工作項目、建立者等相關資訊 |
| 實驗 <br>功能啟用 | visualstudio-devdiv-c2s.msedge.net | 80 | 用來啟用實驗性的新功能或功能變更 |
| 身分識別「徽章」 <br>(使用者名稱和顯示圖片)<br>及 <br>漫遊設定 | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | 用來在 IDE 中顯示使用者的名稱和顯示圖片 <br><br> 用來確保設定變更會從一部電腦漫遊至另一部電腦 |
| 遠端設定 | az700632.vo.msecnd.net | 443 | 用來關閉已知會在 Visual Studio 中造成問題的擴充功能 |
| Windows 工具 | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | HTTPs/443 | 用於 Windows 應用程式市集案例 |
| JSON 結構描述 <br>探索 <br><br>JSON 結構描述 <br>定義<br><br>JSON 結構描述 <br>下一節＜ <br>Azure 資源 | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | HTTP/80<br>HTTPs/443<br><br>HTTP/80<br><br>HTTPs/443 | 用來探索及下載使用者於編輯 JSON 文件時可能會用到的 JSON 結構描述 <br><br>用來取得針對 JSON 的中繼驗證結構描述<br><br>用來取得針對 Azure Resource Manager 部署範本的最新結構描述 |
| NPM 套件 <br>探索 | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | HTTPs/443<br><br>HTTP/80 &<br> HTTPs/443<br>HTTPs/443 | 搜尋 NPM 套件的必要項目，並用於 Web 專案中的用戶端指令碼套件安裝 |
| Bower 套件<br> 圖示<br><br>Bower 套件 <br>搜尋 | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | HTTP/80<br><br>HTTPs/443<br>HTTP/80<br>HTTPs/443 | 提供預設 Bower 套件圖示  <br><br>提供搜尋 Bower 套件的能力 |
| NuGet<br><br>Nuget 套件<br> 探索 | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | HTTPs/443<br><br>HTTP/80 &<br>HTTPs/443<br> | 用來驗證已簽署的 NuGet 套件。<br><br>搜尋 NuGet 套件和版本的必要項目 |
| GitHub 存放庫資訊 | api.github.com | HTTPs/443 | 取得 Bower 套件其他相關資訊的必要項目 |
| Web Linter | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | HTTP/80 | |
| Cookiecutter<br>總管範本<br>探索 <br><br>Cookiecutter <br>總管專案<br> 建立 | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | HTTPs/443<br> | 用來從我們建議的摘要和 GitHub 存放庫探索線上範本 <br><br>用來從需要單次隨選安裝來自 Python 套件索引 (PyPI) 之 Cookiecutter Python 套件的 Cookiecutter 範本建立專案 |
| Python 套件 <br>探索<br><br>Python 套件 <br>管理<br><br>新增 <br>Python <br> project <br>範本 | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | HTTPs/443 | 提供搜尋 pip 套件的能力<br><br>用來在遺失 pip 的情況下自動安裝它 <br><br>用來將下列新的 Python 專案範本解析成 Cookiecutter 範本 URL：<br> - 分類器專案<br>- 叢集專案 <br> - 迴歸專案 <br> - 使用 PyKinect 的 PyGame <br> - Pyvot 專案 |
| Office Web <br>Add-In - 增益集 <br> file:/// <br>驗證 <br>服務 | verificationservice.osi.office.net | HTTPs/443 | 用來驗證針對 Office Web 增益集的資訊清單 |
| SharePoint 和 <br>Office 增益集 | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | HTTPs/443 | 用來將 SharePoint 和 Office 增益集發行並測試到 SharePoint Online 和 Office 365 |
| 工作流程管理員 <br>測試服務<br> 主機 | | HTTP/12292 | 自動針對搭配工作流程測試 SharePoint 增益集所建立的防火牆規則 |
| 自動收集的 <br>可靠性統計資料 <br>及其他 <br>客戶經驗 <br>改進計畫 (CEIP)<br> (針對 Azure SDK 及 <br>SQL 工具) <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | HTTPs/443 | 用來將可靠性統計資料 (當機/停止回應資料) 從使用者傳送至 Microsoft。 若已啟用 [Windows 錯誤報告]，系統仍然會上傳實際的當機/停止回應傾印，此設定只會抑制統計資訊 <br>用來向 Visual Studio 顯示針對 Azure 工具 SDK 擴充功能的匿名使用模式，以及 SQL 工具的使用模式 |
| Visual Studio <br> 客戶經驗 <br>改進計畫 (CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | HTTPs/443 | 用來收集匿名使用模式及錯誤記錄檔 <br><br>用來追蹤 UI 凍結問題 |
| 建立及<br>管理 <br>Azure 資源 | management.azure.com <br>management.core.windows.net | HTTPs/443 | 用來建立 Azure 網站或其他資源，以支援 Web 應用程式、Azure Functions 或 WebJobs 的發行 |
| 已更新的 Web 發行工具 <br>檢查及副檔名 <br>Mahout | marketplace.visualstudio.com | HTTPs/443 | 用來檢查已更新發行工具的可用性。 若停用，可能不會顯示 Web 發行的潛在建議擴充功能 |
| 已更新的 Azure 資源 <br>建立端點資訊 | \*.blob.core.windows.net | HTTPs/443 | 用來更新用於針對特定 Azure 服務建立 Azure 資源的端點。 若停用，將會改用最後所下載的端點位置或內建端點位置 |
| 遠端偵錯和 <br>遠端分析 <br>Azure 網站 | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | 用來將遠端偵錯工具附加至 Azure 網站。 若停用，將無法把遠端偵錯工具附加至 Azure 網站 |
| Active Directory <br>圖形 | graph.windows.net | HTTPs/443 | 用來佈建新的 Azure Active Directory 應用程式。 同時也由 Office 365 MSGraph 已連線服務提供者使用 |
| Azure Functions <br>CLI 更新 <br>勾選 | functionscdn.azureedge.net | HTTPs/443 | 用來檢查 Azure Functions CLI 的更新版本。 若停用，將會改用 CLI 的快取複本 (或是由 Azure Functions 元件所攜帶的複本) |
| Cordova | npmjs.org<br>gradle.org | HTTP/80 &<br/>HTTPs/443 | HTTP 是用於建置期間的 Gradle 下載，HTTPS 則是用來將 Cordova 外掛程式包含在專案中 |
| Cloud Explorer | 1. &#60;clusterendpoint&#62; <br>Service Fabric <br>2. &#60;管理端點&#62;<br>一般 Cloud Exp <br>3. &#60;圖形端點&#62;<br>一般 Cloud Exp<br>4. &#60;儲存體帳戶端點&#62;<br>儲存體節點 <br>5. &#60;Azure 入口網站 URL&#62;<br>一般 Cloud Exp <br>6. &#60;金鑰保存庫端點&#62; <br>Azure Resource Manager VM 節點<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Service Fabric 遠端偵錯和 ETW 追蹤 | <br>1. HTTPs/19080<br>2. HTTPs/443<br>3. HTTPs/443<br>4. HTTPs/443<br>5. HTTPs/443<br>6. HTTPs/443<br>7. tcp/dynamic | 1. 範例： test12.eastus.cloudapp.com<br>2. 抓取訂閱並抓取/管理 Azure 資源<br>3. 抓取 Azure Stack 訂閱<br>4. 管理存放裝置資源（範例： mystorageaccount.blob.core.windows.net）<br>5. [在入口網站中開啟] 快顯功能表選項（在 Azure 入口網站中開啟資源）<br>6. 建立並使用金鑰保存庫進行 VM 的偵錯工具（例如： myvault.vault.azure.net） <br><br>7. 根據叢集中的節點數目和可用的埠，動態配置埠區塊。 <br><br>連接埠區塊將會嘗試取得節點數目的三倍數目 (最少 10 個連接埠)。<br><br>針對串流追蹤，會嘗試從 810 取得連接埠區塊。 若該連接埠區塊已被使用，則會嘗試取得下一個區塊，依此類推。 (若負載平衡器是空的，則最有可能會使用來自 810 的連接埠) <br><br>和偵錯類似，系統會保留四組連接埠區塊： <br>- connectorPort：30398、 <br>- forwarderPort：31398、 <br>- forwarderPortx86：31399、<br>- fileUploadPort：32398<br> |
| 雲端服務 | 1. RDP<br><br>2. core.windows.net <br><br>3.  management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;使用者的雲端服務&#62;.cloudapp.net <br> &#60;使用者的 VM&#62;.&#60;區域&#62;.azure.com | 1. rdp/3389 <br><br> 2. HTTPs/443 <br><br> 3. HTTPs/443 <br><br> 4. HTTPs/443 <br><br> 5. HTTPs/443 <br><br>6. tcp <br>a）30398 <br>b）30400 <br>c）31398 <br>d）31400 <br>e）32398 <br>f）32400 | 1. 雲端服務 VM 的遠端桌面 <br><br> 2. 私人診斷設定的儲存體帳戶元件 <br><br> 3. Azure 入口網站 <br><br> 4. 伺服器總管 Azure 儲存體 &#42; 是名為儲存體帳戶的客戶  <br><br> 5. 開啟入口網站的連結 &#47; 下載訂用帳戶憑證 &#47; 發佈設定檔案 <br><br>6. a) 針對雲端服務及 VM 進行遠端偵錯的連接器本機連接埠<br> 6. b) 針對雲端服務及 VM 進行遠端偵錯的連接器公用連接埠 <br> 6. c) 針對雲端服務及 VM 進行遠端偵錯的轉寄站本機連接埠 <br> 6. d) 針對雲端服務及 VM 進行遠端偵錯的轉寄站公用連接埠  <br> 6. e) 針對雲端服務及 VM 進行遠端偵錯的檔案上傳程式本機連接埠 <br> 6. f) 針對雲端服務及 VM 進行遠端偵錯的檔案上傳程式公開連接埠 |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | HTTPs/443 | 1. 檔 <br><br> 2. 建立叢集功能 <br><br>3. &#42; 是 Azure 金鑰保存庫名稱（範例：-test11220180112110108.vault.azure.net  <br><br>  4. &#42; 是動態的（例如： vsspsextprodch1su1.vsspsext.visualstudio.com） |
| 快照集 <br>偵錯工具 | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42; azurewebsites.net <br> 4. &#42;. scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. 遠端服務/伺服器 IP 位址/FQDN | 1. HTTPs/443 <br>2. HTTPs/443  <br>3. HTTP/80 <br>4. HTTPs/443 <br>5. HTTPs/443 <br>6. Concord/<br> 4022（Visual Studio 版本相依） | 1. 查詢應用程式服務 SKU 大小的 json 檔案 <br>2. 各種 Azure RM 呼叫 <br>3. 透過的網站準備呼叫  <br>4. 客戶的目標 App Service Kudu 端點 <br>5. 在 nuget.org 中發行的查詢網站延伸模組版本 <br>6.[遠端偵錯](../debugger/remote-debugging.md) |
| Azure 串流分析 <br><br>HDInsight | Management.azure.com | HTTPs/443 | 用來檢視、提交、執行及管理 ASA 作業 <br><br> 用來瀏覽 HDI 叢集，以及對 HDI 作業進行提交、診斷及偵錯 |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | HTTPs/443 | 用來對作業進行編譯、提交、檢視、診斷及偵錯；用來瀏覽 ADLS 檔案；用來上傳及下載檔案 |
| 封裝服務 | [account].visualstudio.com <br/> [帳戶].\*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | HTTPs/443 | \* \* \* 只有某些組建工作案例（例如： Nuget 工具安裝程式、Node 工具安裝程式），或如果您想要搭配摘要使用公用上游，才需要 npmjs.org、. nuget.org 和 nodejs.org。 封裝服務的核心功能則需要使用其他三個網域。 |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | 用來與 Azure DevOps Services 連線 |
| 開發人員社群 | sendvsfeedback2.azurewebsites.net/api | HTTPs/443 | 用來呼叫開發人員社區意見反應工具 Api （我的問題、搜尋、投票、批註、提交、上傳、繼續） |
| Intellicode | \*. intellicode.vsengsaas.visualstudio.com | HTTPs/443 | 用來呼叫 Intellicode Api |
| Live Share | \*. liveshare.vsengsaas.visualstudio.com| HTTPs/443 | 用來呼叫 Live Share Api |
| Visual Studio Codespaces | \*. online.visualstudio.com | HTTPs/443 | 用來呼叫 Visual Studio Codespaces Api |
| JavaScript 自動型別取得 | registry.npmjs.org | HTTPs/443 | 用來安裝 TypeScript 類型定義，以提供適用于熱門 JavaScript 程式庫的 Intellisense |
| Visual Studio 訂閱授權服務 | app.vssps.visualstudio.com/apis/<br/>授權/ClientRights | HTTPs/443 | 線上啟用的授權 |
| 偵錯工具 | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>onecore. msvsmon. \* 。位址<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | HTTPs/443 | 1. <br>用於在 Unix/macOS 上透過 SSH 下載 .NET Core 的偵錯工具位 <br><br>2. <br>用於下載遠端 Windows Docker 容器的偵錯工具位<br><br> 3. 用於 .NET framework 來源逐步執行 <br><br> 4. <br>（如果使用者選擇入）用來下載已發佈至 nuget.org 符號伺服器的符號。<br><br> 5. （如果使用者選擇輸入）用於下載 MS 符號和二進位檔，可能也需要用來在傾印中對受控碼進行偵錯工具 |
| Visual Studio Codespaces| \*. online.visualstudio.com | HTTPs/443 | 用來呼叫 Visual Studio Codespaces Api |
| Xamarin Android 應用程式發佈 | \*. googleapis.com <br/> play.google.com <br/>accounts.google.com | HTTPs/443 | 用來與 Google Play 商店服務互動，直接從 Visual Studio 發佈/上傳 Xamarin Android 應用程式。 |
| Azure Container Registry | *. azurecr.io | HTTPs/443 | 存取裝載于 Azure 上的容器登錄，以進行 CICD 管線的設定 |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>對網路相關錯誤進行疑難排解

有時候，在使用防火牆或 Proxy 伺服器的情況下安裝或使用 Visual Studio 時，您可能會遇到與網路或 Proxy 相關的錯誤。 如需這些錯誤訊息之解決方案的詳細資訊，請參閱[對安裝或使用 Visual Studio 時所發生的網路相關錯誤進行疑難排解](troubleshooting-network-related-errors-in-visual-studio.md)頁面。

## <a name="get-support"></a>取得支援

針對安裝相關的問題，我們提供[**安裝聊天**](https://visualstudio.microsoft.com/vs/support/#talktous)（僅限英文）支援選項。

以下是一些支援選項：

* 您可以透過 Visual Studio 安裝程式及 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio.md)工具回報產品的問題。
* 在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/) \(英文\) 中建議功能、追蹤產品問題和尋找解答。
* 您可以使用您的 [GitHub](https://github.com/) 帳戶與我們連絡，以及參加 [Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與其他 Visual Studio 開發人員對話。

## <a name="see-also"></a>另請參閱

* [Live Share 的連線需求](/visualstudio/liveshare/reference/connectivity/)
* [建立 Visual Studio 的網路安裝](create-a-network-installation-of-visual-studio.md)
* [針對 Visual Studio 中的網路相關錯誤進行疑難排解](troubleshooting-network-related-errors-in-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [安裝在防火牆或 Proxy 伺服器後方 (Visual Studio for Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

---
title: 'Visual Studio 檔：新功能的歷程記錄 '
titleSuffix: ''
description: Visual Studio 文件中的新功能歷程記錄
ms.date: 09/30/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 750fcb907350d3bd135bc86e5d1bc1ed211c4a7b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400137"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Visual Studio 文件中的新功能歷程記錄

歡迎使用 Visual Studio 檔的新功能歷程記錄。本主題包含在2020年9月 (開始 2020) 之前的檔主要變更。 如需最新的新功能，請參閱 [Visual Studio 檔：檔中的新功能](whats-new-visual-studio-docs.md)。

## <a name="august-2020"></a>2020 年 8 月
### <a name="azure"></a>Azure

**新文章**

- 使用 Visual Studio 的 VS 2019 16.7 已連線的服務連接服務來[新增 Azure 應用程式見解](../azure/azure-app-insights-add-connected-service.md)
- 使用適用于 VS 2019 16.7 的 Visual Studio 已連線的服務連接服務來[新增 Azure Cache for Redis](../azure/azure-cache-for-redis-add-connected-service.md)
- 使用適用于 VS 2019 16.7 的 Visual Studio 已連線的服務連接服務，[將 Azure Cosmos DB 新增至您的應用程式](../azure/azure-cosmosdb-add-connected-service.md)
- 使用適用于 VS 2019 16.7 的[Visual Studio 已連線的服務聯機服務新增 Azure SignalR](../azure/azure-signalr-add-connected-service.md)
- [將連接加入至](../azure/azure-sql-database-add-connected-service.md) VS 2019 16.7 Azure SQL Database 連接的服務

**更新的文章**

- [使用 Visual Studio 的已連接服務加入 Azure 儲存體](../azure/vs-azure-tools-connected-services-storage.md)
  - VS 2019 16.7 的已連接服務
  - Azure 儲存體聯機服務文章：支援更新 UI 和專案類型

### <a name="code-quality"></a>程式碼品質

**新文章**

- [CA1310：指定 StringComparison 的正確性](/dotnet/fundamentals/code-analysis/quality-rules/ca1310) -新增 CA1310 的檔和 CA1307 的更新檔
- [CA1837：使用 GetCurrentProcess，而不是 ( # A1。](/dotnet/fundamentals/code-analysis/quality-rules/ca1837) CA1837 的識別碼-檔
- [CA1838：避免 `StringBuilder` P/invoke 的參數](/dotnet/fundamentals/code-analysis/quality-rules/ca1838) -新增 CA1838 的檔
- [CA2008：不要在不傳遞 TaskScheduler 的情況下建立工作](/dotnet/fundamentals/code-analysis/quality-rules/ca2008) -新增 CA2008 的檔
- [CA2249：請考慮使用 string。 Contains 取代 IndexOf](/dotnet/fundamentals/code-analysis/quality-rules/ca2249) -CA2249 的檔
- [CA2361：確定包含資料集的自動產生類別 ReadXml ( # A1 未與不受信任的資料搭配使用](/dotnet/fundamentals/code-analysis/quality-rules/ca2361) -更多資料集/DataTable 規則
- [CA2362：自動產生的可序列化類型中不安全的資料集或 DataTable 可能易受遠端程式碼執行攻擊](/dotnet/fundamentals/code-analysis/quality-rules/ca2362) -更多資料集/DataTable 規則
- [IL3000：在發行為 IL3000 的單一檔案-新增檔時，避免使用存取元件檔案路徑](/dotnet/fundamentals/code-analysis/quality-rules/il3000)
- [IL3001：在發行為單一檔案時，避免存取元件檔案路徑](/dotnet/fundamentals/code-analysis/quality-rules/il3001) -IL3001 的新增檔

**已更新**

- [CA1002：不公開泛型清單](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) -新增預先配置-Api 介面區段
- [CA1046：不要在參考](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) 型別上多載運算子 equals-新增預先配置-Api 介面區段
- [CA1307：為了清楚起見，請指定 StringComparison](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) ，並新增 CA1307 的 CA1310 和更新檔檔
- [CA1700：不要將列舉值命名 &#39;保留&#39;](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) -新增預先配置-Api 介面區段
- [CA1707：識別碼不應包含](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) 底線-新增可配置的-Api 介面區段
- [CA1822：將成員標記為靜態](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) -新增預先配置-Api 介面區段
- [CA2351：確定資料集 ReadXml ( # A1's 輸入是受信任](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) -更多資料集/DataTable 規則
- [安裝協力廠商分析器](../code-quality/install-roslyn-analyzers.md) -變更程式碼分析檔的結構和標題

### <a name="containers"></a>容器

**更新的文章**

- 使用 Visual Studio 16.7 發佈 UI 的 Visual Studio 容器工具更新將[ASP.NET 容器部署到容器](../containers/hosting-web-apps-in-docker.md)登錄
- [開始使用 Visual Studio Kubernetes 工具](../containers/bridge-to-kubernetes.md) -Kubernetes 教學課程：新增移除步驟

### <a name="deployment"></a>部署

**新文章**

- [Visual Studio 安裝程式專案擴充功能和 .Net core 3.1](../deployment/installer-projects-net-core.md) -建立安裝程式專案的新說明頁面 .net Core 3.1 功能

**更新的文章**

- 將[您的應用程式部署到資料夾、IIS、Azure 或其他目的地](../deployment/deploying-applications-services-and-components-resources.md)部署更新
- [部署 Visual Studio](../deployment/index.yml) 部署更新

### <a name="extensibility"></a>擴充性

**更新的文章**
- [專案子類型](../extensibility/internals/project-subtypes.md) -修正清單專案縮排
- Visual Studio-AB # 1759333[的色彩值參考](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md)修正遺漏的資料行標題

### <a name="get-started"></a>開始使用

**更新的文章**

- [步驟5：將您的 ASP.NET Core 應用程式部署至 Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) -新已連線的服務 UI 的影片教學課程更新

### <a name="ide"></a>IDE

**新文章**

- [變更 Visual Studio 中的 f1 說明鍵](./not-in-toc/change-f1-help-key.md) -重構預設 f1 說明頁面
- [文字編輯器的 F1](./not-in-toc/default-f1-text-editor.md) 說明-重構預設 F1 說明頁面
- [轉換 `typeof` 為 `nameof` ](./reference/convert-typeof-to-nameof.md) -convert typeof 轉換成 nameof 重構
- [簡化 linq 運算式](./reference/simplify-linq-expression.md) -簡化 linq 運算式重構

**更新的文章**

- [在 Visual Studio 中自訂視窗版面](./customizing-window-layouts-in-visual-studio.md) 配置-新增 monikered 的垂直檔索引標籤資訊以自訂視窗版面配置主題
- [如何回報 Visual Studio 或 Visual Studio 安裝程式的問題](./how-to-report-a-problem-with-visual-studio.md)
  - 已將更多資訊新增至 NMI
  - Redid 整份回報問題頁面
- [F1](./not-in-toc/default.md) 說明-重構預設 F1 說明頁面
- [[自動回復]、[環境]、[選項] 對話方塊](./reference/autorecover-environment-options-dialog-box.md)-新增更新的自動儲存檔案位置資訊
- [選項、文字編輯器、基本 (Visual Basic) 、](./reference/options-text-editor-basic-visual-basic.md) 內嵌參數名稱提示的 Advanced-已新增基本檔
- 內嵌參數名稱提示的[選項、文字編輯器、c #、Advanced](./reference/options-text-editor-csharp-advanced.md) -已新增的基本檔
- [Visual Studio 效能秘訣和訣竅](./visual-studio-performance-tips-and-tricks.md) -新增「停用地圖模式」和「停用自動換行」資訊
- [Visual Studio 2019 中的新功能](./whats-new-visual-studio-2019.md) -使用 16.7 GA 資訊更新 Visual Studio 2019 中的新功能

### <a name="rtvs"></a>RTVS

**更新的文章**

- [使用 SQL Server 和 R](../rtvs/integrating-sql-server-with-r.md) 更正的資料表來包含資料行標頭

## <a name="july-2020"></a>2020 年 7 月
### <a name="code-quality"></a>程式碼品質

**新文章**

- [CA1417：不要 `OutAttribute` 在 P/invoke 的字串參數上使用](/dotnet/fundamentals/code-analysis/quality-rules/ca1417) -新增 CA1417 的檔
- [CA1805：不必要初始化。](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) -新增適用于 CA1805 的檔
- [CA1836：在可用時優先使用 IsEmpty 計數](/dotnet/fundamentals/code-analysis/quality-rules/ca1836) -新增 CA1836 的檔 (偏好 IsEmpty 超過計數) 
- [CA2016：將 CancellationToken 參數轉寄至採用一](/dotnet/fundamentals/code-analysis/quality-rules/ca2016) 份檔 CA2016 的方法-將 CancellationToken 參數轉寄至採用一個
- [CA2350：確定 DataTable. ReadXml ( # A1's 輸入是受信任](/dotnet/fundamentals/code-analysis/quality-rules/ca2350) 的-初始資料集/DataTable 還原序列化規則檔
- [CA2351：確定資料集 ReadXml ( # A1's 輸入是受信任](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) 的-初始資料集/DataTable 還原序列化規則檔
- [CA2352：可序列化類型中 Unsafe 的資料集或 DataTable 可能很容易遭受遠端程式碼執行攻擊](/dotnet/fundamentals/code-analysis/quality-rules/ca2352) -初始資料集/DataTable 還原序列化規則檔
- [CA2353： serializable 類型中不安全的資料集或 datatable](/dotnet/fundamentals/code-analysis/quality-rules/ca2353) -初始資料集/DataTable 還原序列化規則檔
- [CA2354：還原序列化的物件圖形中不安全的資料集或 DataTable 可能易受遠端程式碼執行攻擊](/dotnet/fundamentals/code-analysis/quality-rules/ca2354) -初始資料集/DataTable 還原序列化規則檔
- [CA2355：還原序列化的物件圖形中不安全的資料集或 datatable](/dotnet/fundamentals/code-analysis/quality-rules/ca2355) -初始資料集/DataTable 還原序列化規則檔
- [CA2356： web 還原序列化物件圖形中不安全的資料集或 datatable 類型](/dotnet/fundamentals/code-analysis/quality-rules/ca2356) -初始資料集/DataTable 還原序列化規則檔

### <a name="containers"></a>容器

**新文章**

- 使用 Kubernetes： yaml[設定以 Kubernetes-Local Process 設定本機進程](../containers/configure-bridge-to-kubernetes.md)
- [使用本機進程搭配 Kubernetes (預覽) ](../containers/bridge-to-kubernetes.md) -開發人員空間遷移
- [本機處理序與 Kubernetes 搭配使用的方式](../containers/overview-bridge-to-kubernetes.md)
  - Kubernetes 的本機進程：新增路由區段
  - 開發人員空間遷移

### <a name="cross-platform"></a>跨平台

**更新的文章**

- [變更 log (Visual Studio Tools for Unity，Windows) ](/gamedev/unity/change-log-visual-studio-tools-for-unity.md) 將 VSTU 變更記錄至4.7.1。0
- [變更 Log (Visual Studio Tools for Unity、Mac) ](/gamedev/unity/change-log-visual-studio-tools-for-unity-mac.md) 將 VSTUM 變更記錄至2.7.1。0

### <a name="get-started"></a>開始使用

**新文章**

- [教學課程：擴充簡單的 c # 主控台應用程式](../get-started/csharp/tutorial-console-part-2.md) -發行延伸人行道教學課程第一版

### <a name="ide"></a>IDE

**新文章**

- [開發人員社群指導方針](./developer-community-guidelines.md) -新增 DevCom 指導方針
- [未匯入類型和擴充方法的 IntelliSense 完成](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>安裝

**新文章**

- [使用基本離線配置更新 Visual Studio](../install/update-minimal-layout.md) -檔基本版面配置功能
- [Visual Studio enterprise 指南](../install/visual-studio-enterprise-guide.md) -企業指南

### <a name="javascript"></a>JavaScript

**新文章**

- [編譯 typescript 程式碼 ( # A0) ](../javascript/compile-typescript-code-npm.md) -TypeScript 編譯和組建
- [編譯 typescript 程式碼 (ASP.NET Core) ](../javascript/compile-typescript-code-nuget.md) -TypeScript 編譯和組建

### <a name="msbuild"></a>MSBuild

**新文章**

- [一般 msbuild 專案中繼資料](../msbuild/common-msbuild-item-metadata.md) -MSBuild：使用連結和程式庫新增選擇性中繼資料的資料表
- [Msbuild 中的方案篩選](../msbuild/solution-filters.md) -msbuild 方案篩選

### <a name="test"></a>測試

**新文章**

- [使用 Test explorer 來偵測及分析單元測試](../test/debug-unit-tests-with-test-explorer.md) -test explorer 效能工作

**更新的文章**

- [使用 *.runsettings* 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - 使用 .runsettings 檔案設定單元測試的更新
  - 變更了操作說明的選項，並新增了範例。
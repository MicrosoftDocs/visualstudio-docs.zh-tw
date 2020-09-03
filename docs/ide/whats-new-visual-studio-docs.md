---
title: 'Visual Studio 檔：2020年8月的新功能 '
titleSuffix: ''
description: 2020年8月 Visual Studio 檔中的新功能。
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 4364bd62ac19be958632b8cb2dbbe907013e8a70
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402240"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Visual Studio 檔：2020年8月的新功能

歡迎使用2020年8月 Visual Studio 檔中的新功能。 本文列出在這段期間內檔的一些主要變更。 如需前幾個月新功能的相關資訊，請參閱 [新功能歷程記錄](whats-new-visual-studio-docs-history.md) 主題。

## <a name="azure"></a>Azure

**新文章**

- 使用 Visual Studio 的 VS 2019 16.7 已連線的服務連接服務來[新增 Azure 應用程式見解](/visualstudio/azure/azure-app-insights-add-connected-service)
- 使用適用于 VS 2019 16.7 的 Visual Studio 已連線的服務連接服務來[新增 Azure Cache for Redis](/visualstudio/azure/azure-cache-for-redis-add-connected-service)
- 使用適用于 VS 2019 16.7 的 Visual Studio 已連線的服務連接服務，[將 Azure Cosmos DB 新增至您的應用程式](/visualstudio/azure/azure-cosmosdb-add-connected-service)
- 使用適用于 VS 2019 16.7 的[Visual Studio 已連線的服務聯機服務新增 Azure SignalR](/visualstudio/azure/azure-signalr-add-connected-service)
- [將連接加入至](/visualstudio/azure/azure-sql-database-add-connected-service) VS 2019 16.7 Azure SQL Database 連接的服務

**更新的文章**

- [使用 Visual Studio 的已連接服務加入 Azure 儲存體](/visualstudio/azure/vs-azure-tools-connected-services-storage)
  - VS 2019 16.7 的已連接服務
  - Azure 儲存體聯機服務文章：支援更新 UI 和專案類型

## <a name="code-quality"></a>程式碼品質

**新文章**

- [CA1310：指定 StringComparison 的正確性](/visualstudio/code-quality/ca1310) -新增 CA1310 的檔和 CA1307 的更新檔
- [CA1837：使用 GetCurrentProcess，而不是 ( # A1。](/visualstudio/code-quality/ca1837) CA1837 的識別碼-檔
- [CA1838：避免 `StringBuilder` P/invoke 的參數](/visualstudio/code-quality/ca1838) -新增 CA1838 的檔
- [CA2008：不要在不傳遞 TaskScheduler 的情況下建立工作](/visualstudio/code-quality/ca2008) -新增 CA2008 的檔
- [CA2249：請考慮使用 string。 Contains 取代 IndexOf](/visualstudio/code-quality/ca2249) -CA2249 的檔
- [CA2361：確定包含資料集的自動產生類別 ReadXml ( # A1 未與不受信任的資料搭配使用](/visualstudio/code-quality/ca2361) -更多資料集/DataTable 規則
- [CA2362：自動產生的可序列化類型中不安全的資料集或 DataTable 可能易受遠端程式碼執行攻擊](/visualstudio/code-quality/ca2362) -更多資料集/DataTable 規則
- [IL3000：在發行為 IL3000 的單一檔案-新增檔時，避免使用存取元件檔案路徑](/visualstudio/code-quality/il3000)
- [IL3001：在發行為單一檔案時，避免存取元件檔案路徑](/visualstudio/code-quality/il3001) -IL3001 的新增檔

**已更新**

- [CA1002：不公開泛型清單](/visualstudio/code-quality/ca1002) -新增預先配置-Api 介面區段
- [CA1046：不要在參考](/visualstudio/code-quality/ca1046) 型別上多載運算子 equals-新增預先配置-Api 介面區段
- [CA1307：為了清楚起見，請指定 StringComparison](/visualstudio/code-quality/ca1307) ，並新增 CA1307 的 CA1310 和更新檔檔
- [CA1700：不要將列舉值命名 &#39;保留&#39;](/visualstudio/code-quality/ca1700) -新增預先配置-Api 介面區段
- [CA1707：識別碼不應包含](/visualstudio/code-quality/ca1707) 底線-新增可配置的-Api 介面區段
- [CA1822：將成員標記為靜態](/visualstudio/code-quality/ca1822) -新增預先配置-Api 介面區段
- [CA2351：確定資料集 ReadXml ( # A1's 輸入是受信任](/visualstudio/code-quality/ca2351) -更多資料集/DataTable 規則
- [安裝協力廠商分析器](/visualstudio/code-quality/install-roslyn-analyzers) -變更程式碼分析檔的結構和標題

## <a name="containers"></a>容器

**更新的文章**

- 使用 Visual Studio 16.7 發佈 UI 的 Visual Studio 容器工具更新將[ASP.NET 容器部署到容器](/visualstudio/containers/hosting-web-apps-in-docker)登錄
- [開始使用 Visual Studio Kubernetes 工具](/visualstudio/containers/tutorial-kubernetes-tools) -Kubernetes 教學課程：新增移除步驟

## <a name="deployment"></a>部署

**新文章**

- [Visual Studio 安裝程式專案擴充功能和 .Net core 3.1](/visualstudio/deployment/installer-projects-net-core) -建立安裝程式專案的新說明頁面 .net Core 3.1 功能

**更新的文章**

- 將[您的應用程式部署到資料夾、IIS、Azure 或其他目的地](/visualstudio/deployment/deploying-applications-services-and-components-resources)部署更新
- [部署 Visual Studio](/visualstudio/deployment/index) 部署更新

## <a name="extensibility"></a>擴充性

**更新的文章**
- [專案子類型](/visualstudio/extensibility/internals/project-subtypes) -修正清單專案縮排
- Visual Studio-AB # 1759333[的色彩值參考](/visualstudio/extensibility/ux-guidelines/color-value-reference-for-visual-studio)修正遺漏的資料行標題

## <a name="get-started"></a>開始使用

**更新的文章**

- [步驟5：將您的 ASP.NET Core 應用程式部署至 Azure](/visualstudio/get-started/csharp/tutorial-aspnet-core-ef-step-05) -新已連線的服務 UI 的影片教學課程更新

## <a name="ide"></a>IDE

**新文章**

- [變更 Visual Studio 中的 f1 說明鍵](/visualstudio/ide/not-in-toc/change-f1-help-key) -重構預設 f1 說明頁面
- [文字編輯器的 F1](/visualstudio/ide/not-in-toc/default-f1-text-editor) 說明-重構預設 F1 說明頁面
- [轉換 `typeof` 為 `nameof` ](/visualstudio/ide/reference/convert-typeof-to-nameof) -convert typeof 轉換成 nameof 重構
- [簡化 linq 運算式](/visualstudio/ide/reference/simplify-linq-expression) -簡化 linq 運算式重構

**更新的文章**

- [在 Visual Studio 中自訂視窗版面](/visualstudio/ide/customizing-window-layouts-in-visual-studio) 配置-新增 monikered 的垂直檔索引標籤資訊以自訂視窗版面配置主題
- [如何回報 Visual Studio 或 Visual Studio 安裝程式的問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
  - 已將更多資訊新增至 NMI
  - Redid 整份回報問題頁面
- [F1](/visualstudio/ide/not-in-toc/default) 說明-重構預設 F1 說明頁面
- [[自動回復]、[環境]、[選項] 對話方塊](/visualstudio/ide/reference/autorecover-environment-options-dialog-box)-新增更新的自動儲存檔案位置資訊
- [選項、文字編輯器、基本 (Visual Basic) 、](/visualstudio/ide/reference/options-text-editor-basic-visual-basic) 內嵌參數名稱提示的 Advanced-已新增基本檔
- 內嵌參數名稱提示的[選項、文字編輯器、c #、Advanced](/visualstudio/ide/reference/options-text-editor-csharp-advanced) -已新增的基本檔
- [Visual Studio 效能秘訣和訣竅](/visualstudio/ide/visual-studio-performance-tips-and-tricks) -新增「停用地圖模式」和「停用自動換行」資訊
- [Visual Studio 2019 中的新功能](/visualstudio/ide/whats-new-visual-studio-2019) -使用 16.7 GA 資訊更新 Visual Studio 2019 中的新功能

## <a name="rtvs"></a>RTVS

**更新的文章**

- [使用 SQL Server 和 R](/visualstudio/rtvs/integrating-sql-server-with-r) 更正的資料表來包含資料行標頭

## <a name="community-contributors"></a>社群參與者

下列人員會在這段期間內參與 Visual Studio 檔。 感謝您！ 遵循《 [參與者指南》](https://docs.microsoft.com/contribute/)中的指導方針，瞭解如何參與 Visual Studio 檔。

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG) -Alex 黑色 (11) 
- [Youssef1313](https://github.com/Youssef1313) -Youssef Victor (8) 
- [hyoshioka0128](https://github.com/hyoshioka0128) -Hiroshi Yoshioka (3) 
- [AstroChoco](https://github.com/AstroChoco) -Qian Lu (巧克力)  (1) 
- [athyunnath](https://github.com/athyunnath) -athyunnath Eleti (1) 
- [caro-oviedo](https://github.com/caro-oviedo) -caro oviedo (1) 
- [Evangelink](https://github.com/Evangelink) -Amaury Levé (1) 
- [jethas-bennettjones](https://github.com/jethas-bennettjones) -Shafiq Jetha (1) 
- [nebuk89](https://github.com/nebuk89) -Ben De 聖 Paer-Gotch (1) 
- [pcartwright81](https://github.com/pcartwright81) (1) 
- [pkulikov](https://github.com/pkulikov) -Petr Kulikov (1) 
- [riQQ](https://github.com/riQQ) (1) 
- [tcmetzger](https://github.com/tcmetzger) -Timo Cornelius Metzger (1) 
- [weitzhandler](https://github.com/weitzhandler) -Shimmy (1) 
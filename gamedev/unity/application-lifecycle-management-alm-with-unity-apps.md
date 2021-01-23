---
title: 應用程式生命週期管理 (ALM) 與 Unity 應用程式 | Microsoft Docs
description: 瞭解應用程式生命週期管理 (ALM) 搭配 Unity 應用程式。 複習 Agile 工具、模型、程式碼、組建、測試及改善程式碼品質。
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 3697ac75eb608f6990cb7f8ca976e103f0df8454
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722980"
---
# <a name="devops-with-unity-apps"></a>使用 Unity 應用程式進行 DevOps

開發新型平台的應用程式比起只撰寫程式碼牽涉到更多活動。 這些稱為 DevOps (開發 + 營運) 的活動橫跨了應用程式的整個生命週期，包含規劃和追蹤進度、設計和實作程式碼、管理原始程式碼存放庫、執行組建、管理持續整合和部署、測試 (包含單元測試和 UI 測試)、在開發和生產環境中執行各種形式的診斷，以及透過遙測和分析即時監視應用程式效能和使用者行為。

Visual Studio 與 Azure DevOps Services 和 Team Foundation Server 共同提供各式各樣的 DevOps 功能。 其中許多功能適用於跨平台專案，包括使用 Unity 建立的遊戲和沈浸式圖形化應用程式，尤其是在使用 C# 作為指令碼語言時。 不過，由於 Unity 有其專屬的開發環境和執行階段引擎，因此有幾種 DevOps 功能對於在 Visual Studio 中建置的別種專案並不適用。

下表區別在使用 Unity 時，Visual Studio 中的 DevOps 功能適用與不適用的情形。 請參閱連結文件以取得這項功能的詳細資訊。

## <a name="agile-tools"></a>Agile 工具

參考連結︰[關於 Agile 工具和 Agile 專案管理](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true) (使用 Azure Boards 或 TFS，包括 Team Explorer Everywhere)

一般註解：所有的計劃和追蹤功能都與專案類型和程式碼撰寫語言無關。

|特徵|支援 Unity|其他註解|
|-------------|--------------------------|-------------------------|
|管理待處理項目和衝刺 (Sprint)|是||
|工作追蹤|是||
|小組聊天室共同作業|是||
|看板|是||
|報告和視覺化進度|是||

## <a name="modeling"></a>模型化

參考連結：**[分析架構並製作架構模型](/modeling/analyze-and-model-your-architecture.md)**

一般註解：雖然這些設計功能是獨立的編碼語言，或是使用 C# 之類的 .NET 語言，但它們是在具有物件階層和類別關聯性的傳統應用程式範例上運作。 在 Unity 內設計遊戲牽涉不同的範例 (即圖形物件、音效、著色器、指令碼等的關聯性)。 因此，Visual Studio 模型圖工具未特別與整個 Unity 專案相關。 它們可能用來管理 C# 指令碼內的關聯性，但那只是其中一項功能而已。

|特徵|支援 Unity|其他註解|
|-------------|--------------------------|-------------------------|
|順序圖表|否||
|相依性圖形|否||
|呼叫階層|否||
|類別設計工具|否||
|架構總管|否||
|UML 圖表 (使用案例、活動、類別、元件、序列和 DSL)|否||
|圖層圖表|否||
|圖層驗證|否||

## <a name="code"></a>程式碼

|特徵|支援 Unity|其他註解|
|-------------|--------------------------|-------------------------|
|[使用 Team Foundation 版本控制 (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true) 或 Azure Repos|是|就像任何其他專案一樣，Unity 專案就只是一組可放入版本控制系統的檔案，但此表格後面將會說明一些特殊考量。|
|[開始使用 Azure Repos 中的 Git](/azure/devops/repos/git/gitquickstart?view=vsts&preserve-view=true&tabs=visual-studio)|是|請參閱表格後面的注意事項。|
|[改善程式碼品質](/test/improve-code-quality.md)|是||
|[尋找程式碼變更和其他記錄](/ide/find-code-changes-and-other-history-with-codelens.md)|是||
|[使用 Code Map 偵錯您的應用程式](/modeling/use-code-maps-to-debug-your-applications.md)|是||

使用 Unity 的版本控制特殊考量：

1. Unity 會追蹤單一不透明程式庫 (預設為隱藏) 中遊戲資產的中繼資料。 若要保持檔案與中繼資料同步，則需要顯示中繼資料，並將它儲存在更容易管理的區塊中。 如需詳細資訊，請參閱[搭配 Unity 使用外部版本控制系統 (英文)](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity 文件)。

2. 並非 Unity 專案中的所有檔案和資料夾都適用於原始檔控制 (上面的連結中也會予以描述)。 應該加入 Assets 和 ProjectSettings 資料夾，但不應該加入 Library 和 Temp 資料夾。 如需其他不會進入原始檔控制的已產生檔案清單，請參閱 StackOverflow 上的討論[如何使用 Git 進行 Unity3D 原始檔控制？(英文)](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control)。 許多開發人員也已個別針對這個主題撰寫部落格。

3. Unity 專案中的二進位資產 (例如紋理或音訊檔) 可能會佔用大量儲存體。 各種原始檔控制系統 (如 Git) 會針對進行的每一項變更儲存唯一的檔案複本，即使變更只影響一小部分的檔案也是一樣。 這可能會讓 Git 儲存機制變得過大。 若要解決這個問題，Unity 開發人員通常會選擇只將最後一個資產加入其儲存機制，並使用不同的方法來保留其資產的工作歷程記錄 (例如 OneDrive、DropBox 或 git-annex)。 因為這類資產一般不需要進行版本控制以及原始程式碼變更，所以這種方式適用。 開發人員一般也會將專案編輯器的 [資產序列化模式] 設定為 [強制文字]，以文字格式 (非允許在原始檔控制中進行合併的二進位格式) 來儲存場景檔案。 如需詳細資訊，請參閱[編輯器設定 (英文)](https://docs.unity3d.com/Manual/class-EditorManager.html) (Unity 文件)。

## <a name="build"></a>Build

參考連結：**[Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)**

|特徵|支援 Unity|其他註解|
|-------------|--------------------------|-------------------------|
|內部部署 Team Foundation Server (TFS)|可能|Unity 專案是透過 Unity 環境而非透過 Visual Studio 組建系統所建置 (Visual Studio Tools for Unity 內的建置將會編譯指令碼，而不會產生可執行檔)。 可能會[從命令列建置 Unity 專案](https://docs.unity3d.com/Manual/CommandLineArguments.html) (Unity 文件)，因此，可能會在 TFS 伺服器上設定 MSBuild 處理序來執行適當的 Unity 命令，但前提是要將 Unity 安裝於該電腦上。<br /><br /> Unity 也提供 [Unity 雲端組建 (英文)](https://build.cloud.unity3d.com/landing/)，其會監視 Git 或 SVN 儲存機制，並執行定期建置。 目前不適用於 TFVC 或 Azure DevOps Services。|
|連結至 Azure DevOps Services 的內部部署組建伺服器|可能|假設條件與上面相同，可進一步指示透過 Azure DevOps Services 所觸發的組建使用內部部署 TFS 電腦。 相關指示，請參閱[建置和發行代理程式](/azure/devops/pipelines/agents/agents?view=vsts&preserve-view=true)。|
|Azure DevOps Services 裝載的控制器服務|否|目前不支援 Unity 組建。|
|具有預先定義和後置指令碼的組建定義|是|也可以針對建置前和建置後的指令碼，設定使用 Unity 命令列來執行組建的自訂組建定義。|
|包括閘道簽入的連續整合|是|TFVC 的閘道簽入，只適用於 Git 在提取要求模型上運作的時候，而不是簽入運作時。|

## <a name="test"></a>測試

|特徵|支援 Unity|其他註解|
|-------------|--------------------------|-------------------------|
|規劃測試、建立測試案例和組織測試套件|是||
|手動測試|是||
|測試管理員 (錄製和播放測試)|僅限 Windows 裝置及 Android 模擬器||
|程式碼涵蓋範圍|n/a|不適用，因為是在 Unity 內進行單元測試，而非 Visual Studio 內，請見下文。|
|[對程式碼進行單元測試](/test/unit-test-your-code.md)|在 Unity 內，而非 Visual Studio 內|Unity 提供自己的單元測試架構，作為 [unity 測試控管](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (Unity 資產存放區) 的一部分。 單元測試結果會在 Unity 內報告，但不會顯示在 Visual Studio 內。|
|[使用 UI 自動化來測試您的程式碼](/test/use-ui-automation-to-test-your-code.md)|否|自動程式化 UI 測試會依賴應用程式 UI 中的可讀取控制項；Unity 應用程式在本質上是圖形，因此，自動程式化 UI 測試工具無法讀取內容。|

## <a name="improve-code-quality"></a>改善程式碼品質

參考連結： **[改善程式碼品質](/test/improve-code-quality.md)**

|特徵|支援 Unity|其他註解|
|-------------|--------------------------|-------------------------|
|[分析受控碼品質](/code-quality/code-analysis-for-managed-code-overview.md)|是|可以在 Visual Studio 內分析 C# 指令碼。|
|[使用程式碼複製品偵測來尋找重複程式碼](https://msdn.microsoft.com/library/hh205279.aspx)|是|可以在 Visual Studio 內分析 C# 指令碼。|
|[測量受控程式碼的複雜度和維護性](/code-quality/code-metrics-values.md)|是|可以在 Visual Studio 內分析 C# 指令碼。|
|[效能工具](/profiling/performance-explorer.md)|否|使用 [Unity 分析工具 (英文)](https://docs.unity3d.com/Manual/Profiler.html) (Unity 網站)。|
|[分析 .NET Framework 記憶體問題](https://msdn.microsoft.com/library/dn342825.aspx)|否|Visual Studio 工具並不會為程式碼剖析而連結 Unity 所使用的 Mono 架構。 使用 [Unity 分析工具 (英文)](http://docs.unity3d.com/Manual/Profiler.html) (Unity 文件)。|

## <a name="release-management"></a>版本管理

參考連結︰[在 Azure Pipelines 和 TFS 中建置和發行](/azure/devops/pipelines/overview?view=vsts&preserve-view=true)

|特徵|支援 Unity|其他註解|
|-------------|--------------------------|-------------------------|
|管理發行處理序|是||
|部署至伺服器以便透過指令碼進行側面載入|是||
|上傳至應用程式存放區|部分|您可以針對某些應用程式存放區，使用擴充功能來自動化此程序。 請參閱 [Extensions for Azure DevOps Services](https://marketplace.visualstudio.com/VSTS) (適用於 Azure DevOps Services 的延伸模組)；例如 [extension for Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play) (適用於 Google Play 的延伸模組)。|

## <a name="monitor-with-hockeyapp"></a>使用 HockeyApp 監視

參考連結︰**[使用 HockeyApp 監視 (英文)](https://www.hockeyapp.net/features/)**

|特徵|支援 Unity|其他註解|
|-------------|--------------------------|-------------------------|
|當機分析、遙測和 Beta 發佈|是|HockeyApp 主要用於處理 Beta 發佈和取得當機報告。<br /><br /> 針對來自 C# 指令碼的遙測，可以使用任何分析架構，但前提是它在 Unity 所使用的 .NET 版本上執行。 不過，這只允許遊戲指令碼內的分析，並不會深入 Unity 引擎內部。 目前沒有任何適用的 Application Insights 的外掛程式，但外掛程式適用於其他分析解決方案，例如 [Unity Analytics (英文)](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) 和 [Google Analytics (英文)](https://github.com/googleanalytics/google-analytics-plugin-for-unity)。 當然，了解 Unity 專案本質的服務 (如 Unity Analytics) 所提供的分析比一般架構更有意義。|
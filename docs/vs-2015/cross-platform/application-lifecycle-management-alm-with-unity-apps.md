---
title: 應用程式生命週期管理 (ALM) 與 Unity 應用程式 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: b37f379fc60a260e7c16e87d7c1553429e73fbad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778587"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>應用程式生命週期管理 (ALM) (含 Unity 應用程式)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
開發新型平台的應用程式比起只撰寫程式碼牽涉到更多活動。 這些稱為 DevOps (開發 + 作業) 的活動橫跨整個應用程式生命週期，包含計劃和追蹤工作、設計和實作程式碼、管理原始程式碼儲存機制、執行建置、管理持續整合和部署、測試 (包含單元測試和 UI 測試)、在開發和生產環境中執行各種形式的診斷，以及透過遙測和分析即時監視應用程式效能和使用者行為。  
  
 Visual Studio 以及 Visual Studio Team Services 和 Team Foundation Server 會一同提供各種 DevOps 功能，也稱為「應用程式生命週期管理」或 ALM。 其中許多項目都適用於跨平台專案 (包括使用 Unity 所建立的遊戲和沈浸式圖形化應用程式)，特別是使用 C# 做為指令碼語言時。 不過，因為 Unity 有其專屬開發環境和執行階段引擎，所以許多 ALM 功能不適用，如同其在 Visual Studio 中所建置的其他類型專案中亦不適用。  
  
 下表說明使用 Unity 時 Visual Studio ALM 功能是否適用。 請參閱連結文件以取得這項功能的詳細資訊。  
  
## <a name="agile-tools"></a>Agile 工具  
 參考連結：**[工作](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** （使用 Visual Studio Team Services 或 TFS，包括 Team Explorer Everywhere）  
  
 一般註解：所有的計劃和追蹤功能都與專案類型和程式碼撰寫語言無關。  
  
|功能|支援 Unity|其他註解|  
|-------------|--------------------------|-------------------------|  
|管理待處理項目和衝刺 (Sprint)|是||  
|工作追蹤|是||  
|小組聊天室共同作業|是||  
|看板|是||  
|報告和視覺化進度|是||  
  
## <a name="modeling"></a>模型化  
 參考連結：**[分析架構並製作架構模型](../modeling/analyze-and-model-your-architecture.md)**  
  
 一般註解：雖然這些設計功能是獨立的編碼語言，或是使用 C# 之類的 .NET 語言，但它們是在具有物件階層和類別關聯性的傳統應用程式範例上運作。 在 Unity 內設計遊戲牽涉不同的範例 (即圖形物件、音效、著色器、指令碼等的關聯性)。 因此，Visual Studio 模型圖工具未特別與整個 Unity 專案相關。 它們可能用來管理 C# 指令碼內的關聯性，但那只是其中一項功能而已。  
  
|功能|支援 Unity|其他註解|  
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
  
|功能|支援 Unity|其他註解|  
|-------------|--------------------------|-------------------------|  
|[使用 Team Foundation 版本控制](http://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285)或 Visual Studio Team Services|是|就像任何其他專案一樣，Unity 專案就只是一組可放入版本控制系統的檔案，但此表格後面將會說明一些特殊考量。|  
|[開始使用 Team Services 中的 Git (英文)](http://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|是|請參閱表格後面的注意事項。|  
|[程式碼分析/改善程式碼品質 (參考、建議的變更等)](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|是||  
|[尋找程式碼變更和其他記錄](../ide/find-code-changes-and-other-history-with-codelens.md)|是||  
|[使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)|是||  
  
 使用 Unity 的版本控制特殊考量：  
  
1.  Unity 會追蹤單一不透明程式庫 (預設為隱藏) 中遊戲資產的中繼資料。 若要保持檔案與中繼資料同步，則需要顯示中繼資料，並將它儲存在更容易管理的區塊中。 如需詳細資訊，請參閱[搭配 Unity 使用外部版本控制系統 (英文)](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity 文件)。  
  
2.  並非 Unity 專案中的所有檔案和資料夾都適用於原始檔控制 (上面的連結中也會予以描述)。 應該加入 Assets 和 ProjectSettings 資料夾，但不應該加入 Library 和 Temp 資料夾。 如需其他不會進入原始檔控制的已產生檔案清單，請參閱 StackOverflow 上的討論[如何使用 Git 進行 Unity3D 原始檔控制？(英文)](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control)。 許多開發人員也已個別針對這個主題撰寫部落格。  
  
3.  Unity 專案中的二進位資產 (例如紋理或音訊檔) 可能會佔用大量儲存體。 各種原始檔控制系統 (如 Git) 會針對進行的每一項變更儲存唯一的檔案複本，即使變更只影響一小部分的檔案也是一樣。 這可能會讓 Git 儲存機制變得過大。 若要解決這個問題，Unity 開發人員通常會選擇只將最後一個資產加入其儲存機制，並使用不同的方法來保留其資產的工作歷程記錄 (例如 OneDrive、DropBox 或 git-annex)。 因為這類資產一般不需要進行版本控制以及原始程式碼變更，所以這種方式適用。 開發人員一般也會將專案編輯器的 [資產序列化模式] 設定為 [強制文字]，以文字格式 (非允許在原始檔控制中進行合併的二進位格式) 來儲存場景檔案。 如需詳細資訊，請參閱[編輯器設定 (英文)](http://docs.unity3d.com/Manual/class-EditorManager.html) (Unity 文件)。  
  
## <a name="build"></a>組建  
 參考連結︰**[建置](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|功能|支援 Unity|其他註解|  
|-------------|--------------------------|-------------------------|  
|內部部署 TFS 伺服器|可能|Unity 專案是透過 Unity 環境而非透過 Visual Studio 組建系統所建置 (Visual Studio Tools for Unity 內的建置將會編譯指令碼，而不會產生可執行檔)。 可能會[從命令列建置 Unity 專案](http://docs.unity3d.com/Manual/CommandLineArguments.html) (Unity 文件)，因此，可能會在 TFS 伺服器上設定 MSBuild 處理序來執行適當的 Unity 命令，但前提是要將 Unity 安裝於該電腦上。<br /><br /> Unity 也提供 [Unity 雲端組建 (英文)](https://build.cloud.unity3d.com/landing/)，其會監視 Git 或 SVN 儲存機制，並執行定期建置。 它目前並未使用 Team Foundation 版本控制或 Visual Studio Team Services。|  
|連結至 Visual Studio Team Services 的內部部署組建伺服器|可能|假設條件與上面相同，可進一步指示透過 Visual Studio Team Services 觸發的組建使用內部部署的 TFS 電腦。  如需相關指示，請參閱[組建伺服器](http://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c)。|  
|Visual Studio Team Services 的裝載控制器服務|否|目前不支援 Unity 組建。|  
|具有預先定義和後置指令碼的組建定義|是|也可以針對建置前和建置後的指令碼，設定使用 Unity 命令列來執行組建的自訂組建定義。|  
|包括閘道簽入的連續整合|是|TFVC 的閘道簽入，只適用於 Git 在提取要求模型上運作的時候，而不是簽入運作時。|  
  
## <a name="testing"></a>測試  
 參考連結：**[測試應用程式](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|功能|支援 Unity|其他註解|  
|-------------|--------------------------|-------------------------|  
|規劃測試、建立測試案例和組織測試套件|是||  
|手動測試|是||  
|測試管理員 (錄製和播放測試)|僅限 Windows 裝置及 Android 模擬器||  
|程式碼涵蓋範圍|N/A|不適用，因為是在 Unity 內進行單元測試，而非 Visual Studio 內，請見下文。|  
|[對程式碼進行單元測試](../test/unit-test-your-code.md)|在 Unity 內，而非 Visual Studio 內|Unity 提供專屬單元測試架構做為 [Unity 測試工具 (英文)](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity Asset Store) 的一部分。 單元測試結果會在 Unity 內報告，但不會顯示在 Visual Studio 內。|  
|[使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)|否|自動程式碼 UI 測試會依賴應用程式 UI 中的可讀取控制項；Unity 應用程式在本質上是圖形，因此，自動程式碼 UI 測試工具無法讀取內容。|  
  
## <a name="improve-code-quality"></a>改善程式碼品質  
 參考連結︰**[改善程式碼品質](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|功能|支援 Unity|其他註解|  
|-------------|--------------------------|-------------------------|  
|[分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|是|可以在 Visual Studio 內分析 C# 指令碼。|  
|[使用程式碼複製品偵測來尋找重複程式碼](http://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|是|可以在 Visual Studio 內分析 C# 指令碼。|  
|[測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|是|可以在 Visual Studio 內分析 C# 指令碼。|  
|[效能總管](../profiling/performance-explorer.md)|否|使用 [Unity 分析工具 (英文)](http://docs.unity3d.com/Manual/Profiler.html) (Unity 網站)。|  
|[分析 .NET Framework 記憶體問題](../misc/analyze-dotnet-framework-memory-issues.md)|否|Visual Studio 工具並不會為程式碼剖析而連結 Unity 所使用的 Mono 架構。 使用 [Unity 分析工具 (英文)](http://docs.unity3d.com/Manual/Profiler.html) (Unity 文件)。|  
  
## <a name="release-management"></a>版本管理  
 參考連結：**[使用 Release Management 進行自動部署 (英文)](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|功能|支援 Unity|其他註解|  
|-------------|--------------------------|-------------------------|  
|管理發行處理序|是||  
|部署至伺服器以便透過指令碼進行側面載入|是||  
|上傳至應用程式存放區|Partial|您可以針對某些應用程式存放區，使用擴充功能來自動化此程序。  請參閱[適用於 Visual Studio Team Services 的擴充功能 (英文)](https://marketplace.visualstudio.com/VSTS)；例如[適用於 Google Play 的擴充功能 (英文)](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play)。|  
  
## <a name="monitor-with-hockeyapp"></a>使用 HockeyApp 監視  
 參考連結︰ **[使用 HockeyApp 監視 (英文)](https://www.hockeyapp.net/features/)**  
  
|功能|支援 Unity|其他註解|  
|-------------|--------------------------|-------------------------|  
|當機分析、遙測和 Beta 發佈|是|HockeyApp 主要用於處理 Beta 發佈和取得當機報告。<br /><br /> 針對來自 C# 指令碼的遙測，可以使用任何分析架構，但前提是它在 Unity 所使用的 .NET 版本上執行。 不過，這只允許遊戲指令碼內的分析，並不會深入 Unity 引擎內部。 目前沒有任何適用的 Application Insights 的外掛程式，但外掛程式適用於其他分析解決方案，例如 [Unity Analytics (英文)](https://www.assetstore.unity3d.com/en/#!/content/28120) 和 [Google Analytics (英文)](https://github.com/googleanalytics/google-analytics-plugin-for-unity)。 當然，了解 Unity 專案本質的服務 (如 Unity Analytics) 所提供的分析比一般架構更有意義。|

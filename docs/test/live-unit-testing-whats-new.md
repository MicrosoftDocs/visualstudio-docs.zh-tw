---
title: Visual Studio 2017 中 Live Unit Testing 的新功能
description: 本文說明從 Visual Studio 2017 15.3 版開始，Visual Studio 每個版本中新增至 Live Unit Testing 的新功能。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 10/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
- Live Unit Testing What's New
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: ae1caef04c1ccd1c51c38ddef5dc8c783bdbfaa9
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328830"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Visual Studio 2017 中 Live Unit Testing 的新功能

本主題列出從 Visual Studio 2017 15.3 版開始，各版 Visual Studio 中新增至 Live Unit Testing 的新功能。 如需如何使用 Live Unit Testing 的概觀，請參閱 [Visual Studio 的 Live Unit Testing](live-unit-testing.md)。

## <a name="version-154"></a>15.4 版

從 Visual Studio 2017 15.4 版開始，Live Unit Testing 包含數個區域的改善和增強功能：

- **改善發現能力**. 對於不知道有 Live Unit Testing 功能的使用者，只要使用者開啟內含單元測試但未啟用 Live Unit Testing 的方案，Visual Studio IDE 就會顯示提及 Live Unit Testing 的金色列。 金色列中所呈現的資訊可讓使用者深入了解並啟用 Live Unit Testing。 不符合 Live Unit Testing 必要條件時，金色列也會顯示資訊。 它們包括：

  - 遺漏測試配接器。
  - 具有舊版測試配接器。
  - 需要還原方案所參考的 NuGet 套件。

- **與工作中心通知的整合**. Visual Studio IDE 現在會在工作中心內顯示 Live Unit Testing 背景處理通知，讓使用者可以輕鬆地分辨啟用 Live Unit Testing 時發生什麼狀況。 這可處理在大型方案上啟動 Live Unit Testing 的重要問題。 之前，在涵蓋範圍圖示出現之前有幾分鐘的時間，使用者無法判斷是否真地啟用 Live Unit Testing，以及是否運作。 小事一樁啦！

- **MSTest 架構第 1 版支援**：Live Unit Testing 已使用三個熱門單元測試架構：xUnit、NUnit 和 MSTest。 之前，只有在 MSTest 單元測試專案已使用 MS Test 第 2 版時，Live Unit Testing 才會運作。 從 Visual Studio 2017 15.4 版開始，它現在也支援 MSTest 第 1 版。

- **可靠性和效能**：Live Unit Testing 現在確保系統可以進一步偵測尚未完成完全載入專案的時間，並避免 Live Unit Testing 損毀。 組建效能改善也可在系統知道專案檔中沒有任何變更的情況下，避免對 MSBuild 專案進行重新評估。

- **其他使用者介面精簡**：按一下滑鼠右鍵手勢中令人混淆的 [Live Test Set – Include/Exclude] (即時測試集 - 包含/排除) 選項已重新命名為 [Live Unit Testing Include/Exclude] (Live Unit Testing 包含/排除)。 已移除 [測試] > [Live Unit Testing] 功能表上的 [Reset clean] \(全新重設\) 選項。 現在您可以選取 [**工具**  >  **選項**]  >  **Live Unit Testing** ，然後選取 [**刪除保存的資料**] 來存取它。

## <a name="version-153"></a>15.3 版本

從 Visual Studio 2017 15.3 版開始，Live Unit Testing 具備兩個主要區域的改善和增強功能：

- .NET Core 和 .NET Standard 支援。 您可以在以 C# 或 Visual Basic 所撰寫的 .NET Core 和 .NET Standard 方案上使用 Live Unit Testing。

- 效能改善。 在 Live Unit Testing 下完成首次完整建置和執行測試之後，您會發現效能已大幅加快。 後續於相同方案上啟動 Live Unit Testing 時，您也會察覺到顯著的效能改善。 我們現在會持續保存 Live Unit Testing 所產生的資料，並使用最新檢查盡可能重複使用它。

除了這些主要新增功能之外，Live Unit Testing 也包含下列增強功能：

- 新的小燒杯圖示現在用來區別測試方法與一般方法。 空的小燒杯圖示指出 Live Unit Testing 未包含特定測試。

- 從 Live Unit Testing 涵蓋範圍圖示的快顯 UI 視窗中按一下測試方法時，您現在可以選擇立即從 UI 視窗的該內容中針對測試進行偵錯，而不需要離開程式碼編輯器。 當您查看失敗的測試時，這會特別實用。

- 已將數個額外的可設定選項新增至 [工具]/[選項]/[Live Unit Testing]/[一般]。 您可以限制用於 Live Unit Testing 的記憶體。 您也可以針對開啟的方案，以指定保存 Live Unit Testing 資料的檔案路徑。

- 已將數個額外的功能表項目新增至 [測試]/[Live Unit Testing] 的功能表列底下。 [重設清除] 會刪除保存資料並再次產生它。 [選項] 會跳至 [工具]/[選項]/[Live Unit Testing]/[一般]。

- 您現在可以使用下列屬性，以在原始程式碼中指定要從 Live Unit Testing 排除已設定目標的測試方法：

  - 針對 xUnit：`[Trait("Category", "SkipWhenLiveUnitTesting")]`
  - 針對 NUnit：`[Category("SkipWhenLiveUnitTesting")]`
  - 針對 MSTest：`[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>另請參閱

- [Live Unit Testing 簡介](live-unit-testing-intro.md)
- [Visual Studio 的 Live Unit Testing](live-unit-testing.md)

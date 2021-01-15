---
title: 測試工具
description: 瞭解 Visual Studio 測試控管如何協助您和您的小組開發及維持高標準的程式碼品質。
ms.custom: SEO-VS-2020
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: cc5a1a7b72dcbdba8b874958bbef47ac4b98e936
ms.sourcegitcommit: 993fca11dc373a10150751bc2a045a9701a9db2f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98240318"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>先查看 Visual Studio 中的測試控管

Visual Studio 測試工具可協助您和小組開發及維持絕佳的高標準程式碼表現。

> [!NOTE]
> 所有版本的 Visual Studio 都提供單元測試。 其他測試控管（例如 Live Unit Testing 和 IntelliTest）僅適用于 Visual Studio Enterprise 版。 如需版本的詳細資訊，請參閱[比較 Visual Studio IDE](https://visualstudio.microsoft.com/vs/compare/)。

## <a name="test-explorer"></a>測試總管

[測試總管] 視窗可協助開發人員建立、管理及執行單元測試。 您可以使用 Microsoft 單元測試架構，或使用多種協力廠商架構和開放原始碼架構的其中一種。

::: moniker range="vs-2017"
![Visual Studio 測試總管](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Visual Studio 測試總管 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [開始使用單元測試](unit-test-your-code.md)
* [使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)
* [測試清單編輯器常見問題集](test-explorer-faq.md)
* [安裝協力廠商單元測試架構](install-third-party-unit-test-frameworks.md)

Visual Studio 亦為可延伸，並且會開啟 NUnit 和 xUnit.net 這類協力廠商單元測試配接器的機門。 此外，程式碼複製功能透過協助您識別語意類似的程式碼區塊而成為交付高品質軟體的必要項目，而這些區塊可能適用於一般 Bug 修正或重構。

![協力廠商測試整合](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) 會自動在背景執行單元測試，並在 Visual Studio 程式碼編輯器中以圖形方式顯示程式碼涵蓋範圍和測試結果。

> [!NOTE]
> Live unit 測試僅適用于 Enterprise edition，且僅支援 .NET 程式碼。

## <a name="intellitest"></a>IntelliTest

IntelliTest 會自動產生受控碼的單元測試和測試資料。 IntelliTest 能改善涵蓋範圍，並可大幅節省為新的或現有程式碼建立與維護單元測試的精力。

![IntelliTest 作用中](media/devtest-intellitest.png)

> [!NOTE]
> IntelliTest 僅適用于 Enterprise edition。 以 .NET Framework 為目標的 c # 程式碼支援。 目前不支援 .NET Core 和 .NET Standard。

* [使用 IntelliTest 為程式碼產生單元測試](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest –一個測試以將它們全部加以規則](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [IntelliTest 參考手冊](intellitest-manual/index.md)

## <a name="code-coverage"></a>程式碼涵蓋範圍

[程式碼涵蓋範圍](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)會判斷單元測試這類自動程式化測試所實際測試的專案程式碼比例。 為有效防範 Bug，您的測試應使用或「涵蓋」大部分程式碼。

> [!NOTE]
> 只有在 Enterprise edition 中才可以使用程式碼涵蓋範圍。

程式碼涵蓋範圍分析適用於受控碼和未受控碼 (機器碼)。

當您使用 [測試總管] 執行測試方法程式時，可以選擇程式碼涵蓋範圍。 結果表會顯示程式碼在每個組件、類別和方法中執行的百分比。 此外，原始檔編輯器會顯示已測試的程式碼。

* [使用程式碼涵蓋範圍來決定所測試的程式碼數量](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [使用 Visual Studio (Lab) 的單元測試、程式碼涵蓋範圍和程式碼複製分析 ](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)
* [自訂程式碼涵蓋範圍分析](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) 會以虛設常式或填充碼取代應用程式的其他部分，協助您隔離要測試的程式碼。

> [!NOTE]
> Microsoft Fakes 僅適用于 Enterprise edition，且僅支援 .NET 程式碼。

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>使用自動程式碼 UI 和 Selenium 執行使用者介面測試

自動程式碼 UI 測試提供一種方式，可建立完全自動化的測試來驗證您應用程式之使用者介面的功能和行為。 它們可以跨各種技術 (包括以 XAML 為基礎的 UWP 應用程式、瀏覽器應用程式和 SharePoint 應用程式) 將 UI 測試自動化。

> [!NOTE]
> 自動程式碼 UI 是已淘汰的功能。

不論您選擇最佳品種自動程式化 UI 測試還是 Selenium 的一般瀏覽器 UI 測試，Visual Studio 都會提供您需要的所有工具。

![使用自動程式化 UI 執行 UI 測試](media/devtest-codeduitest.png)

* [使用 UI 自動化來測試您的程式碼](use-ui-automation-to-test-your-code.md)
* [開始建立、編輯和維護自動程式碼 UI 測試](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [使用自動程式碼 UI 測試來測試 UWP 應用程式](test-uwp-app-with-coded-ui-test.md)
* [使用 Visual Studio Enterprise (Lab) 的自動程式碼 UI 測試簡介 ](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)

## <a name="related-scenarios"></a>相關案例

* [探勘和手動測試 (Azure Test Plans)](/azure/devops/test/index?view=vsts&preserve-view=true)
* [負載測試 (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)
* [連續測試 (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)
* [程式碼分析工具](../code-quality/code-analysis-for-managed-code-overview.md)

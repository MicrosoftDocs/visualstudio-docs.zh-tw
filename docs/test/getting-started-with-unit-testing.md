---
title: Visual Studio 中的單元測試使用者入門
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 302dc958892fb79e93ed87d515c1a5b1ac3c5aab
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32425211"
---
# <a name="get-started-with-unit-testing"></a>開始使用單元測試

使用 Visual Studio 來定義和執行單元測試，藉以維護程式碼的健康狀態、確定程式碼涵蓋範圍，以及在客戶遭遇問題之前找出錯誤和失敗。

## <a name="create-unit-tests"></a>建立單元測試

建立單元測試並經常執行它們，以確定您的程式碼運作正常。

1. 建立單元測試專案。

   ![將單元測試專案加入方案](media/createunittest1.png)

1. 命名專案。

   ![單元測試專案範本](media/createunittest2.png)

   專案已加入您的方案中。

   ![[方案總管] 中的單元測試專案](media/createunittest5.png)

1. 在單元測試專案中，加入對要測試之專案的參考。

   ![將參考加入您的單元測試專案](media/createunittest6.png)

1. 選取包含將測試之程式碼的專案。

   ![選取要加入的參考](media/createunittest7.png)

1. 撰寫單元測試的程式碼。

   ![將程式碼新增至您的單元測試](media/createunittest8.png)

您也可以使用**建立單元測試**[命令](create-unit-tests-menu.md)來建立單元測試方法虛設常式。

![使用建立單元測試命令](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>執行單元測試

1. 開啟 [測試總管]。

   ![在 [測試] 功能表上，開啟 [測試總管]](media/rununittest1.png)

1. 執行單元測試。

   ![在測試總管中執行單元測試](media/rununittest2.png)

   您可以在 [測試總管] 中查看通過或失敗的單元測試。

   ![在 [測試總管] 中檢閱單元測試結果](media/rununittest3.png)

## <a name="view-live-unit-test-results"></a>檢視即時單元測試結果

如果您在 Visual Studio 2017 或更新版本中使用 MSTest、xUnit 或 NUnit 測試架構，則可以查看單元測試的即時結果。

> [!NOTE]
> 只有 Visual Studio 2017 Enterprise Edition 才能使用即時單元測試。

1. 從 [測試] 功能表開啟即時單元測試。

   ![開啟即時單元測試](media/live-test-results-start.png)

1. 當您撰寫和編輯程式碼時，在程式碼編輯器視窗中檢視測試的結果。

   ![檢閱測試的結果](media/live-test-results-ui.png)

1. 選擇測試結果指標，以查看更多資訊。

   ![選擇測試結果指標](media/live-test-results-details.png)

如需其他詳細資料，請參閱 [Live Unit Testing](../test/live-unit-testing-intro.md)。

## <a name="generate-unit-tests-with-intellitest"></a>使用 IntelliTest 產生單元測試

當您執行 IntelliTest 時，您很容易就能看到哪些測試失敗，進而加入必要的程式碼來修正測試。 您可以選取產生的測試，將其儲存到測試專案中做為迴歸套件。 當您變更程式碼時，請重新執行 IntelliTest，如此所產生的測試才能與您的程式碼變更保持同步。 若要了解做法，請參閱[使用 IntelliTest 為程式碼產生單元測試](../test/generate-unit-tests-for-your-code-with-intellitest.md)。

![使用 IntelliTest 產生單元測試](media/intellitest.png)

## <a name="run-unit-tests-with-test-explorer"></a>使用測試總管執行單元測試

您可使用測試總管，透過 Visual Studio 或協力廠商單元測試專案來執行單元測試、將測試依分類分組、篩選測試清單，以及建立、儲存和執行測試播放清單。 您也可以偵錯測試和分析測試效能和程式碼涵蓋範圍。 若要了解做法，請參閱[使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)。

![使用 [測試總管] 執行單元測試](media/testexplorer.png)

## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>使用程式碼涵蓋範圍來決定所測試的程式碼數量

若要判斷單元測試等自動程式碼測試實際測試的專案程式碼比例，您可以使用 Visual Studio 程式碼涵蓋範圍功能。 為有效防範 Bug，您的測試應該要使用或「覆蓋」大部分的程式碼。 若要了解做法，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

![使用程式碼涵蓋範圍來決定所測試的程式碼數量](media/codecoverage.png)

## <a name="use-a-different-unit-test-framework"></a>使用不同的單元測試架構

您可以使用協力廠商測試架構 (例如 Boost、Google 及 nUnit)，在 Visual Studio 中執行單元測試。 請使用該架構的外掛程式，讓 Visual Studio 的測試執行者可以使用該架構。

以下是啟用協力廠商測試架構的步驟：

1. 選擇工具列上的 [工具] > [延伸模組和更新...]。

1. 在 [延伸模組和更新] 對話方塊中，展開 [線上] 分類，然後選擇 [Visual Studio Marketplace]。 然後，選擇 [工具] > [測試]。

   ![Visual Studio Marketplace](media/extensions-and-updates-testing.png)

1. 選取您想要安裝架構或配接器，然後選擇 [下載]。

1. 建立類別庫專案，並將它新增至您的方案。

   ![為類別庫專案命名，並將其新增](media/create3rdpartyunittest3.png)

1. 安裝外掛程式。 在 [方案總管] 中選取類別庫專案，然後從其右鍵功能表或快顯功能表中選擇 [管理 NuGet 套件...]。

   ![管理 NuGet 套件來安裝外掛程式](media/create3rdpartyunittest3a.png)

   [NuGet](https://www.nuget.org/) 是 Visual Studio 的延伸模組，您可以用來新增和更新專案的程式庫和工具。

1. 在 [NuGet 套件管理員] 視窗中，搜尋並選取外掛程式，然後選擇 [安裝]。

   ![安裝協力廠商架構](media/create3rdpartyunittest4.png)

   專案中已參考該架構。

   ![協力廠商單元測試架構的參考已新增至方案](media/create3rdpartyunittest6.png)

1. 從類別庫專案中的 [參考] 節點中，選取 [新增參考...]。

   ![將參考新增至專案](media/createunittest6.png)

1. 在 [參考管理員] 對話方塊方塊中，選取包含您要測試之程式碼的專案。

   ![選取您要測試的程式碼專案](media/createunittest7.png)

1. 撰寫單元測試的程式碼。

   ![將程式碼新增至您的單元測試](media/create3rdpartyunittest7.png)

## <a name="see-also"></a>另請參閱

* [建立單元測試命令](create-unit-tests-menu.md)
* [使用 IntelliTest 產生測試](generate-unit-tests-for-your-code-with-intellitest.md)
* [使用測試總管執行測試](run-unit-tests-with-test-explorer.md)
* [判斷程式碼涵蓋範圍](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [改善程式碼品質](improve-code-quality.md)
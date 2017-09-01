---
title: "開發人員測試工具、案例和功能 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit testing, create unit tests
ms.assetid: 9DE41406-8D39-427E-99D9-987E99103B73
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: c559290c8e88c8b4e37feabc7014188fad15434d
ms.openlocfilehash: b36882588281fc95ff4814c148cd428d09196fa1
ms.contentlocale: zh-tw
ms.lasthandoff: 06/08/2017

---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>開發人員測試工具、案例和功能

維護單元測試的程式碼健康狀態。 Visual Studio 提供各種功能強大的工具和技術，供開發人員在測試應用程式時使用：

**案例和功能：**

* [使用 IntelliTest 避免迴歸並達到程式碼涵蓋範圍](#intellitest)
* [使用自動程式碼 UI 和 Selenium 執行使用者介面測試](#ui-testing)
* [Visual Studio Code 涵蓋範圍的有效單元測試](#unit-testing)
* [使用高效能測試總管執行任何架構的單元測試](#test-explorer)
* [開始使用單元測試](getting-started-with-unit-testing.md)

<a name="intellitest"></a>
## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>使用 IntelliTest 避免迴歸並達到程式碼涵蓋範圍

在傳統的單元測試套件中，每個測試案例都代表示範性使用案例，而且判斷提示會體現輸入與輸出之間的關聯性。  驗證一些這類案例可能就已足夠，但當正確但未經測試的輸入引發錯誤回應時，資深開發人員知道即使經過完整測試的程式碼還是潛伏著 Bug。

使用 IntelliTest 改善涵蓋範圍並避免迴歸。
IntelliTest 可大幅節省為新的或現有程式碼建立與維護單元測試的力氣。 

![IntelliTest 作用中](media/devtest-intellitest.png)

* [Introduction to IntelliTest with Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx) (Visual Studio 的 IntelliTest 簡介)
* [IntelliTest – One Test to rule them all](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx) (IntelliTest - 一項掌控全場的測試)
* [IntelliTest Videos](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio) (IntelliTest 影片)
* [開始使用 IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest 參考手冊](intellitest-manual/index.md)

<a name="ui-testing"></a>
## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>使用自動程式碼 UI 和 Selenium 執行使用者介面測試

使用最佳品種或社群核准的 UI 測試來測試使用者介面 (UI)。
自動程式碼 UI 測試提供一種方式，可建立完全自動化的測試來驗證您應用程式之使用者介面的功能和行為。
它們可以跨各種技術 (包括以 XAML 為基礎的 Windows 市集應用程式、瀏覽器應用程式和 SharePoint 應用程式) 將 UI 測試自動化。

不論您選擇最佳品種自動程式碼 UI 測試還是 Selenium 的一般瀏覽器 UI 測試，Visual Studio 都會提供您需要的所有工具。 

![使用自動程式碼 UI 執行 UI 測試](media/devtest-codeduitest.png)

* [使用 UI 自動化來測試您的程式碼](use-ui-automation-to-test-your-code.md)
* [開始建立、編輯和維護自動程式碼 UI 測試](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [使用自動程式碼 UI 測試來測試 Windows 市集應用程式](test-windows-store-8-1-apps-with-coded-ui-tests.md)
* [使用自動程式碼 UI 測試來測試 Windows Phone 應用程式](test-windows-phone-8-1-apps-with-coded-ui-tests.md)
* [使用自動程式碼 UI 測試來測試 SharePoint 應用程式](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Introduction to Coded UI Tests with Visual Studio Enterprise (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx) (Visual Studio Enterprise 的自動程式碼 UI 測試簡介 (實驗室))

<a name="unit-testing"></a>
## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Visual Studio Code 涵蓋範圍的有效單元測試

若要判斷單元測試等自動程式碼測試實際測試的專案程式碼比例，您可以使用 Visual Studio 程式碼涵蓋範圍功能。 為有效防範 Bug，您的測試應該要使用或「覆蓋」大部分的程式碼。

程式碼涵蓋範圍分析適用於 Managed 程式碼 (CLI) 和 Unmanaged (機器碼)。

當您使用 [測試總管] 執行測試方法程式時，可以選擇程式碼涵蓋範圍。 結果表會顯示程式碼在每個組件、類別和方法中執行的百分比。 此外，原始檔編輯器會顯示已測試的程式碼。

![使用 Visual Studio Team Services 和 Team Foundation Server 測試](media/devtest-codecoverage.png)

* [使用程式碼涵蓋範圍來決定所測試的程式碼數量](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Unit Testing, Code Coverage and Code Clone Analysis with Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx) (Visual Studio 的單元測試、程式碼涵蓋範圍和重複程式碼分析 (實驗室))
* [自訂程式碼涵蓋範圍分析](customizing-code-coverage-analysis.md)

<a name="test-explorer"></a>
## <a name="unit-testing-with-any-framework-using-the-high-performance-test-explorer"></a>使用高效能測試總管執行任何架構的單元測試

測試總管可協助開發人員建立、管理和充分發揮單元測試的優點。

![Visual Studio 測試總管](media/devtest-testexplorer.png)

* [開始使用單元測試](unit-test-your-code.md)
* [使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)
* [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)
* [安裝協力廠商單元測試架構](install-third-party-unit-test-frameworks.md)

Visual Studio 亦為可延伸，並且會開啟 NUnit 和 xUnit.net 這類協力廠商單元測試配接器的機門。 此外，程式碼複製功能透過協助您識別語意類似的程式碼區塊而成為交付高品質軟體的必要項目，而這些區塊可能適用於一般 Bug 修正或重構。

![協力廠商測試整合](media/devtest-thirdparty.png)

## <a name="also-see"></a>另請參閱

* [開始使用單元測試](getting-started-with-unit-testing.md)
* [Speeding up Unit Test Execution in Team Foundation Server](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/30/speeding-up-test-execution-in-tfs.aspx) (加速 Team Foundation Server 中的單元測試執行)
* [Parallel and Context Sensitive Unit Test Execution](https://blogs.msdn.microsoft.com/visualstudioalm/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/) (平行和內容區分的單元測試執行)
* [Unit Testing, Code Coverage and Code Clone Analysis with Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx) (Visual Studio 的單元測試、程式碼涵蓋範圍和重複程式碼分析 (實驗室))


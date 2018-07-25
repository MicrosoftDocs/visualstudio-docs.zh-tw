---
title: Visual Studio 中的單元測試
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 487c5b4c730a4b49188857c2681aae6ff87a61e5
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237327"
---
# <a name="unit-test-your-code"></a>對程式碼進行單元測試

單元測試提供開發人員及測試人員一個快速的方法，可在 C#、Visual Basic 和 C++ 專案中查看類別之方法中的邏輯錯誤。

單元測試工具包括：

* **測試總管**&mdash;您可以執行單元測試，並在 [測試總管] 中查看其結果。 您可以使用任何具有 [測試總管] 配接器的單元測試架構，包括協力廠商架構。

* **適用於受控碼的 Microsoft 單元測試架構**&mdash;適用於受控碼的 Microsoft 單元測試架構是與 Visual Studio 一起安裝的，可提供用於測試 .NET 程式碼的架構。

* **適用於 C++ 的 Microsoft 單元測試架構**&mdash;適用於 C++ 的 Microsoft 單元測試架構是作為**使用 C++ 的桌面開發**工作負載的一部分安裝。 它提供用於測試機器碼的架構。 也包含 Google Test、Boost.Test 及 CTest 架構，且協力廠商配接器可用於其他測試架構。 如需詳細資訊，請參閱[撰寫 C/C++ 的單元測試](../test/writing-unit-tests-for-c-cpp.md)。

* **程式碼涵蓋範圍工具**&mdash;您可以使用測試總管中的一個命令來判斷單元測試所執行的產品程式碼數量。

* **Microsoft Fakes 隔離架構**&mdash;Microsoft Fakes 隔離架構可以為在受測程式碼中建立相依性的生產環境和系統程式碼建立替代的類別和方法。 藉由實作函式的偽造委派，您可以控制相依性物件的行為和輸出。

您也可以使用 [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) 來探索 .NET 程式碼，以產生測試資料和單元測試套件。 其會為程式碼中的每一個陳述式產生一個用以執行該陳述式的測試輸入。 程式碼的每個條件分支都會執行大小寫分析。

## <a name="key-tasks"></a>主要工作

下列主題可協助您了解及建立單元測試：

|工作|相關主題|
|-----------|-----------------------|
|**快速入門和逐步解說：** 使用下列主題從程式碼範例來了解 Visual Studio 中的單元測試。|-   [逐步解說：針對 Managed 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [快速入門：搭配測試總管進行以測試為導向的開發工作](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [將單元測試加入至現有的 C++ 應用程式](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)|
|**使用測試總管進行單元測試：** 了解測試總管如何協助建立更具生產力且更有效率的單元測試。|-   [單元測試基本概念](../test/unit-test-basics.md)<br />-   [建立單元測試專案](../test/create-a-unit-test-project.md)<br />-   [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)<br />-   [安裝協力廠商單元測試架構](../test/install-third-party-unit-test-frameworks.md)|
|**對 Managed 程式碼進行單元測試：**|-   [使用適用於 Managed 程式碼的 Microsoft 單元測試架構撰寫適用於 .NET Framework 的單元測試](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**對 C++ 程式碼進行單元測試**|-   [使用適用於 C++ 的 Microsoft 單元測試架構撰寫適用於 C/C++ 的單元測試](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**隔離單元測試**|-   [使用 Microsoft Fakes 在測試期間隔離程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**使用程式碼涵蓋範圍來識別測試專案程式碼的哪個部分：** 了解 Visual Studio 測試工具的程式碼涵蓋範圍功能。|-   [使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**使用負載測試來執行壓力與效能分析：** 您可以建立負載測試，並將單元測試新增至其中，以便找出應用程式中的效能與壓力問題。|-   [負載測試 (VSTS 和 TFS)](/vsts/load-test/)|
|**設立品質閘門：** 您可以建立品質閘門，確定程式碼在簽入之前都必須先經過測試，以確保程式碼的品質。|-   [簽入原則 (VSTS)](/vsts/tfvc/add-check-policies)|
|**設定測試選項：** 例如，您可以指定儲存測試結果的位置。|[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API 參考文件

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 描述 UnitTesting 命名空間，此命名空間可提供屬性、例外狀況、判斷提示和其他支援單元測試的類別。
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> 描述 UnitTesting.Web 命名空間，此命名空間可藉由提供對 ASP.NET 和 Web 服務單元測試的支援，延伸 UnitTesting 命名空間。

## <a name="see-also"></a>另請參閱

- [改善程式碼品質](../test/improve-code-quality.md)

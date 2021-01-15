---
title: '& 工作的單元測試工具'
description: 瞭解可用來讓開發人員和測試人員在程式碼中尋找邏輯錯誤的快速方式的單元測試工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: dc82d72d7c0a333fc28146746a473ed359857490
ms.sourcegitcommit: 993fca11dc373a10150751bc2a045a9701a9db2f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98240279"
---
# <a name="unit-test-tools-and-tasks"></a>單元測試工具和工作

單元測試提供開發人員及測試人員一個快速的方法，可在 C#、Visual Basic 和 C++ 專案中查看類別之方法中的邏輯錯誤。

單元測試工具包括：

* **測試瀏覽器** &mdash;執行單元測試，並在 **測試瀏覽器** 中查看其結果。 您可以使用任何具有 [測試總管] 配接器的單元測試架構，包括協力廠商架構。

* **適用于 managed 程式碼的 Microsoft 單元測試架構** &mdash;適用于 managed 程式碼的 Microsoft 單元測試架構會隨 Visual Studio 一起安裝，並提供用於測試 .NET 程式碼的架構。

* **適用于 c + + 的 Microsoft 單元測試架構** &mdash;適用于 c + + 的 Microsoft 單元測試架構是在 **使用 c + +** 工作負載進行桌面開發時安裝的一部分。 它提供用於測試機器碼的架構。 也包含 Google Test、Boost.Test 及 CTest 架構，且協力廠商配接器可用於其他測試架構。 如需詳細資訊，請參閱[撰寫 C/C++ 的單元測試](../test/writing-unit-tests-for-c-cpp.md)。

* 程式 **代碼涵蓋範圍工具** &mdash;您可以從 Test Explorer 中的一個命令來判斷單元測試所執行的產品程式碼數量。

* **Microsoft Fakes 隔離架構** &mdash;Microsoft Fakes 隔離架構可以針對生產和系統 .NET 程式碼建立替代類別和方法，以在受測程式碼中建立相依性。 藉由實作函式的偽造委派，您可以控制相依性物件的行為和輸出。

針對 .NET，您也可以使用 [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) 探索您的程式碼，並產生測試資料和單元測試套件。 其會為程式碼中的每一個陳述式產生一個用以執行該陳述式的測試輸入。 程式碼的每個條件分支都會執行大小寫分析。

## <a name="key-tasks"></a>主要工作

下列文章可協助您了解及建立單元測試：

|工作|相關主題|
|-|-----------------------|
|**快速入門和** 逐步解說：從程式碼範例瞭解 Visual Studio 中的單元測試。|- [逐步解說：針對 .NET 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [逐步解說：使用 Test Explorer 進行測試導向開發](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [如何：將單元測試新增至 c + + 應用程式](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**使用測試總管進行單元測試：** 了解測試總管如何協助建立更具生產力且更有效率的單元測試。|- [單元測試基本概念](../test/unit-test-basics.md)<br />- [建立單元測試專案](../test/create-a-unit-test-project.md)<br />- [使用 Test Explorer 執行單元測試](../test/run-unit-tests-with-test-explorer.md)<br />- [安裝協力廠商單元測試架構](../test/install-third-party-unit-test-frameworks.md)|
|**對 C++ 程式碼進行單元測試**|- [撰寫適用于 C/c + + 的單元測試](../test/writing-unit-tests-for-c-cpp.md)|
|**使用程式碼涵蓋範圍來識別測試專案程式碼的哪個部分：** 了解 Visual Studio 測試工具的程式碼涵蓋範圍功能。|- [使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**隔離單元測試**|- [使用 Microsoft Fakes 隔離測試中的 .NET 程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**使用負載測試來執行壓力與效能分析：** 瞭解如何建立負載測試，以協助找出應用程式中的效能與壓力問題 (已淘汰的) 。|- [快速入門：建立負載測試專案](../test/quickstart-create-a-load-test-project.md)<br />- [負載測試 (Azure Test Plans 和 TFS)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)|
|**設定品質閘道：** 瞭解如何建立品質閘道，以強制執行在簽入或合併程式碼之前執行的測試。|- [簽入原則 (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts&preserve-view=true)|
|**設定測試選項：** 瞭解如何設定測試選項，例如儲存測試結果的位置。|[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API 參考文件

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 描述 UnitTesting 命名空間，此命名空間可提供屬性、例外狀況、判斷提示和其他支援單元測試的類別。
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> 描述 UnitTesting.Web 命名空間，此命名空間可藉由提供對 ASP.NET 和 Web 服務單元測試的支援，延伸 UnitTesting 命名空間。

## <a name="see-also"></a>另請參閱

- [改善程式碼品質](../test/improve-code-quality.md)
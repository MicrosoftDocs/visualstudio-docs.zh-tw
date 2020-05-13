---
title: 單元測試
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
ms.openlocfilehash: ffe383d2195feb6689954a8ec858b196bae8c06a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565990"
---
# <a name="unit-test-your-code"></a>對程式碼進行單元測試

單元測試提供開發人員及測試人員一個快速的方法，可在 C#、Visual Basic 和 C++ 專案中查看類別之方法中的邏輯錯誤。

單元測試工具包括：

* **測試資源管理器**&mdash;運行單元測試，並在**測試資源管理器**中查看其結果。 您可以使用任何具有 [測試總管]**** 配接器的單元測試架構，包括協力廠商架構。

* **託管代碼**&mdash;的 Microsoft 單元測試框架 託管代碼的 Microsoft 單元測試框架與 Visual Studio 一起安裝，並提供用於測試 .NET 代碼的框架。

* **C++的 Microsoft 單元測試框架**&mdash;C++的 Microsoft 單元測試框架作為**桌面開發**C++工作負載的一部分安裝。 它提供用於測試機器碼的架構。 也包含 Google Test、Boost.Test 及 CTest 架構，且協力廠商配接器可用於其他測試架構。 如需詳細資訊，請參閱[撰寫 C/C++ 的單元測試](../test/writing-unit-tests-for-c-cpp.md)。

* **代碼覆蓋率工具**&mdash;您可以確定單元測試在測試資源管理器中的一個命令執行的產品代碼量。

* **微軟假軟體隔離框架**&mdash;微軟假軟體隔離框架可以為生產和系統代碼創建替代類和方法，在所測試的代碼中創建依賴項。 藉由實作函式的偽造委派，您可以控制相依性物件的行為和輸出。

您也可以使用 [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) 來探索 .NET 程式碼，以產生測試資料和單元測試套件。 其會為程式碼中的每一個陳述式產生一個用以執行該陳述式的測試輸入。 程式碼的每個條件分支都會執行大小寫分析。

## <a name="key-tasks"></a>主要工作

下列文章可協助您了解及建立單元測試：

|工作|相關主題|
|-|-----------------------|
|**快速入門和演練：** 從代碼示例瞭解視覺化工作室中的單元測試。|- [演練：為託管代碼創建和運行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [快速入門：使用測試資源管理器進行測試驅動開發](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [如何：將單元測試添加到C++應用](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**使用測試總管進行單元測試：** 了解測試總管如何協助建立更具生產力且更有效率的單元測試。|- [單元測試基本概念](../test/unit-test-basics.md)<br />- [創建單元測試專案](../test/create-a-unit-test-project.md)<br />- [使用測試資源管理器運行單元測試](../test/run-unit-tests-with-test-explorer.md)<br />- [安裝協力廠商單元測試架構](../test/install-third-party-unit-test-frameworks.md)|
|**對 C++ 程式碼進行單元測試**|- [編寫 C/C++單元測試](../test/writing-unit-tests-for-c-cpp.md)|
|**隔離單元測試**|- [使用微軟偽造產品隔離正在測試的代碼](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**使用程式碼涵蓋範圍來識別測試專案程式碼的哪個部分：** 了解 Visual Studio 測試工具的程式碼涵蓋範圍功能。|- [使用代碼覆蓋率確定要測試的代碼量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**使用負載測試執行應力和性能分析：** 瞭解如何創建負載測試以説明隔離應用程式中的性能和壓力問題。|- [快速入門：創建負載測試專案](../test/quickstart-create-a-load-test-project.md)<br />- [負載測試 (Azure Test Plans 和 TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**設置品質門：** 瞭解如何創建品質門以強制在簽入或合併代碼之前運行測試。|- [簽入原則 (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**設置測試選項：** 瞭解如何配置測試選項，例如，在存儲測試結果的位置。|[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API 參考文件

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 描述 UnitTesting 命名空間，此命名空間可提供屬性、例外狀況、判斷提示和其他支援單元測試的類別。
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> 描述 UnitTesting.Web 命名空間，此命名空間可藉由提供對 ASP.NET 和 Web 服務單元測試的支援，延伸 UnitTesting 命名空間。

## <a name="see-also"></a>另請參閱

- [改善程式碼品質](../test/improve-code-quality.md)

---
title: Visual Studio for Mac 測試控管
description: 使用 Visual Studio for Mac 建立和執行測試。
ms.date: 11/09/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: 3956c3158fd4ec1ad32b76882ac3f9d4cf1ea9bf
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493383"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Visual Studio for Mac 中的測試控管

Visual Studio for Mac 測試控管可協助您和您的小組開發及維持高標準的程式碼品質。 您可以使用 Microsoft 單元測試架構 (MSTest) 、xUnit 或 NUnit 來撰寫及執行單元測試。

## <a name="creating-tests"></a>建立測試
若要開始測試，您可以在方案中建立新的測試專案，方法是以滑鼠右鍵按一下您的方案，然後選擇 [ **加入 > 新專案** ] 功能表。 然後選擇對話方塊左側的其中一個測試分類 (例如， **Web 和主控台 > 測試** 分類) 。 選取您要建立的測試專案類型，然後按 [下一步]。 遵循出現的對話方塊中的指示，然後將新的測試專案新增至您的方案。

![已選取 [Web] 和 [主控台] > [測試] 區段的 [新增專案] 對話方塊，其中顯示 xUnit、MSTest 和 NUnit 專案](media/create-new-test-project.PNG)

> [!NOTE]
> 如需有關如何對 .NET Core 應用程式進行單元測試及選取單元測試架構的詳細資訊，請參閱 [.Net core 中的單元測試和 .NET Standard](/dotnet/core/testing/?pivots=xunit) 檔。

## <a name="running-tests"></a>執行測試
[ **單元測試** ] 視窗是用來執行單元測試，並使用 [ **View > 測試** ] 功能表來開啟。 系統會自動探索解決方案中的單元測試，並顯示在此視窗中，您可以在其中執行所有測試或一組您所選取的測試。

![顯示單元測試清單的 [測試] 視窗，以及用來執行或停止測試的工具列。](media/test-window.PNG)

編輯包含單元測試的 c # 類別時，您可以在測試類別或測試方法中按一下滑鼠右鍵，然後選擇 [ **執行測試 (s])** 或 [ **偵錯工具 ()** ] 功能表來執行測試。 選擇 [ **執行測試 (s])** 功能表項目會在 [測試] 視窗中執行測試，選擇 [ **Debug test] ()** ] 功能表會執行相同的動作，並附加偵錯工具，讓您可以對程式碼進行疑難排解。

![具有執行和 Debug 測試選項的編輯器右鍵功能表](media/run-tests-context-menu.PNG)

當測試執行時，會出現 **測試結果** 視窗，讓您可以檢查成功或失敗的測試，以及執行這些測試的輸出。

![顯示一個測試失敗的 [測試結果] 視窗，以及21個通過的測試和1個失敗的測試計數。](media/test-results-window.PNG)

## <a name="see-also"></a>請參閱

- [.NET Core 與 .NET Standard 中的單元測試](/dotnet/core/testing)
- [開始在 Windows 上使用單元測試 (Visual Studio) ](/visualstudio/test/getting-started-with-unit-testing)
- [Windows) 上的單元測試基本概念 (Visual Studio ](/visualstudio/test/unit-test-basics)
---
title: Visual Studio for Mac 測試控管
ms.date: 08/03/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: acf34677e8d9b477512763be3c43bb9df0c53c46
ms.sourcegitcommit: 935e1388281df0f04147802606b5cb7f513d45ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "88200975"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Visual Studio for Mac 中的測試控管

Visual Studio for Mac 測試控管可協助您和您的小組開發和維持高標準的程式碼卓越。 您可以使用 Microsoft 單元測試架構來撰寫和執行單元測試， (MSTest) 、xUnit 或 NUnit。

## <a name="creating-tests"></a>建立測試
若要開始進行測試，您可以在方案中建立新的測試專案，方法是以滑鼠右鍵按一下方案，然後選擇 [ **加入 > 新增專案 ...** ] 功能表。 然後選擇對話方塊左側的其中一個測試分類 (例如， **Web 和主控台 > 測試** ] 類別目錄) 。 選取您想要建立的測試專案類型，然後按 [下一步]。 依照出現的對話方塊中的指示進行，然後將新的測試專案新增至您的方案。

![已選取 Web 和主控台 > 測試區段的 [新增專案] 對話方塊，顯示 xUnit、MSTest 和 NUnit 專案](media/create-new-test-project.PNG)

> [!NOTE]
> 如需有關如何對 .NET Core 應用程式進行單元測試以及選取單元測試架構的詳細資訊，請參閱 [.Net core 中的單元測試和 .NET Standard](https://docs.microsoft.com/dotnet/core/testing/?pivots=xunit) 檔。

## <a name="running-tests"></a>執行測試
[ **單元測試** ] 視窗是用來執行單元測試，並使用 **View > Pad > 單元測試** ] 功能表開啟。 系統會自動探索您方案中的單元測試，並顯示在此視窗中，您可以在其中執行所有測試或已選取的一組測試。

![顯示單元測試清單的測試視窗，以及執行或停止測試的工具列。](media/test-window.PNG)

編輯包含單元測試的 c # 類別時，您可以在測試類別或測試方法中按一下滑鼠右鍵，然後選擇 [ **執行測試 (]) ** 或 [ **Debug test (s) ** ] 功能表來執行測試。 選擇 [ **執行測試 (]) ** 功能表項目將會在 [測試] 視窗中執行測試，選擇 [ **偵錯工具 () ** ] 功能表會執行相同的動作並附加偵錯工具，以便您可以針對程式碼進行疑難排解。

![具有 [執行和調試測試] 選項的編輯器右鍵功能表](media/run-tests-context-menu.PNG)

當測試正在執行時，會出現一個 **測試結果** 視窗，讓您可以檢查成功或失敗的測試，以及執行這些測試的輸出。

![顯示一個失敗測試的 [測試結果] 視窗以及21個通過測試和1個失敗測試的計數。](media/test-results-window.PNG)

## <a name="see-also"></a>請參閱

- [.NET Core 與 .NET Standard 中的單元測試](/dotnet/core/testing)
- [開始使用 Windows 上的單元測試 (Visual Studio) ](/visualstudio/test/getting-started-with-unit-testing)
- [Windows 上的單元測試基本概念 (Visual Studio) ](/visualstudio/test/unit-test-basics)

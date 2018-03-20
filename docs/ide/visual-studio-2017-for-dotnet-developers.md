---
title: "適用於 .NET 開發人員的 Visual Studio 2017 | Microsoft Docs"
description: "本文概述可協助您更快撰寫更好 .NET 程式碼的 Visual Studio 2017 功能。"
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: article
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: be14af66f5aa5389e9e701eb79dc68ee733c6068
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="visual-studio-2017-for-net-developers"></a>適用於 .NET 開發人員的 Visual Studio 2017

## <a name="smart-code-editor"></a>智慧型程式碼編輯器

- [文件：使用 IntelliSense](using-intellisense.md)
- [文件：智慧型編輯器功能](writing-code-in-the-code-and-text-editor.md)

Visual Studio 透過 .NET ("Roslyn") 編譯器來深入了解您的程式碼，提供您語法顏色標示、程式碼完成、拼字檢查輸入錯誤變數、未匯入的類型解析、大綱、結構視覺化檢視、[CodeLens](find-code-changes-and-other-history-with-codelens.md)，呼叫階層、可暫留的快速資訊、參數說明等智慧型編輯功能，以及用於重構、套用快速動作和產生程式碼的工具。

![Visual Studio 智慧型程式碼編輯器](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

## <a name="navigate-and-search-your-codebase"></a>巡覽並搜尋您的程式碼基底

[文件：巡覽程式碼](navigating-code.md)

透過「移至全部」快速鍵 (**Ctrl+T**) 跳至任何檔案、類型、成員或符號宣告，以快速巡覽您的 .NET 程式碼。 在您的程式碼中尋找符號或常值的所有參考，包括跨 .NET 語言的參考 (**Shift+F12**)。 使用我們的目標式瀏覽命令，協助您直接跳至符號定義 (**F12**) 或實作 (**Ctrl+F12**)。

![移至全部和尋找所有參考](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

## <a name="live-code-analysis-for-code-quality"></a>確保程式碼品質的即時程式碼分析

[文件：重構和快速動作](refactoring-code-generation-quick-actions.md)

Visual Studio 的即時程式碼診斷藉由偵測錯誤和可能有問題的程式碼，來協助您改善程式碼品質。 我們提供快速動作 (**Ctrl**+ ) 來解決在您文件、專案或解決方案中偵測到的問題。 即使您未在編輯器中開啟這些檔案，也可以啟用「完整解決方案分析」來尋找整個方案中的問題。

此外，您可以透過 **Ctrl**+**.** 使用程式碼建議來了解最佳做法、stub 或產生程式碼、重構程式碼，以及採用新的語言功能 。

![使用燈泡功能表套用快速修正和重構](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

## <a name="unit-testing"></a>單元測試

[文件：Visual Studio 中的單元測試](../test/improve-code-quality.md)

針對以 .NET Framework、.NET Standard 或 .NET Core 為目標的任何應用程式，執行以 MSTest、NUnit 或 XUnit 測試架構為基礎的單元測試並進行偵錯。 探索並檢閱您在「測試總管」中的測試，或使用 *Live Unit Testing* (僅限企業版 SKU) 在編輯器中立即看到程式碼變更如何影響您的單元測試。

![Visual Studio 中的 Live Unit Testing](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

## <a name="code-consistency-and-style"></a>程式碼一致性和樣式

- [文件：可攜式自訂編輯器選項](create-portable-custom-editor-options.md)
- [文件：EditorConfig 的 .NET 程式碼樣式設定](editorconfig-code-style-settings-reference.md)

Visual Studio 讓您能夠設定程式碼慣例、偵測違反程式碼樣式的情形，並透過 **Ctrl**+**.** 提供快速修正來補救樣式問題 。 使用 *EditorConfig*，在存放庫中設定和強制執行您小組的格式化、命名和程式碼樣式慣例，並允許覆寫專案和檔案層級的值。

![使用 EditorConfig 設定和強制執行程式碼慣例](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

## <a name="debugging"></a>偵錯

[文件：Visual Studio 偵錯](../debugger/index.md)

Visual Studio 包含最佳的偵錯工具，可讓您偵錯以 .NET Framework、.NET Standard 和 .NET Core 為目標的 .NET 應用程式。 切換並設定條件中斷點 (**F9**)、逐步執行方法呼叫、評估 LINQ 和 Lambda 運算式、設定監看變數、重新附加至處理序、檢查您的呼叫堆疊，甚至是使用 [編輯後繼續] 一面進行偵錯一面進行即時程式碼編輯。

如果您的服務是在 Azure 中執行，使用「快照集偵錯」可即時診斷部署在 Visual Studio 2017 Enterprise 中之雲端應用程式的問題。

![Visual Studio 偵錯](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

## <a name="version-control"></a>版本控制

[文件：Visual Studio 中的版本控制](/vsts/index)

使用 Git 或 TFVC 儲存及更新您在 Visual Studio 中的程式碼。 在編輯器中，使用 Team Explorer 來組織本機變更，並使用狀態列來追蹤暫止的認可和變更。 透過 [Visual Studio 的持續傳遞工具](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio)延伸模組，在 Visual Studio 中設定持續整合和傳遞，以採用敏捷式開發人員工作流程。

![Visual Studio 中的原始檔控制](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

## <a name="extensibility"></a>擴充性

[文件：擴充 Visual Studio](../extensibility/index.md)

Visual Studio 具有豐富的延伸模組生態系統，可供您視需要加以安裝或建立。 從「延伸模組庫」或 *Visual Studio Marketplace* 安裝延伸模組、使用 *VS SDK* 建置您自己的編輯器外掛程式，或使用「.NET 編譯器平台 SDK」建立您自己的即時程式碼分析器或重構。 您可以下載 [Microsoft Code Analysis](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) 延伸模組，以尋找其他程式碼修正和建議。

![Visual Studio 延伸模組庫](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")

## <a name="popular-extensions--shortcuts"></a>熱門的延伸模組和快速鍵

如果您來自其他 IDE 或程式碼撰寫環境，您可能會發現安裝下列其中一個延伸模組會很有幫助：

- [Emacs 模擬](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation )
- [Visual Studio 的快速鍵 (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

以下是常用的 Visual Studio 快速鍵。 請注意，有些延伸模組會解除預設 Visual Studio 按鍵繫結關係，您必須還原按鍵繫結關係才能使用下列命令。 若要將按鍵繫結關係還原為 Visual Studio 的預設，請移至 [工具] > [匯入和匯出設定...] > [重設所有設定]。

| 快速鍵 (所有設定檔) | 命令 | 描述 |
|-|-|-|
| **Ctrl+T** | 移至全部 | 巡覽至任何檔案/類型/成員/符號宣告 |
| **F12** (以及 **Ctrl+按一下滑鼠左鍵**) | 移至定義 | 巡覽至定義符號的位置 |
| **Ctrl+F12** | 移至實作 | 從基底類型或成員巡覽至其各種實作 |
| **Shift+F12** | 尋找所有參考 | 查看所有符號或常值參考 |
| **Ctrl**+**.** (在 C# 設定檔中為 **Alt+Enter**) | 快速動作及重構 | 查看您游標位置或選取的程式碼有哪些程式碼修正、程式碼產生動作、重構或其他快速動作可供使用 |
| **Ctrl**+**E**、**V** | 重複行 | 複製游標所在行的程式碼 (適用於 **Visual Studio 2017 15.6 版**和更新版本) |
| **Ctrl+Q** | 快速啟動 | 搜尋所有 Visual Studio 設定 |
| **F5** | 開始偵錯 | 開始偵錯應用程式 |
| **Ctrl+F5** | 執行而不偵錯 | 在本機執行應用程式而不偵錯 |
| **Ctrl+K、D** (預設設定檔) 或 **Ctrl+E、D** (C# 設定檔) | 格式化文件 | 根據您的新行字元、間距和縮排設定，來清除您檔案中的格式違規 |
| **Ctrl+\\、E** (預設設定檔) 或 **Ctrl+W、E** (C# 設定檔) | 檢視錯誤清單 | 查看您文件、專案或方案中的所有錯誤 |
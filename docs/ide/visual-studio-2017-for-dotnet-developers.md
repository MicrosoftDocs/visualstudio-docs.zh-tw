---
title: 增加您的 .NET 開發生產力
description: 這份導覽、程式碼分析、單元測試及其他功能的概觀，可協助您以更快的速度，撰寫更優質的 .NET 程式碼。
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.date: 06/14/2018
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: ef9101a0dbad68dd75792f34526bac550a331286
ms.sourcegitcommit: a6734c4d76dae3d21b55b10f3bc618dfa6b62dea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42626707"
---
# <a name="visual-studio-2017-c-productivity-guide"></a>Visual Studio 2017 C# 生產力指南

了解 [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 如何讓開發人員比以往更具生產力。 運用我們的效能與生產力改進，像是導覽到反向組譯的組件、鍵入時的變數名稱建議、**測試總管**中的階層架構檢視、[移至全部] (**Ctrl**+**T**) 以導覽至檔案/類型/成員/符號宣告、智慧型**例外狀況協助程式**、程式碼樣式組態和強制執行，以及許多重構和程式碼修正。

## <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>我習慣從不同延伸模組/編輯器/IDE 中使用我的鍵盤快速鍵

**Visual Studio 2017 版本 15.8 的新功能**：若您原先使用其他 IDE 或編碼環境，可將鍵盤配置變更為 *Visual Studio Code* 或 *ReSharper (Visual Studio)*：

![Visual Studio 中的鍵盤配置](../ide/media/VS2017Guide-Keyboard.png)

有些延伸模組也提供鍵盤配置：

- [Visual Studio 的快速鍵 (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs 模擬](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

以下是常用的 Visual Studio 快速鍵：

| 快速鍵 (所有設定檔) | 命令 | 描述 |
|-|-|-|
| **Ctrl**+**T** | 移至全部 | 巡覽至任何檔案/類型/成員/符號宣告 |
| **F12** (以及 **Ctrl**+**按一下滑鼠左鍵**) | 移至定義 | 巡覽至定義符號的位置 |
| **Ctrl**+**F12** | 移至實作 | 從基底類型或成員巡覽至其各種實作 |
| **Shift**+**F12** | 尋找所有參考 | 查看所有符號或常值參考 |
| **Ctrl**+**.** (在 C# 設定檔中為 **Alt**+**Enter**) | 快速動作及重構 | 查看您游標位置或選取的程式碼有哪些程式碼修正、程式碼產生動作、重構或其他快速動作可供使用 |
| **Ctrl**+**D** | 重複行 | 複製游標所在行的程式碼 (適用於 **Visual Studio 2017 15.6 版**和更新版本) |
| **Shift**+**Alt**+**+**/**-** | 展開/折疊選取項目 | 展開或折疊編輯器中的前選取項目 (適用於 **Visual Studio 2017 15.5 版**和更新版本) |
| **Ctrl** + **Alt** + **.** | 插入下一個相符的插入點 | 在下一個符合目前選取項目的位置，新增選取項目及插入點 (在 **Visual Studio 2017 版本 15.8** 及最新版本中提供) |
| **Ctrl**+**Q** | 快速啟動 | 搜尋所有 Visual Studio 設定 |
| **F5** | 開始偵錯 | 開始偵錯應用程式 |
| **Ctrl**+**F5** | 執行而不偵錯 | 在本機執行應用程式而不偵錯 |
| **Ctrl**+**K**、**D** (預設設定檔) 或 **Ctrl**+**E**、**D** (C# 設定檔) | [將文件格式化](code-styles-and-quick-actions.md#format-document-command) | 根據您的新行字元、間距和縮排設定，來清除您檔案中的格式違規 |
| **Ctrl**+**\\**、**Ctrl**+**E** (預設設定檔) 或 **Ctrl**+**W**、**E** (C# 設定檔) | 檢視錯誤清單 | 查看您文件、專案或方案中的所有錯誤 |
| **Alt** + **PgUp/PgDn** | 前往上一個/下一個問題 | 跳到文件中的上一個/下一個錯誤、警告、建議 (在 **Visual Studio 2017 版本 15.8** 及最新版本中提供) |

> [!NOTE]
> 有些擴充功能會將預設的 Visual Studio 按鍵繫結關係解除繫結。 若要使用上述命令，請將按鍵繫結關係還原為 Visual Studio 的預設，方法是前往 [工具] > [匯入和匯出設定] > [重設所有設定] 或 [工具] > [選項] > [鍵盤] > [重設]。

您可在[我們的文件](..\ide\tips-and-tricks-for-visual-studio.md)中深入了解 Visual Studio 的鍵盤快速鍵與命令。

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>我需要快速瀏覽至檔案或型別的方法

Visual Studio 2017 有一項稱為 [移至全部] (**Ctrl**+**T**) 的功能。 [移至全部] 可讓您快速跳到任何檔案、型別、成員或符號宣告。

- 變更此搜尋列的位置，或使用**齒輪**圖示關閉「即時瀏覽預覽」。
- 使用我們的查詢語法 (例如，"t mytype") 來篩選結果。 您也可以將搜尋範圍僅限於目前的文件。
- 支援 camelCase 比對！

![Visual Studio 中的 [移至全部]](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>我的小組對我們的程式碼庫強制執行程式碼樣式規則

您可以使用 *.editorconfig* 檔案來撰寫編碼慣例，並讓它們隨著來源移動。

- 您可以安裝 [EditorConfig 語言服務延伸模組](https://aka.ms/editorconfig) \(英文\)，以便輕鬆地在 Visual Studio 中新增及編輯 *.editorconfig* 檔案。
- 嘗試 [適用於 Visual Studio 的 IntelliCode 延伸模組](/visualstudio/intellicode/intellicode-visual-studio)。 此實驗性延伸模組會從現有的程式碼推斷您的程式碼樣式，然後使用已定義的程式碼樣式喜好設定來建立非空白的 *.editorconfig* 檔案。
- 請參閱 [.NET 程式碼慣例選項](https://aka.ms/editorconfigDocs) 文件。
- 如需範例 *.editorconfig* 檔案，請參閱[此 gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) \(英文\)。

![Visual Studio 中的程式碼樣式強制執行](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>我需要更多的重構和程式碼修正

Visual Studio 2017 提供許多重構、程式碼產生動作，以及程式碼修正。 紅色波浪線代表錯誤，綠色波浪線代表警告，而三個灰色點表示程式碼的建議。 您可以存取程式碼修正，方法是按一下燈泡/螺絲起子圖示，或者按 **Ctrl**+**.** 或 **Alt**+**Enter**。 每個修正都隨附一個預覽視窗，其中顯示修正運作方式的即時程式碼差異比對。

- 常用的快速修正和重構包括：
  - *重新命名*
  - *擷取方法*
  - *變更方法簽章*
  - *產生建構函式*
  - *產生方法*
  - 將型別移到檔案
  - 加入 Null 檢查
  - 加入參數
  - 移除不必要的 Using
  - 詳細資訊請見[文件](https://aka.ms/refactorings)
- 使用 [Roslyn 分析器](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix) \(英文\) 撰寫您自己的重構或程式碼修正。
- 數個社群成員撰寫了新增額外程式碼檢查的免費延伸模組：
  - [FXCop 分析器](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)
  - [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
  - [ Visual Studio 的 SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
  - [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Visual Studio 中的重構](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>我需要尋找使用方式、移至實作、巡覽至反向編譯的組件

Visual Studio 2017 有許多功能，可協助您搜尋和瀏覽程式碼基底。 深入了解[程式碼巡覽功能](../ide/navigating-code.md)

| 功能 | 快速鍵 | 詳細資料/增強功能 |
|- | - | -|
| 尋找所有參考 | **Shift**+**F12**| 結果會以色彩標示，而且可以依專案、定義等進行分組。您也可以「鎖定」結果。 |
| 移至實作 | **Ctrl**+**F12** | 您可以在 `override` 關鍵字上使用 [移至定義] 來瀏覽至覆寫的成員 |
| 移至定義 | **F12** 或 **Ctrl**+**按一下滑鼠左鍵**| 您可以在按一下的同時長按 **Ctrl** 來瀏覽至定義 |
| 查看定義 | **Alt**+**F12** | 定義的內嵌檢視 |
| 結構視覺化檢視 | 大括號之間的灰色虛線 | 暫留以查看您的程式碼架構 |
| 巡覽至反向編譯的組件 | **F12** 或 **Ctrl**+**按一下滑鼠左鍵** | 透過啟用下列功能以巡覽至外部來源 (使用 ILSpy 進行反編譯)：[工具] > [選項] > [文字編輯器] > [C#] > [進階] > [啟用巡覽至反向編譯的原始碼]。 |

![[移至全部] 與 [尋找所有參考]](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>我想要執行並查看我的單元測試

針對 Visual Studio 2017 中的測試經驗，我們做了許多改善。 使用我們的單元測試體驗之一搭配 MSTest v1、MSTest v2、NUnit 或 XUnit 測試架構。

- 「測試總管」測試探索在版本 15.6 中十分快速 (如需最佳結果，請將您的測試配接器升級至最新版本)。
- 使用版本 15.6 中新的「階層排序」來組織 [測試總管] 中的測試。
- [Live Unit Testing](../test/live-unit-testing.md) 會持續執行程式碼變更所影響的測試，並更新內嵌編輯器圖示，讓您知道測試的狀態。 包含或排除「即時測試集合」中的特定測試或測試專案。

![Visual Studio 中 [文字總管] 的階層檢視](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>我想要針對我的程式碼進行偵錯

我們已在 Visual Studio 2017 中加入大量的新偵錯功能：

- 「執行至點選處」可允許您在一行程式碼旁暫留、點擊顯示的綠色 [播放] 圖示，並執行程式直到該行為止。
- 新的「例外狀況協助程式」會將最重要的資訊 (例如 NullReferenceException 中哪個變數為 'null') 放置在對話方塊的最上層。
- [倒退](../debugger/how-to-use-intellitrace-step-back.md)偵錯讓您可以回溯到前面的中斷點或步驟，以檢視應用程式過去的狀態。
- [快照集偵錯](/azure/application-insights/app-insights-snapshot-debugger)可讓您調查即時 Web 應用程式在例外狀況擲回時的狀態 (必須在 Azure 上)。

![Visual Studio 2017 中新的例外狀況協助程式](../ide/media/VSGuide_Debugging.png)

## <a name="i-want-to-use-version-control-with-my-projects"></a>我想要在我的專案中使用版本控制

您可以使用 Git 或 TFVC 來儲存及更新您在 Visual Studio 中的程式碼。

- 使用 **Team Explorer** 來組織本機變更，並使用狀態列來追蹤暫止的認可和變更。
- 透過 [Visual Studio 的持續傳遞工具](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio)延伸模組，在 Visual Studio 中針對您的專案設定持續整合和傳遞，並採用敏捷式開發人員工作流程。

![Visual Studio 中的原始檔控制](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>我需要知道哪些其他功能？

以下是編輯器和生產力功能的清單，可讓撰寫程式碼更有效率。 某些功能可能需要啟用，因為它們預設為關閉 (這些功能可能會在您的電腦上編製項目索引、具爭議性，或目前在實驗中)。

| 功能 | 詳細資料 | 如何啟用 |
|-|-|-|
| 在 [方案總管] 中尋找檔案 | 在 [方案總管] 中反白顯示使用中的檔案 | [工具] > [選項] > [專案和解決方案] > [在方案總管中追蹤使用中的項目] |
| 針對參考組件與 NuGet 套件中的型別新增 Using | 顯示包含程式碼修正的電燈泡，以針對未參考的型別來安裝 NuGet 套件 | [工具] > [選項] > [文字編輯器] > [C#] > [進階] > [為參考組件中的類型建議 Using] 和 [為 NuGet 套件中的類型建議 Using] |
| 啟用完整解決方案分析 | 請在 [錯誤清單] 中查看方案中的所有錯誤 | [工具] > [選項] > [文字編輯器] > [C#] > [進階]  > [啟用完整解決方案分析] |
| 啟用巡覽至反向編譯的原始碼 | 允許從外部來源對類型/成員啟用 [移至定義]，並使用 ILSpy 解編程式來顯示方法主體 | [工具] > [選項] > [文字編輯器] > [C#] > [進階] > [啟用巡覽至反向編譯的原始碼] |
| 完成/建議模式 | 變更 IntelliSense 中的完成行為 -- 具有 IntelliJ 背景的開發人員傾向於在這裡變更預設值 | [功能表] > [編輯] > [IntelliSense] > [切換完成模式] |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | 在編輯器中顯示程式碼參考資訊與變更歷程記錄 | [工具] > [選項] > [文字編輯器] > [所有語言] > [CodeLens] |
| [程式碼片段](../ide/visual-csharp-code-snippets.md) | 協助插入常用樣板作為虛設常式 |  鍵入程式碼片段名稱並按兩次 **Tab** 鍵。 |

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>遺漏功能造成生產力或效能不佳？

您可以使用幾種方式提供意見反應給我們：

- .NET 功能要求可在 [GitHub 存放庫](https://github.com/dotnet/roslyn/issues)中提出。
- Visual Studio 功能要求、錯誤和效能問題可使用 Visual Studio 視窗最右上方的 [傳送意見反應] 圖示來填寫。

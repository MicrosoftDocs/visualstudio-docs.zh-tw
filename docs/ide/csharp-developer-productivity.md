---
title: 增加您的 .NET 開發生產力
description: 這份導覽、程式碼分析、單元測試及其他功能的概觀，可協助您以更快的速度，撰寫更優質的 .NET 程式碼。
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 3e1f82a58dac3b0a6f607d1de7f881c5de9e91aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973271"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>適用於 C# 開發人員的 Visual Studio 生產力指南

了解 Visual Studio 如何讓開發人員比以往更具生產力。 運用我們的效能與生產力改進，像是導覽到反向組譯的組件、鍵入時的變數名稱建議、**測試總管**中的階層架構檢視、[移至全部] (**Ctrl**+**T**) 以導覽至檔案/類型/成員/符號宣告、智慧型**例外狀況協助程式**、程式碼樣式組態和強制執行，以及許多重構和程式碼修正。

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>我習慣從不同編輯器中使用鍵盤快速鍵

::: moniker range="vs-2017"

**Visual Studio 2017 15.8 版的新功能**

::: moniker-end

若您原先使用其他 IDE 或編碼環境，可將鍵盤配置變更為 *Visual Studio Code* 或*ReSharper (Visual Studio)*：

![Visual Studio 中的鍵盤配置](../ide/media/VS2017Guide-Keyboard.png)

有些延伸模組也提供鍵盤配置：

- [Visual Studio 的快速鍵 (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs 模擬](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

以下是常用的 Visual Studio 快速鍵：

| 快速鍵 (所有設定檔) | 命令 | 說明 |
|-|-|-|
| **Ctrl**+**T** | 移至全部 | 巡覽至任何檔案、類型、成員或符號宣告 |
| **F12** (以及 **Ctrl**+**按一下滑鼠左鍵**) | 移至定義 | 巡覽至定義符號的位置 |
| **Ctrl**+**F12** | 移至實作 | 從基底類型或成員巡覽至其各種實作 |
| **Shift**+**F12** | 尋找所有參考 | 查看所有符號或常值參考 |
| **Ctrl**+**.** (在 C# 設定檔中為 **Alt**+**Enter**) | 快速動作及重構 | 查看您游標位置或選取的程式碼有哪些程式碼修正、程式碼產生動作、重構或其他快速動作可供使用 |
| **Ctrl**+**D** | 重複行 | 複製游標所在行的程式碼 (適用於 **Visual Studio 2017 15.6 版**和更新版本) |
| **Shift**+**Alt**+**+**/**-** | 展開/折疊選取項目 | 展開或折疊編輯器中的前選取項目 (適用於 **Visual Studio 2017 15.5 版**和更新版本) |
| **Shift** + **Alt** + **.** | 插入下一個相符的插入點 | 在下一個符合目前選取項目的位置，新增選取項目及插入點 (在 **Visual Studio 2017 版本 15.8** 及最新版本中提供) |
| **Ctrl**+**Q** | 搜尋 | 搜尋所有 Visual Studio 設定 |
| **F5** | 開始偵錯 | 開始偵錯應用程式 |
| **Ctrl**+**F5** | 執行而不偵錯 | 在本機執行應用程式而不偵錯 |
| **Ctrl**+**K**、**D** (預設設定檔) 或 **Ctrl**+**E**、**D** (C# 設定檔) | [將文件格式化](code-styles-and-quick-actions.md#format-document-command) | 根據您的新行字元、間距和縮排設定，來清除您檔案中的格式違規 |
| **Ctrl**+**\\**、**Ctrl**+**E** (預設設定檔) 或 **Ctrl**+**W**、**E** (C# 設定檔) | 檢視錯誤清單 | 查看您文件、專案或方案中的所有錯誤 |
| **Alt** + **PgUp/PgDn** | 前往上一個/下一個問題 | 跳到文件中的上一個/下一個錯誤、警告、建議 (在 **Visual Studio 2017 版本 15.8** 及最新版本中提供) |

> [!NOTE]
> 有些擴充功能會將預設的 Visual Studio 按鍵繫結關係解除繫結。 若要使用上述命令，請將按鍵繫結關係還原為 Visual Studio 的預設，方法是前往 [工具] > [匯入和匯出設定] > [重設所有設定] 或 [工具] > [選項] > [鍵盤] > [重設]。

如需有關鍵盤快速鍵和命令的詳細資訊，請參閱[鍵盤快速鍵](../ide/tips-and-tricks-for-visual-studio.md)。

## <a name="navigate-quickly-to-files-or-types"></a>快速巡覽至檔案或類型

Visual Studio 2017 有一項稱為 [移至全部] (**Ctrl**+**T**) 的功能。 [移至全部] 可讓您快速跳到任何檔案、型別、成員或符號宣告。

- 變更此搜尋列的位置，或使用**齒輪**圖示關閉「即時瀏覽預覽」。
- 使用 `t mytype` 之類的語法來篩選結果。
- 將搜尋範圍僅限於目前的文件。
- 支援駝峰式大小寫比對。

![Visual Studio 中的 [移至全部]](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules-on-a-codebase"></a>對程式碼基底強制執行程式碼樣式規則

您可以使用 *.editorconfig* 檔案來撰寫編碼慣例，並讓它們隨著來源移動。

::: moniker range="vs-2017"

- 您可以安裝 [EditorConfig 語言服務延伸模組](https://aka.ms/editorconfig) \(英文\)，以便輕鬆地在 Visual Studio 中新增及編輯 *.editorconfig* 檔案。

::: moniker-end

::: moniker range=">=vs-2019"

- 在 [工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] 中，從您的程式碼樣式設定自動建立 *.editorconfig* 檔案。

   ![從 VS 2019 中的設定產生 .editorconfig 檔案](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- 嘗試 [適用於 Visual Studio 的 IntelliCode 延伸模組](/visualstudio/intellicode/intellicode-visual-studio)。 此實驗性延伸模組會從現有的程式碼推斷您的程式碼樣式，然後使用已定義的程式碼樣式喜好設定來建立非空白的 *.editorconfig* 檔案。

- 請參閱 [.NET 程式碼慣例選項](editorconfig-code-style-settings-reference.md) 文件。

- 如需範例 *.editorconfig* 檔案，請參閱[此 gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) \(英文\)。

![Visual Studio 中的程式碼樣式強制執行](../ide/media/VSGuide_CodeStyle.png)

## <a name="refactorings-and-code-fixes"></a>重構和程式碼修正

Visual Studio 提供許多重構、程式碼產生動作，以及程式碼修正。 紅色波浪線代表錯誤，綠色波浪線代表警告，而三個灰色點表示程式碼的建議。 您可以藉由按一下燈泡或螺絲起子圖示，或者按 **Ctrl**+**.** 來存取程式碼修正。 或 **Alt**+**Enter**。 每個修正都隨附一個預覽視窗，其中顯示修正運作方式的即時程式碼差異比對。

常用的快速修正和重構包括：

- *重新命名*
- *擷取方法*
- *變更方法簽章*
- *產生建構函式*
- *產生方法*
- 將型別移到檔案
- 加入 Null 檢查
- 加入參數
- 移除不必要的 Using
- Foreach 迴圈到 LINQ 查詢或 LINQ 方法
- *向上提取成員*
- 如需詳細資訊，請參閱[程式碼產生功能](code-generation-in-visual-studio.md)

您可以[安裝 FxCop 分析器](../code-quality/install-fxcop-analyzers.md)來將程式碼問題加上旗標。 或，使用 [Roslyn 分析器](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix) \(英文\) 撰寫您自己的重構或程式碼修正。

數個社群成員撰寫了新增額外程式碼檢查的免費延伸模組：

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [ Visual Studio 的 SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/) \(英文\)

![Visual Studio 中的重構](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>尋找使用方式、移至實作及巡覽至反向編譯的組件

Visual Studio 有許多功能，可協助您搜尋和[巡覽程式碼](../ide/navigating-code.md)。

| 功能 | 快速鍵 | 詳細資料/增強功能 |
|- | - | -|
| 尋找所有參考 | **Shift**+**F12**| 結果會以色彩標示，且可以依專案、定義和參考類型 (例如讀取或寫入) 進行分組。 您也可以「鎖定」結果。 |
| 移至實作 | **Ctrl**+**F12** | 您可以在 `override` 關鍵字上使用 [移至定義] 來瀏覽至覆寫的成員 |
| 移至定義 | **F12** 或 **Ctrl**+**按一下滑鼠左鍵**| 在按一下的同時按 **Ctrl** 來巡覽至定義 |
| 查看定義 | **Alt**+**F12** | 定義的內嵌檢視 |
| 結構視覺化檢視 | 大括號之間的灰色虛線 | 暫留以查看您的程式碼架構 |
| 巡覽至反向編譯的組件 | **F12** 或 **Ctrl**+**按一下滑鼠左鍵** | 啟用功能以巡覽至外部來源 (使用 ILSpy 反向編譯)：[工具] > [選項] > [文字編輯器] > [C#] > [進階] > [啟用巡覽至反向組譯的原始檔]。 |

![[移至全部] 與 [尋找所有參考]](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>改良的 IntelliSense

下載 [IntelliCode 延伸模組](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode) \(英文\)，以取得[內容感知程式碼完成](/visualstudio/intellicode/intellicode-visual-studio)，而不是字母順序清單。 您也可以根據自己的網域特定程式庫，訓練[自訂 IntelliSense 模型](/visualstudio/intellicode/custom-model-faq)。

## <a name="unit-testing"></a>單元測試

從 Visual Studio 2017 開始，已多加改善測試體驗。 您可以使用 MSTest v1、MSTest v2、NUnit 或 XUnit 測試架構來測試。

- [測試總管] 測試探索速度很快。

- 使用「階層排序」來組織 [測試總管] 中的測試。

   ![Visual Studio 中 [文字總管] 的階層檢視](../ide/media/VSGuide_Testing.png)

- [Live Unit Testing](../test/live-unit-testing.md) 會持續執行程式碼變更所影響的測試，並更新內嵌編輯器圖示，讓您知道測試的狀態。 包含或排除即時測試集合中的特定測試或測試專案。 (僅限Visual Studio Enterprise 版。)

## <a name="debugging"></a>偵錯

部分 Visual Studio 偵錯功能包括：

::: moniker range=">=vs-2019"

- 能夠在 [監看式]、[自動變數] 及 [區域變數] 視窗內搜尋字串。
- 「執行至點選處」可讓您在一行程式碼旁暫留、點擊顯示的綠色 [播放] 圖示，並執行程式直到該行為止。
- **例外狀況協助程式**會將最重要的資訊放置在對話方塊的最上層，例如當 `NullReferenceException` 中的變數為 `null` 時。
- [倒退](../debugger/view-historical-application-state.md)偵錯可讓您回溯到前面的中斷點或步驟，以檢視應用程式過去的狀態。
- [快照集偵錯](/azure/application-insights/app-insights-snapshot-debugger)可讓您調查即時 Web 應用程式在例外狀況擲回時的狀態 (必須在 Azure 上)。

::: moniker-end

::: moniker range="vs-2017"

- 「執行至點選處」可讓您在一行程式碼旁暫留、點擊顯示的綠色 [播放] 圖示，並執行程式直到該行為止。
- **例外狀況協助程式**會將最重要的資訊放置在對話方塊的最上層，例如當 `NullReferenceException` 中的變數為 `null` 時。
- [倒退](../debugger/view-historical-application-state.md)偵錯可讓您回溯到前面的中斷點或步驟，以檢視應用程式過去的狀態。
- [快照集偵錯](/azure/application-insights/app-insights-snapshot-debugger)可讓您調查即時 Web 應用程式在例外狀況擲回時的狀態 (必須在 Azure 上)。

::: moniker-end

![Visual Studio 中的例外狀況協助程式](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>版本控制

您可以使用 Git 或 TFVC 來儲存及更新您在 Visual Studio 中的程式碼。

::: moniker range=">=vs-2019"

- 安裝[適用於 Visual Studio 的提取要求](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) \(英文\)，不需要離開 Visual Studio，便可建立、檢閱、簽出及執行提取要求。

::: moniker-end

- 在 [Team Explorer](reference/team-explorer-reference.md) 中組織本機變更，並使用狀態列來追蹤暫止的認可和變更。

- 透過[適用於 Visual Studio 的持續傳遞工具](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) \(英文\) 延伸模組，在 Visual Studio 中針對您的 ASP.NET 專案設定持續整合和傳遞。

![Visual Studio 中的原始程式碼控制](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>我還應該知道哪些其他功能？

以下是編輯器和生產力功能的清單，可讓撰寫程式碼更有效率。 某些功能可能需要啟用，因為它們預設為關閉 (這些功能可能會在您的電腦上編製項目索引、具爭議性，或目前在實驗中)。

| 功能 | 詳細資料 | 如何啟用 |
|-|-|-|
| 在 [方案總管] 中尋找檔案 | 在 [方案總管] 中反白顯示使用中的檔案 | [工具] > [選項] > [專案和解決方案] > [在方案總管中追蹤使用中的項目] |
| 針對參考組件與 NuGet 套件中的型別新增 Using | 顯示包含程式碼修正的錯誤燈泡，以針對未參考的型別來安裝 NuGet 套件 | [工具] > [選項] > [文字編輯器] > [C#] > [進階] > [為參考組件中的類型建議 Using] 和 [為 NuGet 套件中的類型建議 Using] |
| 啟用完整解決方案分析 | 請在 [錯誤清單] 中查看方案中的所有錯誤 | [工具] > [選項] > [文字編輯器] > [C#] > [進階]  > [啟用完整解決方案分析] |
| 啟用巡覽至反向編譯的原始碼 | 允許從外部來源對類型/成員啟用 [移至定義]，並使用 ILSpy 解編程式來顯示方法主體 | [工具] > [選項] > [文字編輯器] > [C#] > [進階] > [啟用巡覽至反向編譯的原始碼] |
| 完成/建議模式 | 變更 IntelliSense 中的完成行為。 具有 IntelliJ 背景的開發人員傾向於使用這裡的非預設設定。 | [功能表] > [編輯] > [IntelliSense] > [切換完成模式] |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | 在編輯器中顯示程式碼參考資訊與變更歷程記錄。 (在 Visual Studio Community 版中無法使用原始程式碼控制 CodeLens 指標。) | [工具] > [選項] > [文字編輯器] > [所有語言] > [CodeLens] |
| [程式碼片段](../ide/visual-csharp-code-snippets.md) | 協助插入常用樣板程式碼作為虛設常式 | 鍵入程式碼片段名稱並按兩次 **Tab** 鍵。 |

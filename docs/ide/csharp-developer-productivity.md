---
title: 增加您的 .NET 開發生產力
description: 這份導覽、程式碼分析、單元測試及其他功能的概觀，可協助您以更快的速度，撰寫更優質的 .NET 程式碼。
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 09a33db9df8e1309792cd6a3722bb82333348d84
ms.sourcegitcommit: 690bfc20744e4b543ee81030a60c8fc6d0d6610f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2021
ms.locfileid: "113038651"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>適用於 C# 開發人員的 Visual Studio 生產力指南

了解 Visual Studio 如何讓開發人員比以往更具生產力。 運用我們的效能與生產力改進，像是導覽到反編譯組件、輸入時的變數名稱建議、**測試總管** 中的階層架構檢視、[移至全部] (**Ctrl**+**T**) 以導覽至檔案/類型/成員/符號宣告、智慧型 **例外狀況協助程式**、程式碼樣式設定和強制執行，以及許多重構和程式碼修正。

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>我習慣從不同編輯器中使用鍵盤快速鍵

::: moniker range="vs-2017"

**Visual Studio 2017 15.8 版的新功能**

::: moniker-end

若您原先使用其他 IDE 或編碼環境，可將鍵盤配置變更為 *Visual Studio Code* 或 *ReSharper (Visual Studio)*：

![Visual Studio 中的鍵盤配置](../ide/media/VS2017Guide-Keyboard.png)

有些延伸模組也提供鍵盤配置：

- [Visual Studio 的快速鍵 (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs 模擬](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

以下是常用的 Visual Studio 快速鍵：

| 快速鍵 (所有設定檔) | 命令 | 描述 |
|-|-|-|
| **Ctrl** +**T** | 移至全部 | 巡覽至任何檔案、類型、成員或符號宣告 |
| **F12** (也 + **按 Ctrl 按一下**)  | 移至定義 | 巡覽至定義符號的位置 |
| **Ctrl** +**F12** | 移至實作 | 從基底類型或成員巡覽至其各種實作 |
| **Shift** +**F12** | 尋找所有參考 | 查看所有符號或常值參考 |
| **Alt** +**首頁** | 移至基底 | 流覽繼承鏈 |
| **Ctrl** +**.**  (也會 + 在 c # 設定檔中 **輸入 Alt Enter**)  | 快速動作及重構 | 查看您游標位置或選取的程式碼有哪些程式碼修正、程式碼產生動作、重構或其他快速動作可供使用 |
| **Ctrl** +**D** | 重複行 | 複製游標所在行的程式碼 (適用於 **Visual Studio 2017 15.6 版** 和更新版本) |
| **Shift** +**Alt**+**+**/**-** | 展開/折疊選取項目 | 展開或折疊編輯器中的前選取項目 (適用於 **Visual Studio 2017 15.5 版** 和更新版本) |
| **Shift**  + **Alt**  + **.** | 插入下一個相符的插入點 | 在下一個符合目前選取項目的位置，新增選取項目及插入點 (在 **Visual Studio 2017 版本 15.8** 及最新版本中提供) |
| **Ctrl** +**問：** | 搜尋 | 搜尋所有 Visual Studio 設定 |
| **F5** | [偵錯] | 開始偵錯應用程式 |
| **Ctrl** +**F5** | 執行而不偵錯 | 在本機執行應用程式而不偵錯 |
| **Ctrl** +**K**、**d** (預設設定檔) 或 **Ctrl** + **E**、**d** (c # 設定檔)  | 格式化文件 | 根據您的新行字元、間距和縮排設定，來清除您檔案中的格式違規 |
| **Ctrl** + **\\** 、**ctrl** + **E** (預設設定檔) 或 **ctrl** + **W**、**E** (c # 設定檔)  | 檢視錯誤清單 | 查看您文件、專案或方案中的所有錯誤 |
| **Alt**  + **PgUp/>pgdn** | 前往上一個/下一個問題 | 跳到文件中的上一個/下一個錯誤、警告、建議 (在 **Visual Studio 2017 版本 15.8** 及最新版本中提供) |
| **Ctrl** +**K**、**/** | 切換單行註解/取消註解 | 此命令會根據您的選取項目是否已被註解來新增或移除單行註解 |
| **Ctrl** +**Shift**+**/** | 切換區塊註解/取消註解 | 此命令會根據您所選取的項目來新增或移除區塊註解 |

> [!NOTE]
> 有些擴充功能會將預設的 Visual Studio 按鍵繫結關係解除繫結。 若要使用上述命令，請前往 [**工具** 匯  >  **入和匯出設定**  >  **重設所有設定** 或 **工具**  >  **選項** 的  >  **鍵盤**  >  **重設**]，將您的 keybindings.json 還原為 Visual Studio 的預設值。

如需鍵盤快速鍵和命令的詳細資訊，請參閱[生產力快速鍵](../ide/productivity-shortcuts.md)及[常用鍵盤快速鍵](default-keyboard-shortcuts-in-visual-studio.md)。

## <a name="navigate-quickly-to-files-or-types"></a>快速巡覽至檔案或類型

Visual Studio 有稱為 [移至全部] (**Ctrl**+**T**) 的功能。 [**移至全部**] 可讓您快速跳到任何檔案、類型、成員或符號宣告。

- 變更此搜尋列的位置，或使用 **齒輪** 圖示關閉「即時瀏覽預覽」。
- 使用 `t mytype` 之類的語法來篩選結果。
- 將搜尋範圍僅限於目前的文件。
- 支援駝峰式大小寫比對。

![Visual Studio 中的 [移至全部]](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>底強制執行程式碼樣式規則

您可以使用 EditorConfig 檔案來撰寫編碼慣例，並讓它們隨著來源移動。

![Visual Studio 中的程式碼樣式強制執行](../ide/media/VSGuide_CodeStyle.png)

- 加入預設值或。選擇 [**加入**  >  **新專案**]，將 EditorConfig 檔案加入至您的專案。 在 [加入新項目] 對話方塊中，搜尋 "editorconfig"。 選取其中一個 [editorconfig 檔案] 項目範本，然後選擇 [新增]。

   ![Visual Studio 中的 EditorConfig 項目範本](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- 根據您在 **工具** > **選項** > **文字編輯器** > **c #** 程式 > **代碼樣式** 中的程式碼樣式設定，自動建立 editorconfig 檔案。

   ![從 VS 2019 中的設定產生 .editorconfig 檔案](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Visual Studio 中 IntelliCode 的[程式碼推斷功能](/visualstudio/intellicode/code-style-inference)可從現有程式碼推斷程式碼樣式。 然後它會使用已定義的程式碼樣式喜好設定來建立非空白的 EditorConfig 檔案。

- 直接透過編輯器設定程式碼樣式規則的嚴重性層級。 如果您目前沒有 editorconfig 檔案，系統會為您產生一個檔案。 將游標放在錯誤、警告或建議，然後輸入 **Ctrl** + **。** 以開啟 [快速動作與重構] 功能表。 選取 [ **設定或隱藏問題**]。 然後選取規則，並選擇您想要為該規則設定的嚴重性層級。 這會以規則的新嚴重性更新現有的 EditorConfig。

   ![直接在編輯器中設定程式碼樣式規則的嚴重性層級](../ide/media/configure-severity-level.png)

請參閱 [.NET 編碼慣例選項](/dotnet/fundamentals/code-analysis/code-style-rule-options)文件，其中也包含完整 EditorConfig 檔案的範例。

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>程式碼清除

Visual Studio 透過 [程式碼清除] 功能，讓您能依需求對程式碼檔案 (包括程式碼樣式喜好設定) 進行格式化。 若要執行程式碼清除，請按一下編輯器底部的 [掃帚] 圖示，或按下 **ctrl** + **K**、 **ctrl** + **E**。

![Visual Studio 2019 中的 [程式碼清除] 按鈕](media/execute-code-cleanup.png)

您也可以跨整個專案或解決方案執行程式碼清除。 以滑鼠右鍵按一下 [方案總管] 中的專案或解決方案名稱，選取 [分析與程式碼清除]，然後選取 [執行程式碼清除]。

![跨整個專案或解決方案執行程式碼清除](media/run-code-cleanup-project-solution.png)

除了針對空格、縮排等對檔案進行格式化之外，[程式碼清除] 也能套用選取的程式碼樣式。 系統會從 [EditorConfig 檔案](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) (如果您針對專案有該檔案的話) 讀取您針對每個程式碼樣式的偏好設定，或是從 [選項] 對話方塊中的[程式碼樣式設定](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box)讀取那些偏好設定。

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>重構和程式碼修正

Visual Studio 提供許多重構、程式碼產生動作，以及程式碼修正。 紅色波浪線代表錯誤，綠色波浪線代表警告，而三個灰色點表示程式碼的建議。 您可以按一下燈泡或螺絲起子圖示，或按 **Ctrl 鍵** 來存取程式碼修正 + **。** 或 **Alt** + **Enter**。 每個修正都隨附一個預覽視窗，其中顯示修正運作方式的即時程式碼差異比對。

常用的快速修正和重構包括：

- 重新命名
- 擷取方法
- 變更方法簽章
- 產生建構函式
- 產生方法
- 將類型移到檔案
- 加入 Null 檢查
- 新增參數
- 移除不必要的 Using
- Foreach 迴圈到 LINQ 查詢或 LINQ 方法
- 向上提取成員

如需詳細資訊，請參閱程式 [代碼產生功能](code-generation-in-visual-studio.md)。

您可以[安裝 FxCop 分析器](../code-quality/install-fxcop-analyzers.md)來將程式碼問題加上旗標。 或，使用 [Roslyn 分析器](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md) \(英文\) 撰寫您自己的重構或程式碼修正。

數個社群成員撰寫了新增額外程式碼檢查的免費延伸模組：

::: moniker range="vs-2017"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [ Visual Studio 的 SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/) \(英文\)

::: moniker-end

::: moniker range=">=vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [ Visual Studio 的 SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/) \(英文\)

::: moniker-end

![Visual Studio 中的重構](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>尋找使用方式、移至實作及巡覽至反向編譯的組件

Visual Studio 有許多功能，可協助您搜尋和[巡覽程式碼](../ide/navigating-code.md)。

| 功能 | 快速鍵 | 詳細資料/增強功能 |
|- | - | -|
| 尋找所有參考 | **Shift** +**F12**| 結果會以色彩標示，且可以依專案、定義和參考類型 (例如讀取或寫入) 進行分組。 您也可以「鎖定」結果。 |
| 移至實作 | **Ctrl** +**F12** | 您可以在 `override` 關鍵字上使用 [移至定義] 來瀏覽至覆寫的成員 |
| 移至定義 | **F12** 或 **按 Ctrl 鍵** + | 在按一下的同時按 **Ctrl** 來巡覽至定義 |
| 查看定義 | **Alt** +**F12** | 定義的內嵌檢視 |
| 結構視覺化檢視 | 大括號之間的灰色虛線 | 暫留以查看您的程式碼架構 |
| 巡覽至反向編譯的組件 | **F12** 或 **按 Ctrl 鍵** +  | 藉由啟用功能：**工具**  >  **選項**  >  **文字編輯器**  >  **c #**  >  **Advanced**  >  **啟用流覽至反向組譯來源**，以 ILSpy) 流覽至外部來源 (反向組譯。 |

![[移至全部] 與 [尋找所有參考]](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>改良的 IntelliSense

使用適用於 Visual Studio 的 IntelliCode 來取得[內容感知程式碼完成](/visualstudio/intellicode/intellicode-visual-studio)，而非單純的字母順序清單。 您也可以根據自己的網域特定程式庫，訓練[自訂 IntelliSense 模型](/visualstudio/intellicode/custom-model-faq)。

## <a name="unit-testing"></a>單元測試

從 Visual Studio 2017 開始，已多加改善測試體驗。 您可以使用 MSTest v1、MSTest v2、NUnit 或 XUnit 測試架構來測試。

- [測試總管] 測試探索速度很快。

- 使用「階層排序」來組織 [測試總管] 中的測試。

   ![Visual Studio 中 [文字總管] 的階層檢視](../ide/media/VSGuide_Testing.png)

- [即時單元測試](../test/live-unit-testing.md) 會持續執行您的程式碼變更所影響的測試，並更新內嵌編輯器圖示，讓您知道測試的狀態。 包含或排除即時測試集合中的特定測試或測試專案。 (僅限Visual Studio Enterprise 版。)

## <a name="debugging"></a>偵錯

部分 Visual Studio 偵錯功能包括：

::: moniker range=">=vs-2019"

- 能夠在 [監看式]、[自動變數] 及 [區域變數] 視窗內搜尋字串。
- 「執行至點選處」可讓您在一行程式碼旁暫留、點擊顯示的綠色 [播放] 圖示，並執行程式直到該行為止。
- **例外狀況協助程式**，其會將最重要的資訊放置在對話方塊的最上層，例如當 `NullReferenceException` 中的變數為 `null` 時。
- [倒退](../debugger/view-historical-application-state.md)偵錯可讓您回溯到前面的中斷點或步驟，以檢視應用程式過去的狀態。
- [快照集偵錯](/azure/application-insights/app-insights-snapshot-debugger)可讓您調查即時 Web 應用程式在例外狀況擲回時的狀態 (必須在 Azure 上)。

::: moniker-end

::: moniker range="vs-2017"

- 「執行至點選處」可讓您在一行程式碼旁暫留、點擊顯示的綠色 [播放] 圖示，並執行程式直到該行為止。
- **例外狀況協助程式**，其會將最重要的資訊放置在對話方塊的最上層，例如當 `NullReferenceException` 中的變數為 `null` 時。
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

![Visual Studio 中的原始檔控制](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>我還應該知道哪些其他功能？

以下是編輯器和生產力功能的清單，可讓撰寫程式碼更有效率。 某些功能可能需要啟用，因為它們預設為關閉 (這些功能可能會在您的電腦上編製項目索引、具爭議性，或目前在實驗中)。

| 功能 | 詳細資料 | 如何啟用 |
|-|-|-|
| 在 [方案總管] 中尋找檔案 | 在 [方案總管] 中反白顯示使用中的檔案 | **工具**  > **選項**  > **專案和方案**  > **追蹤方案總管中的活動專案** |
| 針對參考組件與 NuGet 套件中的型別新增 Using | 顯示包含程式碼修正的錯誤燈泡，以針對未參考的型別來安裝 NuGet 套件 | **工具**  > **選項**  > **文字編輯器**  > **C #**  > **Advanced**  > **針對參考元件中的類型建議 using** ，並 **針對 NuGet 套件中的類型建議 using** |
| 啟用完整解決方案分析 | 在 [**錯誤清單**] 中查看方案中的所有錯誤 | **工具**  > **選項**  > **文字編輯器**  > **C #**  > **Advanced**  > **啟用完整解決方案分析** |
| 啟用巡覽至反向編譯的原始碼 | 允許從外部來源對類型/成員啟用 [移至定義]，並使用 ILSpy 解編程式來顯示方法主體 | **工具**  > **選項**  > **文字編輯器**  > **C #**  > **Advanced**  > **啟用流覽至反向組譯來源** |
| 完成/建議模式 | 變更 IntelliSense 中的完成行為。 具有 IntelliJ 背景的開發人員傾向於使用這裡的非預設設定。 | **功能表**  > **編輯**  > **IntelliSense**  > **切換完成模式** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | 在編輯器中顯示程式碼參考資訊與變更歷程記錄。 (在 Visual Studio Community 版中無法使用原始程式碼控制 CodeLens 指標。) | **工具**  > **選項**  > **文字編輯器**  > **所有語言**  > **CodeLens** |
| [程式碼片段](../ide/visual-csharp-code-snippets.md) | 協助插入常用樣板程式碼作為虛設常式 | 輸入程式碼片段名稱並按 **tab** 鍵兩次。 |

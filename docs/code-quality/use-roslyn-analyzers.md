---
title: 分析器規則嚴重性和抑制
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431406"
---
# <a name="use-code-analyzers"></a>使用代碼分析器

.NET 編譯器平臺 （"Roslyn"） 代碼分析器在鍵入時分析您的 C# 或視覺化基本代碼。 每個*診斷*或規則都有一個預設嚴重性和抑制狀態，可以覆蓋您的專案。 本文介紹設置規則嚴重性、使用規則集和禁止衝突。

## <a name="analyzers-in-solution-explorer"></a>解決方案資源管理器中的分析儀

你可以從**解決方案資源管理器**執行分析器診斷的自訂。 如果將[分析器安裝](../code-quality/install-roslyn-analyzers.md)為 NuGet 包，則**分析器**節點將顯示在**解決方案資源管理器**中的 **"參考"** 或**依賴項**節點下。 如果展開**分析器**，然後展開分析器程式集之一，則會看到程式集中的所有診斷。

![解決方案資源管理器中的分析器節點](media/analyzers-expanded-in-solution-explorer.png)

您可以在"**屬性"** 視窗中查看診斷的屬性，包括其描述和預設嚴重性。 要查看屬性，請按右鍵規則並選擇 **"屬性**"，或選擇規則，然後按**Alt**+**Enter**。

![屬性視窗中的診斷屬性](media/analyzer-diagnostic-properties.png)

要查看診斷的線上文檔，請按右鍵診斷並選擇"**查看説明**"。

**解決方案資源管理器**中每個診斷器旁邊的圖示對應于您在編輯器中打開規則集時看到的圖示：

- 圓圈中的"x"表示**錯誤**[的嚴重性](#rule-severity)
- 三角形中的"！ [severity](#rule-severity) **Warning**
- 圓圈中的"i"表示**資訊**[的嚴重性](#rule-severity)
- 淺色背景上的圓圈中的"i"表示**隱藏**[的嚴重性](#rule-severity)
- 圓圈中的向下箭頭表示診斷被抑制

![解決方案資源管理器中的診斷圖示](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>規則嚴重性

::: moniker range=">=vs-2019"

如果將[分析器](../code-quality/install-roslyn-analyzers.md)作為 NuGet 包安裝，則可以配置分析器規則或*診斷*的嚴重性。 從 Visual Studio 2019 版本 16.3 開始，您可以在[Editor Config 檔中](#set-rule-severity-in-an-editorconfig-file)配置規則的嚴重性。 您還可以[從解決方案資源管理器](#set-rule-severity-from-solution-explorer)或[規則集檔中](#set-rule-severity-in-the-rule-set-file)更改規則的嚴重性。

::: moniker-end

::: moniker range="vs-2017"

如果將[分析器](../code-quality/install-roslyn-analyzers.md)作為 NuGet 包安裝，則可以配置分析器規則或*診斷*的嚴重性。 可以從[解決方案資源管理器](#set-rule-severity-from-solution-explorer)或[規則集檔中](#set-rule-severity-in-the-rule-set-file)更改規則的嚴重性。

::: moniker-end

下表顯示了不同的嚴重性選項：

| 嚴重性（解決方案資源管理器） | 嚴重性（編輯器設定檔） | 構建時間行為 | 編輯器行為 |
|-|-|-|
| 錯誤 | `error` | 衝突在錯誤清單和命令列生成輸出中顯示為*錯誤*，並導致生成失敗。| 有問題的代碼用紅色波浪線底線，並在滾動欄中用紅色小框標記。 |
| 警告 | `warning` | 衝突在錯誤清單和命令列生成輸出中顯示為*警告*，但不會導致生成失敗。 | 有問題的代碼用綠色波浪線底線，並在滾動欄中用綠色小框標記。 |
| 資訊 | `suggestion` | 衝突在錯誤清單中顯示為 *"消息*"，在命令列生成輸出中根本不顯示。 | 有問題的代碼用灰色波浪線底線，並在滾動欄中用一個小灰色框標記。 |
| Hidden | `silent` | 使用者不可見。 | 使用者不可見。 但是，診斷報告給 IDE 診斷引擎。 |
| None | `none` | 完全抑制。 | 完全抑制。 |
| 預設 | `default` | 對應于規則的預設嚴重性。 要確定規則的預設值是什麼，請查看"屬性"視窗。 | 對應于規則的預設嚴重性。 |

以下代碼編輯器的螢幕截圖顯示了三個不同的衝突，其嚴重性不同。 請注意波浪形的顏色和右側滾動欄中的小彩色方塊。

![代碼編輯器中的錯誤、警告和資訊衝突](media/diagnostics-severity-colors.png)

以下螢幕截圖顯示了與錯誤清單中顯示的三個衝突相同的衝突：

![錯誤清單中的錯誤、警告和資訊衝突](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>在編輯器設定檔中設置規則嚴重性

（視覺工作室 2019 版本 16.3 及更高版本）

您可以使用以下語法在 Editor Config 檔中設置編譯器警告或分析器規則的嚴重性：

`dotnet_diagnostic.<rule ID>.severity = <severity>`

在 Editor Config 檔中設置規則的嚴重性優先于規則集或解決方案資源管理器中設置的任何嚴重性。 您可以在 Editor Config 檔中[手動](#manually-configure-rule-severity)配置嚴重性，也可以通過衝突旁邊的燈泡[自動](#automatically-configure-rule-severity)配置嚴重性。

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>在編輯器設定檔中一次設置多個分析器規則的規則嚴重性

（視覺工作室 2019 版本 16.5 及更高版本）

您可以使用 Editor Config 檔中的單個條目設置特定類別分析器規則或所有分析器規則的嚴重性。

- 為分析器規則類別設置規則嚴重性：

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- 為所有分析器規則設置規則嚴重性：

`dotnet_analyzer_diagnostic.severity = <severity>`

如果您有多個適用于特定規則 ID 的條目，則以下是選擇適用條目的優先順序順序：

- 按 ID 劃分的單個規則的嚴重性條目優先于類別的嚴重性條目。
- 類別的嚴重性條目優先于所有分析器規則的嚴重性輸入。

請考慮以下編輯器配置示例，其中[CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822)具有"性能"類別：

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

在前面的示例中，所有三個條目都適用于 CA1822。 但是，使用指定的優先順序規則，第一個基於規則 ID 的嚴重性條目勝於下一個條目。 在此示例中，CA1822 將具有有效的嚴重性"錯誤"。 具有"性能"類別的所有其餘規則都將具有嚴重性"警告"。 所有剩餘的分析器規則（沒有"性能"類別）都將具有嚴重性"建議"。

#### <a name="manually-configure-rule-severity"></a>手動設定規則嚴重性

1. 如果專案還沒有編輯器設定檔，[請添加一個](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)。

2. 為要在相應的檔副檔名下配置的每個規則添加一個條目。 例如，要將[CA1822](ca1822.md)的嚴重性設置為`error`C# 檔，該條目如下所示：

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> 對於 IDE 代碼樣式分析器，還可以使用不同的語法（例如），`dotnet_style_qualification_for_field = false:suggestion`在 Editor Config 檔中配置它們。 但是，如果使用`dotnet_diagnostic`語法設置嚴重性，則它優先。 有關詳細資訊，請參閱[編輯器配置的語言約定](../ide/editorconfig-language-conventions.md)。

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>將現有規則集檔轉換為編輯器設定檔

從 Visual Studio 2019 版本 16.5 開始，規則集檔被棄用，轉而使用 Editor Config 檔來分析器配置託管代碼。 大多數用於分析器規則嚴重性配置的 Visual Studio 工具已更新為處理 Editor Config 檔而不是規則集檔。 編輯器設定檔允許您配置分析器規則分型和分析器選項，包括 Visual Studio IDE 代碼樣式選項。 強烈建議您將現有規則集檔轉換為 Editor Config 檔。 還建議您將 Editor Config 檔保存在回購的根目錄或解決方案資料夾中。 通過使用回購或解決方案資料夾的根目錄，可以確保此檔中的嚴重性設置分別自動應用於整個回購或解決方案。

有幾種方法可以將現有規則集檔轉換為 EditorConfig 檔：

- 從視覺化工作室的規則集編輯器（需要視覺化工作室 2019 16.5 或更高版本）。 如果專案已使用特定的規則集檔作為其`CodeAnalysisRuleSet`，則可以將其轉換為 Visual Studio 中規則集編輯器中的等效編輯器設定檔。

    1. 按兩下解決方案資源管理器中的規則集檔。

       規則集檔應在規則集編輯器中打開。 您應該在規則集編輯器的頂部看到一個可按一下**的資訊列**。

       ![將規則集轉換為規則集編輯器中的編輯器設定檔](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **按一下**資訊列連結。

       這將打開一個 **"保存為"** 對話方塊，允許您選擇要生成 Editor Config 檔的目錄。

    3. **按一下**"**保存**"按鈕以生成編輯器設定檔。

       生成的編輯器配置應在編輯器中打開。 此外，MSBuild 屬性`CodeAnalysisRuleSet`在專案檔案中得到更新，以便它不再引用原始規則集檔。

- 從命令列：

    1. 安裝 NuGet 包[Microsoft.代碼分析.規則集到編輯器轉換器](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter)。

    2. 從`RulesetToEditorconfigConverter.exe`已安裝的包執行，將規則集檔和 Editor Config 檔的路徑作為命令列參數。

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

下面是要轉換的規則集檔示例：

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

下面是轉換後的編輯器設定檔：

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```

#### <a name="automatically-configure-rule-severity"></a>自動設定規則嚴重性

##### <a name="configure-from-light-bulb-menu"></a>從燈泡功能表配置

Visual Studio 提供了一種從["快速操作"](../ide/quick-actions.md)燈泡功能表中配置規則嚴重性的快速方法。

1. 發生違規後，將滑鼠懸停在編輯器中的違規切換上，然後打開燈泡功能表。 或者，將游標放在行上，然後按**Ctrl**+**。** (句點)。

2. 從燈泡功能表中，選擇 **"配置"或"禁止"配置**>**\<規則 ID>嚴重性**。

   ![在視覺化工作室中從燈泡功能表配置規則嚴重性](media/configure-rule-severity.png)

3. 在此處，選擇一個嚴重性選項。

   ![將規則嚴重性配置為建議](media/configure-rule-severity-suggestion.png)

   Visual Studio 向 Editor Config 檔添加一個條目，以將規則配置為請求的級別，如預覽框中所示。

   > [!TIP]
   > 如果專案中還沒有編輯器設定檔，Visual Studio 會為您創建一個。

##### <a name="configure-from-error-list"></a>從錯誤清單配置

Visual Studio 還提供一種從錯誤清單內容功能表配置規則嚴重性操作的便捷方法。

1. 發生衝突後，按右鍵錯誤清單中的診斷條目。

2. 在內容功能表中，選擇 **"設置嚴重性**"。

   ![在視覺化工作室中從錯誤清單中配置規則嚴重性](media/configure-rule-severity-error-list.png)

3. 在此處，選擇一個嚴重性選項。

   Visual Studio 向編輯器設定檔添加一個條目，以將規則配置為請求的級別。

   > [!TIP]
   > 如果專案中還沒有編輯器設定檔，Visual Studio 會為您創建一個。

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>從解決方案資源管理器設置規則嚴重性

1. 在解決方案資源管理器中，展開**引用** > **分析器**（或 .NET Core 專案**的依賴關係** > **分析器**）。

2. 展開包含要為其設置嚴重性的規則的程式集。

::: moniker range=">=vs-2019"
3. 按右鍵規則並選擇 **"設置嚴重性**"。 在內容功能表中，選擇其中一個嚴重性選項。

   Visual Studio 向編輯器設定檔添加一個條目，以將規則配置為請求的級別。 如果專案使用規則集檔而不是 Editor Config 檔，則嚴重性條目將添加到規則集檔中。

   > [!TIP]
   > 如果專案中還沒有編輯器設定檔或規則集檔，Visual Studio 會為您創建新的編輯器設定檔。
::: moniker-end

::: moniker range="vs-2017"
3. 按右鍵規則並選擇 **"設置規則集嚴重性**"。 在內容功能表中，選擇其中一個嚴重性選項。

   規則的嚴重性保存在活動規則集檔中。
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>在規則集檔中設置規則嚴重性

![解決方案資源管理器中的規則集檔](media/ruleset-in-solution-explorer.png)

1. 通過在**解決方案資源管理器**中按兩下活動規則集檔，在**引用** > **分析器**節點的按右鍵功能表上選擇 **"打開活動規則集"，** 或在專案**的代碼分析**屬性頁上選擇 **"打開"來打開**活動規則集檔。

   如果這是您第一次編輯規則集，Visual Studio 會複製預設規則集檔，將其*\<命名為>.ruleset，* 並將其添加到專案中。 此自訂規則集也將成為專案的活動規則集。

   > [!NOTE]
   > .NET Core 和 .NET 標準專案不支援**解決方案資源管理器**中規則集的功能表命令，例如，**打開活動規則集**。 要為 .NET Core 或 .NET 標準專案指定非預設規則集，請手動[將**代碼分析規則集**屬性添加到](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project)專案檔案中。 您仍然可以在 Visual Studio 規則集編輯器 UI 中的規則集中配置規則。

1. 通過展開它包含的程式集流覽到規則。

1. 在"**操作"** 列中，選擇要打開下拉清單的值，並從清單中選擇所需的嚴重性。

   ![在編輯器中打開規則集檔](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>抑制違規行為

有多種方法可以禁止違反規則：

::: moniker range=">=vs-2019"

- 在**編輯器設定檔中**

  將嚴重性設置為`none`， 例如`dotnet_diagnostic.CA1822.severity = none`，

- 從 **"分析"** 功能表

  選擇 **"分析** > **生成"和"抑制**功能表列上的活動問題"以抑制所有當前衝突。 這有時稱為"基線"。

::: moniker-end

::: moniker range="vs-2017"

- 從 **"分析"** 功能表

  選擇 **"分析** > **運行代碼分析"並抑制**功能表列上的活動問題，以抑制所有當前衝突。 這有時稱為"基線"。

::: moniker-end

- 從**解決方案資源管理器**

  將規則的嚴重性設置為 **"無**"。

- 從**規則集編輯器**

  取消選中其名稱旁邊的框或將 **"操作"** 設置為 **"無**"。

- 從**代碼編輯器**

  將游標放在有衝突的程式碼中，然後按**Ctrl**+**週期 （.）** 打開 **"快速操作"** 功能表。 在 **"源/在抑制檔"中選擇****"抑制 CAXXXX"。**  > 

  ![從快速操作功能表中抑制診斷](media/suppress-diagnostic-from-editor.png)

- 從**錯誤清單中**

  選擇要禁止禁止的規則，然後按右鍵並選擇 **"在** > **源/抑制檔中"的"抑制"。**

  - 如果禁止在**源中**，則"**預覽更改"** 對話方塊將打開並顯示添加到原始程式碼的 C# [#pragma警告](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)或可視基本[#Disable警告](/dotnet/visual-basic/language-reference/directives/directives)指令的預覽。

    ![在代碼檔中添加#pragma警告的預覽](media/pragma-warning-preview.png)

  - 如果選擇 **"在禁止禁止檔"，** 則"**預覽更改"** 對話方塊將打開並<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>顯示添加到全域抑制檔中的屬性的預覽。

    ![將禁止抑制消息屬性添加到抑制檔的預覽](media/preview-changes-in-suppression-file.png)

  在 **"預覽更改"** 對話方塊中，選擇 **"應用**"。

  > [!NOTE]
  > 如果在**解決方案資源管理器**中看不到 **"抑制**"功能表選項，則衝突可能來自生成而不是即時分析。 **"錯誤清單**"顯示即時代碼分析和生成中的診斷或規則衝突。 由於生成診斷可能過時，例如，如果您已編輯代碼以修復衝突但尚未重新生成，則無法從**錯誤清單**中禁止這些診斷。 來自即時分析（IntelliSense）的診斷始終與當前源處於最新狀態，可以從**錯誤清單中**進行抑制。 要從所選內容中排除*生成*診斷，請將"**僅生成 + IntelliSense"** 的錯誤**清單**源篩選器切換到 **"僅 IntelliSense"。** 然後，選擇要禁止的診斷並繼續，如前面所述。
  >
  > ![視覺化工作室中的錯誤清單源篩選器](media/error-list-filter.png)

## <a name="command-line-usage"></a>命令列使用

在命令列生成專案時，如果滿足以下條件，則生成輸出中將顯示規則衝突：

- 分析儀作為 NuGet 包安裝，而不是 VSIX 擴展。

- 專案代碼中違反了一個或多個規則。

- 違反規則[的嚴重性](#rule-severity)設置為**警告**，在這種情況下，衝突不會導致生成失敗，或者**錯誤**，在這種情況下，衝突會導致生成失敗。

生成輸出的詳細程度不會影響是否顯示規則衝突。 即使**具有安靜的**詳細程度，規則衝突也會出現在生成輸出中。

> [!TIP]
> 如果您習慣于從命令列運行舊版分析，或者使用*FxCopd.exe*或通過 msbuild 使用**RunCodeAnalysis**標誌，下面介紹如何使用代碼分析器執行此操作。

要在使用 msbuild 生成專案時在命令列看到分析器衝突，請運行如下所示的命令：

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

下圖顯示了生成包含分析器規則衝突的專案的命令列生成輸出：

![包含違規的 MSBuild 輸出](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>從屬專案

在 .NET Core 專案中，如果向具有 NuGet 分析器的專案增加參考，則這些分析器也會自動添加到從屬專案中。 要禁用此行為，例如，如果從屬專案是單元測試專案，請通過設置私有資產屬性，將 NuGet 包標記為引用專案的 *.csproj*或 *.vbproj*檔中的**私有：**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>另請參閱

- [視覺化工作室中的代碼分析器概述](../code-quality/roslyn-analyzers-overview.md)
- [提交代碼分析器錯誤](https://github.com/dotnet/roslyn-analyzers/issues)
- [使用規則集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [禁止代碼分析警告](../code-quality/in-source-suppression-overview.md)

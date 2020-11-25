---
title: 分析器設定
ms.date: 09/02/2020
description: 瞭解如何自訂 Roslyn 分析器規則。 瞭解如何調整分析器嚴重性、隱藏違規，以及將檔案指定為產生的程式碼。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f5ca27d44e611ab3b541dfb5992ef37d230513c3
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040637"
---
# <a name="overview"></a>概觀

每個 Roslyn 分析器 *診斷* 或規則都有預設的嚴重性和隱藏狀態，可針對您的專案進行覆寫和自訂。 本文涵蓋設定分析器嚴重性和抑制分析器違規。

## <a name="configure-severity-levels"></a>設定嚴重性層級

::: moniker range=">=vs-2019"

從 Visual Studio 2019 版本16.3 開始，您可以在 [EditorConfig](#set-rule-severity-in-an-editorconfig-file)檔中設定分析器規則或 *診斷* 的嚴重性，從燈泡 [功能表](#set-rule-severity-from-the-light-bulb-menu)和從 [錯誤清單]。

::: moniker-end

::: moniker range="vs-2017"

如果您將分析器 [安裝](../code-quality/install-roslyn-analyzers.md)為 NuGet 套件，您可以設定分析器規則或 *診斷* 的嚴重性。 您可以 [從方案總管](#set-rule-severity-from-solution-explorer) 或 [在規則集檔案中](#set-rule-severity-in-the-rule-set-file)變更規則的嚴重性。

::: moniker-end

下表顯示不同的嚴重性選項：

| 嚴重性 (方案總管)  | 嚴重性 (EditorConfig 檔)  | 組建階段行為 | 編輯器行為 |
|-|-|-|
| 錯誤 | `error` | 違規在錯誤清單和命令列組建輸出中會顯示為 *錯誤* ，導致組建失敗。| 有問題的程式碼會以紅色波浪線加上底線，並在捲軸中以小紅色方塊標記。 |
| 警告 | `warning` | 違規在錯誤清單和命令列組建輸出中會顯示為 *警告* ，但不會造成組建失敗。 | 有問題的程式碼會以綠色波浪線加上底線，並在捲軸中以小綠色方塊標記。 |
| Info | `suggestion` | 違規會以 *訊息* 形式出現在錯誤清單中，而不是在命令列組建輸出中。 | 有問題的程式碼會以灰色波浪線加上底線，並在捲軸中以小灰色方塊標記。 |
| Hidden | `silent` | 使用者看不到。 | 使用者看不到。 不過，診斷會回報給 IDE 診斷引擎。 |
| None | `none` | 已完全隱藏。 | 已完全隱藏。 |
| 預設 | `default` | 對應于規則的預設嚴重性。 若要判斷規則的預設值為何，請查看屬性視窗。 | 對應于規則的預設嚴重性。 |

如果分析器發現規則違規，就會在 [程式碼編輯器] 中回報它們， (在違規程序代碼) 和 [錯誤清單] 視窗中的 *波浪* 線。

錯誤清單中報告的分析器違規符合規則的 [嚴重性層級設定](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) 。 分析器違規也會在程式碼編輯器中顯示為違規程序代碼底下的波浪線。 下圖顯示三個 &mdash; 錯誤 (紅色波浪線) 、一個警告 (綠色波浪線) ，以及一個建議 (三個灰色的點) ：

![Visual Studio 中的程式碼編輯器中的波浪線](media/diagnostics-severity-colors.png)

下列螢幕擷取畫面顯示出現在 [錯誤清單] 中的三個違規：

![錯誤清單中的錯誤、警告和資訊違規](media/diagnostics-severities-in-error-list.png)

許多分析器規則或 *診斷* 都有一或多個相關聯的程式 *代碼修正* ，可套用以修正規則違規。 程式碼修正會顯示在燈泡圖示功能表中，並顯示其他類型的[快速動作](../ide/quick-actions.md)。 如需這些程式碼修正的資訊，請參閱[一般的快速動作](../ide/quick-actions.md)。

![分析器違規和快速動作程式碼修正](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>「隱藏」嚴重性與「無」嚴重性

`Hidden` 依預設啟用的嚴重性規則，與停用或 `None` 嚴重性規則有幾種不同之處。

- 如果已針對嚴重性規則註冊任何程式碼修正 `Hidden` ，則會在 Visual Studio 中以燈泡程式碼重構動作的形式提供修正程式，即使使用者看不到隱藏的診斷也是一樣。 這不是停用的 `None` 嚴重性規則的情況。
- `Hidden` 您可以透過 [在 EditorConfig 檔中一次設定多個分析器規則的規則嚴重性](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file)的專案來大量設定嚴重性規則。 `None` 無法以這種方式設定嚴重性規則。 相反地，它們必須透過 [針對每個規則識別碼在 EditorConfig 檔中設定規則嚴重性](#set-rule-severity-in-an-editorconfig-file)的專案來設定。

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>在 EditorConfig 檔案中設定規則嚴重性

 (Visual Studio 2019 16.3 版和更新版本) 

您可以使用下列語法，在 EditorConfig 檔中設定編譯器警告或分析器規則的嚴重性：

`dotnet_diagnostic.<rule ID>.severity = <severity>`

在 EditorConfig 檔案中設定規則的嚴重性優先于規則集或方案總管中設定的任何嚴重性。 您可以 [手動](#manually-configure-rule-severity-in-an-editorconfig-file) 設定 EditorConfig 檔中的嚴重性，或 [自動](#set-rule-severity-from-the-light-bulb-menu) 完成違規旁邊出現的燈泡。

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>在 EditorConfig 檔案中一次設定多個分析器規則的規則嚴重性

 (Visual Studio 2019 16.5 版和更新版本) 

您可以使用 EditorConfig 檔中的單一專案，為分析器規則或所有分析器規則的特定類別設定嚴重性。

- 設定分析器規則類別的規則嚴重性：

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- 設定所有分析器規則的規則嚴重性：

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> 一次設定多個分析器規則的專案只適用于 *預設啟用* 的規則。 分析器封裝中預設標示為停用的分析器規則必須透過明確的 `dotnet_diagnostic.<rule ID>.severity = <severity>` 專案啟用。

如果您有多個適用于特定規則識別碼的專案，以下是選擇適用專案的優先順序：

- 個別規則依識別碼的嚴重性專案優先于類別的嚴重性專案。
- 類別的嚴重性專案優先于所有分析器規則的嚴重性專案。

請考慮下列 EditorConfig 範例，其中 [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) 具有「效能」類別：

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

在上述範例中，這三個專案都適用于 CA1822。 不過，使用指定的優先順序規則時，第一個以規則識別碼為基礎的嚴重性專案優先于下一個專案。 在此範例中，CA1822 會有「錯誤」的有效嚴重性。 所有具有「效能」類別的其餘規則都會有「警告」的嚴重性。 所有其餘的分析器規則（沒有「效能」類別）都會有「建議」的嚴重性。

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>在 EditorConfig 檔案中手動設定規則嚴重性

1. 如果您的專案尚未有 EditorConfig 檔案，請 [新增一個](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)。

2. 針對您想要在對應的副檔名下設定的每個規則，新增專案。 例如，若要為 c # 檔案設定 [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) 的嚴重性 `error` ，此專案看起來如下：

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> 針對 IDE 程式碼樣式分析器，您也可以使用不同的語法在 EditorConfig 檔中設定它們，例如 `dotnet_style_qualification_for_field = false:suggestion` 。 但是，如果您使用語法設定嚴重性 `dotnet_diagnostic` ，則會優先使用。 如需詳細資訊，請參閱 [EditorConfig 的語言慣例](/dotnet/fundamentals/code-analysis/style-rules/language-rules)。

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>從燈泡功能表設定規則嚴重性

Visual Studio 提供一個便利的方式，從 [ [快速動作](../ide/quick-actions.md) ] 燈泡功能表設定規則的嚴重性。

1. 違規發生之後，將滑鼠停留在編輯器的違規波浪線上，然後開啟燈泡功能表。 或者，將游標放在這一行，然後按下 **Ctrl** + **。** (句點)。

2. 從燈泡功能表中，選取 [ **設定或隱藏問題** > **設定 \<rule ID> 嚴重性**]。

   ![從 Visual Studio 中的燈泡功能表設定規則嚴重性](media/configure-rule-severity.png)

3. 從該處選擇其中一個嚴重性選項。

   ![將規則嚴重性設定為建議](media/configure-rule-severity-suggestion.png)

   Visual Studio 將專案新增至 EditorConfig 檔案，以將規則設定為要求的層級，如預覽方塊中所示。

   > [!TIP]
   > 如果專案中還沒有 EditorConfig 檔案，Visual Studio 為您建立一個檔案。

### <a name="set-rule-severity-from-the-error-list-window"></a>從 [錯誤清單] 視窗設定規則嚴重性

Visual Studio 也提供方便的方式，從 [錯誤清單] 內容功能表設定規則的嚴重性。

1. 違規發生之後，以滑鼠右鍵按一下 [錯誤清單] 中的診斷專案。

2. 從內容功能表中，選取 [ **設定嚴重性**]。

   ![在 Visual Studio 中從錯誤清單設定規則嚴重性](media/configure-rule-severity-error-list.png)

3. 從該處選擇其中一個嚴重性選項。

   Visual Studio 將專案新增至 EditorConfig 檔案，以將規則設定為要求的層級。

   > [!TIP]
   > 如果專案中還沒有 EditorConfig 檔案，Visual Studio 為您建立一個檔案。

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>從方案總管設定規則嚴重性

您可以從 **方案總管** 進行大部分的分析器診斷自訂。 如果您 [將分析器安裝](../code-quality/install-roslyn-analyzers.md)為 NuGet 封裝，**分析器** 節點會出現在 **方案總管** 的 [**參考**] 或 [相依性 **]** 節點底下。 如果您展開 [ **分析器**]，然後展開其中一個分析器元件，則會在元件中看到所有診斷。

![方案總管中的分析器節點](media/analyzers-expanded-in-solution-explorer.png)

您可以在 [ **屬性** ] 視窗中，查看診斷的屬性，包括其描述和預設嚴重性。 若要查看屬性，請以滑鼠右鍵按一下規則，然後選取 [**屬性**]，或選取規則，然後按下 **Alt** + **enter**。

![屬性視窗中的診斷屬性](media/analyzer-diagnostic-properties.png)

若要查看診斷的線上檔，請以滑鼠右鍵按一下診斷，然後選取 [ **View Help**]。

**方案總管** 中每個診斷旁邊的圖示，會對應至您在編輯器中開啟它時，在規則集中看到的圖示：

- 圓形中的 "x" 表示 **錯誤** 的 [嚴重性](#configure-severity-levels)
- 三角形中的 "！" 表示 **警告** 的 [嚴重性](#configure-severity-levels)
- 圓形中的 "i" 表示 **資訊** 的 [嚴重性](#configure-severity-levels)
- 亮色背景上圓形中的 "i" 表示 [嚴重性](#configure-severity-levels) 為 **隱藏**
- 圓形中的向下箭號表示已隱藏診斷

![方案總管中的診斷圖示](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>將現有的規則集檔案轉換成 EditorConfig 檔案

從 Visual Studio 2019 16.5 版開始，規則集檔案已被取代為 managed 程式碼的分析器設定 EditorConfig 檔。 大部分適用于分析器的 Visual Studio 工具規則嚴重性設定都已更新為可在 EditorConfig 檔案上運作，而不是在規則集檔案上運作。 EditorConfig 檔案可讓您設定分析器規則嚴重性和分析器選項，包括 Visual Studio IDE 程式碼樣式選項。 強烈建議您將現有的規則集檔案轉換成 EditorConfig 檔案。 此外，也建議您將 EditorConfig 檔案儲存在存放庫的根目錄或方案資料夾中。 您可以使用存放庫或方案資料夾的根目錄，確定此檔案的嚴重性設定會分別自動套用至整個存放庫或解決方案。

有幾種方式可將現有的規則集檔案轉換成 EditorConfig 檔案：

- 從 Visual Studio 中的規則集編輯器 (需要 Visual Studio 2019 16.5 或更新版本) 。 如果您的專案已使用特定的規則集檔案作為其 `CodeAnalysisRuleSet` ，您可以從 Visual Studio 內的規則集編輯器將它轉換成同等的 EditorConfig 檔。

    1. 按兩下方案總管中的規則集檔案。

       規則集檔案應該會在規則集編輯器中開啟。 您應該會在規則集編輯器頂端看到可點擊的 **資訊** 列。

       ![將規則集轉換為規則集編輯器中的 EditorConfig 檔案](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. 選取 [ **資訊** 列] 連結。

       這應該會開啟 [ **另存** 新檔] 對話方塊，讓您選取要產生 EditorConfig 檔案的目錄。

    3. 選取 [ **儲存** ] 按鈕以產生 EditorConfig 檔案。

       產生的 EditorConfig 應該會在編輯器中開啟。 此外，MSBuild 屬性 `CodeAnalysisRuleSet` 會在專案檔中更新，使其不再參考原始的規則集檔案。

- 從命令列：

    1. 安裝 NuGet 套件 [CodeAnalysis. RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter)。

    2. `RulesetToEditorconfigConverter.exe`從已安裝的套件執行，並以規則集檔案和 EditorConfig 檔案的路徑作為命令列引數。

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

以下是要轉換的範例規則集檔案：

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

以下是已轉換的 EditorConfig 檔案：

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
::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>從方案總管設定規則嚴重性

1. 在方案總管中，展開 [**參考**  >  **分析器** **]** (或 [  >  .net Core 專案的相依性 **分析器**]) 。

2. 展開包含您要為其設定嚴重性之規則的元件。

::: moniker range=">=vs-2019"
3. 以滑鼠右鍵按一下規則，然後選取 [ **設定嚴重性**]。 在內容功能表中，選擇其中一個嚴重性選項。

   Visual Studio 將專案新增至 EditorConfig 檔案，以將規則設定為要求的層級。 如果您的專案使用規則集檔案，而不是 EditorConfig 檔案，則會將嚴重性專案加入至規則集檔案。

   > [!TIP]
   > 如果專案中還沒有 EditorConfig 檔案或規則集檔案，Visual Studio 為您建立新的 EditorConfig 檔案。
::: moniker-end

::: moniker range="vs-2017"
3. 以滑鼠右鍵按一下規則，然後選取 [ **設定規則集嚴重性**]。 在內容功能表中，選擇其中一個嚴重性選項。

   規則的嚴重性會儲存在使用中的規則集檔案中。
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>設定規則集檔案中的規則嚴重性

![方案總管中的規則集檔案](media/ruleset-in-solution-explorer.png)

1. 以下列其中一種方式開啟主動規則集檔案：

- 在 **方案總管** 中，按兩下檔案，以滑鼠右鍵按一下 [**參考**  >  **分析器**] 節點，然後選取 [開啟使用中 **規則集**]。
- 在專案的 [程式 **代碼分析** ] 屬性頁上，選取 [ **開啟** ]。

  如果這是您第一次編輯規則集，Visual Studio 建立預設規則集檔案的複本，並將其命名為 *\<projectname> 規則* 集，並將它新增至您的專案。 此自訂規則集也會成為專案的作用中規則集。

   > [!NOTE]
   > .NET Core 和 .NET Standard 專案不支援 **方案總管** 中規則集的功能表命令，例如， **Open Active rule Set**。 若要為 .NET Core 或 .NET Standard 專案指定非預設的規則集，請手動 [將 **CodeAnalysisRuleSet** 屬性加入](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) 至專案檔。 您仍然可以在 Visual Studio 規則集編輯器 UI 的規則集內設定規則。

1. 展開包含的元件，以流覽至規則。

1. 在 [ **動作** ] 資料行中，選取值以開啟下拉式清單，並從清單中選擇所需的嚴重性。

   ![在編輯器中開啟規則集檔案](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>設定產生的程式碼

分析器會在專案中的所有原始程式檔上執行，並在其上報告違規。 不過，這些違規在產生的程式碼檔案上並不實用，例如設計工具產生的程式碼檔案、組建系統所產生的暫時性來源檔案等等。使用者無法手動編輯這些檔案，以及/或不在意在這類工具產生的檔案中修正違規。

根據預設，執行分析器的分析器驅動程式會將具有特定名稱、副檔名或自動產生之檔案標頭的檔案視為產生的程式碼檔案。 例如，以或結尾的檔案名 `.designer.cs` `.generated.cs` 會視為產生的程式碼。 不過，這些啟發學習法可能無法識別使用者原始程式碼中所有自訂產生的程式碼檔案。

從 Visual Studio 2019 16.5 開始，終端使用者可以在 [EditorConfig](https://editorconfig.org/)檔中設定特定檔案和/或資料夾，以視為產生的程式碼。 請遵循下列步驟來新增這類設定：

1. 如果您的專案尚未有 EditorConfig 檔案，請 [新增一個](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)。

2. 新增 `generated_code = true | false` 特定檔案和/或資料夾的專案。 例如，若要將名稱結尾為的所有檔案視為產生的程式 `.MyGenerated.cs` 代碼，則專案會如下所示：

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>隱藏違規

有多種方式可以隱藏規則違規：

::: moniker range=">=vs-2019"

- 在 **EditorConfig** 檔案中

  將嚴重性設定為 `none` ，例如 `dotnet_diagnostic.CA1822.severity = none` 。

- 從 [ **分析** ] 功能表

  選取 [**分析**  >  **組建]，並隱藏** 功能表列上的 [作用中問題]，以隱藏所有目前的違規。 這有時稱為「基準」。

::: moniker-end

::: moniker range="vs-2017"

- 從 [ **分析** ] 功能表

  選取 [**分析**  >  **執行程式碼分析]，並隱藏** 功能表列上的 [作用中問題]，以隱藏所有目前的違規。 這有時稱為「基準」。

::: moniker-end

- 從 **方案總管**

  將規則的嚴重性設定為 [ **無**]。

- 從 **規則集編輯器**

  清除其名稱旁邊的核取方塊，或將 [ **動作** ] 設為 [ **無**]。

- 從程式 **代碼編輯器**

  將游標放在具有違規的程式程式碼中，然後按下 **Ctrl** + **句號 (。 )** 開啟 [**快速動作**] 功能表。 選取 [**隱藏**  >  **來源/在隱藏** 專案檔中的 CAXXXX]。

  ![從 [快速動作] 功能表隱藏診斷](media/suppress-diagnostic-from-editor.png)

- 從 **錯誤清單**

  選取您要隱藏的規則，然後以滑鼠右鍵按一下並選取 [ **Suppress**  >  **在來源/隱藏隱藏** 專案檔中隱藏]。

  - 如果您 **在 [來源] 中** 隱藏，[ **預覽變更** ] 對話方塊隨即開啟，並顯示已新增至原始程式碼的 c # [#pragma 警告](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) 或 Visual Basic [#Disable 警告](/dotnet/visual-basic/language-reference/directives/directives) 指示詞的預覽。

    ![在程式碼檔案中新增 #pragma 警告的預覽](media/pragma-warning-preview.png)

  - 如果您選取 [ **在隱藏** 專案檔中]，[ **預覽變更** ] 對話方塊隨即開啟，並顯示 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 已新增至全域隱藏專案檔的屬性預覽。

    ![將 SuppressMessage 屬性新增至隱藏專案檔的預覽](media/preview-changes-in-suppression-file.png)

  在 [ **預覽變更** ] 對話方塊中 **，選取 [** 套用]。

  > [!NOTE]
  > 如果您在 **方案總管** 中看不到 [**隱藏**] 功能表選項，則可能是來自組建而不是即時分析的違規。 **錯誤清單** 會顯示即時程式碼分析和組建中的診斷或規則違規。 由於組建診斷可能會過時，例如，如果您已編輯程式碼來修正違規，但尚未重建，則無法從 **錯誤清單** 中隱藏這些診斷。 從即時分析或 IntelliSense 進行的診斷一律會以最新的來源為最新狀態，而且可以從 **錯誤清單** 中隱藏。 若要從您的選取範圍中排除 *組建* 診斷，請將 **錯誤清單** 來源篩選器從 **Build + Intellisense** 改為 **僅限 intellisense**。 然後，選取您要隱藏的診斷，並依照先前的說明進行。
  >
  > ![Visual Studio 中的錯誤清單來源篩選](media/error-list-filter.png)

## <a name="command-line-usage"></a>命令列使用方式

當您在命令列中建立專案時，如果符合下列條件，則會在組建輸出中出現規則違規：

- 分析器會安裝為 NuGet 套件，而不是 VSIX 擴充功能。

- 專案的程式碼中違反了一或多個規則。

- 違反規則的 [嚴重性](#configure-severity-levels) 設定為 [ **警告**]，在這種情況下，違規不會造成組建失敗或 **錯誤**，在此情況下，違規會導致組建失敗。

組建輸出的詳細資訊不會影響是否顯示規則違規。 即使有 **無** 訊息詳細程度，規則違規也會出現在組建輸出中。

> [!TIP]
> 如果您習慣從命令列執行舊版分析，不論是使用 *FxCopCmd.exe* 或透過 Msbuild 搭配 **>runcodeanalysis** 旗標，以下就是使用程式碼分析器來執行這項作業的方法。

當您使用 msbuild 建立專案時，若要在命令列中看到分析器違規，請執行如下的命令：

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

下圖顯示建立包含分析器規則違規之專案的命令列組建輸出：

![包含違規的 MSBuild 輸出](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>相依專案

在 .NET Core 專案中，如果您加入具有 NuGet 分析器之專案的參考，則也會自動將這些分析器新增至相依專案。 若要停用此行為，例如，如果相依專案是單元測試專案，請藉由設定 **PrivateAssets** 屬性，將 NuGet 套件標記為所參考專案的 *.csproj* 或 *vbproj* 檔案中的私用套件：

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼分析器總覽](../code-quality/roslyn-analyzers-overview.md)
- [提交程式碼分析器 bug](https://github.com/dotnet/roslyn-analyzers/issues)
- [使用規則集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [隱藏程式碼分析警告](../code-quality/in-source-suppression-overview.md)
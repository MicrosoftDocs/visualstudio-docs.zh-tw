---
title: 分析器規則嚴重性和隱藏專案
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6362d3f14065aaf9661e85266753642e4201ca48
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548033"
---
# <a name="use-code-analyzers"></a>使用程式碼分析器

.NET Compiler Platform ("Roslyn") 程式碼分析器會C#在您輸入時分析或 Visual Basic 程式碼。 每個*診斷*或規則都有預設的 [嚴重性] 和 [隱藏] 狀態, 可以針對您的專案覆寫。 本文涵蓋設定規則嚴重性、使用規則集, 以及隱藏違規。

## <a name="analyzers-in-solution-explorer"></a>方案總管中的分析器

您可以從**方案總管**進行大部分的分析器診斷自訂。 如果您將[分析器安裝](../code-quality/install-roslyn-analyzers.md)為 NuGet 套件, [**分析器**] 節點會出現在**方案總管**的 [**參考**] 或 [相依性 **]** 節點底下。 如果您展開 [**分析器**], 然後展開其中一個分析器元件, 您會在元件中看到所有診斷。

![方案總管中的分析器節點](media/analyzers-expanded-in-solution-explorer.png)

您可以在 [**屬性**] 視窗中, 查看診斷的屬性, 包括其描述和預設嚴重性。 若要查看屬性, 請以滑鼠右鍵按一下規則並選取 [**屬性**], 或選取規則, 然後按下**Alt** + **enter**。

![屬性視窗中的診斷屬性](media/analyzer-diagnostic-properties.png)

若要查看診斷的線上檔, 請以滑鼠右鍵按一下 [診斷], 然後選取 [ **View Help**]。

**方案總管**中的每個診斷旁邊的圖示會對應至您在編輯器中開啟時, 在規則集內看到的圖示:

- 圓圈中的 "i" 表示**資訊**的[嚴重性](#rule-severity)
- 三角形中的 "!" 表示[嚴重性](#rule-severity)**警告**
- 圓圈中的 "x" 表示**錯誤**的[嚴重性](#rule-severity)
- 淺彩色背景上圓形中的 "i" 表示[嚴重性](#rule-severity)為**隱藏**
- 圓圈中的向下箭號表示診斷已隱藏

![方案總管中的診斷圖示](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>規則集

[規則集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)是一個 XML 檔案, 可儲存個別診斷的嚴重性和隱藏狀態。

> [!NOTE]
> 規則集可以包含舊版分析和程式碼分析器的規則。

若要在 [規則集編輯器] 中編輯作用中的規則集, 請以滑鼠右鍵按一下**方案總管**中的 [**參考** > **分析器**] 節點, 然後選取 [**開啟 active rule set**]。 如果這是您第一次編輯規則集, Visual Studio 會建立預設規則集檔案的複本, 並將其 *\<* 命名為專案名稱 >。 此自訂規則集也會成為專案的作用中規則集。

若要變更專案的作用中規則集, 請流覽至專案屬性的 [程式**代碼分析**] 索引標籤。 從 [**執行此規則集**] 底下的清單中選取規則集。 若要開啟規則集, 請選取 [**開啟**]。

> [!NOTE]
> .NET Core 和 .NET Standard 專案不支援**方案總管**中規則集的功能表命令, 例如,**開啟 Active rule Set**。 若要為 .NET Core 或 .NET Standard 專案指定非預設的規則集, 請以手動方式[將**CodeAnalysisRuleSet**屬性新增](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project)至專案檔。 您仍然可以在 Visual Studio 規則集編輯器 UI 中的規則集內設定規則。

## <a name="rule-severity"></a>規則嚴重性

如果您將分析器[安裝](../code-quality/install-roslyn-analyzers.md)為 NuGet 套件, 您可以設定分析器規則或*診斷*的嚴重性。 下表顯示診斷的嚴重性選項:

|Severity|組建時間行為|編輯器行為|
|-|-|-|
|Error|違規在**錯誤清單**和命令列組建輸出中會顯示為*錯誤*, 並導致組建失敗。|有問題的程式碼會加上紅色波浪線, 並在捲軸中以小紅色方塊標示。|
|警告|違規在**錯誤清單**和命令列組建輸出中會顯示為*警告*, 但不會導致組建失敗。|有問題的程式碼會加上綠色的彎曲, 並以捲軸中的小綠色方塊標示。|
|資訊|違規會在**錯誤清單**中顯示為*訊息*, 而不是在命令列組建輸出中。|有問題的程式碼會加上灰色的彎曲, 並以捲軸中的小型灰色方塊標示。|
|Hidden|使用者看不到。|使用者看不到。 不過, 診斷會回報給 IDE 診斷引擎。|
|無|已完全隱藏。|已完全隱藏。|

此外, 您可以將規則設定為**預設值**, 以「重設」其嚴重性。 每個診斷都有預設的嚴重性, 可在 [**屬性**] 視窗中看到。

下列螢幕擷取畫面顯示 [程式碼編輯器] 中的三個不同的診斷違規, 其中包含三個不同的嚴重性。 請注意曲線的色彩, 以及右側捲軸中的小方塊。

![程式碼編輯器中的錯誤、警告和資訊違規](media/diagnostics-severity-colors.png)

下列螢幕擷取畫面顯示出現在**錯誤清單**中的三個違規:

![錯誤清單中的錯誤、警告和資訊違規](media/diagnostics-severities-in-error-list.png)

在**方案總管**中變更規則的嚴重性之後, 您可以從**方案總管**或在 *\<專案名稱 >. 規則集*檔案中變更規則的嚴重性。

![方案總管中的規則集檔案](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>從方案總管設定規則嚴重性

1. 在**方案總管**中, 展開 [**參考** > **分析器**(.net Core 專案的相依性**分析器**) **]**  > 。

1. 展開包含您要為其設定嚴重性之規則的元件。

1. 以滑鼠右鍵按一下規則, 然後選取 [**設定規則集嚴重性**]。 在飛出功能表中, 選取其中一個 [嚴重性] 選項。

   規則的嚴重性會儲存在作用中的規則集檔案中。

### <a name="set-rule-severity-in-the-rule-set-file"></a>在規則集檔案中設定規則嚴重性

1. 在**方案總管**中按兩下[規則集](analyzer-rule-sets.md)檔案, 在 [**分析器**] 節點的右鍵功能表上選取 [開啟作用中**規則集**], 或選取 [程式**代碼分析**] 屬性頁上的 [**開啟**] 來開啟專案。

1. 藉由展開其包含的元件來流覽至規則。

1. 在 [**動作**] 資料行中, 選取值以開啟下拉式清單, 並從清單中選取所需的嚴重性。

   ![規則集檔案在編輯器中開啟](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>隱藏違規

有多種方式可以抑制規則違規:

- 從 [**分析**] 功能表

  選取 [**分析** > ] [**執行程式碼分析] 並隱藏**功能表列上的 [作用中問題], 以隱藏所有目前的違規 這有時稱為「基準化」。

- 從**方案總管**

  若要抑制**方案總管**中的違規, 請將規則的嚴重性設定為 [**無**]。

- 從**規則集編輯器**

  若要隱藏 [規則集編輯器] 中的違規, 請取消核取其名稱旁的方塊, 或將 [**動作**] 設為 [**無**]。

- 從程式**代碼編輯器**

  若要隱藏程式碼編輯器中的違規, 請將游標放在含有違規的程式程式碼中, 然後按**Ctrl** + **。** 開啟 [**快速動作**] 功能表。 選取 [隱藏**來源/** 隱藏專案檔中的**CAXXXX**  > ]。

  ![隱藏 [快速動作] 功能表中的診斷](media/suppress-diagnostic-from-editor.png)

- 從**錯誤清單**

  您可以從**錯誤清單**中隱藏一或多個診斷, 方法是選取您要隱藏的診斷, 然後以滑鼠右鍵按一下並選取 [**在隱藏**專案檔中**隱藏** > ]。

  - 如果您**在 [來源] 中**隱藏, [**預覽變更**] 對話方塊隨即開啟, C#並顯示已新增至原始程式碼的[#pragma 警告](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)或 Visual Basic [#Disable 警告](/dotnet/visual-basic/language-reference/directives/directives)指示詞的預覽。

    ![在程式碼檔案中新增 #pragma 警告的預覽](media/pragma-warning-preview.png)

  - 如果您選取 [**在隱藏**專案檔中], [**預覽變更**] 對話方塊隨即開啟<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> , 並顯示已新增至全域隱藏專案檔案的屬性預覽。

    ![將 SuppressMessage 屬性新增至隱藏專案檔案的預覽](media/preview-changes-in-suppression-file.png)

  在 [**預覽變更**] 對話方塊中, 選取 [套用]。

  > [!NOTE]
  > 如果**方案總管**中沒有看到 [**隱藏**] 功能表選項, 則違規可能來自組建而非即時分析。 **錯誤清單**會顯示即時程式碼分析和組建中的診斷或規則違規。 由於組建診斷可能過時, 例如, 如果您已編輯程式碼來修正違規, 但尚未重建, 則無法從**錯誤清單**中隱藏這些診斷。 即時分析或 IntelliSense 的診斷一律會與目前的來源保持最新狀態, 而且可以從**錯誤清單**中隱藏。 若要從您的選取範圍中排除*組建*診斷, 請將**錯誤清單**來源篩選器從**Build + Intellisense**切換為**僅限 intellisense**。 然後, 選取您想要隱藏的診斷, 並如先前所述繼續進行。
  >
  > ![Visual Studio 中的錯誤清單來源篩選](media/error-list-filter.png)

## <a name="command-line-usage"></a>命令列使用方式

當您在命令列中建立專案時, 如果符合下列條件, 規則違規會出現在組建輸出中:

- 分析器會安裝為 Nuget 套件, 而不是 VSIX 延伸模組。

- 專案的程式碼違反了一或多個規則。

- 違反之規則的[嚴重性](#rule-severity)設定為 [**警告**], 在此情況下, 違規會導致組建失敗或**發生錯誤**, 在這種情況下, 違規會導致組建失敗。

組建輸出的詳細資訊不會影響是否顯示規則違規。 即使使用**安靜**的詳細資訊, 規則違規也會出現在組建輸出中。

> [!TIP]
> 如果您習慣從命令列執行舊版分析, 不論是使用*fxcopcmd.exe*或透過 Msbuild 與**RunCodeAnalysis**旗標, 都可以使用程式碼分析器來進行。

若要在使用 msbuild 建立專案時, 于命令列查看分析器違規, 請執行如下的命令:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

下圖顯示建立包含分析器規則違規之專案的命令列組建輸出:

![包含違規的 MSBuild 輸出](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>相依專案

在 .NET Core 專案中, 如果您將參考加入具有 NuGet 分析器的專案, 這些分析器也會自動加入至相依專案。 若要停用此行為 (例如, 如果相依專案是單元測試專案), 請藉由設定**PrivateAssets**屬性, 將 NuGet 套件標記為所參考專案之 *.csproj*或*vbproj*檔案中的私用:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼分析器總覽](../code-quality/roslyn-analyzers-overview.md)
- [提交程式碼分析器 bug](https://github.com/dotnet/roslyn-analyzers/issues)
- [使用規則集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [隱藏程式碼分析警告](../code-quality/in-source-suppression-overview.md)

---
title: 安裝 FxCop 分析器
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fec188ba61a7e4d3f27caad03f0a5d32b6758a32
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974999"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>在 Visual Studio 中安裝 FxCop 分析器

Microsoft 建立了一組稱為[CodeAnalysis](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)的分析器，其中包含舊版分析中最重要的 "FxCop" 規則。 這些分析器會檢查您的程式碼中是否有安全性、效能和設計問題，以及其他專案。

您可以將這些 FxCop 分析器安裝為 NuGet 套件或做為 Visual Studio 的 VSIX 擴充功能。 若要深入瞭解各項的優缺點，請參閱 @no__t 0NuGet 套件與VSIX 擴充功能 @ no__t-0。

## <a name="nuget-package"></a>NuGet 套件

您可以直接從專案的 [程式碼分析] [屬性] 頁面安裝[CodeAnalysis FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 套件：

1. 以滑鼠右鍵按一下**方案總管**中的專案節點，選取 [**屬性**]，然後選取 [程式**代碼分析**] 索引標籤。

   ![從 Visual Studio 的屬性頁面安裝 FxCop 分析器套件](media/install-fxcop-properties-page.png)

2. 選取 [安裝]。

   Visual Studio 會安裝最新版本的 CodeAnalyzers. FxCopAnalyzers 套件。 元件會出現在**方案總管**的 [**參考**]  > **分析器**底下。

   ![方案總管中的分析器節點](media/solution-explorer-analyzers-node.png)

### <a name="custom-installation"></a>自訂安裝

針對自訂安裝，例如，若要指定不同版本的封裝，請選取專案的 [程式碼分析] 屬性頁面上的省略號（...）按鈕。 此按鈕會開啟 NuGet 套件管理員，並以 "CodeAnalysis. FxCopAnalyzers" 作為搜尋字串。

![從 Visual Studio 的屬性頁面安裝自訂 FxCop 分析器套件](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> 根據您的 Visual Studio 版本，判斷要安裝[的分析器套件版本](#fxcopanalyzers-package-versions)。 您也可以從[套件管理員 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)安裝套件。

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers 套件版本

使用下列指導方針來決定要針對您的 Visual Studio 版本安裝的 FxCop 分析器套件版本：

| Visual Studio 版本 | FxCop 分析器套件版本 |
| - | - |
| Visual Studio 2019 （所有版本）<br />Visual Studio 2017 15.8 版和更新版本 | [新版](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 版本15.5 至15。7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 版本15.3 至15。4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 版本15.0 至15。2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 update 2 和3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

在 Visual Studio 2017 15.5 版和更新版本上，您可以安裝[Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)延伸模組，其中包含 managed 專案的所有 FxCop 分析器。

1. 在 Visual Studio 中，選取 [**工具**] [>] [**擴充功能和更新**]。

   [擴充功能和更新] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)下載延伸模組。

2. 在左窗格中展開 [**線上**]，然後選取 [ **Visual Studio Marketplace**]。

3. 在搜尋方塊中，輸入「程式碼分析」，然後尋找**Microsoft Code analysis 2017**延伸模組。

   ![Microsoft 程式碼分析2017延伸模組](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)延伸模組包含 managed 專案的所有 FxCop 分析器。 若要安裝此延伸模組：

1. 在 Visual Studio 中，選取 [**擴充**功能 >] [**管理延伸**模組]。

   [**管理延伸**模組] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)下載延伸模組。

2. 在左窗格中展開 [**線上**]，然後選取 [ **Visual Studio Marketplace**]。

3. 在搜尋方塊中，輸入「程式碼分析」，然後尋找**Microsoft Code analysis 2019**延伸模組。

   ![Microsoft 程式碼分析2019延伸模組](media/manage-extensions-code-analysis.png)

::: moniker-end

4. 選取 [**下載**]。

   已下載延伸模組。

5. 選取 **[確定]** 以關閉對話方塊，然後關閉 Visual Studio 的所有實例，以啟動**VSIX 安裝程式**。

   [ **VSIX 安裝程式**] 對話方塊隨即開啟。

   ::: moniker range="vs-2017"

   ![適用于 Microsoft 程式碼分析的 VSIX 安裝程式](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. 選取 [**修改**] 以開始安裝。

   一或兩分鐘後，安裝就會完成。

7. 選取 [**關閉**]，然後再次開啟 [Visual Studio]。

::: moniker range="vs-2017"

如果您想要檢查是否已安裝延伸模組，請選取 [**工具**] [ > ] [**擴充功能和更新**]。 在 [**擴充功能和更新**] 對話方塊中，選取左側的 [**已安裝**] 類別，然後依名稱搜尋延伸模組。

::: moniker-end

::: moniker range=">=vs-2019"

如果您想要檢查是否已安裝延伸模組，請選取 [**擴充**功能  > ] [**管理延伸**模組]。 在 [**管理擴充**功能] 對話方塊中，選取左側的 [**已安裝**] 類別，然後依名稱搜尋延伸模組。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼分析器總覽](../code-quality/roslyn-analyzers-overview.md)
- [在 Visual Studio 中使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)
- [從舊版分析遷移至程式碼分析器](../code-quality/fxcop-analyzers.yml)

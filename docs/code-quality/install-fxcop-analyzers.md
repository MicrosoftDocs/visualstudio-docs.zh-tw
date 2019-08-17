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
ms.openlocfilehash: b5cb0fa5985cbc923713330289d7f83ed1fd954e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551101"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>在 Visual Studio 中安裝 FxCop 分析器

Microsoft 建立了一組稱為[CodeAnalysis](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)的分析器, 其中包含舊版分析中最重要的 "FxCop" 規則。 這些分析器會檢查您的程式碼中是否有安全性、效能和設計問題, 以及其他專案。

您可以將這些 FxCop 分析器安裝為 NuGet 套件或做為 Visual Studio 的 VSIX 擴充功能。 若要深入瞭解各項的優缺點, 請參閱[NuGet 套件與VSIX 延伸](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)模組。

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>將 FxCop 分析器安裝為 NuGet 套件

1. 根據您的 Visual Studio 版本, 判斷要安裝[的分析器套件版本](#fxcopanalyzers-package-versions)。

2. 使用 [[套件管理員主控台](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)] 或 [[套件管理員] UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console), 在 Visual Studio 中安裝套件。

   > [!NOTE]
   > 每個分析器套件的 [nuget.org] 頁面會顯示要貼入**封裝管理員主控台**的命令。 甚至還有一個方便的按鈕, 可將文字複製到剪貼簿。
   >
   > ![顯示套件管理員主控台命令的 NuGet.org 頁面](media/nuget-package-manager-command.png)

   系統會安裝分析器元件, 而且它們會出現在 [**參考** > ]**分析器**下的**方案總管**中。

   ![方案總管中的分析器節點](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers 套件版本

使用下列指導方針來決定要針對您的 Visual Studio 版本安裝的 FxCop 分析器套件版本:

| Visual Studio 版本 | FxCop 分析器套件版本 |
| - | - |
| Visual Studio 2019 (所有版本)<br />Visual Studio 2017 15.8 版和更新版本 | [2.9.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.3) |
| Visual Studio 2017 版本15.5 至15。7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 版本15.3 至15。4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 版本15.0 至15。2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 update 2 和3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>將 FxCop 分析器安裝為 VSIX

::: moniker range="vs-2017"

在 Visual Studio 2017 15.5 版和更新版本上, 您可以安裝[Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)延伸模組, 其中包含 managed 專案的所有 FxCop 分析器。

1. 在 Visual Studio 中, 選取 [**工具** > ] [**擴充功能和更新**]。

   [擴充功能和更新] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者, 直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)下載延伸模組。

2. 在左窗格中展開 [**線上**], 然後選取 [ **Visual Studio Marketplace**]。

3. 在搜尋方塊中, 輸入「程式碼分析」, 然後尋找**Microsoft Code analysis 2017**延伸模組。

   ![Microsoft 程式碼分析2017延伸模組](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)延伸模組包含 managed 專案的所有 FxCop 分析器。 若要安裝此延伸模組:

1. 在 Visual Studio 中, 選取 [**擴充** >功能] [**管理擴充**功能]。

   [**管理延伸**模組] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者, 直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)下載延伸模組。

2. 在左窗格中展開 [**線上**], 然後選取 [ **Visual Studio Marketplace**]。

3. 在搜尋方塊中, 輸入「程式碼分析」, 然後尋找**Microsoft Code analysis 2019**延伸模組。

   ![Microsoft 程式碼分析2019延伸模組](media/manage-extensions-code-analysis.png)

::: moniker-end

4. 選取 [**下載**]。

   已下載延伸模組。

5. 選取 **[確定]** 以關閉對話方塊, 然後關閉 Visual Studio 的所有實例, 以啟動**VSIX 安裝程式**。

   [ **VSIX 安裝程式**] 對話方塊隨即開啟。

   ::: moniker range="vs-2017"

   ![適用于 Microsoft 程式碼分析的 VSIX 安裝程式](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. 選取 [**修改**] 以開始安裝。

   一或兩分鐘後, 安裝就會完成。

7. 選取 [**關閉**], 然後再次開啟 [Visual Studio]。

::: moniker range="vs-2017"

如果您想要檢查是否已安裝延伸模組, 請選取 [**工具** > ] [**擴充功能和更新**]。 在 [**擴充功能和更新**] 對話方塊中, 選取左側的 [**已安裝**] 類別, 然後依名稱搜尋延伸模組。

::: moniker-end

::: moniker range=">=vs-2019"

如果您想要檢查是否已安裝延伸模組, 請選取 [**擴充** > 功能] [**管理延伸**模組]。 在 [**管理擴充**功能] 對話方塊中, 選取左側的 [**已安裝**] 類別, 然後依名稱搜尋延伸模組。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼分析器總覽](../code-quality/roslyn-analyzers-overview.md)
- [在 Visual Studio 中使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)
- [從舊版分析遷移至程式碼分析器](../code-quality/fxcop-analyzers.yml)

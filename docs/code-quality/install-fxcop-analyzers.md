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
ms.openlocfilehash: a8b13e9f5ed76b61279212bfdedf33b25f694221
ms.sourcegitcommit: 4c7a0c2d712eb24609216577a793e912a6083eaf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "57983451"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>在 Visual Studio 中安裝 FxCop 分析器

Microsoft 建立了一組的分析器，稱為[Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)，其中包含靜態程式碼分析，轉換為 Roslyn 分析器的最重要 」 FxCop 」 規則。 這些分析器會檢查您的程式碼的安全性、 效能和設計問題，其他項目。

您可以安裝這些 FxCop 分析器，NuGet 套件的形式，或為 Visual Studio 的 VSIX 擴充功能。 若要深入了解每個優缺點，請參閱[NuGet 封裝 vs。VSIX 擴充功能](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)。

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>若要安裝 NuGet 套件形式的 FxCop 分析器

1. [判斷哪一個分析器套件版本](#fxcopanalyzers-package-versions)安裝，請根據您的 Visual Studio 版本。

2. 在 Visual Studio 中，使用安裝套件[Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)或[套件管理員 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)。

   > [!NOTE]
   > 每個分析器套件的 nuget.org 頁面會顯示貼到命令**Package Manager Console**。 甚至還有一些好用的按鈕，以將文字複製到剪貼簿。
   >
   > ![顯示套件管理員主控台命令的 NuGet.org 頁面](media/nuget-package-manager-command.png)

   安裝分析器組件，以及它們出現在**方案總管**下方**參考** > **分析器**。

   ![在方案總管 中的 分析器 節點](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers 套件版本

您可以使用下列指導方針來判斷哪個版本的 FxCop 分析器套件，以用於您版本的 Visual Studio 安裝：

| Visual Studio 版本 | FxCop 分析器套件版本 |
| - | - |
| Visual Studio 2017 15.5 版和更新版本 | 2.6.3 例如 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3 |
| Visual Studio 2017 15.3 到 15.4 版 | 2.3.0-beta1 例如 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1 |
| Visual Studio 2017 版本 15.0 至 15.2 | 2.0.0-beta2 例如 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2 |
| Visual Studio 2015 update 2 和 3 | 版本 1.2.0-beta2 例如 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2 |
| Visual Studio 2015 Update 1 | 1.1.0 版，例如 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1。 |
| Visual Studio 2015 RTW | 1.0.1 版例如 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1 |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>若要安裝為 VSIX 的 FxCop 分析器

在 Visual Studio 2017 15.5 版和更新版本，您可以安裝[Microsoft 程式碼分析 2017年](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)延伸模組，其中包含所有的 managed 專案的 FxCop 分析器。

::: moniker range="vs-2017"

1. 在 Visual Studio 中，選取**工具** > **擴充功能和更新**。

   [擴充功能和更新] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，下載的擴充功能，直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中，選取**延伸模組** > **管理延伸模組**。

   **管理延伸模組**對話方塊隨即開啟。

   > [!NOTE]
   > 或者，下載的擴充功能，直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)。

::: moniker-end

1. 依序展開**線上**左的窗格中，然後選取**Visual Studio Marketplace**。

1. 在 [搜尋] 方塊中，輸入 「 程式碼分析 」，然後尋找**Microsoft 程式碼分析 2017年**延伸模組。

   ![Microsoft 程式碼分析延伸模組](media/extensions-and-updates-code-analysis.png)

1. 選取 **下載**。

   下載擴充功能。

1. 選取  **確定**以關閉對話方塊，然後關閉 Visual Studio 啟動的所有執行個體**VSIX 安裝程式**。

   **VSIX 安裝程式**對話方塊隨即開啟。

   ![Microsoft 程式碼分析的 VSIX 安裝程式](media/vsix-installer-code-analysis.png)

1. 選取 **修改**開始安裝。

1. 一或兩分鐘，安裝完成之後。 選取 [關閉] 。

1. 重新開啟 Visual Studio。

::: moniker range="vs-2017"

如果您想要檢查擴充功能是否已安裝，請選取**工具** > **擴充功能和更新**。 在**擴充功能和更新**對話方塊中，選取**已安裝**在左側的類別目錄，然後依名稱搜尋延伸模組。

::: moniker-end

::: moniker range=">=vs-2019"

如果您想要檢查擴充功能是否已安裝，請選取**延伸模組** > **管理延伸模組**。 在**管理延伸模組**對話方塊中，選取**已安裝**在左側的類別目錄，然後依名稱搜尋延伸模組。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的 Roslyn 分析器的概觀](../code-quality/roslyn-analyzers-overview.md)
- [在 Visual Studio 中使用 Roslyn 分析器](../code-quality/use-roslyn-analyzers.md)
- [從 FxCop 移轉至 Roslyn 分析器](../code-quality/fxcop-analyzers.yml)
---
title: 安裝 FxCop 分析器
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508767"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>在視覺工作室安裝 FxCop 分析儀

微軟創建了一套分析器，稱為[微軟.CodeAnalysis.FxCopAnalyzers，](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)其中包含傳統分析中最重要的"FxCop"規則。 這些分析器檢查代碼的安全性、性能和設計問題等。

您可以將這些 FxCop 分析器作為 NuGet 套裝軟體安裝，也可以作為 Visual Studio 的 VSIX 副檔名安裝。 要瞭解每個的優缺點，請參閱[NuGet 包與 VSIX 擴展](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)。

## <a name="nuget-package"></a>Nuget 套件

::: moniker range=">=vs-2019"

在 Visual Studio 2019 版本 16.3 及更高版本中，您可以直接從專案的代碼分析屬性頁面安裝[Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 包：

1. 按右鍵**解決方案資源管理器**中的專案節點，選擇 **"屬性**"，然後選擇 **"代碼分析**"選項卡。

   ![從 Visual Studio 中的屬性頁面安裝 FxCop 分析儀包](media/install-fxcop-properties-page.png)

2. 選取 [安裝]****。

   Visual Studio 安裝最新版本的 Microsoft.CodeAnalysis.FxCopAnalyzers 套裝軟體。 程式集顯示在**參考** > **分析器**下**的解決方案資源管理器**中。

   ![解決方案資源管理器中的分析器節點](media/solution-explorer-analyzers-node.png)

如果您使用的是舊版本的 Visual Studio 2019，請使用[包管理器主控台](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)或[包管理器 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)安裝包。

::: moniker-end

::: moniker range="vs-2017"

1. 根據您的 Visual Studio 版本確定要安裝[的分析器包版本](#fxcopanalyzers-package-versions)。

2. 使用[包管理器主控台](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)或[包管理器 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)在 Visual Studio 中安裝包。

   > [!NOTE]
   > 每個分析器包的nuget.org頁顯示要粘貼到**包管理器主控台**的命令。 甚至還有一個方便的按鈕來將文本複製到剪貼簿。
   >
   > ![顯示包管理器主控台命令的NuGet.org頁](media/nuget-package-manager-command.png)

   安裝分析器程式集，它們顯示在**參考**>**分析器**下**的解決方案資源管理器**中。

::: moniker-end

### <a name="custom-installation"></a>自訂安裝

對於自訂安裝（例如，要指定包的不同版本），請選擇專案代碼分析屬性頁上的省略號 （...） 按鈕。 此按鈕打開 NuGet 包管理器，其中"Microsoft.CodeAnalysis.FxCopAnalyzers"作為搜索字串。

![從 Visual Studio 中的屬性頁面安裝自訂 FxCop 分析儀包](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> 根據您的 Visual Studio 版本確定要安裝[的分析器包版本](#fxcopanalyzers-package-versions)。 您還可以從[包管理器 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)安裝包。

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzer 套裝軟體版本

使用以下準則確定要為 Visual Studio 版本安裝哪個版本的 FxCop 分析器包：

| Visual Studio 版本 | FxCop 分析儀包版本 |
| - | - |
| 視覺工作室 2019 （所有版本）<br />視覺工作室 2017 版本 15.8 及更高版本 | [最新](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| 視覺工作室 2017 版本 15.5 到 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| 視覺工作室 2017 版本 15.3 到 15.4 | [2.3.0-貝塔1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 版本 15.0 到 15.2 | [2.0.0-貝塔2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| 視覺工作室 2015 更新 2 和 3 | [1.2.0-貝塔2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

在 Visual Studio 2017 版本 15.5 及更高版本上，您可以安裝[Microsoft 代碼分析 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)擴展，其中包含託管專案的所有 FxCop 分析器。

1. 在視覺化工作室中，選擇 **"工具**>**擴展和更新**"。

   [擴充功能和更新]**** 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，直接從[視覺化工作室市場](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)下載擴展。

2. 在左側窗格中展開**連線**，然後選擇**視覺化工作室市場**。

3. 在搜索框中，鍵入"代碼分析"，並查找 Microsoft**代碼分析 2017**副檔名。

   ![微軟代碼分析 2017 擴展](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Microsoft 代碼分析 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)擴展包含託管專案的所有 FxCop 分析器。 要安裝此擴展：

1. 在視覺化工作室中，選擇**擴展**>**管理擴展**。

   將打開"**管理擴展"** 對話方塊。

   > [!NOTE]
   > 或者，直接從[視覺化工作室市場](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)下載擴展。

2. 在左側窗格中展開**連線**，然後選擇**視覺化工作室市場**。

3. 在搜索框中，鍵入"代碼分析"，並查找 Microsoft**代碼分析 2019**副檔名。

   ![微軟代碼分析 2019 擴展](media/manage-extensions-code-analysis.png)

::: moniker-end

4. 選擇**下載**。

   將下載擴展。

5. 選擇 **"確定"** 以關閉對話方塊，然後關閉 Visual Studio 的所有實例以啟動**VSIX 安裝程式**。

   將打開**VSIX 安裝程式**對話方塊。

   ::: moniker range="vs-2017"

   ![用於微軟代碼分析的 VSIX 安裝程式](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. 選擇 **"修改"** 以啟動安裝。

   一兩分鐘後，安裝完成。

7. 選擇 **"關閉**"，然後再次打開視覺工作室。

::: moniker range="vs-2017"

如果要檢查是否安裝了擴展，請選擇 **"工具** > **擴展和更新**"。 在"**擴展和更新"** 對話方塊中，選擇左側的 **"已安裝**"類別，然後按名稱搜索副檔名。

::: moniker-end

::: moniker range=">=vs-2019"

如果要檢查是否安裝了擴展，請選擇 **"擴展** > **管理擴展**"。 在"**管理擴展"** 對話方塊中，選擇左側的 **"已安裝**"類別，然後按名稱搜索副檔名。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [視覺化工作室中的代碼分析器概述](../code-quality/roslyn-analyzers-overview.md)
- [在 Visual Studio 中使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)
- [從舊分析遷移到代碼分析器](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)

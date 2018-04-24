---
title: 安裝 Visual Studio 中的 Roslyn 分析器
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8a3b40b3b471e6bb57da561ac51f23086a0f01bd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="install-net-compiler-platform-analyzers"></a>安裝.NET 編譯器平台分析器

Visual Studio 2017 包含一組核心.NET 編譯器平台 (*Roslyn*) 分析器。 這些分析器一律會在上。 NuGet 封裝，或是在 Visual Studio 擴充功能，您可以安裝其他的分析器*VSIX*檔案。

## <a name="to-install-nuget-package-analyzers"></a>若要安裝 NuGet 封裝分析器

1. [判斷哪一個分析器封裝版本](https://github.com/dotnet/roslyn-analyzers#recommended-version-of-analyzer-packages)安裝，請根據您的 Visual Studio 版本。

1. 在 Visual Studio 中，使用安裝套件[Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)或[封裝管理員 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)。

   > [!NOTE]
   > 針對每個分析器封裝 nuget.org 頁面會顯示要貼上的命令**Package Manager Console**。 即使是很方便的按鈕，以將文字複製到剪貼簿。
   >
   > ![顯示套件管理器主控台命令的 NuGet.org 頁面](media/nuget-package-manager-command.png)

   分析器組件已安裝，且會出現在**方案總管 中**下**參考** > **分析器**。

   ![在 [方案總管] 的分析器節點](media/solution-explorer-analyzers-node.png)

## <a name="to-install-vsix-analyzers"></a>若要安裝 VSIX 分析器

1. 在 Visual Studio 中，選取**工具** > **擴充功能和更新**。

   [擴充功能和更新] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，下載擴充功能直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)。

1. 展開**線上**左的窗格中，然後選取**Visual Studio Marketplace**。

1. 在 [搜尋] 方塊中，輸入 「 程式碼分析 」，並尋找**Microsoft 程式碼分析 2017年**延伸模組。

   ![Microsoft 程式碼分析擴充功能](media/extensions-and-updates-code-analysis.png)

1. 選取**下載**。

   下載擴充功能。

1. 選取**確定**以關閉對話方塊，然後關閉 Visual Studio 啟動的所有執行個體**VSIX 安裝程式**。

   **VSIX 安裝程式**對話方塊隨即開啟。

   ![Microsoft 程式碼分析的 VSIX 安裝程式](media/vsix-installer-code-analysis.png)

1. 選取**修改**開始安裝。

1. 一兩分鐘之後, 在安裝完成。 選取**關閉**。

1. 一次開啟 Visual Studio。

如果您想要檢查是否已安裝，請選取副檔名**工具** > **擴充功能和更新**。 在**擴充功能和更新**對話方塊中，選取**已安裝**類別目錄的左側，然後依名稱搜尋延伸模組。

## <a name="next-steps"></a>後續步驟

- [在 Visual Studio 中使用 Roslyn 分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的 Roslyn 分析器的概觀](../code-quality/roslyn-analyzers-overview.md)
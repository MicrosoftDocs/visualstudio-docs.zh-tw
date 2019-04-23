---
title: 安裝 Roslyn 分析器
ms.date: 08/03/2018
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
ms.openlocfilehash: 1afeb6f75648ce2ab1687fa9262ab28b658b0d70
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077806"
---
# <a name="install-net-compiler-platform-analyzers"></a>安裝.NET Compiler Platform 分析器

Visual Studio 包含一組核心.NET 編譯器平台 (*Roslyn*) 分析器。 這些分析器會永遠啟用。 您可以安裝其他的分析器，NuGet 套件，或是在 Visual Studio 擴充功能*VSIX*檔案。

## <a name="to-install-nuget-analyzer-packages"></a>若要安裝 NuGet 分析器套件

1. 尋找您想要在 www.nuget.org 安裝分析器套件。

   例如，您可能想要[安裝 Microsoft FxCop 分析器](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package)來檢查您的程式碼，如需安全性和效能問題，其他項目。 或者，安裝[StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)來尋找程式碼基底中的樣式問題。

2. 在 Visual Studio 中，使用安裝套件[Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)或[套件管理員 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)。

   > [!NOTE]
   > 每個分析器套件的 www.nuget.org 頁面會顯示貼到命令**Package Manager Console**。 甚至還有一些好用的按鈕，以將文字複製到剪貼簿。

   分析器組件已安裝，並會出現在**方案總管**下方**參考** > **分析器**。

## <a name="to-install-vsix-analyzers"></a>若要安裝 VSIX 分析器

::: moniker range="vs-2017"

1. 在 Visual Studio 中，選取**工具** > **擴充功能和更新**。

   [擴充功能和更新] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，您可以在其中尋找並下載分析器擴充功能，直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com)。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中，選取**延伸模組** > **管理延伸模組**。

   **管理延伸模組**對話方塊隨即開啟。

   > [!NOTE]
   > 或者，您可以在其中尋找並下載分析器擴充功能，直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com)。

::: moniker-end

2. 依序展開**線上**左的窗格中，然後選取**Visual Studio Marketplace**。

3. 在 [搜尋] 方塊中，輸入您想要安裝的分析器延伸模組的名稱。 例如，您可能想要[安裝 Microsoft FxCop 分析器](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix)來檢查您的程式碼，如需安全性和效能問題，其他項目。

4. 選取 **下載**。

   下載擴充功能。

5. 選取  **確定**以關閉對話方塊，然後關閉 Visual Studio 啟動的所有執行個體**VSIX 安裝程式**。

   **VSIX 安裝程式**對話方塊隨即開啟。

   ![Microsoft 程式碼分析的 VSIX 安裝程式](media/vsix-installer-code-analysis.png)

6. 選取 **修改**開始安裝。

7. 一或兩分鐘，安裝完成之後。 選取 [關閉] 。

8. 重新開啟 Visual Studio。

::: moniker range="vs-2017"

如果您想要檢查擴充功能是否已安裝，請選取**工具** > **擴充功能和更新**。 在**擴充功能和更新**對話方塊中，選取**已安裝**在左側的類別目錄，然後依名稱搜尋延伸模組。

::: moniker-end

::: moniker range=">=vs-2019"

如果您想要檢查擴充功能是否已安裝，請選取**延伸模組** > **管理延伸模組**。 在**管理延伸模組**對話方塊中，選取**已安裝**在左側的類別目錄，然後依名稱搜尋延伸模組。

::: moniker-end

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用 Roslyn 分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的 Roslyn 分析器的概觀](../code-quality/roslyn-analyzers-overview.md)
- [安裝 FxCop 分析器](../code-quality/install-fxcop-analyzers.md)
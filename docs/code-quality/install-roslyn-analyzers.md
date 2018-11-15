---
title: 安裝 Roslyn 分析器
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: aa0805b3cffe5a44ae2c6198c6ca2682ceca9f95
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865399"
---
# <a name="install-net-compiler-platform-analyzers"></a>安裝.NET Compiler Platform 分析器

Visual Studio 2017 包含一組核心.NET 編譯器平台 (*Roslyn*) 分析器。 這些分析器會永遠啟用。 您可以安裝其他的分析器，NuGet 套件，或是在 Visual Studio 擴充功能*VSIX*檔案。

## <a name="to-install-nuget-analyzer-packages"></a>若要安裝 NuGet 分析器套件

1. 尋找您想要在 www.nuget.org 安裝分析器套件。例如，您可能想要[安裝 Microsoft FxCop 分析器](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package)來檢查您的程式碼，如需安全性和效能問題，其他項目。

2. 在 Visual Studio 中，使用安裝套件[Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)或[套件管理員 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)。

   > [!NOTE]
   > 每個分析器套件的 www.nuget.org 頁面會顯示貼到命令**Package Manager Console**。 甚至還有一些好用的按鈕，以將文字複製到剪貼簿。
   > 
   > ![顯示套件管理員主控台命令的 NuGet.org 頁面](media/nuget-install-command.png)

   分析器組件已安裝，並會出現在**方案總管**下方**參考** > **分析器**。

## <a name="to-install-vsix-analyzers"></a>若要安裝 VSIX 分析器

1. 在 Visual Studio 中，選取**工具** > **擴充功能和更新**。

   [擴充功能和更新] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，您可以在其中尋找並下載分析器擴充功能，直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com)。

2. 依序展開**線上**左的窗格中，然後選取**Visual Studio Marketplace**。

3. 在 [搜尋] 方塊中，輸入您想要安裝的分析器延伸模組的名稱。 例如，您可能想要[安裝 Microsoft FxCop 分析器](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix)來檢查您的程式碼，如需安全性和效能問題，其他項目。

4. 選取 **下載**。

   下載擴充功能。

5. 選取  **確定**以關閉對話方塊，然後關閉 Visual Studio 啟動的所有執行個體**VSIX 安裝程式**。

   **VSIX 安裝程式**對話方塊隨即開啟。

   ![Microsoft 程式碼分析的 VSIX 安裝程式](media/vsix-installer-code-analysis.png)

6. 選取 **修改**開始安裝。

7. 一或兩分鐘，安裝完成之後。 選取 **關閉**。

8. 重新開啟 Visual Studio。

如果您想要檢查擴充功能是否已安裝，請選取**工具** > **擴充功能和更新**。 在**擴充功能和更新**對話方塊中，選取**已安裝**在左側的類別目錄，然後依名稱搜尋延伸模組。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用 Roslyn 分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的 Roslyn 分析器的概觀](../code-quality/roslyn-analyzers-overview.md)
- [安裝 FxCop 分析器](../code-quality/install-fxcop-analyzers.md)
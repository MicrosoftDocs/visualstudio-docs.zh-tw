---
title: 安裝 Roslyn 分析器
ms.date: 08/03/2018
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
ms.openlocfilehash: 9a833cb46811bd97467fdb048272c9feb2bb7873
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587377"
---
# <a name="install-net-compiler-platform-code-analyzers"></a>安裝 .NET Compiler Platform 程式碼分析器

Visual Studio 包含一組核心的 .NET Compiler Platform （*Roslyn*）分析器。 這些分析器一律是 on。 您可以將其他分析器安裝為 NuGet 套件，或做為*VSIX*檔案中的 Visual Studio 延伸模組。

## <a name="to-install-nuget-analyzer-packages"></a>安裝 NuGet 分析器套件

1. 尋找您要安裝在 www.nuget.org 上的分析器套件。

   例如，您可能會想要[安裝 Microsoft FxCop 分析器](install-fxcop-analyzers.md#nuget-package)，以檢查您的程式碼中是否有安全性和效能問題，以及其他專案。 或者，安裝[stylecop 能夠](https://www.nuget.org/packages/stylecop.analyzers/)以尋找程式碼基底中的樣式問題。

2. 使用 [[套件管理員主控台](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)] 或 [[套件管理員] UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)，在 Visual Studio 中安裝套件。

   > [!NOTE]
   > 每個分析器套件的 www.nuget.org 頁面會顯示要貼入**封裝管理員主控台**的命令。 甚至還有一個方便的按鈕，可將文字複製到剪貼簿。

   分析器元件會安裝並顯示在**方案總管**的 [**參考**] > **分析器**底下。

## <a name="to-install-vsix-analyzers"></a>安裝 VSIX 分析器

::: moniker range="vs-2017"

1. 在 Visual Studio 中，選取 [**工具**] > [**擴充功能和更新**]。

   [擴充功能和更新] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，您也可以直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com)尋找和下載分析器延伸模組。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中，選取 **擴充**功能 > **管理延伸**模組。

   [**管理延伸**模組] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，您也可以直接從[Visual Studio Marketplace](https://marketplace.visualstudio.com)尋找和下載分析器延伸模組。

::: moniker-end

2. 在左窗格中展開 [**線上**]，然後選取 [ **Visual Studio Marketplace**]。

3. 在 [搜尋] 方塊中，輸入您想要安裝之分析器擴充功能的名稱。 例如，您可能會想要[安裝 Microsoft FxCop 分析器](install-fxcop-analyzers.md#vsix)，以檢查您的程式碼中是否有安全性和效能問題，以及其他專案。

4. 選取 [下載]。

   已下載延伸模組。

5. 選取 **[確定]** 以關閉對話方塊，然後關閉 Visual Studio 的所有實例，以啟動**VSIX 安裝程式**。

   [ **VSIX 安裝程式**] 對話方塊隨即開啟。

   ![適用于 Microsoft 程式碼分析的 VSIX 安裝程式](media/vsix-installer-code-analysis.png)

6. 選取 [**修改**] 以開始安裝。

7. 一或兩分鐘後，安裝就會完成。 選取 [關閉]。

8. 再次開啟 Visual Studio。

::: moniker range="vs-2017"

如果您想要檢查是否已安裝延伸模組，請選取 [**工具**] > [**擴充功能和更新**]。 在 [**擴充功能和更新**] 對話方塊中，選取左側的 [**已安裝**] 類別，然後依名稱搜尋延伸模組。

::: moniker-end

::: moniker range=">=vs-2019"

如果您想要檢查是否已安裝延伸模組，請選取 [**延伸**模組] > [**管理延伸**模組]。 在 [**管理擴充**功能] 對話方塊中，選取左側的 [**已安裝**] 類別，然後依名稱搜尋延伸模組。

::: moniker-end

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>請參閱

- [Visual Studio 中的程式碼分析器總覽](../code-quality/roslyn-analyzers-overview.md)
- [安裝 FxCop 分析器](../code-quality/install-fxcop-analyzers.md)

---
title: 安裝協力廠商分析器
ms.date: 08/27/2020
description: 瞭解如何在 Visual Studio 中安裝協力廠商分析器。 瞭解如何在 .vsix 檔和 NuGet 分析器套件中安裝分析器。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3d4833ba922ddde1a1770cfd75cf446f210e2c79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859849"
---
# <a name="install-third-party-analyzers"></a>安裝第三方分析器

Visual Studio 包含一組核心 .NET Compiler Platform (*Roslyn*) 分析器。 這些分析器一律為開啟。 您可以將其他分析器安裝為 NuGet 套件，或作為 *VSIX* 檔案中的 Visual Studio 延伸模組。

## <a name="to-install-nuget-analyzer-packages"></a>若要安裝 NuGet 分析器套件

1. 尋找您想要在 www.nuget.org 上安裝的分析器套件。

   例如，您可能會想要安裝 [StyleCop](https://www.nuget.org/packages/stylecop.analyzers/) 來尋找程式碼基底中的樣式問題。

2. 使用 [封裝管理員主控台](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) 或 [封裝管理員 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)，在 Visual Studio 中安裝套件。

   > [!NOTE]
   > 每個分析器套件的 [www.nuget.org] 頁面會顯示要貼到 **封裝管理員主控台** 的命令。 甚至還有一個方便的按鈕可以將文字複製到剪貼簿。

   分析器元件會安裝並顯示在 **方案總管** 的 **參考**  >  **分析器** 下。

## <a name="to-install-vsix-analyzers"></a>安裝 VSIX 分析器

::: moniker range="vs-2017"

1. 在 Visual Studio 中，選取 [ **工具** > **擴充功能和更新**]。

   [擴充功能和更新] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，您也可以直接從 [Visual Studio Marketplace](https://marketplace.visualstudio.com)尋找並下載分析器擴充功能。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中，選取 [ **擴充** 功能 > **管理延伸** 模組]。

   [ **管理擴充** 功能] 對話方塊隨即開啟。

   > [!NOTE]
   > 或者，您也可以直接從 [Visual Studio Marketplace](https://marketplace.visualstudio.com)尋找並下載分析器擴充功能。

::: moniker-end

2. 展開左窗格中的 [ **線上** ]，然後選取 [ **Visual Studio Marketplace**]。

3. 在 [搜尋] 方塊中，輸入您想要安裝的分析器擴充功能名稱。

4. 選取 [下載]。

   延伸模組會下載。

5. 選取 **[確定** ] 關閉對話方塊，然後關閉 Visual Studio 的所有實例，以啟動 **VSIX 安裝程式**。

   [ **VSIX 安裝程式** ] 對話方塊隨即開啟。

   ![適用于 Microsoft 程式碼分析的 VSIX 安裝程式](media/vsix-installer-code-analysis.png)

6. 選取 [ **修改** ] 以開始安裝。

7. 在一或兩分鐘後，安裝就會完成。 選取 [關閉]。

8. 再次開啟 Visual Studio。

::: moniker range="vs-2017"

如果您想要檢查是否已安裝擴充功能，請選取 [**工具**  >  **擴充功能和更新**]。 在 [ **擴充功能和更新** ] 對話方塊中，選取左側的 [ **已安裝** ] 類別，然後依名稱搜尋延伸模組。

::: moniker-end

::: moniker range=">=vs-2019"

如果您想要檢查是否已安裝擴充功能，請選取 [**擴充** 功能管理延伸模組]  >  ****。 在 [ **管理擴充** 功能] 對話方塊中，選取左側的 [ **已安裝** ] 類別，然後依名稱搜尋延伸模組。

::: moniker-end

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼分析器總覽](../code-quality/roslyn-analyzers-overview.md)
- [安裝 .NET 分析器](../code-quality/install-net-analyzers.md)

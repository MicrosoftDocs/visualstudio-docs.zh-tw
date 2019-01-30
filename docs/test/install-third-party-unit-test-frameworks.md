---
title: 安裝協力廠商單元測試架構
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4cf2635cf46b1fa8b395cb8a7cab8769ae6ed6d3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960110"
---
# <a name="install-unit-test-frameworks"></a>安裝單元測試架構

Visual Studio 測試總管可以執行任何已針對總管開發配接器介面的單元測試架構。 架構的安裝程式會安裝二進位檔，並加入支援語言版本的 Visual Studio 專案範本。 當您使用範本來建立專案時，系統會向測試總管註冊架構。 Visual Studio 方案可包含多個單元測試專案，這些專案使用不同的架構並提供不同的語言版本。 [測試總管] 會全部一起執行。

[MSTest](getting-started-with-unit-testing.md) 是由 Visual Studio 提供的測試架構，預設會與 Visual Studio 一起安裝。

## <a name="acquire-frameworks"></a>取得架構

您可以使用 Visual Studio 延伸模組管理員或從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)，下載並安裝協力廠商單元測試架構。 您也可以從其他網站 (例如架構的網站) 下載架構。

### <a name="install-from-visual-studio"></a>從 Visual Studio 安裝

1. 選擇標準功能表上的 [工具]，然後選擇 [延伸模組和更新]。

2. 依序展開 [線上] > [Visual Studio Marketplace] > [工具]。 選擇 [測試]。

3. 瀏覽清單以尋找架構。

4. 選取架構並選擇 [下載]。

如需詳細資訊，請參閱[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。

### <a name="install-from-the-web"></a>從 Web 安裝

如果您知道對哪個架構感興趣：

1. 開啟 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。

2. 在 [尋找] 方塊中鍵入架構的名稱。

3. 在結果清單中選擇架構，以巡覽至工具的 [Visual Studio Marketplace] 頁面。

若要瀏覽架構和其他測試工具的清單：

1. 開啟 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。

2. 在 [依分類/集合篩選] 中，選擇 [See all] (全部查看)。

3. 在 [分類] 清單 (標示為 [正在顯示]) 中，展開 [工具] 節點，然後選擇 [測試]。

4. 在結果清單中選擇架構，以巡覽至工具的 [Visual Studio Marketplace] 頁面。

## <a name="update-to-the-latest-test-adapters"></a>更新至最新的測試配接器

若要體驗最佳的測試探索和執行，請更新至最新穩定的測試配接器。 如需 MSTest、NUnit 和 xUnit 測試配接器的詳細資訊，請參閱 [Visual Studio 部落格](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/) \(英文\)。

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>更新至最新穩定的測試配接器版本

1. 巡覽至 [工具] > [NuGet 套件管理員] > [管理方案的 NuGet 套件]，開啟解決方案的 NuGet 套件管理員。

2. 按一下 [更新] 索引標籤並搜尋已安裝的 MSTest、NUnit 或 xUnit 測試配接器。

3. 選取每個測試配接器，然後選取下拉式功能表中最新穩定的版本。

4. 選擇 [安裝] 按鈕。

   ![升級測試配接器](media/install-adapter-upgrade.png)

## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)

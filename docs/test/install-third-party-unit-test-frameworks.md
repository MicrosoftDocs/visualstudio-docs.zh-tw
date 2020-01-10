---
title: 安裝協力廠商單元測試架構
ms.date: 04/01/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b70e26adc7c0c9a8dc409d9b4b971b233418b8e1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594275"
---
# <a name="install-unit-test-frameworks"></a>安裝單元測試架構

Visual Studio 測試總管可以從任何已針對其開發配接器介面的單元測試架構中執行測試。 安裝架構會複製二進位檔，並新增支援語言版本的 Visual Studio 專案範本。 當您使用範本來建立專案時，系統會向測試總管註冊架構。

Visual Studio 方案可包含多個單元測試專案，這些專案使用不同的架構並提供不同的語言版本。

[MSTest](getting-started-with-unit-testing.md) 是 Visual Studio 提供的預設安裝測試架構。

## <a name="acquire-frameworks"></a>取得架構

使用 **NuGet 套件管理員**安裝協力廠商單元測試架構。

1. 以滑鼠右鍵按一下會包含您測試程式碼的專案，然後選取 [管理 NuGet 套件]。

2. 在 **NuGet 套件管理員**中，搜尋您想要安裝的測試架構，然後按一下 [安裝]。

   ![Visual Studio 中的 NuGet 套件管理員](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>更新至最新的測試配接器

若要體驗最佳的測試探索和執行，請更新至最新穩定的測試配接器。 如需 MSTest、NUnit 和 xUnit 測試配接器的詳細資訊，請參閱 [Visual Studio 部落格](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/) \(英文\)。

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>更新至最新穩定的測試配接器版本

1. 巡覽至 [工具] > [NuGet 套件管理員] > [管理方案的 NuGet 套件]，開啟解決方案的 NuGet 套件管理員。

2. 按一下 [更新] 索引標籤並搜尋已安裝的 MSTest、NUnit 或 xUnit 測試配接器。

3. 選取每個測試配接器，然後選取下拉式功能表中最新穩定的版本。

4. 選擇 [安裝] 按鈕。

   ![升級測試配接器](media/install-adapter-upgrade.png)

## <a name="see-also"></a>請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)

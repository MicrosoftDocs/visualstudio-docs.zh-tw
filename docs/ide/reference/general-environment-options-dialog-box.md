---
title: 選項對話方塊、環境、一般
description: 瞭解如何使用 [環境] 區段中的 [一般] 頁面，來變更 IDE 的色彩主題、狀態列設定、副檔名關聯等等。
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6068f63cc9c2e7abe36b6eac804beaaa6603303e
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617262"
---
# <a name="options-dialog-box-environment--general"></a>選項對話方塊：環境 \> 一般

使用此頁面來變更整合式開發環境 (IDE) 之色彩佈景主題、狀態列設定和副檔名關聯等其他選項。 開啟 [工具] 功能表，並選擇 [選項]，然後開啟 [環境] 資料夾，再選擇 [一般] 頁面，即可存取 [選項] 對話方塊。

## <a name="visual-experience"></a>視覺效果

**色彩佈景主題**

選擇 IDE 的 [藍色]、[淺色]、[深色] 或 [藍色 (更高對比)] 色彩佈景主題。

您可以從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) 下載和安裝 **Visual Studio 色彩佈景主題編輯器**，以安裝其他預先定義的佈景主題，以及建立自訂佈景主題。 安裝此工具之後，其他色彩佈景主題會出現在 [色彩佈景主題] 清單方塊中。

**將標題大寫樣式套用至功能表列**

功能表預設會使用標題大寫樣式。 取消選取此選項，改為使用所有大寫樣式。

::: moniker range=">=vs-2019"

**為不同像素密度的螢幕最佳化呈現方式 (需要重新啟動)**

此選項可啟用或停用個別監視器 DPI (每英吋的點數) 感知 (或 *PMA*)。 當 PMA 啟用時，使用任何監視器顯示比例與 DPI 設定都能清晰顯示 Visual Studio 使用者介面，包括跨多個監視器顯示時。 若要啟用 PMA，您需要 Windows 10 2018 4 月更新或更新版本和 .NET Framework 4.8 或更新版本。 (如果不符合這兩個必要條件，這個選項會呈現灰色。)

> [!TIP]
> - Windows 10 有設定顯示為 [讓 Windows 嘗試修正應用程式，讓他們不會模糊不清]。 如果您選取 [為不同像素密度的螢幕將呈現方式最佳化] 選項，則 **開啟** 該 Windows 設定會有顯著效果。
> - Windows 10 也包含 [程式相容性疑難排解員]。 我們不建議您嘗試使用該疑難排解工具來修正 Visual Studio 的外觀。

::: moniker-end

**自動根據用戶端效能調整視覺效果**

指定 Visual Studio 自動將調整設定為視覺效果還是明確地設定調整。 這項調整可能會將色彩顯示從漸層變更為單色，也可能會限制在功能表或快顯視窗中使用動畫。

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 有設定顯示為 [讓 Windows 嘗試修正應用程式，讓他們不會模糊不清]。 如果 Visual Studio 在您的監視器上顯示模糊，建議您 **開啟** 該設定。 請考慮升級至 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)，因為它是感知個別監視器 DPI 的應用程式，能大幅改善顯示清晰度。

::: moniker-end

**啟用豐富的用戶端體驗**

啟用 Visual Studio 的完整視覺效果 (包括漸層和動畫)。 使用遠端桌面連線或較舊的圖形介面卡時，請清除這個選項，因為這些功能在這些情況下的效能可能不佳。 只有在您清除 [自動根據用戶端效能調整視覺效果] 選項時，才能使用這個選項。

**使用硬體圖形加速 (如果有)**

使用硬體圖形加速 (如果有)，而非軟體加速。

## <a name="other"></a>其他

**要在 Windows 功能表中顯示的項目**

自訂 [視窗] 功能表之 [視窗] 清單中顯示的視窗數目。 輸入 1 和 24 之間的數字。 預設值是 10。

**顯示在最近使用的清單中的項目數**

自訂出現在 [檔案] 功能表上的最近使用的專案和檔案數目。 輸入 1 和 24 之間的數字。 預設值是 10。 這是擷取最近使用的專案和檔案的簡單方法。

**顯示狀態列**

顯示狀態列。 狀態列位於 IDE 視窗底部，並顯示進行中作業的進度資訊。

**[關閉] 按鈕只會影響使用中的工具視窗**

指定按一下 [關閉] 按鈕時，只會關閉具有焦點的工具視窗，而非停駐集中的所有工具視窗。 預設會選取這個選項。

**[自動隱藏] 按鈕只會影響使用中的工具視窗**

指定按一下 [自動隱藏] 按鈕時，只會自動隱藏具有焦點的工具視窗，而非停駐集中的所有工具視窗。 根據預設，這個選項並未選取。

## <a name="see-also"></a>另請參閱

- [自訂視窗版面配置](../../ide/customizing-window-layouts-in-visual-studio.md)

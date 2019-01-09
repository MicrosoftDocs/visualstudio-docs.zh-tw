---
title: 選項對話方塊、環境、一般
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15af9d627e425df57443cbf663b2b231b74f9a7e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945531"
---
# <a name="general-environment-options-dialog-box"></a>選項對話方塊、環境、一般

使用此頁面來變更整合式開發環境 (IDE) 之色彩佈景主題、狀態列設定和副檔名關聯等其他選項。 開啟 [工具] 功能表，並選擇 [選項]，然後開啟 [環境] 資料夾，再選擇 [一般] 頁面，即可存取 [選項] 對話方塊。 如果此頁面未出現在清單中，請在 [選項] 對話方塊中選取 [顯示所有設定] 核取方塊。

## <a name="visual-experience"></a>視覺效果

**色彩佈景主題**

選擇 IDE 的 [藍色]、[淺色] 或 [深色] 色彩佈景主題。

您可以從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) 下載和安裝 **Visual Studio 色彩佈景主題編輯器**，以安裝其他預先定義的佈景主題，以及建立自訂佈景主題。 安裝此工具之後，其他色彩佈景主題會出現在 [色彩佈景主題] 清單方塊中。

**將字首大寫套用至功能表列**

功能表預設會使用 [字首大寫]。 取消核取此選項，藉此設為 [全部大寫]。

**自動根據用戶端效能調整視覺效果**

指定 Visual Studio 自動將調整設定為視覺效果還是明確地設定調整。 這項調整可能會將色彩顯示從漸層變更為單色，也可能會限制在功能表或快顯視窗中使用動畫。

**啟用豐富的用戶端效果**

啟用 Visual Studio 的完整視覺效果 (包括漸層和動畫)。 使用遠端桌面連線或較舊的圖形介面卡時，請清除這個選項，因為這些功能在這些情況下的效能可能不佳。 只有在您清除 [自動根據用戶端效能調整視覺效果] 選項時，才能使用這個選項。

**使用硬體圖形加速 (如果有)**

使用硬體圖形加速 (如果有)，而非軟體加速。

## <a name="other"></a>其他

**個項目顯示在 [視窗] 功能表中**

自訂 [視窗] 功能表之 [視窗] 清單中顯示的視窗數目。 輸入 1 與 24 之間的數字。 數字預設為 10。

**顯示在最近使用的清單中的項目數**

自訂出現在 [檔案] 功能表上的最近使用的專案和檔案數目。 輸入 1 與 24 之間的數字。 數字預設為 10。 這是擷取最近使用的專案和檔案的簡單方法。

**顯示狀態列**

顯示狀態列。 狀態列位於 IDE 視窗底部，並顯示進行中作業的進度資訊。

**[關閉] 按鈕只影響作用中的工具視窗**

指定按一下 [關閉] 按鈕時，只會關閉具有焦點的工具視窗，而非停駐集中的所有工具視窗。 根據預設，這個選項是選取的。

**自動隱藏 按鈕只影響作用中的工具視窗**

指定按一下 [自動隱藏] 按鈕時，只會自動隱藏具有焦點的工具視窗，而非停駐集中的所有工具視窗。 根據預設，這個選項並未選取。

## <a name="see-also"></a>另請參閱

- [環境選項對話方塊](../../ide/reference/environment-options-dialog-box.md)
- [自訂視窗版面配置](../../ide/customizing-window-layouts-in-visual-studio.md)
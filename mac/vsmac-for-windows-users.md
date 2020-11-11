---
title: 適用于 Windows 使用者的 Visual Studio for Mac
description: 針對熟悉在 Windows 作業系統上使用 Visual Studio 的開發人員提供 Visual Studio for Mac 的簡介。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: 880811c675aac34a18a65c6eccb8ee10f3347d4c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493370"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>適用于 Windows 使用者的 Visual Studio for Mac

從一個作業系統遷移到另一個作業系統可能會很困難。 跨平臺應用程式（從使用者介面到功能表項目的分類）通常會有細微的差異。 您將在這裡瞭解 Windows 的 Visual Studio for Mac 和 Visual Studio 之間最常見的差異。 您也將瞭解 macOS 和 Windows 之間的幾個不同慣例。

## <a name="keyboard-shortcuts"></a>鍵盤快速鍵

就開發人員而言，許多人都習慣使用鍵盤來進行工作和導覽。 在 Mac 與 Windows 電腦之間，鍵盤上的某些按鍵是共通的。 您可以 forgiven，以為鍵盤動作（例如複製和貼上）使用相同的按鍵組合。 這不一定都是如此。 幸好，您可以在 Visual Studio for Mac 中變更金鑰系結，以與 Windows 中 Visual Studio 的系結緊密相符。

當您第一次執行 Visual Studio for Mac 時，您會看到鍵盤快速鍵選取範圍視窗：按鍵系結 ![ 視窗](media/ide-tour-2019-keyboard-shortcut.png)

如果您稍後想要變更金鑰系結，您可以在 [喜好設定：索引鍵系結喜好設定] 中找到設定 ![](media/customizing-the-ide-image10a.png)

請務必注意，macOS 會使用不同的全系統快捷方式來使用 Windows。 變更按鍵系結喜好設定可讓您在 Visual Studio for Mac 中使用熟悉的 Windows 快捷方式。 不過，在 macOS 的其他區域中，您必須熟悉 macOS 快捷方式。

MacOS 命令 (⌘) 輔助按鍵通常可以取代 Windows 中的控制項索引鍵。 以下是一些範例，以及其他常用的快速鍵：

|Task                   |Windows 快捷方式         |macOS 快捷方式      |
|-----------------------|-------------------------|--------------------|
|複製                   |`Ctrl + C`               |`⌘ + C`             |
|貼上                  |`Ctrl + V`               |`⌘ + V`             |
|剪下                    |`Ctrl + X`               |`⌘ + X`             |
|復原                   |`Ctrl + Z`               |`⌘ + Z`             |
|取消復原                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|刪除資料指標的右邊 |`Delete`                 |`fn + Backspace`    |
|刪除詞彙            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> 您可以在 [Apple 支援網站](https://support.apple.com/en-us/HT201236)上找到 macOS 快捷方式的完整清單。

## <a name="menus"></a>功能表

MacOS 中的功能表與 Windows 中的功能表的組織方式不同。 Visual Studio for Mac 不例外。 您可以在這裡找到一些最常見的功能表選項：

|Task                   |Visual Studio (Windows)                                              |Visual Studio for Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|喜好設定 (選項)   |工具 > 選項 .。。                                                   |Visual Studio > 喜好設定 .。。       |
|延伸模組             |擴充功能 > 管理延伸模組                                       |Visual Studio > 延伸模組 .。。        |
|版面配置                |視窗 > 套用視窗配置 > [選取版面配置]                       |View > 版面配置 > [選取版面配置]               |
|更新                |協助 > 檢查更新                                             |Visual Studio > 檢查更新 .。。 |
|NuGet 套件管理員  |> NuGet 封裝管理員 > 管理 NuGet 套件或解決方案的工具 .。。 |Project > 管理 NuGet 套件 .。。   |
|尋找工具             |編輯 > 尋找和取代 > [選取工具]                              |搜尋 > [選取工具]               |
|Visual Studio 概觀    |> Microsoft Visual Studio 的相關資訊                                 |有關 Visual Studio 的 Visual Studio >  

> [!NOTE]
> 您可以在[IDE 導覽](ide-tour.md)中找到 Visual Studio for Mac 中最常見功能的總覽
---
title: 適用于 Windows 使用者的 Visual Studio for Mac
description: 介紹 Visual Studio for Mac 中的協助工具功能，以及如何啟用它們。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984267"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>適用于 Windows 使用者的 Visual Studio for Mac

從某個作業系統遷移到另一個作業系統可能會很困難。 跨平臺應用程式中通常會有微小的差異，從使用者介面到功能表項目的分類。 使用者也會有 acclimatizing 到新作業系統使用者介面的學習曲線。 在這裡，您將瞭解 Windows 的 Visual Studio for Mac 和 Visual Studio 之間最常見的差異。 您也將瞭解 macOS 與 Windows 之間的一些不同慣例。

## <a name="keyboard-shortcuts"></a>鍵盤快速鍵

身為開發人員，許多人都習慣使用鍵盤來進行您的工作和導覽。 鍵盤上的某些按鍵在 Mac 和 Windows 電腦之間是共通的。 您可以 forgiven，以為鍵盤動作（例如複製和貼上）使用相同的按鍵組合。 這不一定都是如此。 幸好，您可以在 Visual Studio for Mac 中變更您的金鑰系結，以與 Windows 中 Visual Studio 的系結緊密相符。

第一次執行 Visual Studio for Mac 您將會看到 [鍵盤快速鍵] 選取視窗： ![索引鍵系結 視窗](media/ide-tour-2019-keyboard-shortcut.png)

如果您稍後想要變更金鑰系結，您可以在 [喜好設定： ![索引鍵系結] 喜好設定中找到設定](media/customizing-the-ide-image10a.png)

請務必注意，macOS 會使用 Windows 的不同全系統快捷方式。 變更按鍵系結喜好設定可讓您在 Visual Studio for Mac 中使用熟悉的 Windows 快捷方式。 不過，在 macOS 的其他區域中，您必須熟悉 macOS 快捷方式。

MacOS 命令（則是⌘）輔助按鍵通常可以取代 Windows 中的控制鍵。 以下是一些範例，以及其他常用的快捷方式：

|工作                   |Windows 快捷方式         |macOS 快捷方式      |
|-----------------------|-------------------------|--------------------|
|複製                   |`Ctrl + C`               |`⌘ + C`             |
|貼上                  |`Ctrl + V`               |`⌘ + V`             |
|剪下                    |`Ctrl + X`               |`⌘ + X`             |
|復原                   |`Ctrl + Z`               |`⌘ + Z`             |
|重做                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|刪除資料指標右方 |`Delete`                 |`fn + Backspace`    |
|刪除詞彙            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> 您可以在[Apple 支援網站](https://support.apple.com/en-us/HT201236)上找到完整的 macOS 快捷方式清單。

## <a name="menus"></a>功能表

MacOS 中的功能表與 Windows 中的功能表有不同的組織方式。 Visual Studio for Mac 不會發生例外狀況。 您可以在這裡找到一些最常見的功能表選項：

|工作                   |Visual Studio (Windows)                                              |Visual Studio for Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|喜好設定（選項）  |工具 > 選項 。                                                   |Visual Studio > 喜好設定 。       |
|擴充功能             |延伸模組 > 管理延伸模組                                       |Visual Studio > 延伸模組 。        |
|版面配置                |視窗 > 套用視窗版面配置 > [選取版面配置]                       |View > [選取版面配置]               |
|更新                |協助 > 檢查更新                                             |Visual Studio > 檢查是否有更新 。 |
|NuGet 封裝管理員  |> NuGet 套件管理員 > 管理 NuGet 套件或解決方案的工具 。 |專案 > 管理 NuGet 套件 。   |
|Pad/Windows         |View > [選取 Pad/window]                                         |View > Pad > [選取面板/視窗]  |
|尋找工具             |編輯 > 尋找和取代 > [選取工具]                              |搜尋 > [選取工具]               |
|Visual Studio 概觀    |有關 Microsoft Visual Studio 的協助 >                                 |有關 Visual Studio 的 Visual Studio >  

> [!NOTE]
> 您可以在[IDE 導覽](ide-tour.md)中找到 Visual Studio for Mac 中最常見的功能總覽
---
title: 適用于 Windows 使用者的 Mac 視覺化工作室
description: 在 Mac 視覺化工作室仲介紹協助工具以及如何啟用這些功能。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984267"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>適用于 Windows 使用者的 Mac 視覺化工作室

從一個作業系統遷移到另一個作業系統可能令人望而生畏。 跨平臺應用程式（從使用者介面到功能表項目的分類）通常存在細微差異。 使用者還將有適應新作業系統使用者介面的學習曲線。 在這裡，您將瞭解 Mac 視覺化工作室和適用于 Windows 的視覺化工作室之間的最常見區別。 您還將瞭解 macOS 和 Windows 之間的幾種不同的約定。

## <a name="keyboard-shortcuts"></a>鍵盤快速鍵

作為開發人員，你們中的許多人將習慣于使用鍵盤執行任務和導航。 鍵盤上的某些鍵在 Mac 和 Windows PC 之間很常見。 認為鍵盤操作（如複製和粘貼）使用相同的組合組合是可以原諒的。 情況並非總是如此。 幸運的是，您可以在 Mac 的 Visual Studio 中更改金鑰綁定，以與 Windows 中的 Visual Studio 綁定緊密匹配。

首次為 Mac 運行 Visual Studio 時，您將看到鍵盤快速鍵選擇視窗：![鍵綁定視窗](media/ide-tour-2019-keyboard-shortcut.png)

如果以後要更改金鑰綁定，可以在首選項中找到設置：![金鑰綁定首選項](media/customizing-the-ide-image10a.png)

請務必注意，macOS 使用不同的系統範圍的 Windows 快捷方式。 更改金鑰綁定首選項將允許您在 Mac 的 Visual Studio 中使用熟悉的 Windows 快捷方式。 但是，在 macOS 的其他領域，您需要熟悉 macOS 快捷方式。

macOS 命令 （*） 修改器鍵通常可以替換 Windows 中的"控制"鍵。 下面是一些示例和其他常用的快捷方式：

|Task                   |視窗快捷方式         |macOS 快捷方式      |
|-----------------------|-------------------------|--------------------|
|[複製]                   |`Ctrl + C`               |`⌘ + C`             |
|貼上                  |`Ctrl + V`               |`⌘ + V`             |
|剪下                    |`Ctrl + X`               |`⌘ + X`             |
|復原                   |`Ctrl + Z`               |`⌘ + Z`             |
|取消復原                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|刪除游標的權利 |`Delete`                 |`fn + Backspace`    |
|刪除詞彙            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> 你可以在[蘋果支援網站上](https://support.apple.com/en-us/HT201236)找到macOS快捷方式的完整清單。

## <a name="menus"></a>功能表

macOS 中的功能表的組織方式與 Windows 中的功能表不同。 Mac 的視覺工作室也不例外。 您可以在此處找到一些最常見的功能表選項：

|Task                   |Visual Studio (Windows)                                              |Visual Studio for Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|首選項（選項）  |工具>選項...                                                   |視覺工作室>首選項...       |
|延伸模組             |擴展>管理擴展                                       |視覺工作室>擴展...        |
|版面配置                |視窗>> [選擇佈局] 應用視窗佈局                       |查看> [選擇佈局]               |
|更新                |説明>檢查更新                                             |視覺化工作室>檢查更新... |
|NuGet 套件管理員  |> NuGet 包管理器的工具>管理 NuGet 包或解決方案... |專案>管理 NuGet 包...   |
|墊板/窗戶         |查看> [選擇鍵盤 / 視窗]                                         |查看>>墊 [選擇鍵盤 / 視窗]  |
|查找工具             |編輯>查找和替換> [選擇工具]                              |搜索> [選擇工具]               |
|Visual Studio 概觀    |有關微軟視覺工作室>説明                                 |視覺工作室>關於視覺工作室  

> [!NOTE]
> 您可以在[IDE 旅遊](ide-tour.md)中找到 Mac 視覺化工作室中最常見的功能概述
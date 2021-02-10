---
title: Visual Studio 協助工具祕訣和訣竅
description: 深入了解可讓 Visual Studio 整合式開發環境 (IDE) 更便於每個人 (包括行動不便人士) 使用的祕訣和訣竅。
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59206c206f04aaf3506771ee2310daebd0af273a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939743"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Visual Studio 協助工具祕訣和訣竅

Visual Studio 有與螢幕助讀程式和其他輔助技術相容的內建協助工具功能。 不論您是想要使用鍵盤快速鍵來瀏覽 IDE，還是使用高對比佈景主題來改善可見度，您都可以在此頁面上找到數個相關做法的秘訣和訣竅。

我們也說明了如何使用註釋來顯示程式碼的相關實用資訊，以及如何設定組建和中斷點事件的音效提示。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 的協助工具](/visualstudio/mac/accessibility)。

## <a name="save-your-ide-settings"></a>儲存 IDE 設定

您可以儲存視窗配置、鍵盤對應配置和其他喜好設定，來自訂 IDE 體驗。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="modify-your-ide-for-high-contrast-viewing"></a>修改您的 IDE 進行高對比檢視

對有些人而言，部分色彩十分難以辨識。 如果您想要在撰寫程式碼時有更高的對比，但不想要使用一般的 [高對比] 佈景主題，我們現在提供 [藍色 (更高對比)] 佈景主題。

  ![比較藍色佈景主題和藍色 (超對比) 佈景主題](media/blue-extra-contrast-theme.png "顯示藍色主題和藍色超對比主題比較的螢幕擷取畫面")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>使用註釋顯示程式碼的實用資訊

Visual Studio 編輯器包含許多文字「裝飾」，讓您知道程式碼特定點的特性和功能，例如螺絲起子和燈泡圖示、錯誤和警告的「波浪線」、書籤等等。 您可以使用「顯示程式碼行註釋」命令集協助探索，然後巡覽這些裝飾。

  ![使用「顯示程式碼行註釋」命令集](media/show-line-annotations-command-set.png "顯示線條注釋功能表項目的螢幕擷取畫面")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>使用鍵盤快速鍵來存取工具列

Visual Studio IDE 工具列的作用與許多工具視窗相同。 下列鍵盤快速鍵可協助您存取它們。

|功能|說明|鍵盤快速鍵|
|-------------|-----------------| - |
|IDE 工具列|選取 [標準] 工具列上的第一個按鈕。|**Alt**、 **Ctrl** + **Tab**|
|工作視窗工具列|將焦點移至工具視窗中的工具列。 <br> <br> **注意：** 這適用於大部分的工具視窗，但只限焦點在工具視窗中時。 此外，您必須先選擇 SHIFT 鍵再選擇 ALT 鍵。 在部分工具視窗 (例如 Team Explorer) 中，您必須先按住 SHIFT 鍵再選擇 ALT 鍵。|**Shift** +**Alt**|
|工具列|移至下一個工具列中的第一個項目 (當工具列有焦點時)。|**Ctrl** +**Tab**|

### <a name="other-useful-keyboard-shortcuts"></a>其他實用的鍵盤快速鍵

一些其他實用的鍵盤快速鍵包括下列各項。

|功能|說明|鍵盤快速鍵|
|-------------|-----------------| - |
|IDE|開啟或關閉高對比。 <br> <br> **注意：** 標準 Windows 鍵盤快捷方式|**左 Alt** +**左移** +**PrtScn**|
|對話方塊|選取或清除對話方塊中的核取方塊選項。 <br> <br> **注意：** 標準 Windows 鍵盤快捷方式|**空白鍵**|
|操作功能表|開啟操作 (滑鼠右鍵) 功能表。 <br> <br> **注意：** 標準 Windows 鍵盤快捷方式|**Shift** +**F10**|
|功能表|使用其快速鍵來快速存取功能表項目。 選擇 **Alt** 鍵，然後選擇功能表中加底線的字母來啟用命令。 例如，若要在 Visual Studio 中查看 [開啟專案] 對話方塊，您可以選擇 [ **Alt** + **F** + **O** + **P**]。  <br><br> **注意：** 標準 Windows 鍵盤快捷方式|**Alt**  + **[字母]**|
|搜尋方塊|使用 Visual Studio 中的搜尋功能。|**Ctrl** +**問：**|
|[工具箱] 視窗|在 [工具箱] 索引標籤之間移動。|**Ctrl** +**向上鍵**<br /><br /> 及<br /><br /> **Ctrl** +**向下箭** 號|
|[工具箱] 視窗|將控制項從 [工具箱] 新增至表單或設計工具。|**Enter**|
|選項對話方塊：環境 > 鍵盤|刪除 [按快速鍵] 選項中所輸入的按鍵組合。|**退格鍵**|
|[通知] 工具視窗|使用兩個鍵盤快速鍵按鍵組合 (一個後面接著另一個) 來開啟 [通知] 工具視窗。 接著，使用方向鍵來選取通知以檢視該通知。| **Ctrl** +**&#92;**， **Ctrl** + **N**|

> [!NOTE]
> 根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>使用鍵盤快速鍵來存取通知

當通知出現在 IDE 中時，以下是您可以使用鍵盤快速鍵來存取 [通知] 視窗的方式：

1. 從 IDE 中的任何地方，依序按下下列兩個鍵盤快速鍵，再按一次： **ctrl** + **&#92;** 然後按 **ctrl** + **N**。

   [通知] 視窗隨即開啟。

   ![Visual Studio IDE 中的 [通知] 工具視窗](media/toast-notification.png "Visual Studio IDE 中 [通知] 視窗的螢幕擷取畫面")

1. 使用 **Tab** 鍵或方向鍵來選取通知。

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>使用音效小程式設定組建與中斷點提示

您可以使用 Windows 的音效小程式，指派 Visual Studio 程式事件的音效。 具體而言，您可以指派下列程式事件的音效：

* 遇到中斷點
* 已取消組建
* 組建失敗
* 組建成功

方法如下：

1. 在執行 Windows 10 電腦的 [搜尋] 方塊中鍵入 **變更系統音效**。

   ![Windows 10 中的搜尋方塊](media/type-here-to-search.png "Windows 10 中搜尋方塊的螢幕擷取畫面")

   (或者，如啟用 Cortana，說出「嘿 Cortana」，接著說出「變更系統音效」。)

1. 按兩下 [變更系統音效]。

   ![Windows 10 中的搜尋結果](media/change-system-sounds.png "Windows 10 中「變更系統音效」搜尋結果的螢幕擷取畫面")

1. 在 [音效] 對話方塊中，按一下 [音效] 索引標籤。

1. 在 [程式事件] 中，捲動至 [Microsoft Visual Studio]，然後選取要套用到所選事件的音效。

   ![Windows 10 中 [音效] 小程式的 [音效] 索引標籤](media/sound-applet.png "Windows 10 中 [音效] 小程式的 [音效] 索引標籤")

1. 按一下 [確定]  。

::: moniker range="vs-2017"

> [!TIP]
> 若要深入了解協助工具更新，請參閱 [Accessibility improvements in Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Visual Studio 2017 15.3 版中的協助工具改善) 部落格文章。

::: moniker-end

## <a name="see-also"></a>另請參閱

* [Visual Studio 的協助工具功能](../../ide/reference/accessibility-features-of-visual-studio.md)
* [如何：在 Visual Studio 中自訂功能表和工具列](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)
* [協助工具 (Visual Studio for Mac)](/visualstudio/mac/accessibility)
* [Microsoft Accessibility](https://www.microsoft.com/Accessibility) (Microsoft 協助工具)

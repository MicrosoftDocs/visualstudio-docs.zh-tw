---
title: 瞭解方案總管工具視窗
description: 瞭解如何使用 Visual Studio 中的 [方案總管] 工具視窗，建立 & 管理您的檔案、專案和方案。
ms.date: 06/29/2021
ms.topic: conceptual
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 005e6fd3e49d3a3ab739740d2aaa1dd77df5e5df
ms.sourcegitcommit: 3d0f4930e0ccf49f89bbcfe12a949fbbf37aae07
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113131496"
---
# <a name="how-to-use-solution-explorer"></a>如何使用方案總管

您可以使用 [方案總管] 工具視窗來建立 & 管理您的方案和專案，以及查看 & 與程式碼互動。 在本文中，我們將詳細說明使用者介面 (UI) 可協助您這麼做的選項。

> [!NOTE]
> 本主題僅適用於 Windows 上的 Visual Studio。

## <a name="solution-explorer-tool-window"></a>方案總管工具視窗

首先，讓我們看看 [VISUAL STUDIO IDE](../get-started/visual-studio-ide.md)中的方案總管工具視窗，以及具有兩個專案的 Open c # 主控台解決方案。

[![Visual Studio 中的 [方案總管] 工具視窗。](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

此工具視窗包含下列 UI (使用者介面) 元素：

- **功能表列**，您可以在其中控制檔案的顯示方式
- **搜尋** 列，您可以在其中搜尋特定檔案和檔案類型
- **主視窗**，您可以在其中查看及管理檔案、專案、& 方案
- **方案節點**，您可以在其中管理您的解決方案 () 
- **專案節點**，您可以在其中管理專案 (s) 
- [相依性 **] 節點**，您可以在其中管理方案 & 專案相依性
- **程式節點**，您可以在其中查看、編輯及管理您的程式或應用程式 (應用程式) 
- [ **[Git 變更]](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)** 索引標籤，您可以在 Visual Studio 中使用 Git & GitHub，以與您的小組共同作業專案

> [!TIP]
> 如果您沒有看到 [方案總管] 工具視窗，您可以在 Visual Studio 功能表列中，使用 **View**  >  **方案總管** 或按下 **Ctrl** + **Alt** + **L** 來開啟它。

## <a name="solution-explorer-menu-bar"></a>方案總管的功能表列

若要繼續，讓我們仔細看看方案總管的功能表列。

![Visual Studio 中的 [方案總管] 功能表列。](media/solution-explorer-menu-bar.png)

功能表列包含下列 UI 元素，從左至右：

- [**上一頁**] 按鈕，在搜尋結果之間切換
- **向前** 按鈕，在搜尋結果之間切換
- [**首頁**] 按鈕，以返回預設視圖
- **切換** 按鈕，在解決方案和可用的視圖之間切換
- **暫止的變更篩選** 按鈕 & 下拉式功能表，以查看具有暫止變更的開啟檔案或檔案
- **與使用** 中檔按鈕同步處理，以從程式碼編輯器找出檔案
- 重新 **整理按鈕，** 只有在您選取相依性（例如函式或封裝）時才會出現
- [**全部** 折迭] 按鈕，以折迭主視窗中的檔案視圖
- [**顯示所有** 檔案] 按鈕，以查看所有檔案，包括已卸載的 [專案](filtered-solutions.md#toggle-unloaded-project-visibility)
- [**屬性**] 按鈕，以查看及變更特定檔案和元件的設定
- **預覽選取的專案** 按鈕，以在程式碼編輯器中查看選取的檔案或元件

### <a name="solution-explorer-right-click-context-menu"></a>方案總管右鍵內容功能表

在方案總管中，您可以使用滑鼠右鍵內容功能表來與您互動的數個檔案屬性。 如需有關滑鼠右鍵內容功能表選項的詳細資訊，請參閱 [管理專案和方案屬性](managing-project-and-solution-properties.md) 頁面。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的解決方案和專案是什麼？](solutions-and-projects-in-visual-studio.md)
- [在 Visual Studio 中自訂視窗版面配置](customizing-window-layouts-in-visual-studio.md)

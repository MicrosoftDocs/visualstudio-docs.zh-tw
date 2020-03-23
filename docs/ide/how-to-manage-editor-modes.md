---
title: 全螢幕和虛擬空間模式
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77f224a6e3a1b12ed17799ddf6a2fc5c23f5d4cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591030"
---
# <a name="how-to-manage-editor-modes"></a>如何：管理編輯器模式

您可以使用各種不同的顯示模式來顯示 Visual Studio 程式碼編輯器。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與本文中描述的不同。 若要變更您的設定 (例如變更為 [一般]**** 或 [Visual C++]**** 設定)，請選擇 [工具]**** > [匯入和匯出設定]****，然後選擇 [重設所有設定]****。

## <a name="enable-full-screen-mode"></a>啟用全螢幕模式

您可以選擇隱藏所有工具視窗，並通過啟用**全屏**模式僅查看文件視窗。

- 按 **"Alt**+**移位**+**輸入"** 進入或退出**全屏**模式。

     -- 或 --

- 在 [命令]**** 視窗中發出命令 `View.Fullscreen`。

## <a name="enable-virtual-space-mode"></a>啟用虛擬空間模式

在 [虛擬空間]**** 模式中，會在每一行程式碼的結尾插入空格。 選取這個選項，可在程式碼旁邊一致的位置上放置註解。

1. 選取 [工具]**** 功能表上的 [選項]****。

2. 展開 [文字編輯器]**** 資料夾，然後選擇 [所有語言]**** 全域設定此選項，或選擇特定語言的資料夾。 例如，要僅在"可視基本"中打開行號，請選擇**基本** > **文字編輯器**節點。

3. 選取 [一般]**** 選項，然後在 [設定]**** 下選取 [啟用虛擬空間]****。

    > [!NOTE]
    > 在 [資料行選取]**** 模式中會啟用 [虛擬空間]****。 未啟用 [虛擬空間]**** 模式時，插入點會從一行結尾直接移到下一行的第一個字元。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)
- [字體和顏色、環境、選項對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)

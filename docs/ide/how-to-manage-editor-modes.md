---
title: 全螢幕和虛擬空間模式
description: 瞭解如何管理 Visual Studio 編輯器模式，以最適合您的方式來顯示所有工具和視窗。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 2b86859f5f5718871499bb1f3e2014da59f956db
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597141"
---
# <a name="how-to-manage-editor-modes"></a>如何：管理編輯器模式

您可以使用各種不同的顯示模式來顯示 Visual Studio 程式碼編輯器。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與本文中描述的不同。 若要變更您的設定 (例如變更為 [一般] 或 [Visual C++] 設定)，請選擇 [工具] > [匯入和匯出設定]，然後選擇 [重設所有設定]。

## <a name="enable-full-screen-mode"></a>啟用全螢幕模式

您可以藉由啟用 **全螢幕** 模式，選擇隱藏所有工具視窗，並只查看文件視窗。

- 按 **Alt** + **Shift** + **enter** 進入或離開 **全螢幕** 模式。

     -- 或 --

- 在 [命令] 視窗中發出命令 `View.Fullscreen`。

## <a name="enable-virtual-space-mode"></a>啟用虛擬空間模式

在 [虛擬空間] 模式中，會在每一行程式碼的結尾插入空格。 選取這個選項，可在程式碼旁邊一致的位置上放置註解。

1. 選取 [工具] 功能表上的 [選項]。

2. 展開 [文字編輯器] 資料夾，然後選擇 [所有語言] 全域設定此選項，或選擇特定語言的資料夾。 例如，若只要在 Visual Basic 中開啟行號，請選擇 [**基本**  >  **文字編輯器**] 節點。

3. 選取 [一般] 選項，然後在 [設定] 下選取 [啟用虛擬空間]。

    > [!NOTE]
    > 在 [資料行選取] 模式中會啟用 [虛擬空間]。 未啟用 [虛擬空間] 模式時，插入點會從一行結尾直接移到下一行的第一個字元。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)
- [選項對話方塊、環境、字型和色彩](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)

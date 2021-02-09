---
title: 使用 Visual Studio 搜尋
description: 瞭解如何使用 Visual Studio 搜尋來尋找設定、功能表和程式碼。
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 101875b3a600a71c832498d05073187d2cf0b774
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873901"
---
# <a name="use-visual-studio-search"></a>使用 Visual Studio 搜尋

Visual Studio 的整合式開發環境 (IDE) 有許多功能表、選項和功能，這可能很難記住。 Visual Studio 搜尋功能是單一搜尋方塊，可協助開發人員尋找 IDE 功能表和選項，同時搜尋您的程式碼。 無論您是 Visual Studio 或有經驗的開發人員，這項功能都能提供快速的方式來搜尋 IDE 功能和您的程式碼。

使用 **Ctrl** + **Q** 鍵盤快速鍵來存取搜尋方塊，或按一下預設位於功能表列旁的 Visual Studio 搜尋輸入方塊：

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Visual Studio 搜尋方塊" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Visual Studio 搜尋執行的命令是 `Window.QuickLaunch` ，您可能會看到這項功能稱為「快速搜尋」或「快速啟動」。

不同于其他搜尋功能，例如 [檔案中尋找] 或 [搜尋] 方案總管，在 Visual Studio 的結果中搜尋會包含 IDE 功能、功能表選項、檔案名等等。 下列各節將討論 Visual Studio 搜尋可找到的不同結果類型。

## <a name="search-menus-options-and-windows"></a>搜尋功能表、選項和視窗

您可以使用 Visual Studio 搜尋方塊來尋找設定、選項和類似的設定專案。 例如，搜尋 [ *變更主題* ] 以快速尋找並開啟對話方塊，讓您變更 Visual Studio 色彩主題，如下列螢幕擷取畫面所示：

:::image type="content" source="media/visual-studio-search-options.png" alt-text="搜尋 Visual Studio 設定和選項":::

> [!TIP]
> 在大多數情況下，Visual Studio 搜尋也會提醒您功能表、快速鍵和結果中每個專案的位置。

您可以使用 Visual Studio 搜尋方塊來尋找功能表項目和命令。 例如，搜尋 *clean sol* 以快速尋找並執行 [清除方案] 命令。 搜尋結果也會提醒您如何在功能表中找到此命令，如下列螢幕擷取畫面所示：

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="搜尋 Visual Studio 功能表項目和命令":::

最後，您可以搜尋可能意外關閉的 windows 或面板。 例如，搜尋 *測試* 以尋找並開啟 [測試瀏覽器] 視窗：

:::image type="content" source="media/visual-studio-search-window.png" alt-text="搜尋 Visual Studio 視窗和麵板":::

## <a name="search-files-and-code"></a>搜尋檔案和程式碼

Visual Studio 搜尋也會在您的方案專案中搜尋檔案名、程式碼、方法和其他相符專案。 在下列螢幕擷取畫面中，搜尋 *markdown* 已找到 MarkdownMetaExtractor.cs 檔、 `MarkdownMetaExtractor` 類別和方案內的兩個方法：

:::image type="content" source="media/visual-studio-search-files.png" alt-text="使用 Visual Studio 搜尋搜尋檔案":::

您也可以進行「camel 大寫字母」搜尋。 在下列螢幕擷取畫面中，搜尋 *FSS* 已找到 **F****舊版的****大小 canner** 檔、類別和方法：

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="使用 Visual Studio 搜尋的 Camel hump 搜尋":::

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](reference/visual-studio-commands.md)
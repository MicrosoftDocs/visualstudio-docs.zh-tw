---
title: Blend for Visual Studio 功能導覽
titleSuffix: ''
description: 瞭解 Blend for Visual Studio 的工作區 UI 和功能，這是設計以 XAML 為基礎的 Windows 和 Web 應用程式的元件。
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fdc3fc2241807cd1b36ec64d620c7b46a498918
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889261"
---
# <a name="blend-for-visual-studio-overview"></a>Blend for Visual Studio 概觀

Blend for Visual Studio 可協助您設計以 XAML 為基礎的 Windows 及 Web 應用程式。 它提供與 Visual Studio 相同的基本 XAML 設計體驗，並新增可處理動畫和表現方式等進階工作的視覺化設計工具。 如需 Blend 和 Visual Studio之間的比較，請參閱[在 Visual Studio 和 Blend for Visual Studio 中設計 XAML](../xaml-tools/designing-xaml-in-visual-studio.md)。

Blend for Visual Studio 是 Visual Studio 的元件。 若要安裝 Blend，請在 **Visual Studio 安裝程式** 中選擇 **通用 Windows 平台開發** 或 **.NET 桌面開發** 工作負載。 這兩個工作負載都包含 Blend for Visual Studio 元件。

![UWP 工作負載元件](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![.NET 桌面開發工作負載元件](media/installer-dotnet-desktop.png)

如果您是 Blend for Visual Studio 的新手，請花點時間熟悉工作區的獨特功能。 本主題會帶領您快速導覽。

## <a name="tools-panel"></a>工具面板

您可以使用 Blend for Visual Studio 中的 [工具] 面板來建立及修改應用程式中的物件。 當您開啟 *.xaml* 檔案時，[工具] 面板會顯示在 XAML 設計工具的左側。

您可以選取工具，然後使用滑鼠在畫板上繪製以建立物件。

![Blend for Visual Studio 的 [工具] 面板](media/blend-tools-panel.png)

> [!TIP]
> [工具] 面板中的某些工具會有不同的變化，例如您可以選擇橢圓形或線條，而不是矩形。 若要存取這些變化，請以滑鼠右鍵按一下或按住工具。
>
> ![Blend for Visual Studio 的圖形工具變化](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>選取工具

選取物件和路徑。 使用 [直接選取] 工具可選取巢狀物件和路徑區段。

### <a name="view-tools"></a>檢視工具

調整畫板的檢視方式，例如移動瀏覽和縮放。

### <a name="brush-tools"></a>筆刷工具

使用物件的視覺屬性，例如轉換筆刷或套用漸層。

### <a name="object-tools"></a>物件工具

繪製畫板上最常用的物件，例如路徑、圖形、版面配置面板、文字及控制項。

### <a name="asset-tools"></a>資產工具

存取 [資產] 視窗，以及顯示資產庫中最近使用過的資產。

## <a name="assets-window"></a>資產視窗

[資產] 視窗包含所有可用的控制項，類似於 Visual Studio 的 **工具箱**。 除了控制項之外，您還可以在 [資產] 視窗中找到可新增至畫板的所有項目，包括樣式、媒體、行為和效果。 若要開啟 [資產] 視窗中，請選擇 [檢視] > [資產] 視窗，或按 **Ctrl**+**Alt**+**X**。

![Blend for Visual Studio 的 [資產] 視窗](media/blend-assets-window.png)

- 在 [搜尋資產] 方塊中輸入文字以篩選資產清單。
- 使用右上方的按鈕，在資產的 [格線] 模式與 [清單] 模式檢視之間切換。

## <a name="objects-and-timeline-window"></a>[物件與時間軸] 視窗

使用此視窗可依您想要的方式，在畫板上組織物件以製作動畫。 若要開啟 [物件與時間軸] 視窗，請選擇 [檢視] > [文件大綱]。 除了 Visual Studio 的 [[文件大綱] 視窗](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window)中提供的功能之外，Blend for Visual Studio 中 [物件與時間軸] 視窗的右側還有時間軸組合區域。 當您建立和編輯動畫時，請使用時間軸。

![動畫模式中的 [物件與時間軸] 視窗](media/storyboard-timeline.png)

使用分鏡腳本相關按鈕 ![Blend for Visual Studio 中的分鏡腳本按鈕](media/storyboard-buttons.png) 來建立、刪除、關閉或選取分鏡腳本。 使用右側的時間軸組合區域來檢視時間軸及移動主要畫面格。

將滑鼠游標暫留在視窗中的每個按鈕上，以深入了解可用的功能。

## <a name="see-also"></a>另請參閱

- [製作物件動畫](../xaml-tools/animate-objects-in-xaml-designer.md)
- [繪製圖案與路徑](../xaml-tools/draw-shapes-and-paths.md)
- [在 Visual Studio 和 Blend for Visual Studio 中設計 XAML](../xaml-tools/designing-xaml-in-visual-studio.md)

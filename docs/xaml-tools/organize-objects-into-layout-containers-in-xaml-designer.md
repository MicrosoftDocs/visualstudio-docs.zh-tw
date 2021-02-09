---
title: 將物件組織在版面配置容器中
description: 瞭解 XAML 設計工具中用來排列頁面上物件的版面配置面板和控制項，例如格線、畫布、框線和 Viewbox。
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: d42a7509ceef03d2e74f470d7d4ab0efb5913e13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900843"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>在 XAML 設計工具中將物件組織在版面配置容器中

本文會描述 XAML 設計工具的版面配置面板和控制項。

想像一下您想讓物件 (例如影像、按鈕和視訊等物件) 出現在頁面上的哪個位置。 或許您想讓物件出現在資料列和資料行中、在垂直或水平的單一行中，或在固定位置中。

在利用此機會思考頁面可能會如何出現之後，請選擇版面配置面板。 所有頁面都會以此開始，因為您需要一些項目來新增物件。 預設是 [格線]，但可以變更。

版面配置面板可協助您在頁面上排列物件，但不僅僅如此。 此面板還可協助您針對不同螢幕大小和解析度進行設計。 當使用者執行您的應用程式時，版面配置面板中的所有項目會調整大小以符合他們裝置的實際螢幕面積。 當然，如果不想要讓版面配置這麼做，您可以針對某部分版面配置或整個版面配置覆寫該行為。 您可以使用高度和寬度屬性來控制該行為。

## <a name="layout-panels"></a>版面配置面板

選擇這些版面配置面板的其中一個，開始您的頁面。 您可以有一個以上的頁面。 例如，您著手開始的是 [格線] 版面配置面板，然後將 **StackPanel** 新增至 [格線] 中的區域，以便可以在該項目中垂直排列控制項。

下列版面配置面板只是最普遍使用的面板，除此之外還有其他面板。 您可以在 Visual Studio 的 [工具箱] 或 Blend for Visual Studio 的 [資產] 面板中找到所有控制項。

### <a name="grid"></a>方格

將物件排列成資料列和資料行。

![格線配置面板](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>同型方格

將物件排列成相等或同型的方格區域。 此面板適合用來排列影像清單。

(僅適用於 WPF 專案)

![UniformGrid 版面配置面板](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

### <a name="canvas"></a>畫布

以任何想要的方式排列物件。 當使用者執行您的應用程式時，這些項目在螢幕上會具有固定位置。

![畫布配置面板](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

水平或垂直排列單一行中的物件。

![StackPanel 版面配置面板](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

以循序方式從左到右排列物件。 若面板的最右側邊緣沒有足夠空間時，會將內容「換行」到下一行，從左到右、從上到下依此類推。 您也可以讓換行面板變成垂直方向，讓物件從上到下、從左到右地流動。

(僅適用於 WPF 專案)

![WrapPanel 版面配置面板](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

排列物件，使其停留或「停駐」在面板的一個邊緣。

(僅適用於 WPF 專案)

![DockPanel 版面配置面板](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**觀看短片：** ![播放按鈕](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>配置控制項

您也可以將物件加入至版面配置控制項。 控制項不像版面配置面板一樣具有豐富的功能，但會發現控制項在特定情況下很有幫助。

下列版面配置控制項是最熱門的控制項，除此之外還有其他控制項。 您可以在 Visual Studio 的 [工具箱] 或 Blend for Visual Studio 的 [資產] 面板中找到所有控制項。

### <a name="border"></a>框線

在物件周圍建立框線、背景或兩者。 您可以只將一個將物件新增至 **Border**。 如果您想要為多個物件套用框線或背景，請將版面配置面板新增至 **Border**。 然後，將物件加入至該面板或控制項。

![框線版面配置控制項](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>快顯

在視窗中向使用者顯示資訊或選項。 您可以只將一個將物件新增至 **Popup**。 **Popup** 預設會包含 **Grid**，但您可以加以變更。

### <a name="scrollviewer"></a>ScrollViewer

可讓使用者向下捲動頁面或頁面的區域。 您只能將一個物件新增至 **ScrollViewer**，因此新增 **Grid** 或 **StackPanel** 這類版面配置面板相當合理。

![ScrollViewer 版面配置控制項](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

縮放物件的作用就像是使用縮放控制項一樣。 您可以只將一個物件新增至 **Viewbox**。 如果您要將該效果套用至多個物件，請將版面配置面板新增至 **ViewBox**，然後將控制項新增至該版面配置面板。

![ViewBox 版面配置控制項](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>另請參閱

- [使用 XAML 設計工具中的項目](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [使用 XAML 設計工具建立 UI](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)

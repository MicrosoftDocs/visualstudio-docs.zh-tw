---
title: Working with elements in XAML Designer
description: 瞭解如何在 Visual Studio 或 Blend for Visual Studio 中使用 XAML 設計工具中的元素。
ms.custom: SEO-VS-2020
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1af793ec7ecd741de1fc1b4bb1cb48dbf2ef32f3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047127"
---
# <a name="work-with-elements-in-xaml-designer"></a>使用 XAML 設計工具中的項目

您可以使用 XAML、程式碼或 XAML 設計工具，將項目 (控制項、配置和圖形) 加入至應用程式。 本主題說明如何在 Visual Studio 或 Blend for Visual Studio 中，使用 XAML 設計工具來處理項目。

## <a name="add-an-element-to-a-layout"></a>將項目新增至版面配置

「版面配置」是調整 UI 項目大小以及定位項目的程序。 若要定位視覺效果項目，您必須將它們放在版面配置 [Panel](xref:Windows.UI.Xaml.Controls.Panel)。 `Panel` 有一個子屬性，此子屬性是 [FrameworkElement](xref:Windows.UI.Xaml.FrameworkElement) 類型的集合。 您可以使用各種 `Panel` 子元素 (例如 [Canvas](xref:Windows.UI.Xaml.Controls.Canvas)、[StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) 和 [Grid](xref:Windows.UI.Xaml.Controls.Grid)) 作為版面配置容器，並在頁面上定位和排列元素。

根據預設，`Grid` 面板可做為頁面或表單中的最上層版面配置容器。 您可以在最上層頁面配置中加入配置面板、控制項或其他項目。

若要在 XAML 設計工具中將項目新增至版面配置，請執行下列其中一個動作：

- 按兩下 [工具箱] 中的項目 (或是在 [工具箱] 中選取項目，然後按 **Enter**)。

- 將項目從 [工具箱] 拖曳至畫板。

- 在 [工具箱] 中，選取其中一個繪圖工具 (例如 [Ellipse](xref:Windows.UI.Xaml.Shapes.Ellipse) 或 [Rectangle](xref:Windows.UI.Xaml.Shapes.Rectangle))，然後在使用中面板中繪製項目。

## <a name="change-the-layering-order-of-elements"></a>變更項目的圖層順序

當 XAML 設計工具的畫板上有兩個項目時，系統會依照圖層順序將其中一個項目顯示在另一個項目的前面。 [文件大綱] 視窗的項目清單底端是最上層項目 (設定項目的 **ZIndex** 屬性時除外)。 當您將項目插入頁面、表單或版面配置容器時，項目會自動放在作用中容器項目內其他項目的上層。 若要變更項目的順序，您可以使用 [順序] 命令，或在 [文件大綱] 視窗中拖曳物件樹狀結構中的項目。

若要變更圖層順序，請執行下列其中一個動作：

- 在 [文件大綱] 視窗中，將項目上下拖曳以建立所需的圖層順序。

- 在 [文件大綱] 視窗或畫板中，以滑鼠右鍵按一下您要變更圖層順序的項目，並指向 [順序]，然後按一下下列其中一項：

  - **提到最上層** 可將項目移到這個順序的最上層。

  - **上移一層** 可將項目在這個順序中上移一層。

  - **下移一層** 可將項目在這個順序中下移一層。

  - **移到最下層** 可將項目移到這個順序的最下層。

- 在 [屬性] 視窗的 [版面配置] 區段中，變更 **ZIndex** 屬性。 如有重疊的項目，**ZIndex** 屬性會優先於 [文件大綱] 視窗中顯示的項目順序。 當元素重疊時，具有較高 **ZIndex** 值的元素會出現在前面。

## <a name="change-the-alignment-of-an-element"></a>變更項目的對齊方式

您可以使用功能表命令或將項目拖曳至對齊線，來對齊畫板中的項目。

「對齊線」是視覺效果提示，可協助您以相對於應用程式中其他項目的方式對齊項目。

若要使用功能表命令來對齊兩個或多個項目：

1. 選取您要對齊的項目  您可以按住 **Ctrl** 鍵並選取項目，來選取多個項目。

2. 在 [屬性] 視窗的 [版面配置] 區段中，選取 **HorizontalAlignment** 下的下列其中一個屬性：[靠左]、[置中]、[靠右] 或 [自動縮放]。

3. 在 [屬性] 視窗的 [版面配置] 區段中，選取 **VerticalAlignment** 下的下列其中一個屬性：[靠上]、[置中]、[靠下] 或 [自動縮放]。

若要在包含至少兩個項目的版面配置中，使用 XAML 設計工具中的對齊線來對齊兩個或多個項目，請拖曳其中一個項目或調整其大小，使其邊緣對齊另一個項目的邊緣。

邊緣對齊時，會出現「對齊界限」以指出對齊方式。 對齊界限是一條紅色虛線。 只有在啟用 [貼齊至對齊線]  時才會顯示對齊界限。 如需顯示對齊界限的畫板圖例，請參閱[使用 XAML 設計工具建立 UI](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)。

## <a name="change-an-elements-margins"></a>變更項目的邊界

XAML 設計工具中的邊界決定畫板上項目周圍的空白間距。 例如，邊界指定項目的外緣與該項目所在 `Grid` 面板的界限之間的間距。 邊界也可指定 `StackPanel` 中內含項目之間的間距。

若要在 [屬性] 視窗中變更項目的邊界：

1. 選取要變更邊界的項目。

2. 在 [屬性] 視窗的 [版面配置] 下，變更任何 [邊界] 屬性 ([靠上]、[靠左]、[靠右] 或 [靠下]) 的值 (這些值以像素為單位，或使用裝置獨立單位，約 1/96 英吋)。

在畫板中，若要變更項目相對於項目版面配置容器的邊界，請在選取項目且該項目在版面配置容器中時，按一下出現在項目周圍的「邊界提示」。 如需顯示邊界提示的圖例，請參閱[使用 XAML 設計工具建立 UI](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)。

如果邊界提示呈開啟狀態 (不論是垂直或水平)，則表示尚未設定該邊界。 如果邊界提示呈關閉狀態，則表示已設定該邊界。

當您開啟邊界裝飾項但未設定相反側的邊界時，相反側的邊界會根據畫板中的項目位置設為正確的值。 請一律至少為相反側的邊界 (例如 [左] 和 [右] 邊界) 設定一個屬性。

> [!IMPORTANT]
> 放在某些版面配置容器 (例如 [Canvas](xref:Windows.UI.Xaml.Controls.Canvas)) 中的元素沒有邊界裝飾項。 視 `StackPanel` 的方向而定，放在 [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) 內的元素會有左右邊界或上下邊界的邊界裝飾項。

## <a name="group-and-ungroup-elements"></a>將項目群組和取消群組

在 XAML 設計工具中群組兩個以上的項目，可以建立新配置容器並將這些項目放在該容器內。 將兩個以上的項目一起放在配置容器中，可讓您輕鬆地選取、移動及轉換群組，就如同將該群組中的所有項目都當成一個項目。 群組對於識別彼此相關的項目也很有幫助，例如組成導覽項目的按鈕。 取消項目群組時，只要刪除內含項目的配置容器即可。

若要將項目群組成新的版面配置容器：

1. 選取您要群組的項目   (若要選取多個專案，請按住 **Ctrl** 鍵，同時按一下它們。 ) 

2. 以滑鼠右鍵按一下選取的項目，並指向 [群組置入]，然後按一下您要置入群組的版面配置容器類型。

    > [!TIP]
    > 如果您選取 [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox)、[Border](xref:Windows.UI.Xaml.Controls.Border) 或 [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) 來將元素分組，元素就會放在 [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border)或 [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) 內的新 [Grid](xref:Windows.UI.Xaml.Controls.Grid) 面板中。 如果您將這其中一個版面配置容器中的元素取消分組，則只會刪除 [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox)、[Border](xref:Windows.UI.Xaml.Controls.Border) 或 [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer)，[Grid](xref:Windows.UI.Xaml.Controls.Grid) 面板則會保留下來。 若要刪除 `Grid` 面板，請再次取消項目的群組。

若要將項目取消群組並刪除版面配置，請以滑鼠右鍵按一下您要取消群組的群組，然後按一下 [取消群組]。 您也可以以滑鼠右鍵按一下 [文件大綱] 視窗中的選取項目，然後按一下 [群組置入] 或 [取消群組]，將項目群組或取消群組。

## <a name="reset-the-element-layout"></a>重設項目配置

您可以使用版面配置重設命令，還原某個項目特定版面配置屬性的預設值。 您可以使用此命令，個別或全部重設項目的邊界、對齊方式、寬度、高度和大小。

若要重設專案配置，請以滑鼠右鍵按一下 [檔大綱] 視窗或畫板中的專案，然後選擇 [**版面** 配置  >  **重設** 屬性 *名稱*]，其中 *PropertyName* 是您想要重設的屬性 (或選擇 [全部 **重**  >  **設**]，以重設專案) 的所有版面配置屬性。

## <a name="see-also"></a>請參閱

- [使用 XAML 設計工具建立 UI](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)

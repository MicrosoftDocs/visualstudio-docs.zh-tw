---
title: 使用 XAML 設計工具建立 UI
ms.date: 03/28/2019
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3cd26f35111fc2e79290b30e7ae488b268e558d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899423"
---
# <a name="create-a-ui-by-using-xaml-designer-in-visual-studio"></a>在 Visual Studio 中使用 XAML 設計工具建立 UI

Visual Studio 中的 XAML 設計工具提供視覺化介面，協助您設計以 XAML 為基礎的 Windows 和 Web 應用程式。 您可以從 [工具箱]  拖曳控制項並在 [屬性]  視窗中設定屬性，藉此建立應用程式的使用者介面。 您也可以在 [XAML] 檢視中直接編輯 XAML。

如需進階 XAML 設計工作，例如動畫和行為，請參閱 [Creating a UI by using Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)。 如需工具之間的比較，另請參閱[在 Visual Studio 和 Blend for Visual Studio 中設計 XAML](../designers/designing-xaml-in-visual-studio.md)。

## <a name="xaml-designer-workspace"></a>XML 設計工具工作區

XAML 設計工具中的工作區是由數個視覺化介面項目所組成。 其中包括**畫板**、**XAML 編輯器**、[裝置] 視窗、[文件大綱] 視窗和 [屬性] 視窗。 若要開啟 XAML 設計工具，請以滑鼠右鍵按一下 [方案總管]  中的 XAML 檔案，然後選擇 [設計工具檢視] 。

## <a name="authoring-views"></a>製作檢視

XAML 設計工具提供 [XAML] 檢視和同步處理的 [設計] 檢視，來顯示應用程式呈現的 XAML 標記。 在 Visual Studio 中開啟 XAML 檔案後，您可以使用 [設計]  和 [XAML]  索引標籤，在 [設計] 檢視和 [XAML] 檢視之間切換。 您可以使用 [交換窗格]  按鈕，切換哪一個視窗要出現在最上方：畫板或 XAML 編輯器。

在 [設計] 檢視中，含有 *「畫板」* (Artboard) 的視窗是作用中視窗，可做為主要工作介面。 您可以透過它加入或繪製項目，然後修改這些項目，以視覺化方式在您的應用程式中設計頁面。 如需詳細資訊，請參閱 [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md)。 下圖顯示 [設計] 檢視中的畫板。

![XAML 設計工具的 [設計] 檢視](../designers/media/xaml_editor_design_view.png)

畫板可提供下列功能：

**對齊線**

對齊線是當控制項邊緣對齊時，或文字基線對齊時顯示為紅色虛線的 *「對齊界限」* (Alignment Boundary)。 只有在啟用 [貼齊至對齊線]  時才會顯示對齊界限。

**Grid 滑軌**

`Grid` 滑軌可用來管理 [Grid](/uwp/api/Windows.UI.Xaml.Controls.Grid) 面板中的資料列和資料行。 您可以建立及刪除列和欄，以及調整其相對寬度和高度。 出現在畫板左邊的垂直 Grid 滑軌適用於列，而出現在頂端的水平線則適用於欄。

**Grid 裝飾項**

格線提示會顯示為格線滑軌上已附加垂直或水平線的三角形。 當您拖曳格線提示時，相鄰欄或列的寬度或高度會在您移動滑鼠時更新。

格線提示可用來控制格線之列和欄的的寬度和高度。 您可以在格線滑軌中按一下，新增欄或列。 當您針對具有兩個或更多欄或列的格線面板新增列或欄時，出現在滑軌外部的迷你工具列可讓您明確地設定寬度和高度。 這個迷你工具列可讓您設定格線列和欄的調整大小選項。

**調整控點大小**

調整大小控點會出現在選取的控制項上，讓您調整控制項的大小。 當您調整控制項的大小時，通常會出現寬度和高度值，協助您調整控制項的大小。 如需在 [設計] 檢視中操作控制項的詳細資訊，請參閱[在 XAML 設計工具中使用項目](../designers/working-with-elements-in-xaml-designer.md)。

**邊界**

邊界代表控制項邊緣與其容器邊緣之間的固定間距。 您可以使用 [屬性] 視窗中 **[版面配置]** 底下的 [Margin](/uwp/api/windows.ui.xaml.frameworkelement.margin) 屬性設定控制項的邊界。

**邊界裝飾項**

您可以使用邊界裝飾項來變更項目相對於其版面配置容器的邊界。 當邊界裝飾項呈開啟狀態時，則未設定邊界且邊界裝飾項會顯示中斷的鏈結。 如果未設定邊界，則在執行階段調整版面配置容器的大小時，項目的位置維持不變。 當邊界裝飾項呈關閉狀態時，邊界裝飾項會顯示不中斷的鏈結，而且在執行階段調整版面配置容器的大小時，項目會隨著邊界移動 (邊界會保持固定)。

**項目控點**

您可以利用指標移至項目周圍之藍色方塊的角落時出現在畫板上的項目控點，對項目進行修改。 這些控點可讓您旋轉項目、調整項目大小、翻轉項目、移動項目，或將圓角半徑加入項目。 項目控點的符號因函式而有所不同，並根據指標的確切位置而變更。 如果看不到項目控點，請確定已選取項目。

在 [設計] 檢視中，畫面的左下方區域會提供其他畫板命令，如下所示：

![設計檢視命令](../designers/media/xaml_editor_design_controls.png)

這個工具列提供下列命令：

**縮放**

縮放可讓您調整設計介面的大小。 您可以從 12.5% 放大到 800%，或選取 [調整成選取的大小]  和 [調整成全部的大小] 等選項。

**顯示/隱藏貼齊格線**

顯示或隱藏可顯示格線的貼齊格線。 啟用 [貼齊至格線] 或 [貼齊至對齊線] 時會使用格線。

**開啟/關閉貼齊至格線**

如果在畫板上拖曳項目時啟用了 [貼齊至格線]  ，該項目通常會對齊最接近的水平和垂直格線。

**開啟/關閉貼齊至對齊線**

對齊線可協助您讓控制項彼此對齊。 如果已啟用 [貼齊至對齊線]  ，當您將控制項拖曳到其他控制項的相對位置，而部分控制項的邊緣和文字水平或垂直對齊時，對齊界限就會出現。 對齊界限會顯示為一條紅色虛線。

在 [XAML] 檢視中，含有 XAML 編輯器的視窗是作用中視窗，而 XAML 編輯器是您主要的撰寫工具。 可延伸應用程式標記語言 (XAML) 提供宣告式的 XML 架構詞彙來指定應用程式的使用者介面。 [XAML] 檢視包括 IntelliSense、自動格式化、語法反白顯示和標記巡覽。 下圖顯示 [XAML] 檢視：

![[XAML] 檢視](../designers/media/xaml_editor.png)

**分割檢視列**

當 XAML 編輯器位於視窗下方時，分割檢視列就會出現在 [XAML] 檢視的頂端。 分割檢視列可讓您控制 [設計] 檢視和 [XAML] 檢視的相對大小。 您也可以交換檢視的位置 (使用 [交換窗格]  按鈕)，指定要水平或垂直排列檢視，以及是否摺疊任一個檢視。

**標記縮放**

標記縮放可讓您調整 [XAML] 檢視的大小。 您可以從 20% 放大到 400%。

## <a name="document-outline-window"></a>文件大綱視窗

XAML 設計工具的 [文件大綱] 視窗類似 Blend for Visual Studio 的 [物件與時間軸] 視窗。 [文件大綱] 會協助您執行下列工作：

- 檢視畫板上所有項目的階層式結構。

- 選取項目以進行修改 (在階層中進行移動、在畫板上進行修改、在 [屬性] 視窗中設定其屬性等)。 如需詳細資訊，請參閱[在 XAML 設計工具中使用項目](../designers/working-with-elements-in-xaml-designer.md)。

- 為控制項項目建立及修改樣板。

- 使用所選元素的右鍵功能表 (操作功能表)。 畫板中選取的項目也可以使用相同的功能表。

若要檢視 [文件大綱] 視窗，請在功能表列上依序選擇 [檢視] > [其他視窗] > [文件大綱]。

![Visual Studio 的 [文件大綱] 視窗](../designers/media/document-outline-window.png)

[文件大綱] 視窗中的可用選項包括：

**文件大綱**

[文件大綱] 視窗的主要檢視會以樹狀結構顯示文件的階層。 您可以利用文件大綱的階層本質，在各種詳細層級上檢查文件，以及單獨或依群組鎖定和隱藏項目。

**顯示/隱藏**

顯示或隱藏 [文件大綱] 中的項目所對應的畫板項目。 使用 [顯示/隱藏] 按鈕 (顯示時會出現眼睛符號)，或者按 **CTRL**+**H** 隱藏項目及按 **Shift**+**Ctrl**+**H** 顯示項目。

**鎖定/解除鎖定**

鎖定或解除鎖定對應文件大綱項目的畫板項目。 無法修改鎖定的項目。 使用 [鎖定/解除鎖定] 按鈕 (鎖定時會出現掛鎖符號)，或者按 **Ctrl**+**L** 鎖定項目及按 **Shift**+**Ctrl**+**L** 解除鎖定。

**將範圍傳回 pageRoot**

[文件大綱] 視窗頂端顯示向上箭號符號的選項，可將文件大綱傳回到前一個範圍。 只有您在樣式或樣板的範圍內時，選定範圍才適用。

## <a name="properties-window"></a>屬性視窗

[屬性] 視窗可讓您設定控制項的屬性值。 看起來如下：

![屬性視窗](../designers/media/xaml-designer-properties-window.png)

[屬性] 視窗的頂端有各種選項。 您可以使用 [名稱]  方塊，變更目前選取項目的名稱。 在左上角，有一個代表目前選取項目的圖示。 若要依分類或依字母順序排列屬性，請按一下 [排列依據] 清單中的 [分類] 、[名稱]  或 [來源]  。 若要查看控制項的事件清單，請按一下顯示閃電符號的 [事件]  按鈕。

若要搜尋屬性，請在搜尋方塊中開始鍵入屬性的名稱。 在您鍵入文字時，[屬性] 視窗會顯示符合搜尋的屬性。 有些屬性可讓您藉由選取向下箭號按鈕來設定進階屬性。

如需使用屬性和處理事件的詳細資訊，請參閱[控制項和模式簡介](/windows/uwp/design/controls-and-patterns/controls-and-events-intro)

每個屬性值的右邊是顯示為方塊符號的 *「屬性標記」* (Property Marker)。 屬性標記的有無表示屬性是否已套用資料繫結或資源。 例如，白色方塊符號表示預設值，黑色方塊符號通常表示已套用本機資源，而橙色方塊通常表示已套用資料繫結。 當您按一下屬性標記時，您可以巡覽至樣式定義、開啟資料繫結產生器，或開啟資源選擇器。

## <a name="see-also"></a>另請參閱

- [使用 XAML 設計工具中的元素](../designers/working-with-elements-in-xaml-designer.md)
- [如何建立和套用資源](../designers/how-to-create-and-apply-a-resource.md)
- [逐步解說：在 XAML 設計工具中繫結至資料](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
---
title: XAML 設計工具概觀
description: 深入瞭解 Blend for Visual Studio 中的 XAML 設計工具工作區 UI 和功能，其中提供視覺化介面，協助您設計以 XAML 為基礎的應用程式。
ms.custom: SEO-VS-2020
ms.date: 03/03/2020
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
- Blend.Start.Dev12
ms.devlang: CSharp
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 132a5aef33b501ad17a2a089684cfe927321b2e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966483"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>使用 XAML 設計工具建立 UI

Visual Studio 和 Blend for Visual Studio 中的 XAML 設計工具提供視覺化介面，協助您設計以 XAML 為基礎的應用程式，例如 WPF 和 UWP。 您可以藉由從 [工具箱] 視窗 (在 Blend for Visual Studio 的 [資產] 視窗中) 拖曳控制項，並在 [屬性] 視窗中設定屬性，為您的應用程式建立使用者介面。 您也可以在 [XAML] 檢視中直接編輯 XAML。

如果是進階使用者，您甚至可以[自訂 XAML 設計工具](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md)。

> [!NOTE]
> Xamarin 不支援 XAML 設計工具。 若要在應用程式執行時，查看您的 Xamarin. Forms XAML Ui 並進行編輯，請使用適用于 Xamarin 的 XAML 熱重新載入。 如需詳細資訊，請參閱 [適用于 Xamarin (Preview 的 XAML 熱重新載入) ](/xamarin/xamarin-forms/xaml/hot-reload/) 頁面。

## <a name="xaml-designer-workspace"></a>XML 設計工具工作區

XAML 設計工具中的工作區是由數個視覺化介面項目所組成。 這包括「畫板」 (視覺化設計界面)、XAML 編輯器、[文件大綱] 視窗 (Blend for Visual Studio 中的 [物件與時間軸] 視窗)，以及 [屬性] 視窗。 若要開啟 XAML 設計工具，請以滑鼠右鍵按一下 [方案總管]  中的 XAML 檔案，然後選擇 [設計工具檢視] 。

XAML 設計工具提供 [XAML] 檢視和同步處理的 [設計] 檢視，來顯示應用程式呈現的 XAML 標記。 在 Visual Studio 或 Blend for Visual Studio 中開啟 XAML 檔案之後，您可以使用 [設計] 和 [XAML] 索引標籤，在 [設計] 檢視與 [XAML] 檢視之間切換。 您可以使用 [交換窗格] 按鈕 ![「XAML 設計工具」中的 [交換窗格] 按鈕](media/swap-panes.PNG) 來切換要出現在最上方的視窗：畫板或 XAML 編輯器。

### <a name="design-view"></a>設計檢視

在 [設計] 檢視中，含有畫板的視窗是作用中視窗，您可以使用它作為主要工作介面。 您可以使用它，透過新增、繪製或修改元素，以視覺化方式設計您應用程式中的頁面。 如需詳細資訊，請參閱[使用 XAML 設計工具中的項目](../xaml-tools/working-with-elements-in-xaml-designer.md)。 下圖顯示 [設計] 檢視中的畫板。

![XAML 設計工具的 [設計] 檢視](media/xaml-artboard.png)

畫板可提供下列功能：

**對齊線**

對齊線是當控制項邊緣對齊或文字基線對齊時，要出現並顯示為紅色虛線的「對齊界限」。 只有在啟用 [貼齊至對齊線]  時才會顯示對齊界限。

**Grid 滑軌**

Grid 滑軌可用來管理 [Grid](xref:Windows.UI.Xaml.Controls.Grid) 面板中的資料列和資料行。 您可以建立及刪除列和欄，以及調整其相對寬度和高度。 出現在畫板左邊的垂直 Grid 滑軌適用於列，而出現在頂端的水平線則適用於欄。

**Grid 裝飾項**

格線提示會顯示為格線滑軌上已附加垂直或水平線的三角形。 當您拖曳格線提示時，相鄰欄或列的寬度或高度會在您移動滑鼠時更新。

格線提示可用來控制格線之列和欄的的寬度和高度。 您可以在格線滑軌中按一下，新增欄或列。 當您針對具有兩個或更多欄或列的格線面板新增列或欄時，出現在滑軌外部的迷你工具列可讓您明確地設定寬度和高度。 這個迷你工具列可讓您設定格線列和欄的調整大小選項。

![XAML 設計工具中的 Grid 裝飾項](media/grid-adorner.png)

**調整控點大小**

調整大小控點會出現在選取的控制項上，讓您調整控制項的大小。 當您調整控制項的大小時，通常會出現寬度和高度值，協助您調整控制項的大小。 如需有關在 [設計] 檢視中操作控制項的詳細資訊，請參閱[使用 XAML 設計工具中的項目](../xaml-tools/working-with-elements-in-xaml-designer.md)。

**邊界**

邊界代表控制項邊緣與其容器邊緣之間的固定間距。 您可以使用 [**屬性**] 視窗中 [**版面** 配置] 下的 [[邊界](xref:Windows.UI.Xaml.FrameworkElement.Margin)] 屬性來設定控制項的邊界。

**邊界裝飾項**

使用邊界裝飾項來變更元素相對於其版面配置容器的邊界。 當邊界裝飾項呈開啟狀態時，則未設定邊界且邊界裝飾項會顯示中斷的鏈結。 如果未設定邊界，則在執行階段調整版面配置容器的大小時，項目的位置維持不變。 當邊界裝飾項呈關閉狀態時，邊界裝飾項會顯示不中斷的鏈結，而且在執行階段調整版面配置容器的大小時，項目會隨著邊界移動 (邊界會保持固定)。

**項目控點**

您可以利用指標移至項目周圍之藍色方塊的角落時出現在畫板上的項目控點，對項目進行修改。 這些控點可讓您旋轉項目、調整項目大小、翻轉項目、移動項目，或將圓角半徑加入項目。 元素控點的符號會因函式而有所不同，並依指標的確切位置而變更。 如果看不到項目控點，請確定已選取項目。

在 [設計] 檢視中，視窗的左下方區域會提供額外的畫板命令，如下所示：

![設計檢視命令](media/xaml-design-view-controls.png)

這個工具列提供下列命令：

**縮放**

縮放可讓您調整設計介面的大小。 您可以從 12.5% 放大到 800%，或選取 [符合選取項目] 和 [全部調整] 等選項。

**顯示/隱藏貼齊格線**

顯示或隱藏可顯示格線的貼齊格線。 啟用 [貼齊至格線] 或 [貼齊至對齊線] 時會使用格線。

**開啟/關閉貼齊至格線**

如果已啟用 [ **貼齊至格線** ]，當您將專案拖曳到畫板上時，元素通常會對齊最接近的水準和垂直格線。

**切換畫板背景**

在淺色與深色背景之間切換。

**開啟/關閉貼齊至對齊線**

對齊線可協助您讓控制項彼此對齊。 如果已啟用 [貼齊至對齊線]  ，當您將控制項拖曳到其他控制項的相對位置，而部分控制項的邊緣和文字水平或垂直對齊時，對齊界限就會出現。 對齊界限會顯示為一條紅色虛線。

**停用專案程式碼**

停用[專案程式碼](debugging-or-disabling-project-code-in-xaml-designer.md) (例如自訂控制項和值轉換器)，並重新載入設計工具。

### <a name="xaml-view"></a>[XAML] 檢視

在 [XAML] 檢視中，含有 XAML 編輯器的視窗是作用中視窗，而 XAML 編輯器是您主要的撰寫工具。 可延伸應用程式標記語言 (XAML) 提供宣告式的 XML 架構詞彙來指定應用程式的使用者介面。 [XAML] 檢視包括 IntelliSense、自動格式化、語法反白顯示和標記巡覽。 下圖顯示已開啟 IntelliSense 功能表的 XAML 檢視：

![[XAML] 檢視](media/xaml-editor.png)

## <a name="document-outline-window"></a>文件大綱視窗

Visual Studio 中的 [文件大綱] 視窗類似 Blend for Visual Studio 中的 [[物件與時間軸] 視窗](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window)。 [文件大綱] 可協助您執行下列工作：

- 檢視畫板上所有項目的階層式結構。

- 選取專案，讓您可以加以修改。 例如，您可以在階層中四處移動，或在屬性視窗中設定其屬性。 如需詳細資訊，請參閱[使用 XAML 設計工具中的項目](../xaml-tools/working-with-elements-in-xaml-designer.md)。

- 為控制項項目建立及修改樣板。

- [建立動畫](animate-objects-in-xaml-designer.md) (僅適用於 Blend for Visual Studio)。

若要在 Visual Studio 中查看 [檔大綱] 視窗，請在功能表列上選取 [**查看**  >  **其他 Windows**  >  **檔大綱**]。
若要在 Blend for Visual Studio 中查看物件與時間軸視窗，請在功能表列上選取 [**視圖**  >  **檔大綱**]。

![Visual Studio 的 [文件大綱] 視窗](media/document-outline-window.png)

[文件大綱]/[物件與時間軸] 視窗的主要檢視會以樹狀結構顯示文件的階層。 您可以利用文件大綱的階層本質，以各種不同詳細層級檢查文件，以及單獨或依群組鎖定和隱藏元素。 [檔大綱]/物件與時間軸視窗中提供下列選項：

**顯示/隱藏**

顯示或隱藏畫板元素。 出現時，會顯示為眼睛符號。 您也可以按 **ctrl** + **h** 來隱藏專案，並使用 **Shift** + **ctrl** + **h** 來顯示它。

**鎖定/解除鎖定**

將畫板元素鎖定或解除鎖定。 無法修改鎖定的項目。 鎖定時，會顯示為掛鎖符號。 您也可以按 **ctrl** + **l** 來鎖定元素，並 + 將 **ctrl** + **l** 解除鎖定。

**將範圍傳回 pageRoot**

[文件大綱]/[物件與時間軸] 視窗頂端顯示向上箭號符號的選項，可移至前一個範圍。 只有您在樣式或樣板的範圍內時，選定範圍才適用。

## <a name="properties-window"></a>屬性視窗

[屬性] 視窗可讓您設定控制項的屬性值。 其看起來會像下面這樣：

![屬性視窗](media/xaml-designer-properties-window.png)

[屬性] 視窗的頂端有各種選項：

- 變更 [名稱] 方塊中目前所選元素的名稱。
- 在左上角，有一個代表目前選取項目的圖示。
- 若要依分類或依字母順序排列屬性，請按一下 [排列依據] 清單中的 [分類] 、[名稱]  或 [來源]  。
- 若要查看控制項的事件清單，請按一下顯示為閃電符號的 [事件] 按鈕。
- 若要搜尋屬性，請在搜尋方塊中開始鍵入屬性的名稱。 在您鍵入文字時，[屬性] 視窗會顯示符合搜尋的屬性。

有些屬性可讓您藉由選取向下箭號按鈕來設定進階屬性。

每個屬性值的右邊是顯示為方塊符號的 *「屬性標記」* (Property Marker)。 屬性標記的有無表示屬性是否已套用資料繫結或資源。 例如，白色方塊符號表示預設值，黑色方塊符號通常表示已套用本機資源，而橙色方塊通常表示已套用資料繫結。 當您按一下屬性標記時，您可以巡覽至樣式定義、開啟資料繫結產生器，或開啟資源選擇器。

如需有關使用屬性及處理事件的詳細資訊，請參閱[控制項和模式的簡介](/windows/uwp/design/controls-and-patterns/controls-and-events-intro)。

## <a name="see-also"></a>另請參閱

- [使用 XAML 設計工具中的項目](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [如何建立和套用資源](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [逐步解說：在 XAML 設計工具中繫結至資料](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)

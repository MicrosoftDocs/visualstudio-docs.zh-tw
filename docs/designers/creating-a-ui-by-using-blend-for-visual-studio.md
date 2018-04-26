---
title: 使用 Blend for Visual Studio 建立 UI
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66addedc32c7023e774cd28f340f8216516c3fb7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>使用 Blend for Visual Studio 建立 UI

Blend for Visual Studio 可協助您設計以 XAML 為基礎的 Windows 及 Web 應用程式。 它提供與 Visual Studio 相同的基本 XAML 設計體驗，並新增可處理動畫和表現方式等進階工作的視覺化設計工具。 如需 Blend 和 Visual Studio之間的比較，請參閱[在 Visual Studio 和 Blend for Visual Studio 中設計 XAML](../designers/designing-xaml-in-visual-studio.md)。

Blend for Visual Studio 是 Visual Studio 的元件。 若要安裝 Blend，請在 **Visual Studio 安裝程式**中選擇 **通用 Windows 平台開發**或 **.NET 桌面開發**工作負載。 這兩個工作負載都包含 Blend for Visual Studio 元件。

![UWP 工作負載元件](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![.NET 桌面開發工作負載元件](media/installer-dotnet-desktop.png)

如果您是 Blend for Visual Studio 的新手，請花點時間熟悉工作區的獨特功能。 本主題會帶領您快速導覽。

> [!NOTE]
> 若要導覽共用的設計功能，例如畫板、[文件大綱] 視窗和 [裝置] 視窗，請參閱[使用 XAML 設計工具建立 UI](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)。

## <a name="tour-of-the-tools-panel"></a>[工具] 面板導覽

您可以使用 Blend for Visual Studio 中的 [工具] 面板來建立及修改應用程式中的物件。 您可以選取工具，然後使用滑鼠在畫板上繪製以建立物件。

![[工具] 面板](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|||||
|-|-|-|-|
|![](../designers/media/b1_1.png "B1_1")|**選取工具**：選取物件和路徑。<br /><br /> 使用 [直接選取] 工具可選取巢狀物件和路徑區段。|![圖說文字 A](../designers/media/b5_label_a.png "b5_label_A")|**漸層和筆刷工具**|
|![](../designers/media/b1_2.png "B1_2")|**檢視工具**：調整畫板的檢視方式，例如移動瀏覽和縮放。|![圖說文字 B](../designers/media/b5_label_b.png "b5_label_B")|**路徑工具**|
|![](../designers/media/b1_3.png "B1_3")|**筆刷工具**：處理物件的視覺屬性，例如轉換筆刷、繪製物件，或選取某個物件的屬性以套用至另一個物件。|![圖說文字 C](../designers/media/b5_label_c.png "b5_label_C")|**圖形工具**|
|![](../designers/media/b1_4.png "B1_4")|**物件工具**：繪製畫板上最常用的物件，例如路徑、圖形、版面配置面板、文字及控制項。|![圖說文字 D](../designers/media/b5_label_d.png "b5_label_D")|**版面配置面板**|
|![](../designers/media/b1_5.png "B1_5")|**資產工具**：存取 [資產] 面板，以及顯示資產庫中最近使用過的資產。|![圖說文字 E](../designers/media/b5_label_e.png "b5_label_E")|**文字控制項**|
|||![圖說文字 F](../designers/media/b5_label_f.png "b5_label_F")|**通用控制項**|

**觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [工具列](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4)。

## <a name="tour-of-the-assets-panel"></a>[資產] 面板導覽

您可以在 [資產] 面板中找到所有控制項，這個面板類似 Visual Studio 中的 [工具箱]。 除了控制項之外，您還會在 [資產] 面板中找到可新增至畫板的所有項目，包括樣式、媒體、行為和效果。

![[資產] 面板](../designers/media/blend5_assets_panel.png "Blend5_Assets_panel")

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**搜尋方塊**：在 [搜尋] 方塊中輸入文字，即可篩選資產清單。|
|![](../designers/media/b1_2.png "B1_2")|**格線模式與清單模式**：切換資產的 [格線模式] 檢視與 [清單模式] 檢視。|
|![](../designers/media/b1_3.png "B1_3")|**資產分類**：按一下分類或子分類可檢視該分類中的資產清單。|
|![](../designers/media/b1_4.png "B1_4")|**樣式**：顯示資源字典中所包含的所有樣式。|
|![](../designers/media/b1_5.png "B1_5")|**描述**：檢視所選的資產分類或子分類的描述。|

## <a name="tour-of-the-objects-and-timeline-panel"></a>[物件與時間軸] 面板導覽

使用這個面板可依所需在畫板上組織物件以製作動畫。

![動畫模式中的 [物件與時間軸] 面板](../designers/media/b5_object_timeline_animation.png "b5_object_timeline_animation")

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**物件檢視**：檢視文件的視覺化樹狀結構。 您可以向下鑽研至不同層級的詳細資料。 您也可以加入圖層，以進一步組織畫板上的物件。 如此一來您就能以群組形式加以鎖定並隱藏。|
|![](../designers/media/b1_2.png "B1_2")|**錄製模式指標**：查看時間軸中是否正在錄製屬性變更。|
|![](../designers/media/b1_3.png "B1_3")|**分鏡腳本選擇器**：檢視您所建立的分鏡腳本清單。|
|![](../designers/media/b1_4.png "B1_4")|**關閉分鏡腳本**：關閉目前的分鏡腳本。|
|![](../designers/media/b1_5.png "B1_5")|**分鏡腳本選項**：建立、重複、回復、刪除、重新命名或關閉分鏡腳本。|
|![](../designers/media/b1_6.png "B1_6")|**播放控制項**：透過時間軸瀏覽。 您也可以拖曳播放點來瀏覽 (或「快轉」) 時間軸。|
|![](../designers/media/b1_7.png "B1_7")|**將範圍傳回**：讓物件檢視範圍回到前一個根物件或前一個範圍。 只有在要修改樣式或範本時才能這麼做。|
|![](../designers/media/b1_8.png "B1_8")|**錄製主要畫面格**：錄製目前時間點上所選物件屬性的快照集。|
|![](../designers/media/b1_9.png "B1_9")|**貼齊選項**：設定時間軸貼齊、貼齊解析度，以及關閉時間軸貼齊。|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**顯示/隱藏**、**鎖定/解除鎖定**：顯示或隱藏物件檢視的可見性與鎖定選項。|
|![](../designers/media/b1_11.png "B1_11")|**時間軸上的播放點位置**：以毫秒為單位顯示目前時間。 您也可以在此欄位中直接輸入時間值，以跳至特定的時間點。 精確度取決於 [貼齊選項] 中設定的貼齊解析度。|
|![](../designers/media/b1_12.png "B1_12")|**播放點**：判斷動畫位於哪個時間點。 您可以在時間軸上拖曳播放點來預覽動畫。|
|![](../designers/media/b1_13.png "B1_13")|**時間軸上設定的主要畫面格**：變更特定時間點的屬性值。|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**變更物件順序**：設定物件的顯示順序。 按一下此按鈕可在結構檢視中依 Z 順序 (由前至後) 或依標記順序 (物件出現在 **XAML** 檢視中的順序) 來排列物件。|
|![](../designers/media/b1_15.png "B1_15")|**時間軸縮放**：設定時間軸的縮放解析度。 放大可讓您更詳細地編輯動畫，而縮小則可顯示更長時間內所發生的概況詳情。 如果放大後無法在所要的時間點上設定主要畫面格，請驗證貼齊解析度是否設定得夠高。|
|![圖說文字 16](../designers/media/b5_label_16.png "b5_label_16")|**時間軸組合區域**：檢視時間軸，並拖曳主要畫面格或使用其捷徑功能表以使其來回移動。|

## <a name="tour-of-the-properties-panel"></a>[屬性] 面板導覽

使用此面板可檢視和修改物件的屬性。 您也可以直接在畫板上設定屬性。 如果這麼做，屬性變更將反映在 [屬性] 面板中。

![[屬性] 面板](../designers/media/blend5_properties_panel.png "Blend5_properties_panel")

**分類**：展開和摺疊屬性的分類。 按一下 [展開] ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") 和 [摺疊] ![摺疊](../designers/media/b5_collapse_button.png "b5_collapse_button")，即可顯示或隱藏分類詳細資料。

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**名稱及類型**：檢視所選物件的圖示、名稱及類型。|
|![](../designers/media/b1_2.png "B1_2")|**排列依據**：依名稱、來源或分類的字母順序排列屬性。|
|![](../designers/media/b1_3.png "B1_3")|**筆刷屬性**：設定筆刷的視覺屬性，例如 [填滿] 筆刷、[筆觸] 筆刷和 [前景] 筆刷。|
|![](../designers/media/b1_4.png "B1_4")|**色彩編輯器**：使用單色和漸層筆刷。|
|![](../designers/media/b1_5.png "B1_5")|**色彩選擇器**：選取色彩。|
|![](../designers/media/b1_6.png "B1_6")|**色卡**：檢視初始色彩、目前色彩和最後色彩|
|![](../designers/media/b1_7.png "B1_7")|**色彩選擇工具**：在螢幕上使用任何元素的色彩。 選取 [單色筆刷] 時可以使用 [色彩選擇工具]。 選取 [漸層筆刷] 時可以使用 [色彩選擇工具]。|
|![](../designers/media/b1_8.png "B1_8")|**屬性和事件**：設定屬性或選擇所選元素的事件。|
|![](../designers/media/b1_9.png "B1_9")|**搜尋方塊**：搜尋屬性。 在 [搜尋] 方塊中輸入文字，以篩選所顯示的屬性。|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**筆刷編輯器索引標籤**：用來選取筆刷編輯器。 您可以選擇 [無筆刷]、[單色筆刷]、[漸層筆刷]、[拼貼筆刷] 或 [筆刷資源]。|
|![](../designers/media/b1_11.png "B1_11")|**色彩資源**：將完全相同的色彩套用到不同的屬性。 [色彩資源] 索引標籤包含 [本機資源] 和 [系統資源]。|
|![](../designers/media/b1_12.png "B1_12")|**RGB 色彩空間**：調整 [R]、[G] 或 [B] (紅色、綠色、藍色) 數字編輯器的值來修改色彩。|
|![](../designers/media/b1_13.png "B1_13")|**Alpha 色板**：使用 [A] 旁邊的數字編輯器來修改 Alpha 值。|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**將色彩轉換成資源**：將選取的色彩轉換成色彩資源。 當您按一下 [色彩資源] 索引標籤時會顯示色彩資源。|
|![](../designers/media/b1_15.png "B1_15")|**十六進位值**：檢視所顯示色彩的十六進位值。|
|![圖說文字 16](../designers/media/b5_label_16.png "b5_label_16")|**漸層滑桿**：只有選取漸層筆刷時才會出現。|
|![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8")|**顯示進階屬性**：檢視較不常用之屬性的分類。|

**觀看短片︰**![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [[屬性] 面板](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7)。

## <a name="see-also"></a>另請參閱

- [插入控制項並修改其行為](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [製作物件動畫](../designers/animate-objects-in-xaml-designer.md)
- [繪製圖案與路徑](../designers/draw-shapes-and-paths.md)
- [在 Visual Studio 和 Blend for Visual Studio 中設計 XAML](../designers/designing-xaml-in-visual-studio.md)
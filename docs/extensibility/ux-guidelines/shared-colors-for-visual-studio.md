---
title: 適用於 Visual Studio 共用色彩 |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c4a4a25c2dfdeb33bfadcf8416a0cbc4726658
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649950"
---
# <a name="shared-colors-for-visual-studio"></a>適用於 Visual Studio 的共用的色彩
當您在設計 UI 使用通用的 Visual Studio shell 項目，或您想要介面項目保持一致與類似的功能時，使用套件定義檔案中現有的語彙基元名稱，以選擇並指派色彩。 這可確保您的 UI 與整體 Visual Studio 環境保持一致，而且會在加入或更新佈景主題時自動更新。

本文說明常見 UI 項目以及它們使用的語彙基元名稱，以在建置類似的 UI 時進行參考。 如需如何存取這些色彩語彙基元的特定資訊，請參閱 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。

請務必正確地使用語彙基元名稱：

-   **使用根據函式，不是色彩本身的語彙基元名稱。** 常見共用色彩是與特定介面項目相關聯，並且僅適用於相同或類似的功能。 例如，請不要只因為您喜歡微調進度動畫之已按下下拉式方塊的色彩，就重複使用該色彩。 下拉式方塊和動畫的函式不同，而且如果與下拉式方塊變更相關聯的色彩，可能不再是動畫項目的適當色彩。 一致地使用色彩可協助引導您的使用者並避免混淆。

-   **以正確的組合來使用背景和文字色彩。** 要與文字搭配使用的背景色彩將有相關聯的文字色彩。 務必使用背景所指定的文字色彩。 如果沒有相關聯的文字色彩，請勿使用該背景色彩，您希望顯示文字的任何介面。 其他的文字和背景色彩組合可能會導致介面無法讀取。

-   **使用其位置適用的控制項色彩。** 處於特定狀態中，部分 Visual Studio 控制項沒有個別框線和背景色彩。 而是會選取其後介面的色彩。 務必根據控制項所放置的位置，而為其使用適合的語彙基元名稱。

> [!IMPORTANT]
> 請勿使用 「 起始頁 」 或"Cider"。 類別目錄中的權杖

## <a name="common-shared-controls"></a>通用共用控制項

當您使用標準的 Visual Studio 命令列在您的功能時，您必須已設定樣式的 shell 控制項的存取。 您不應該重新範本這些常見的控制項。 不過，如果您需要建置自訂命令列，則可能也需要建置自訂控制項。 在該情況下，請務必針對下列每個控制項使用正確的語彙基元名稱，讓您的 UI 與 Visual Studio 的其餘部分一致。

### <a name="button-controls"></a>按鈕控制項

![按鈕控制項紅線](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303年 155_ButtonControlRedline")

| 使用... | 請勿使用... |
| --- | --- |
| ...為您想要使用 Visual Studio 佈景主題 （淺、 暗色調、 藍色或系統高對比佈景主題） 整合的文件區域中的按鈕。 | ...，將會顯示針對不屬於 Visual Studio 佈景主題的自訂背景的按鈕。 |

**Button： 標準狀態**

![標準按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />標準按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.Button` |
| 按鈕框線 | `CommonControls.ButtonBorder` |

**Button： 預設狀態**

![預設值 按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />預設值 按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonDefault` |
| 按鈕框線 | `CommonControls.ButtonBorderDefault` |

**停用的狀態的按鈕：**

![已停用的按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />已停用的按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonDisabled` |
| 按鈕框線 | `CommonControls.ButtonBorderDisabled` |

**Button： 暫留狀態**

![動態顯示按鈕](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />停留時顯示按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonHover` |
| 按鈕框線 | `CommonControls.ButtonBorderHover` |

**已按下的狀態的按鈕：**

![已按下的按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />已按下的按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonPressed` |
| 按鈕框線 | `CommonControls.ButtonBorderPressed` |

**按鈕： 已取得焦點狀態**

![焦點的按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />焦點的按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonFocused` |
| 按鈕框線 | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>核取方塊控制項
![核取方塊 （紅線）](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303年 161_CheckboxRedline")<br />核取方塊 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...在文件內含的核取方塊控制項的區域。 | ...的任何未核取方塊控制項的 UI。 |

**核取方塊： 預設狀態**

![Check box](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />預設值 核取方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackground` |
| Border | `CommonControls.CheckBoxBorder` |
| 文字 | `CommonControls.CheckBoxText` |
| 圖像 | `CommonControls.CheckBoxGlyph` |

**核取方塊： 停用狀態**

![已停用核取方塊](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303年 163_CheckboxDisabled")<br />已停用核取方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundDisabled` |
| Border | `CommonControls.CheckBoxBorderDisabled` |
| 文字 | `CommonControls.CheckBoxTextDisabled` |
| 圖像 | `CommonControls.CheckBoxGlyphDisabled` |

**核取方塊： 將滑鼠停留狀態**

 ![暫留時的核取方塊](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303年 164_CheckboxHover")<br />停留時顯示核取方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundHover` |
| Border | `CommonControls.CheckBoxBorderHover` |
| 文字 | `CommonControls.CheckBoxTextHover` |
| 圖像 | `CommonControls.CheckBoxGlyphHover` |

**核取方塊： 按下狀態**

![已按下核取方塊](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303年 165_CheckboxPressed")<br />已按下核取方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundPressed` |
| Border | `CommonControls.CheckBoxBorderPressed` |
| 文字 | `CommonControls.CheckBoxTextPressed` |
| 圖像 | `CommonControls.CheckBoxGlyphPressed` |

**核取方塊： 狀態已取得焦點**

![具有焦點的核取方塊](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303年 166_CheckboxFocused")<br />具有焦點的核取方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundFocused` |
| Border | `CommonControls.CheckBoxBorderFocused` |
| 文字 | `CommonControls.CheckBoxTextFocused` |
| 圖像 | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>下拉式清單和下拉式方塊
![Drop-down/combo box (redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />下拉式清單下拉式方塊 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...的下拉式清單和下拉式方塊中的文件也。 | ...的任何不是下拉式清單或下拉式方塊的 UI。 |
| | ...的命令列[下拉式清單](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)或是[下拉式方塊](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)。 |

**下拉式清單和下拉式方塊： 預設狀態**

![Default drop-down/combo box](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />預設清單/下拉式方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackground` |
| Border | `CommonControls.ComboBoxBorder` |
| 文字 | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| 圖像 | `CommonControls.ComboBoxGlyph` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackground` |

**下拉式清單和下拉式方塊： 停用狀態**

![Disabled drop-down/combo box](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />停用的下拉式清單下拉式方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundDisabled` |
| Border | `CommonControls.ComboBoxBorderDisabled` |
| 文字 | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| 圖像 | `CommonControls.ComboBoxGlyphDisabled` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**下拉式清單和下拉式方塊： 將滑鼠停留狀態**

![動態顯示下拉式清單下拉式方塊](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303年 170_DropDownComboBoxHover")<br />停留時顯示下拉式方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundHover` |
| Border | `CommonControls.ComboBoxBorderHover` |
| 文字 | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| 圖像 | `CommonControls.ComboBoxGlyphHover` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundHover` |

**下拉式清單和下拉式方塊： 按下狀態**

![Pressed drop-down/combo box](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />已按下的下拉式清單下拉式方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundPressed` |
| Border | `CommonControls.ComboBoxBorderPressed` |
| 文字 | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| 圖像 | `CommonControls.ComboBoxGlyphPressed` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**下拉式清單和下拉式方塊清單項目 」 檢視： 已按下狀態**

 ![按下的清單項目檢視的下拉式清單下拉式方塊](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303年 174_DropDownComboBoxListView")<br />按下的清單項目檢視的下拉式清單下拉式方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Border | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| 項目文字 | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| 背景陰影 | `CommonControls.ComboBoxListBackgroundShadow` |

**下拉式清單和下拉式方塊： 狀態已取得焦點**

![下拉式清單下拉式方塊具有焦點](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303年 172_DropDownComboBoxFocused")<br />具有焦點的下拉式清單下拉式方塊

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundFocused` |
| Border | `CommonControls.ComboBoxBorderFocused` |
| 文字 | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| 圖像 | `CommonControls.ComboBoxGlyphFocused` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**下拉式清單和下拉式方塊： 文字輸入選取範圍**

![下拉式清單下拉式方塊文字輸入選取範圍](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303年 173_DropDownComboBoxTextInput")<br />下拉式清單下拉式方塊的文字輸入選取範圍

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 反白顯示 | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>表格式資料 (方格) 控制項
表格式資料控制項 (也稱為方格控制項) 是 Visual Studio 通用控制項，可用來在多個資料行中顯示大量資料。 標準表格式資料控制項可以位於 Visual Studio 的多個位置：[錯誤清單] 工具視窗、IntelliTrace 報告和記憶體堆積檢視等等。 請一律使用所提供的標準表格式資料控制項。 在一些罕見情況下，您可能無法存取標準表格式資料控制項。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他表格式資料控制項一致。

![表格式資料/方格控制項 （紅線）](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303年 197_TabularDataGridControlRedline")<br />表格式資料/方格控制項 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...的表格式或方格控制項。 | ...的任何不是表格式或方格控制項的 UI。 |

#### <a name="column-headers"></a>資料行標頭
資料行標頭包含背景、框線、標題文字，以及通常在依該資料行排序方格時使用的選用字符。

**資料行標頭： 預設狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Header.Default` |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (字符) | `Header.Glyph` |
| Border | `Header.SeparatorLine` |

**資料行標頭： 暫留狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Header.MouseOver` |
| 前景 (文字) | `Environment.CommandBarTextHover` |
| 前景 (字符) | `Header.MouseOverGlyph` |
| Border | `Header.SeparatorLine` |

**資料行標頭： 按下狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundPressed` |
| 前景 (文字) | `CommonControls.CheckBoxBorderPressed` |
| 前景 (字符) | `CommonControls.CheckBoxTextPressed` |
| Border | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>清單檢視項目
 清單檢視項目包含背景和內容。 內容可以是文字及/或圖示。

**清單檢視項目： 預設狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | 透明 |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| Border | None |

**清單檢視項目： 作用中狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (文字) | `TreeView.SelectedItemActiveText` |
| Border | None |

**清單檢視項目： 非使用中狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (文字) | `TreeView.SelectedItemInactiveText` |
| Border | None |

### <a name="ui-text"></a>UI 文字

#### <a name="instructional-text"></a>說明文字
說明文字提供顯著的主要說明所要執行動作的對話方塊或文件頁面。

![預設的說明文字](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />預設的說明文字

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>次要的說明文字
在文件頁面中有大量文字和控制項，有些指示的文字會使用不同的色彩值。 這有助於傳達的資訊是最重要的並降低整體密度的 UI 項目。 (另請參閱下一節上提示文字。)

![次要的說明文字](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />次要的說明文字

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>提示文字
提示文字會出現在空的控制項，如下一個控制項，或對使用者顯示的下一個空白文件介面上。 您可以使用視窗或控制項的背景使用提示文字。

**預設提示文字**

![預設提示文字](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />預設提示文字

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `Environment.ControlEditHintText` |

**必要的提示文字**

![必要提示文字](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />必要的提示文字

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `Environment.ControlRequiredHintText` |
| 背景 | `Environment.ControlRequiredBackground` |

**搜尋方塊控制項的文字**

> 請參閱[搜尋方塊](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes)的搜尋控制項的相關其他色彩語彙基元。

![搜尋方塊控制項的文字](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />搜尋方塊控制項的文字

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>超連結
超連結是一個沒有前景/背景配對的控制項。 在所有情況下，使用前景超連結的色彩，其會正確地顯示在深色、 灰色，並使用白色背景。 如果您未使用的色彩語彙基元的超連結控制項，您會看到的預設系統色彩的 「 已按下 」 這即閃爍紅色。 這是控制項未使用正確的環境色彩語彙基元的訊號。

![Hyperlink (redline)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />超連結 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您需要建立自訂超連結。 | ...的任何項目不是超連結。 |

**超連結： 預設狀態**

![預設的超連結](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303年 134_Hyperlink")<br />預設的超連結

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlink` |

**超連結： 暫留狀態**

![暫留時的超連結](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303年 135_HyperlinkHover")<br />停留時顯示超連結

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlinkHover` |

**已按下的狀態的超連結：**

![已按下超連結](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303年 136_HyperlinkPressed")<br />已按下超連結

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlinkPressed` |

**停用的狀態的超連結：**

![已停用的超連結](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303年 137_HyperlinkDisabled")<br />已停用的超連結

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>資訊列
資訊列用來提供所指定內容的詳細資訊，而且一律會出現在文件視窗或工具視窗的頂端。

![Infobar (redline)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />資訊列 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...時建立自訂資訊列。 | ...的不是資訊列類似的 UI 項目。 |

**資訊列： 預設狀態**

![預設資訊列](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303年 139_Infobar")<br />預設資訊列

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.InfoBarBackground` |
| 前景 (文字) | `InfoBar.InfoBar` |
| Border | `InfoBar.InfoBarBorder` |

**資訊列關閉 (&times;) 按鈕： 預設狀態**

![預設關閉資訊列 (&times;) 按鈕](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />預設關閉資訊列 (&times;) 按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButton` |
| Border | `InfoBar.CloseButtonBorder` |
| 圖像 | `InfoBar.CloseButtonGlyph` |

**資訊列關閉 (&times;) 按鈕： 將滑鼠停留狀態**

![關閉資訊列 (&times;) 按鈕，停留](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />資訊列關閉 (&times;) 動態顯示按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButtonHover` |
| Border | `InfoBar.CloseButtonHoverBorder` |
| 圖像 | `InfoBar.CloseButtonHoverGlyph` |

**資訊列關閉 (&times;) 按鈕： 按下狀態**

![按下關閉資訊列 (&times;) 按鈕](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />按下關閉資訊列 (&times;) 按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButtonDown` |
| Border | `InfoBar.CloseButtonDownBorder` |
| 圖像 | `InfoBar.CloseButtonDownGlyph` |

**資訊列超連結按鈕： 預設狀態**

![預設資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />預設資訊列超連結按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `InfoBar.Hyperlink` |

**資訊列超連結按鈕： 將滑鼠停留狀態**

![暫留時的資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />暫留時的資訊列超連結按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `Infobar.HyperlinkMouseOver`<br />（含底線） |

**資訊列超連結按鈕： 按下狀態**

![已按下的資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />已按下的資訊列超連結按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `Infobar.HyperlinkMouseDown`<br />（含底線） |

**（在一個句子） 資訊列內嵌超連結： 預設狀態**

![預設內嵌資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />預設內嵌資訊列超連結按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `InfoBar.Hyperlink` |

**（在一個句子） 資訊列內嵌超連結： 將滑鼠停留狀態**

![暫留時的資訊列內嵌超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />暫留時的資訊列內嵌超連結按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `Infobar.HyperlinkMouseOver`<br />（含底線） |

**（在一個句子） 資訊列內嵌超連結： 按下狀態**

![已按下的資訊列內嵌超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />按下 資訊列內嵌超連結按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 （文字） | `Infobar.HyperlinkMouseDown`<br />（含底線） |

**資訊列按鈕： 預設狀態**

![預設資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />預設資訊列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.Button` |
| 前景 （文字） | `InfoBar.Button` |
| Border | `InfoBar.ButtonBorder` |

**資訊列按鈕： 將滑鼠停留狀態**

![暫留時的資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />暫留時的資訊列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonMouseOver` |
| 前景 （文字） | `InfoBar.ButtonMouseOver` |
| Border | `InfoBar.ButtonMouseOverBorder` |

**資訊列按鈕： 按下狀態**

![已按下的資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />已按下的資訊列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonMouseDown` |
| 前景 （文字） | `InfoBar.ButtonMouseDown` |
| Border | `InfoBar.ButtonMouseDownBorder` |

**資訊列按鈕： 停用狀態**

![已停用資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />已停用資訊列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonDisabled` |
| 前景 （文字） | `InfoBar.ButtonDisabled` |
| Border | `InfoBar.ButtonDisabledBorder` |

**資訊列按鈕： 已取得焦點狀態**

![具有焦點的資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />具有焦點的資訊列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonFocus` |
| 前景 （文字） | `InfoBar.ButtonFocus` |
| Border | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>捲軸
捲軸的樣式根據 Visual Studio 環境，而且不需要設定佈景主題。 不過，您可能會決定您想要利用捲軸中使用時，您的 UI 一律會顯示與 Visual Studio 環境的這個部分一致的色彩。

![捲軸 （紅線）](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303年 140_ScrollbarRedline")<br />捲軸 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您建立 UI，您想要符合 Visual Studio 捲軸。 | ...為任何您不希望一定要相符的項目捲軸 UI。 |

**捲軸： 預設狀態**

![預設捲軸](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303年 141_Scrollbar")<br />預設捲軸

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 捲軸 | `Environment.ScrollBarBackground` |
| 前景 (捲動方塊) | `Environment.ScrollBarThumbBackground` |

**捲軸： 將滑鼠停留狀態**

![暫留時顯示捲軸](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303年 143_ScrollbarHover")<br />停留時顯示捲軸

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 捲軸 | `Environment.ScrollBarBackground` |
| 前景 (捲動方塊) | `Environment.ScrollBarThumbMouseOverBackground` |

*捲軸： 按下狀態**

![已按下的捲軸](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303年 145_ScrollbarPressed")<br />按下捲軸

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 捲軸 | `Environment.ScrollBarBackground` |
| 前景 (捲動方塊) | `Environment.ScrollBarThumbPressedBackground` |

**捲軸箭號： 預設狀態**

![預設捲軸箭號](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303年 142_ScrollbarArrow")<br />預設捲軸箭號

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowBackground`<br />（設定為與捲軸相同的色彩）。 |
| 前景 (字符) | `Environment.ScrollBarArrowGlyph` |

**捲軸箭號： 將滑鼠停留狀態**

![捲軸箭號暫留時](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303年 144_ScrollbarArrowHover")<br />停留時顯示捲軸箭號

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowMouseOverBackground`<br />（設定為與捲軸相同的色彩）。 |
| 前景 (字符) | `Environment.ScrollBarArrowGlyphMouseOver` |

**捲軸箭號： 按下狀態**

![已按下的捲軸箭號](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303年 146_ScrollbarArrowPressed")<br />按下捲軸箭號

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowPressedBackground`<br />（設定為與捲軸相同的色彩）。 |
| 前景 (字符) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>搜尋方塊
可能的話，會使用 Visual Studio 環境所提供的通用搜尋控制項。 搜尋方塊色彩位於 **ShellColors.pkgdef** 檔案的 "SearchControl" 分類中，其中包含輸入欄位、動作按鈕、下拉式按鈕和下拉式功能表的語彙基元名稱。

搜尋方塊可以是數種狀態中的其中一種，但其中有一些互斥：

-   「已取得焦點」或「未取得焦點」指的是游標是否在文字方塊中。

-   「使用中」或「非使用中」指的是使用者是否已在文字方塊中輸入搜尋查詢。

-   「暫留」表示使用者已將滑鼠指標放在搜尋方塊上方 (這種狀態會覆寫所有其他狀態)。

-   「已停用」表示已關閉目前內容的搜尋功能。

![搜尋方塊中 （紅線）](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303年 110_SearchBoxRedline")<br />搜尋方塊中 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您在設計自訂的搜尋方塊中。 | ...的任何項目不在搜尋方塊。 |
| | ...您不想要一律符合搜尋條件的項目方塊 UI。 |

**搜尋輸入的欄位已取得焦點**

![焦點式的搜尋輸入的欄位](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303年 111_SearchInputFieldFocused")<br />搜尋輸入的欄位已取得焦點

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.FocusedBackground` |
| 前景 (文字) | `SearchControl.FocusedBackground` |
| Border | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**未取得焦點，在作用中的搜尋輸入的欄位**

![搜尋輸入的欄位未取得焦點](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303年 114_SearchInputFieldUnfocused")<br />未取得焦點，在作用中的搜尋輸入的欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.SearchActiveBackground` |
| 前景 (文字) | `SearchControl.SearchActiveBackground` |
| Border | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**未取得焦點、 非使用中的搜尋輸入的欄位**

![未取得焦點、 非使用中的搜尋輸入的欄位](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303年-114-1_SearchInputFieldUnfocusedInactive")<br />未取得焦點、 非使用中的搜尋輸入的欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.Unfocused` |
| 前景 (文字) | `SearchControl.Unfocused` |
| Border | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**反白顯示的搜尋輸入的欄位 （僅限文字）**

![反白顯示的搜尋輸入的欄位](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303年 120_SearchInputFieldHighlight")<br />反白顯示的搜尋輸入的欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.Selection` |
| 前景 (文字) | `SearchControl.FocusedBackground` |
| Border | None |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**已停用的搜尋輸入的欄位**

![已停用搜尋輸入的欄位](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303年 121_SearchInputFieldDisabled")<br />已停用的搜尋輸入的欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.Disabled` |
| 前景 (文字) | `SearchControl.Disabled` |
| Border | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**焦點式的搜尋動作按鈕**

![搜尋動作按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303年 112_SearchActionButtonFocused")<br />焦點式的搜尋動作按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (搜尋字符) | `SearchControl.SearchGlyph` |
| 前景 (停止字符) | `SearchControl.StopGlyph` |
| 前景 (清除字符) | `SearchControl.ClearGlyph` |
| Border | N/A |

**未取得焦點的搜尋動作按鈕**

![未取得焦點的搜尋動作按鈕](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303年 115_SearchActionButtonUnfocused")<br />未取得焦點的搜尋動作按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (搜尋字符) | `SearchControl.SearchGlyph` |
| 前景 (停止字符) | `SearchControl.StopGlyph` |
| 前景 (清除字符) | `SearchControl.ClearGlyph` |
| Border | N/A |

**按下搜尋動作按鈕**

![已按下的搜尋動作按鈕](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303年-116-1_SearchActionButtonPressed")<br />按下搜尋動作按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.ActionButtonMouseDown` |
| 前景 (字符) | `SearchControl.ActionButtonMouseDownGlyph` |
| Border | `SearchControl.ActionButtonMouseDownBorder` |

**已停用的搜尋動作按鈕**

![已停用搜尋動作按鈕](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303年 122_SearchActionButtonDisabled")<br />已停用的搜尋動作按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `SearchControl.ActionButtonDisabledGlyph` |
| Border | None |

**焦點式的搜尋下拉式按鈕**

![焦點式的搜尋下拉式按鈕](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303年 113_SearchDropdownButtonFocused")<br />焦點式的搜尋下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.FocusedDropDownButton` |
| 前景 (字符) | `SearchControl.FocusedDropDownButtonGlyph` |
| Border | `SearchControl.FocusedDropDownButtonBorder` |

**未取得焦點的搜尋下拉式按鈕**

![未取得焦點的搜尋下拉式按鈕](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303年 116_SearchDropdownButtonUnfocused")<br />未取得焦點的搜尋下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.UnfocusedDropDownButton` |
| 前景 (字符) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Border | `SearchControl.UnfocusedDropDownButtonBorder` |

**已按下搜尋下拉式按鈕**

![已按下的搜尋下拉式按鈕](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303年-116-2_SearchDropdownButtonPressed")<br />已按下搜尋下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.MouseDownDropDownButton` |
| 前景 (字符) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Border | `SearchControl.MouseDownDropDownButtonBorder` |

**已停用的搜尋下拉式按鈕**

![已停用搜尋下拉式按鈕](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303年 123_SearchDropdownButtonDisabled")<br />已停用的搜尋下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `SearchControl.DisabledDownButtonGlyph` |
| Border | None |

#### <a name="search-drop-down-lists"></a>搜尋下拉式清單
搜尋方塊下拉式選單中有可能會比在 Visual Studio 中其他下拉式功能表稍微更為複雜。 建議的搜尋 」 和 「 搜尋選項 」 章節可出現在單獨或一起在功能表中，且每個會個別著色。 這兩個區段同時出現時，也會有一條線來區隔它們，而且會有框線括住整個下拉式功能表。

![搜尋下拉式清單 （紅線）](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303年 124_SearchDropdownRedline")<br />搜尋下拉式清單 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您要在其中建立自訂搜尋下拉式清單。 | ...為出現在其他內容中的下拉式清單。 |
| ...的正確清單元件的正確語彙基元名稱。 | ...在任何非指定的背景/前景組合。 |

**搜尋下拉式清單項目**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| Border | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| 陰影 | `Environment.DropShadowBackground` |

**建議的搜尋： 預設狀態**

![預設建議的搜尋](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303年 125_SearchSuggested")<br />預設建議的搜尋

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `SearchControl.PopupItemText` |

**建議的搜尋： 將滑鼠停留狀態**

![建議的搜尋停留](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303年 128_SearchSuggestedHover")<br />暫留時建議的搜尋

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `SearchControl.PopupMouseOverItemText` |
| Border | `SearchControl.PopupControlMouseOverBorder` |

**搜尋選項： 預設狀態**

![搜尋核取方塊](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303年 126_SearchCheckbox")<br />預設的搜尋選項 （核取方塊）

![搜尋選項](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303年 127_SearchOptions")<br />預設的搜尋選項 （連結）

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupSectionBackgroundGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (核取方塊文字) | `SearchControl.PopupCheckboxText` |
| 前景 (連結文字) | `SearchControl.PopupButtonText` |
| 頁首背景 | `SearchControl.PopupSectionHeaderGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (頁首文字) | `SearchControl.PopupSectionHeaderText` |

**搜尋選項： 將滑鼠停留狀態**

![搜尋選項 （核取方塊） 停留](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303年 129_SearchCheckboxHover")<br />暫留時的搜尋選項 （核取方塊）

![暫留時顯示搜尋選項 （連結）](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303年 130_SearchOptionsHover")<br />暫留時的搜尋選項 （連結）

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (核取方塊文字) | `SearchControl.PopupCheckboxMouseDownText` |
| 前景 (連結文字) | `SearchControl.PopupButtonMouseDownText` |
| Border | `SearchControl.PopupControlMouseOverBorder` |

**搜尋選項： 按下狀態**

![按下搜尋選項 （核取方塊）](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303年 131_SearchSuggestedPressed")<br />按下搜尋選項 （核取方塊）

![按下搜尋選項 （連結）](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303年 132_SearchOptionsPressed")<br />按下搜尋選項 （連結）

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 核取方塊背景 | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (核取方塊文字) | `SearchControl.PopupCheckboxMouseDownText` |
| 連結背景 | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (連結文字) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a> 樹狀檢視
數個工具視窗，包括方案總管 中，伺服器總管 中，以及類別 檢視中，實作階層式組織配置，其色彩受到中的色彩名稱所`TreeView`類別目錄。 樹狀檢視中的所有項目都會有背景和文字色彩。 具有巢狀子項目的項目也具有字符可指出展開還是摺疊項目。

![樹狀檢視 （紅線）](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303年 147_TreeViewRedline")<br />樹狀檢視 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...您需要實作階層式組織檢視的任何位置。 | ...的任何項目不是類似的樹狀檢視。 |
| | ...在任何非指定的背景/前景組合。 |

**樹狀檢視項目： 預設狀態**

![預設樹狀檢視項目](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303年 148_TreeView")<br />預設樹狀檢視項目

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.Background` |
| 前景 (文字) | `TreeView.Background` |
| 前景 (字符) | `TreeView.Glyph` |
| Border | None |

**樹狀檢視項目： 將滑鼠停留狀態**

![暫留時顯示的樹狀檢視項目](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303年 149_TreeViewHover")<br />暫留時顯示的樹狀檢視項目

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.Background` |
| 前景 (文字) | `TreeView.Background` |
| 前景 (字符) | `TreeView.GlyphMouseOver` |
| Border | None |

**樹狀檢視項目： 拖曳至上方狀態**

![透過樹狀檢視項目上拖曳](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303年 150_TreeViewDragOver")<br />在樹狀檢視項目拖曳至上方

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.DragOverItem` |
| 前景 (文字) | `TreeView.DragOverItem` |
| 前景 (字符) | `TreeView.DragOverItemGlyph` |
| Border | None |

**樹狀檢視項目： 選取，已取得焦點狀態**

![選取和已取得焦點的樹狀檢視項目](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303年 151_TreeViewFocused")<br />選取並具有焦點的樹狀檢視項目

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (文字) | `TreeView.SelectedItemActive` |
| 前景 (字符) | `TreeView.SelectedItemActiveGlyph` |
| Border | `TreeView.FocusVisualBorder` |

**樹狀檢視項目： 已選取，未取得焦點的狀態**

![選取和未取得焦點的樹狀檢視項目](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303年 152_TreeViewUnfocused")<br />選取和未取得焦點的樹狀檢視項目

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (文字) | `TreeView.SelectedItemInactive` |
| 前景 (字符) | `TreeView.SelectedItemInactiveGlyph` |
| Border | None |

**樹狀檢視項目： xml-script，選取，而且已取得焦點狀態**

![選取和樹狀檢視項目著重於暫留](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303年 153_TreeViewFocusedHover")<br />暫留時的選取和焦點的樹狀檢視項目

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (文字) | `TreeView.SelectedItemActive` |
| 前景 (字符) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Border | `TreeView.FocusVisualBorder` |

**樹狀檢視項目： 暫留、 選取，且未取得焦點狀態**

![暫留時的選取和未取得焦點的樹狀檢視項目](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303年 154_TreeViewUnfocusedHover")<br />暫留時的選取和未取得焦點的樹狀檢視項目

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (文字) | `TreeView.SelectedItemInactive` |
| 前景 (字符) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Border | None |

## <a name="shell-appearance"></a>Shell 外觀

### <a name="background"></a>背景
環境背景包含兩個層級。 下層是涵蓋整個 IDE 的單色。 上層可放入命令櫃下方以及 IDE 左右兩側邊緣的工具視窗自動隱藏通道之間。 Nahoře a dole 背景圖層會設定為相同的色彩，在淺色調和暗色調佈景主題。

![Visual Studio shell 背景 （紅線）](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303年 187_ShellBackgroundRedline")<br />Visual Studio shell 背景 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...的要符合 Visual Studio 環境背景的位置。 | ...為位置非背景表面的填色。 |
| | ...為要放置前景項目上的背景。 |

**下圖層 shell 外觀**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.EnvironmentBackground` |

**最上層 shell 外觀**

> 設定為與 Visual Studio 2013 淺色調和暗色調佈景主題相同色彩值的漸層停駐點。

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>命令櫃
兩組語彙基元名稱用於命令櫃背景：一組用於功能表列所在的位置，一組用於命令列所在的位置。 個別命令列群組有其專屬背景色彩值 (會在＜命令列＞一節中詳細討論)。 功能表列和命令列文字分別會在功能表和命令列一節中進行討論。

![Visual Studio 命令櫃 （紅線）](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303年 188_CommandShelfRedline")<br />Visual Studio 命令櫃 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...針對您放置功能表或工具列的區域。 | ...針對不是命令櫃類似的區域。 |
|...使用正確的背景/前景語彙基元名稱組合。 | |

**命令櫃功能表列**

> 設定為與 Visual Studio 2013 淺色調和暗色調佈景主題相同色彩值的漸層停駐點。

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**命令櫃命令列**

> 設定為與 Visual Studio 2013 淺色調和暗色調佈景主題相同色彩值的漸層停駐點。

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>資訊清單設計工具
資訊清單設計工具的設計是用來輕鬆地編輯 Windows 8 和 Windows Phone 8 專案中的資訊清單檔。 雖然沒有任何共用架構可供取用，但是可能適合您比對方向/瀏覽索引標籤和整體結構的設計版面配置和色彩。 如需版面配置詳細資料的詳細資訊，請參閱 [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。

![資訊清單設計工具 （紅線）](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303年 175_ManifestDesignerRedline")<br />資訊清單設計工具 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...的類似資訊清單設計工具的設計工具。 | ...如果您有超過六個索引標籤。 |
| ...來代替使用 文件中的編輯器頂端的 通用 索引標籤控制項區域。 | ...的任何不結構與資訊清單設計工具類似的 UI。 |

**資訊清單設計工具所選取索引標籤： 預設狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.TabActive` |
| Border | None |

**資訊清單設計工具選取的 podokno popisu： 預設狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.DescriptionPane` |

**資訊清單設計工具所選取的內容頁面上： 預設狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Background` |
| 對話方塊 Helper 文字 | `ManifestDesigner.WatermarkText`<br />（這個語彙基元名稱不符合其函式）。 |

**資訊清單設計工具索引標籤： 未選取狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Tab.Inactive` |

**資訊清單設計工具索引標籤： 暫留狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>命令結構

###  <a name="BKMK_CommandMenus"></a> 功能表
功能表可能會發生在 Visual Studio 的數個位置： 主要功能表列、 內嵌在文件或工具視窗中，或以滑鼠右鍵按一下 IDE 各位置上。 針對個別項目的一節中會討論與其他 UI 項目相關聯之功能表的實作。 您應該一律使用 Visual Studio 環境所提供的標準功能表實作。 不過，在一些罕見情況下，您可能無法存取標準 Visual Studio 功能表。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他功能表一致。

![Visual Studio 功能表 （紅線）](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303年 000_MenuRedline")<br />Visual Studio 功能表 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您需要建立自訂功能表。| ...單獨的背景色彩。 一律使用指定的背景/前景組合。 |
| ...當您有想要符合 Visual Studio 功能表的新 UI 元件。| |

#### <a name="menu-titles"></a>功能表標題
功能表標題包含背景、框線和標題文字，以及選用字符 (通常是在命令列中找到功能表時)。

![功能表標題 （紅線）](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303年 001_MenuTitleRedline")<br />功能表標題 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您要在其中建立自訂功能表標題。 | ...您不一定想要的項目符合功能表標題。 |
| | ...在任何非指定的背景/前景組合。 |

**功能表標題： 預設狀態**

![預設的功能表標題](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303年 002_MenuTitleDefault")<br />預設的功能表標題

![預設使用字符的功能表標題](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303年 003_MenuTitleWithGlyphDefault")<br />預設使用字符的功能表標題

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 （文字） | `Environment.CommandBarTextActive` |
| 前景 （字符） | `Environment.CommandBarMenuGlyph` |
| Border | None |

**功能表標題： 將滑鼠停留狀態**

![暫留時顯示的功能表標題](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303年 004_MenuTitleHover")<br />停留時顯示功能表標題

![使用暫留時的字符的功能表標題](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303年 005_MenuTitleWithGlyphHover")<br />停留時顯示使用字符的功能表標題

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 （文字） | `Environment.CommandBarTextHover` |
| 前景 （字符） | `Environment.CommandBarMenuMouseOverGlyph` |
| Border | `Environment.CommandBarBorder` |

**功能表標題： 按下狀態**

![按下功能表標題](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303年 006_MenuTitlePressed")<br />已按下的功能表標題

![按下使用字符的功能表標題](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303年 007_MenuTitleWithGlyphPressed")<br />按下使用字符的功能表標題

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (字符) | `Environment.CommandBarMenuMouseDownGlyph` |
| Border | `Environment.CommandBarMenuBorder`<br />（只有左側、 頂端，與右側相加。） |

**功能表標題： 停用狀態**

![停用使用字符的功能表標題](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303年 008_MenuTitleWithGlyphDisabled")<br />使用字符的已停用的功能表標題

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (文字) | `Environment.CommandBarTextInactive` |
| 前景 (字符) | `Environment.CommandBarTextInactive` |
| Border | None |

#### <a name="menu-items"></a>功能表項目
個別功能表項目包含功能表文字和選用圖示、核取方塊或子功能表字符。 其背景和文字色彩會在滑鼠游標暫留時變更。 這個色彩語彙基元是背景/前景配對。

![功能表項目紅線](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303年 009_MenuItemRedline")

| 使用... | 請勿使用... |
|---|---|
| ...任何下拉式清單，就會啟動從功能表列或命令列。 | ...的另一個內容中任何下拉式清單。 |
| | ...在任何非指定的背景/前景組合。 |

**功能表項目： 預設狀態**

![預設的功能表項目](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303年 010_MenuDefault")<br />預設功能表項目

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuBackgroundGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (子功能表字符) | `Environment.CommandBarMenuSubmenuGlyph` |
| Border | `Environment.CommandBarMenuBorder` |
| 圖示通道背景 | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| 陰影 | `Environment.DropShadowBackground` |

**功能表項目： 核取及選取狀態**

![已核取功能表](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303年 011_MenuChecked")<br />已核取的功能表項目

![選取 [功能表]](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303年 012_MenuSelected")<br />選取的功能表項目

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 核取標記 | `Environment.CommandBarCheckBox` |
| 核取記號背景 | `Environment.CommandBarSelectedIcon` |
| 圖示背景 | `Environment.CommandBarSelected` |
| 圖示框線 | `Environment.CommandBarSelectedBorder` |

**功能表項目： 將滑鼠停留狀態**

![Menu hover](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />暫留時顯示的功能表項目

![核取功能表動態顯示](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303年 014_MenuHoverChecked")<br />檢查暫留時顯示的功能表項目

![已選取功能表動態顯示](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303年 015_MenuHoverSelected")<br />暫留時的所選的功能表項目

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuItemMouseOver` |
| 前景 (文字) | `Environment.CommandBarMenuItemMouseOver` |
| 前景 (子功能表字符) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| 核取標記 | `Environment.CommandBarCheckBoxMouseOver` |
| 核取記號背景 | `Environment.CommandBarHoverOverSelectedIcon` |
| 圖示背景 | `Environment.CommandBarHoverOverSelected` |
| 圖示框線 | `Environment.CommandBarHoverOverSelectedIconBorder` |

**功能表項目： 停用狀態**

![已停用功能表](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303年 016_MenuDisabled")<br />已停用的功能表項目

![停用的功能表已核取](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303年 017_MenuDisabledChecked")<br />已停用的功能表項目核取記號

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.CommandBarTextInactive` |
| 前景 (子功能表字符) | `Environment.CommandBarMenuSubmenuGlyph` |
| 核取標記 | `Environment.CommandBarCheckBoxDisabled` |
| 核取記號背景 | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>命令列
命令列可以出現在多個位置中 Visual Studio IDE 中，最值得注意的是命令櫃並內嵌在工具或文件視窗。

一般情況下，請一律使用 Visual Studio 環境所提供的標準命令列實作。 使用標準機制可確保正確地顯示所有視覺化詳細資料，而且互動式項目的行為會與其他 Visual Studio 命令列控制項一致。 不過，如果您需要建置專屬的命令列，請確定您使用下列語彙基元名稱正確地設定樣式。

![命令列紅線](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303年 018_CommandBarRedline")<br />命令列 （紅線）

![溢位按鈕紅線](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303年 019_OverflowButtonRedline")<br />溢位按鈕 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...在您需要內嵌的命令列的位置，但目前無法使用標準的 Visual Studio 命令列實作。 | ...的不是命令列類似的 UI 項目。 |
| | ...的命令列元件以外，指定語彙基元名稱。 |

#### <a name="command-bar-groups"></a>命令列群組
命令列群組包含一組相關的命令列控制項，而且可能包含任意數目的按鈕，分割按鈕、下拉式功能表、下拉式方塊或功能表。 這些控制項的色彩受到個別的語彙基元名稱所規範，並且會在本指南的其他位置個別討論。 分隔線用來將命令列群組分成相關的子群組。

![命令列群組紅線](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303年 020_CommandBarGroupRedline")<br />命令列群組 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...在您需要內嵌的命令列的位置，但目前無法使用標準的 Visual Studio 命令列實作。 | ...的不是命令列類似的 UI 項目。 |
| | ...的命令列元件以外，指定語彙基元名稱。 |

**命令列群組： 預設狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| Border | `Environment.CommandBarToolBarBorder` |
| 拖曳控點 | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>命令圖示
![命令圖示紅線](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303年 021_CommandIconRedline1")<br />命令圖示 （紅線）

![具有文字的命令圖示紅線](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303年 022_CommandIconRedline2")<br />具有文字的命令圖示 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...針對任何將放在命令列的按鈕。 | ...為具有專屬語彙基元名稱的控制項。 |
| | ...在任何非指定的背景/前景組合。 |

**命令圖示： 預設狀態**

![命令圖示預設值](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303年 023_CommandIconDefault")<br />預設命令圖示

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A (繼承自命令列背景) |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| Border | N/A |

**命令圖示： 預設選取的狀態**

![預設值，選取的命令圖示](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303年 024_CommandIconDefaultSelected")<br />預設值，選取的命令圖示

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarSelected` |
| 前景 (文字) | `Environment.CommandBarTextSelected` |
| Border | `Environment.CommandBarSelectedBorder` |

**命令圖示： 暫留或焦點狀態**

![命令圖示動態顯示或焦點](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303年 025_CommandIconHover")<br />命令圖示動態顯示或焦點

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.CommandBarTextHover` |
| Border | `Environment.CommandBarBorder` |

**命令圖示： 暫留或焦點狀態中，選取**

![選取命令圖示動態顯示或焦點](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303年 026_CommandIconHoverSelected")<br />選取的命令圖示動態顯示或焦點

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarHoverOverSelected` |
| 前景 (文字) | `Environment.CommandBarTextHoverOverSelected` |
| Border | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **命令圖示： 按下狀態**

![按下命令圖示](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303年 027_CommandIconPressed")<br />已按下的命令圖示

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseDownBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.CommandBarTextMouseDown` |
| Border | `Environment.CommandBarBorder` |

**命令圖示： 停用狀態**

![已停用的命令圖示](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303年 028_CommandIconDisabled")<br />已停用的命令圖示

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A (繼承自命令列背景) |
| 前景 (文字) | `Environment.CommandBarTextInactive` |
| Border | N/A |

####  <a name="BKMK_CommandComboBox"></a> 命令列下拉式方塊

> [!IMPORTANT]
> 下拉式方塊與下拉式清單類似，但包括可編輯的文字區域。 如果下拉式清單不包含可編輯的文字區域，使用的色彩語彙基元[命令列下拉式清單](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)。

![命令列下拉式方塊紅線](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303年 029_ComboBoxRedline")<br />命令列下拉式方塊 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當建置自訂下拉式方塊。 | ...的任何項目不想永遠符合命令列 UI。 |
| ...建立下拉式方塊類似的命令列控制項時。 | ...當您有存取權已設定樣式的下拉式方塊。 |

**命令列下拉式方塊輸入的欄位： 預設狀態**

![命令列下拉式方塊輸入的欄位](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303年 030_ComboBoxInputField")<br />命令列下拉式方塊輸入的欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxBackground` |
| 前景 (文字) | `Environment.ComboBoxText` |
| Border | `Environment.ComboBoxBorder` |
| Separator | 沒有分隔符號 |

**命令列下拉式清單按鈕： 預設狀態**

![下拉式方塊&#45;向下按鈕](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303年 031_ComboBoxDropdownButton")<br />命令列下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A (繼承自命令列背景) |
| 前景 (字符) | `Environment.ComboBoxGlyph` |

**命令列下拉式清單中： 預設狀態**

![命令列下拉式清單](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303年 032_ComboBoxDropdownList")<br />命令列下拉式清單

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxPopupBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.ComboBoxItemText` |
| Border | `Environment.ComboBoxPopupBorder` |

**命令列下拉式方塊輸入的欄位： 將滑鼠停留狀態**

![命令列下拉式方塊輸入的欄位停留](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303年 033_ComboBoxInputFieldHover")<br />命令列下拉式方塊輸入的欄位暫留時顯示

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxMouseOverBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.ComboBoxMouseOverText` |
| Border | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **命令列下拉式清單按鈕： 將滑鼠停留狀態**

![命令列下拉式按鈕，停留](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303年 034_ComboBoxDropdownButtonHover")<br />暫留時的命令列下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxButtonMouseOverBackground` |
| 前景 (字符) | `Environment.ComboBoxMouseOverGlyph` |

**命令列下拉式清單： 將滑鼠停留狀態**

 ![暫留時的命令列下拉式清單](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303年 035_ComboBoxDropdownListHover")<br />暫留時的命令列下拉式清單

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 (功能表項目) | `Environment.ComboBoxItemMouseOverBackground` |
| 前景 (文字) | `Environment.ComboBoxItemMouseOverText` |
| 框線 (功能表項目) | `Environment.ComboBoxItemMouseOverBorder` |

 **命令列下拉式方塊輸入的欄位： 已取得焦點狀態**

![命令列下拉式方塊輸入欄位已取得焦點](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303年 036_ComboBoxInputFieldFocused")<br />命令列下拉式方塊輸入的欄位已取得焦點

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxFocusedBackground` |
| 前景 (文字) | `Environment.ComboBoxFocusedText` |
| Border | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**命令列下拉式清單按鈕： 已取得焦點狀態**

![命令列下拉式按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303年 037_ComboBoxDropdownButtonFocused")<br />具有焦點的命令列下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxFocusedButtonBackground` |
| 前景 (字符) | `Environment.ComboBoxFocusedGlyph` |

 **命令列下拉式方塊輸入的欄位： 按下狀態**

![按下下拉式方塊輸入欄位列的命令](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303年 038_ComboBoxInputFieldPressed")<br />按下命令列下拉式方塊輸入的欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxMouseDownBackground` |
| 前景 (文字) | `Environment.ComboBoxMouseDownText` |
| Border | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**命令列下拉式清單按鈕： 按下狀態**

![命令列下拉式按鈕已按下](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303年 039_ComboBoxDropdownButtonPressed")<br />按下命令列下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxButtonMouseDownBackground` |
| 前景 (字符) | `Environment.ComboBoxMouseDownGlyph` |

**命令列下拉式方塊輸入的欄位： 停用狀態**

![停用命令列下拉式方塊輸入欄位](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303年 041_ComboBoxInputFieldDisabled")<br />已停用的命令列下拉式方塊輸入欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxDisabledBackground` |
| 前景 (文字) | `Environment.ComboBoxDisabledText` |
| Border | `Environment.ComboBoxDisabledBorder` |
| Separator | 沒有分隔符號 |

**命令列下拉式清單按鈕： 停用狀態**

![停用命令列下拉式按鈕](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303年 040_ComboBoxDropdownButtonDisabled")<br />已停用的命令列下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a> 命令列下拉式清單

> [!IMPORTANT]
>  下拉式清單與下拉式方塊類似，但沒有可編輯的文字區域。 如果下拉式清單包括可編輯的文字區域，使用的色彩語彙基元[命令列下拉式方塊](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)。

![命令列下拉式清單 （紅線）](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303年 042_DropdownRedline")<br />命令列下拉式清單 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您要在其中建立自訂的下拉式清單控制項。 | ...的任何項目不是類似於下拉式清單。 |
| | ...的下拉式方塊或分割按鈕。 |

**命令列下拉式清單選取項目欄位： 預設狀態**

![預設命令列下拉式清單選取項目欄位](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303年 043_DropdownSelectionField")<br />預設命令列下拉式清單選取項目欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownBackground` |
| 前景 (文字) | `DropDownText` |
| Border | `DropDownBorder` |
| Separator | 沒有分隔符號 |

**命令列下拉式清單按鈕： 預設狀態**

![預設命令列下拉式按鈕](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303年 044_DropdownButton")<br />預設命令列下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `Environment.DropDownGlyph` |

**命令列下拉式清單中： 預設狀態**

![預設命令列下拉式清單](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303年 045_DropdownList")<br />預設命令列下拉式清單

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownPopupBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.ComboBoxItemText` |
| Border | `Environment.DropDownPopupBorder` |
| 陰影 | `Environment.DropShadowBackground` |

**命令列下拉式清單選取項目欄位： 將滑鼠停留狀態**

![暫留時的命令列下拉式選取欄位](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303年 046_DropdownSelectionFieldHover")<br />暫留時的命令列下拉式清單選取項目欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownMouseOverBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.DropDownMouseOverText` |
| Border | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**命令列下拉式清單按鈕： 將滑鼠停留狀態**

![命令列下拉式按鈕，停留](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303年 047_DropdownButtonHover")<br />暫留時的命令列下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownButtonMouseOverBackground` |
| 前景 (字符) | `Environment.DropDownMouseOverGlyph` |

**命令列下拉式清單： 將滑鼠停留狀態**

![暫留時的命令列下拉式清單](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303年 048_DropdownListHover")<br />暫留時的命令列下拉式清單

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 (功能表項目) | `Environment.ComboBoxItemMouseOverBackground` |
| 前景 (文字) | `Environment.ComboBoxItemMouseOverText` |
| 框線 (功能表項目) | `Environment.ComboBoxItemMouseOverBorder` |

 **命令列下拉式清單選取項目欄位： 按下狀態**

![卸除&#45;下按下的選取項目欄位](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303年 049_DropdownSelectionFieldPressed")<br />按下下拉式選取欄位列的命令

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownMouseDownBackground` |
| 前景 (文字) | `Environment.DropDownMouseDownText` |
| Border | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**命令列下拉式清單按鈕： 按下狀態**

![命令列下拉式按鈕已按下](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303年 050_DropdownButtonPressed")<br />按下命令列下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownButtonMouseDownBackground` |
| 前景 (字符) | `Environment.DropDownMouseDownGlyph` |

**命令列下拉式清單選取項目欄位： 停用狀態**

![停用命令列下拉式清單選取項目欄位](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303年 051_DropdownSelectionFieldDisabled")<br />已停用的命令列下拉式清單選取項目欄位

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownDisabledBackground` |
| 前景 (文字) | `Environment.DropDownDisabledText` |
| Border | `Environment.DropDownDisabledBorder` |
| Separator | 沒有分隔符號 |

**命令列下拉式清單按鈕： 停用狀態**

![停用命令列下拉式按鈕](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303年 052_DropdownButtonDisabled")<br />已停用的命令列下拉式按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>命令列分割按鈕
分割按鈕會與其他命令列控制項 (例如按鈕、 功能表和命令列文字) 共用許多語彙基元名稱。 基於使用方便，會在這裡重複所有必要的動作和下拉式按鈕語彙基元名稱。 分割按鈕下拉式清單會實作[命令列功能表](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)。

![分割按鈕紅線](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303年 053_SplitButtonRedline")<br />命令列分割按鈕 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您要建立的自訂分割按鈕。 | ...為其他種類的按鈕。 |
| | ...在任何非指定的背景/前景組合。 |

**命令列分割按鈕： 預設狀態**

![預設命令列分割按鈕](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303年 054_SplitButton")<br />預設的命令列分割按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (字符) | `Environment.CommandBarSplitButtonGlyph` |
| Border | N/A |
| Separator | N/A |

**命令列分割按鈕： 將滑鼠停留狀態**

![命令列將分割動態顯示按鈕](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303年 055_SplitButtonHover")<br />命令列將分割動態顯示按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.CommandBarTextHover` |
| 前景 (字符) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Border | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**命令列分割按鈕： 按下狀態**

![命令列分割按鈕已按下](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303年 056_SplitButtonPressed")<br />已按下的命令列分割按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseDownBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.CommandBarTextMouseDown` |
| 前景 (字符) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Border | `Environment.CommandBarBorder` |
| Separator | N/A |

**命令列分割按鈕： 停用狀態**

![停用命令列分割按鈕](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303年 057_SplitButtonDisabled")<br />已停用的命令列分割按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (文字) | `Environment.ComboBoxItemTextInactive` |
| 前景 (字符) | `Environment.CommandBarTextInactive` |
| Border | N/A |
| Separator | N/A |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>命令列 [其他選項] 和 [溢位] 按鈕
可透過加入或移除相關命令列按鈕來自訂命令列群組時，會使用 [其他選項] 按鈕。 如果因水平空間不足而截斷命令列，以及按一下時顯示包含無法顯示之命令列按鈕的功能表，則會出現 [溢位] 按鈕。 這兩個按鈕的色彩是透過同一組語彙基元名稱所控制。

![命令列 [更多選項] 按鈕 （紅線）](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303年 058_MoreOptionsRedline")<br />命令列 [更多選項] 按鈕 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...的自訂 [其他選項] 或者 [溢位] 按鈕。 | ...為沒有類似的功能，[其他選項] 或 [溢位] 按鈕的按鈕。 |

**命令列 [其他選項] 和 [溢位] 按鈕： 預設狀態**

![預設命令列 [更多選項] 按鈕](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303年 059_MoreOptions")<br />預設的命令列 [更多選項] 按鈕

![預設命令列 '溢位 按鈕](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303年 060_Overflow")<br />預設命令列 '溢位 按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsBackground` |
| 前景 (字符) | `Environment.CommandBarOptionsGlyph` |

**命令列 [其他選項] 和 [溢位] 按鈕： 將滑鼠停留狀態**

![命令列上暫留時的 [更多選項] 按鈕](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303年 061_MoreOptionsHover")<br />命令列上暫留時的 [更多選項] 按鈕

![命令列 '溢位 按鈕暫留時](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303年 062_OverflowOptions")<br />命令列 'Overflow' 動態顯示按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (字符) | `Environment.CommandBarOptionsMouseDownGlyph` |

**命令列 [其他選項] 和 [溢位] 按鈕： 按下狀態**

![命令列 [更多選項] 按鈕已按下](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303年 063_MoreOptionsPressed")<br />按下命令列 [更多選項] 按鈕

![按下溢位](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303年 064_OverflowPressed")<br />按下命令列 '溢位 按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (字符) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>文件視窗
沒有需要進行複寫的文件視窗中，因為它們 Visual Studio 環境所提供。 不過，您可能會決定要利用文件視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。

使用文件視窗色彩語彙基元時, 請小心只針對類似的項目，而且一定成對使用它們。 如果您不這麼做，您可能會收到非預期的結果，在 UI 中。

### <a name="document-window-frames"></a>文件視窗框架
文件視窗可以停駐在 IDE 中或浮動為不同的視窗。 當文件視窗浮動在 IDE 外部時，它仍然位於 文件區域，並有背景、 框線、 文字和索引標籤的色彩相同時，它是 IDE 的一部分。 不過，文件位在具有其專屬背景、框線和文字色彩的框架內。 工具視窗停駐在文件區域時，會從文件視窗語彙基元名稱繼承其索引標籤的行為和色彩。

![停駐文件視窗 （紅線）](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303年 065_DockedDocumentWindowRedline")<br />停駐文件視窗 （紅線）

![浮動文件視窗 （紅線）](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303年 066_FloatingDocumentWindowRedline")<br />浮動文件視窗 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...您要建立您想要比對文件視窗的 UI 的任何位置。 | ...您不想自動變更如果任何 ui 在 shell 具有佈景主題更新。 |

**停駐或浮動文件視窗中： 預設狀態**

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | 根據文件類型 |
| 前景 (文字) | 根據文件類型 |
| Border | `Environment.ToolWindowBorder` |

**具有焦點，浮動文件視窗框架： 預設狀態**

![預設已取得焦點，浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303年 067_FrameFocused")<br />預設已取得焦點，浮動文件視窗框架

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowFloatingFrame` |
| 前景 (文字) | `Environment.ToolWindowFloatingFrame` |
| 前景 (字符) | `Environment.RaftedWindowButtonActiveGlyph` |
| Border | `Environment.MainWindowActiveDefaultBorder` |
| 框線 (字符) | `Environment.RaftedWindowButtonActiveBorder`<br />（設為透明） |

**未取得焦點、 浮動文件視窗框架： 預設狀態**

![預設未取得焦點、 浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303年 068_FrameUnfocused")<br />預設未取得焦點、 浮動文件視窗框架

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowFloatingFrameInactive` |
| 前景 (文字) | `Environment.ToolWindowFloatingFrameInactive` |
| 前景 (字符) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Border | `Environment.MainWindowInactiveBorder` |
| 框線 (字符) | `Environment.RaftedWindowButtonInactiveBorder`<br />（設為透明） |

**具有焦點，浮動文件視窗框架： 將滑鼠停留狀態**

![具有焦點，暫留時浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303年 069_FrameFocusedHover")<br />具有焦點，暫留時浮動文件視窗框架

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 (字符) | `Environment.RaftedWindowButtonHoverActive` |
| 前景 (字符) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| 框線 (字符) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**未取得焦點、 浮動文件視窗框架： 將滑鼠停留狀態**

![暫留時顯示未取得焦點、 浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303年 070_FrameUnfocusedHover")<br />暫留時顯示未取得焦點、 浮動文件視窗框架

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 (字符) | `EnvironmentRaftedWindowButtonHoverInactive` |
| 前景 (字符) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| 框線 (字符) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**具有焦點，浮動文件視窗框架： 按下狀態**

![具有焦點，按下浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303年 071_FrameFocusedPressed")<br />具有焦點，按下浮動文件視窗框架

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 (字符) | `Environment.RaftedWindowButtonDown` |
| 前景 (字符) | `Environment.RaftedWindowButtonDownGlyph` |
| 框線 (字符) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>文件索引標籤
文件索引標籤位在索引標籤通道中，表示目前開啟的文件以及目前選取的文件或使用中文件。 工具視窗也可以停駐在文件索引標籤通道中 (如果使用者將它們放在那裏)。 在此情況下，他們會使用與文件視窗相同的索引標籤色彩。 如果所建立的 UI 要一律符合文件視窗色彩 (包括佈景主題更新，或已安裝新的佈景主題時)，則請參考這些色彩語彙基元。

![文件索引標籤 （紅線）](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303年 072_DocumentTabRedline")<br />文件索引標籤 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...您要在任何地方建立 UI，您想要比對文件索引標籤，並自動選取佈景主題更新或新的佈景主題色彩。 | ...為任何您不想在 shell 具有佈景主題更新的時機自動變更的 UI。 |

#### <a name="open-document-tabs"></a>開啟文件索引標籤
每個開啟的文件都會有顯示其名稱之文件索引標籤通道中的索引標籤。 可以在背景中選取或開啟文件，而且它們的索引標籤會反映這些狀態：

-   選取的索引標籤代表目前顯示在文件區域中的文件。 選取的索引標籤會有可延伸至文件區域頂端的文件框線。

-   背景索引標籤是任何非目前選取之索引標籤的文件索引標籤。按一下之後，它們會成為選取的索引標籤，並從這些語彙基元名稱取得所有背景、框線和文字色彩。

![開啟的文件 索引標籤 （紅線）](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303年 073_OpenDocumentTabRedline")<br />開啟的文件 索引標籤 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您要在其中建立自訂的文件索引標籤。 | ...的暫時 （預覽） 索引標籤。 |
| | ...您不想要時自動變更任何 ui 在 shell 具有佈景主題更新。 |

**已選取，已取得焦點的文件索引標籤**

![選取、 文件索引標籤已取得焦點](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303年 074_SelectedTabFocused")<br />已選取，已取得焦點的文件索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabSelectedGradientTop`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.FileTabSelectedText` |
| Border | `Environment.FileTabSelectedBorder`<br />（設定為相同的色彩，做為背景）。 |
| 文件框線 | `Environment.FileTabDocumentBorderBackground` |

**已選取，未取得焦點的文件索引標籤**

![已選取，未取得焦點的文件索引標籤](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303年 075_SelectedTabUnfocused")<br />已選取，未取得焦點的文件索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabInactiveGradientTop`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.FileTabInactiveText` |
| Border | `Environment.FileTabInactiveBorder`<br />（設定為相同的色彩，做為背景）。 |
| 文件框線 | `Environment.FileTabInactiveDocumentBorderBackground` |

**背景文件索引標籤： 預設狀態**

![預設背景文件索引標籤](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303年 076_BackgroundTab")<br />預設背景文件索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabBackground` |
| 前景 (文字) | `Environment.FileTabText` |
| Border | `Environment.FileTabBorder`<br />（設定為相同的色彩，做為背景）。 |

**背景文件索引標籤： 暫留狀態**

![暫留時背景文件索引標籤](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303年 077_BackgroundTabHover")<br />暫留時背景文件索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabHotGradientTop`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.FileTabHotText` |
| Border | `Environment.FileTabHotBorder`<br />（設定為相同的色彩，做為背景）。 |

#### <a name="preview-tab"></a>預覽索引標籤
也稱為 「 暫時性 」 索引標籤。使用者按一下方案總管工具視窗中的項目時，預覽索引標籤會出現在文件索引標籤通道右側。 它可作為文件的預覽，也可讓使用者選擇持續在文件索引標籤通道左側開啟文件。 一次只能開啟一個預覽索引標籤。 預覽索引標籤同時具有背景和選取的狀態 (例如開啟的索引標籤)，而且可以在其作用中狀態取得焦點或未取得焦點。

![預覽索引標籤 （紅線）](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303年 078_PreviewTabRedline")<br />預覽索引標籤 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...任何地方您要建立暫時預覽，並想要某個項目符合目前的預覽索引標籤色彩。 | ...為任何種類的文件] 或 [不是暫時性的索引標籤 （預覽）。 |
| | ...您不想要時自動變更任何 ui 在 shell 具有佈景主題更新。 |

**焦點或選取的預覽索引標籤**

![焦點或選取的預覽索引標籤](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303年 079_PreviewTabFocused")<br />焦點或選取的預覽索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalSelectedActive` |
| 前景 (文字) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Border | `Environment.FileTabProvisionalSelectedActiveBorder`<br />（設定為相同的色彩，做為背景）。 |
| 文件框線 | `Environment.FileTabProvisionalSelectedActiveBorder` |

**未取得焦點或選取的預覽索引標籤**

![未取得焦點或選取的預覽索引標籤](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303年 080_PreviewTabUnfocused")<br />未取得焦點或選取的預覽索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalSelectedInactive` |
| 前景 (文字) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Border | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| 文件框線 | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**背景預覽索引標籤： 預設狀態**

![預設背景預覽索引標籤](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303年 081_PreviewBackgroundTab")<br />預設背景預覽索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalInactive` |
| 前景 (文字) | `Environment.FileTabProvisionalInactiveForeground` |
| Border | `Environment.FileTabProvisionalInactiveBorder`<br />（設定為相同的色彩，做為背景）。 |

**背景預覽索引標籤： 暫留狀態**

![暫留時背景預覽索引標籤](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303年 082_PreviewBackgroundTabHover")<br />暫留時背景預覽索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalHover` |
| 前景 (文字) | `Environment.FileTabProvisionalHoverForeground` |
| Border | `Environment.FileTabProvisionalHoverBorder`<br />（設定為相同的色彩，做為背景）。 |

#### <a name="document-overflow-button"></a>文件溢位按鈕
如果開啟一個或多個文件 (不論目前組態中是否有垂直空間可放入所有文件索引標籤)，則會有文件溢位按鈕。 文件溢位下拉式選單，會受到[命令列功能表](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)色彩時，會顯示一份所有開啟的文件，顯示和隱藏，並根據所有開啟的文件是變更溢位字符顯示索引標籤通道中。

![文件溢位按鈕 （紅線）](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303年 083_OverflowRedline")<br />文件溢位按鈕 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您要在其中建立自訂文件溢位按鈕。 | ...針對未與溢位按鈕類似的 UI。 |
| | ...的命令列溢位按鈕。 |

**文件溢位按鈕： 預設狀態**

![預設文件溢位按鈕](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303年 084_Overflow")<br />預設文件溢位按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonBackground` |
| 前景 (字符) | `Environment.DocWellOverflowButtonGlyph` |
| Border | N/A |

**文件溢位按鈕： 將滑鼠停留狀態**

![暫留時的文件溢位按鈕](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303年 085_OverflowHover")<br />暫留時顯示文件溢位按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonMouseOverBackground` |
| 前景 (字符) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Border | `Environment.DocWellOverflowButtonMouseOverBorder` |

**文件溢位按鈕： 按下狀態**

![文件溢位按鈕按下的](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303年 086_OverflowPressed")<br />按下的文件溢位按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonMouseDownBackground` |
| 前景 (字符) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Border | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>標記
Visual Studio 支援標記，可讓使用者宣告可搜尋關鍵字，以進行追蹤。 例如，專案經理和開發人員可以使用 Team Foundation Server (TFS) 來標記工作項目。 下列表格提供以暫停和已選取狀態顯示之標記本身和「關閉圖示」字符的色彩名稱。

![在 Visual Studio 中的標記 （紅線）](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303年 176_TaggingRedline")<br />在 Visual Studio 中的標記 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...針對支援標記的 UI。 | ...的任何其他類型的 UI。 |

#### <a name="tags"></a>Tags

**標記： 預設狀態**

![預設標籤](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303年 177_Tag")<br />預設標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Tag.Background` |
| 前景 (文字) | `Tag.Background` |

**標籤： 暫留狀態**

![暫留時顯示標記](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303年 178_TagHover")<br />停留時顯示標記

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Tag.HoverBackground` |
| 前景 (文字) | `Tag.HoverBackgroundText` |

**標籤： 按下狀態**

![按下標記](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303年 179_TagPressed")<br />已按下的標記

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Tag.PressedBackground` |
| 前景 (文字) | `Tag.PressedBackgroundText` |

**標記： 已選取的狀態**

![選取標記](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303年 180_TagSelected")<br />選取的標記

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Tag.SelectedBackground` |
| 前景 (文字) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>關閉 (&times;) 標記圖像 （glyph）

**關閉 (&times;) 標記圖像 （glyph）： 預設狀態**

![預設關閉 (&times;) 標記圖像](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303年 181_TagGlyph")<br />預設關閉 (&times;) 標記圖像 （glyph）

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Tag.TagHoverGlyph` |

**關閉 (&times;) 標記圖像 （glyph）： 將滑鼠停留狀態**

![關閉 (&times;) 標記暫留時的字符](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303年 182_TagGlyphHover")<br />關閉 (&times;) 暫留時顯示標記圖像 （glyph）

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagHoverGlyphHoverBackground` |
| 前景 (字符) | `Tag.TagHoverGlyphHover` |
| Border | `Tag.TagHoverGlyphHoverBorder` |

**關閉 (&times;) 標記圖像 （glyph）： 已按下狀態**

![按下 關閉 (&times;) 標記圖像](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303年 183_TagGlyphPressed")<br />按下 關閉 (&times;) 標記圖像 （glyph）

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagHoverGlyphPressedBackground` |
| 前景 (字符) | `Tag.TagHoverGlyphPressed` |
| Border | `Tag.TagHoverGlyphPressedBorder` |

**選取以關閉標記 (&times;) 圖像 （glyph): 預設狀態**

![預設選取的標記，使用 關閉 (&times;) 圖像](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303年 184_TagSelected")<br />預設選取的標記，使用 關閉 (&times;) 圖像 （glyph)

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Tag.TagSelectedGlyph` |

**選取以關閉標記 (&times;) 圖像 （glyph): 將滑鼠停留狀態**

![選取以關閉標記 (&times;) 暫留時的字符](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303年 185_TagSelectedHover")<br />選取以關閉標記 (&times;) 暫留時顯示的圖像 （glyph)

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagSelectedGlyphHoverBackground` |
| 前景 (字符) | `Tag.TagSelectedGlyphHover` |
| Border | `Tag.TagSelectedGlyphHoverBorder` |

**選取以關閉標記 (&times;) 圖像 （glyph): 已按下狀態**

![選取的已按下 關閉標記 (&times;) 圖像](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303年 186_TagSelectedPressed")<br />選取的已按下 關閉標記 (&times;) 圖像 （glyph)

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagSelectedGlyphPressedBackground` |
| 前景 (字符) | `Tag.TagSelectedGlyphPressed` |
| Border | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>工具視窗
沒有需要進行複寫的工具視窗，因為它們 Visual Studio 環境所提供。 不過，您可能會決定要利用工具視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。

![工具視窗 （紅線）](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303年 087_ToolWindowRedline")<br />工具視窗 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...您要建立 UI，您要尋找工具視窗的任何位置。 | ...您不想要時自動變更任何 ui 在 shell 具有佈景主題更新。 |

### <a name="tool-window-frame"></a>工具視窗框架
Visual Studio 中的工具視窗用於許多不同的工作，而且可以存在於數種不同狀態的其中一種狀態。 如果開啟工具視窗，則可以將它指派至文件區域四邊的任何一邊。 工具視窗也可以浮動在 IDE 外面，讓它們可以重新定位在使用者螢幕內的任何位置。 浮動視窗一律位在 IDE 頂端。 最後，工具視窗可以停駐為文件視窗，以及顯示為文件區域中的索引標籤。 會使用文件視窗語彙基元名稱，將已停駐為文件視窗的工具視窗局部上色。

![工具視窗框架 （紅線）](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303年 088_ToolWindowFrameRedline")<br />工具視窗框架 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...您要建立 UI，您要尋找工具視窗的任何位置。 | ...您不想要時自動變更任何 ui 在 shell 具有佈景主題更新。 |

**停駐的工具視窗**

![停駐的工具視窗](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303年 089_ToolWindowDocked")<br />停駐的工具視窗

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| Border | `Environment.ToolWindowBorder` |

**浮動，已取得焦點的工具視窗**

![浮動，已取得焦點的工具視窗](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303年 090_ToolWindowFocused")<br />浮動，已取得焦點的工具視窗

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| Border | `Environment.MainWindowActiveDefaultBorder` |

**浮動，未取得焦點的工具視窗**

![浮動，未取得焦點的工具視窗](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303年 091_ToolWindowUnfocused")<br />浮動，未取得焦點的工具視窗

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| Border | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>工具箱類似 windows
工具箱是其中一個 Visual Studio 中最常使用的通用工具視窗。 它實際上就是樹狀結構控制項特殊佈景主題和套用的樣式。

![Toolbox-like window (redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />類似 [工具箱] 的視窗 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...當您在設計工具視窗，您想要一律與 shell 工具箱一致。 | ...的任何項目不是類似於工具箱 中的 UI，或如果您不確定是否 UI 將會有問題在 shell 工具箱色彩變更。 |

**[工具箱] 節點： 預設狀態**

![預設工具箱父節點](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303年 190_ToolboxParentNode")<br />預設工具箱父節點

![預設工具箱子節點](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303年 191_ToolboxChildNode")<br />預設工具箱子節點

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolboxContent`<br />（標題） |
| 背景 | `Environment.ToolWindowBackground`<br />（個別的項目或如果沒有可用的控制項的整個視窗） |
| Border | None |
| 前景 (字符) | `Environment.ToolboxContent` |
| 前景 (文字) | `Environment.ToolboxContent` |

**[工具箱] 子節點： 將滑鼠停留狀態**

![暫留時顯示工具箱子節點](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303年 192_ToolboxChildNodeHover")<br />停留時顯示工具箱子節點

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolboxContentMouseOver`<br />（只有個別項目） |
| Border | None |
| 前景 (文字) | `Environment.ToolboxContentMouseOver`<br />（只有個別項目） |

**選取的工具箱節點： 已取得焦點狀態**

![具有焦點，選取的工具箱父節點](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303年 193_ToolboxParentNodeFocused")<br />具有焦點，選取的工具箱父節點

![具有焦點，選取工具箱子節點](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303年 194_ToolboxChildNodeFocused")<br />具有焦點，選取工具箱子節點

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| Border | `TreeView.FocusVisualBorder`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 前景 (字符) | `TreeView.SelectedItemActive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 前景 (文字) | `TreeView.SelectedItemActive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |

**選取的工具箱節點： 未取得焦點的狀態**

![已選取，未取得焦點的工具箱父節點](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303年 195_ToolboxParentNodeUnfocused")<br />已選取，未取得焦點的工具箱父節點

![已選取，未取得焦點的工具箱子節點](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303年 196_ToolboxChildNodeUnfocused")<br />已選取，未取得焦點的工具箱子節點

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| Border | None |
| 前景 (字符) | `TreeView.SelectedItemInactive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 前景 (文字) | `TreeView.SelectedItemInactive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |

### <a name="tool-window-title-bar"></a>工具視窗標題列
標題列框線不是真正的框線，而是粗線頂端的標題列。 它沒有其未取得焦點狀態的語彙基元名稱。

![工具視窗標題列 （紅線）](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303年 092_ToolWindowTitleBarRedline")<br />工具視窗標題列 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...您要建立 UI，您要尋找工具視窗的任何位置。 | ...您不想要時自動變更任何 ui 在 shell 具有佈景主題更新。 |

**具有焦點的標題列**

![具有焦點的標題列](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303年 093_TitleBarFocused")<br />已取得焦點的標題列

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.TitleBarActiveGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.TitleBarActiveText` |
| Border | `Environment.TitleBarActiveBorder`<br />（設定為相同的色彩，做為背景）。 |
| 拖曳控點 | `Environment.TitleBarDragHandleActive` |

**未取得焦點的標題列**

![未取得焦點的標題列](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303年 094_TitleBarUnfocused")<br />未取得焦點的標題列

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.TitleBarInactiveGradientBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.TitleBarInactiveText` |
| Border | N/A |
| 拖曳控點 | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>工具視窗標題列按鈕
![標題列按鈕 （紅線）](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303年 095_TitleBarButtonRedline")<br />標題列按鈕 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...按鈕，會出現在 UI 中使用的工具視窗標題列的色彩語彙基元。 | ...按鈕，會出現在其他位置。 |
| | ...在任何非指定的背景/前景組合。 |

**標題列按鈕已取得焦點： 預設狀態**

![預設值，標題列按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303年 096_TitleBarButtonFocused")<br />預設情況下，具有焦點的標題列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Environment.ToolWindowButtonActiveGlyph` |
| Border | N/A |

**未取得焦點的標題列按鈕： 預設狀態**

![預設值，未取得焦點的標題列按鈕](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303年 097_TitleBarButtonUnfocused")<br />預設情況下，未取得焦點的標題列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Environment.ToolWindowButtonInactiveGlyph` |
| Border | N/A |

**標題列按鈕已取得焦點： 將滑鼠停留狀態**

![暫留時，標題列按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303年 098_TitleBarButtonFocusedHover")<br />暫留時的焦點的標題列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonHoverActive` |
| 前景 (字符) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Border | `Environment.ToolWindowButtonHoverActiveBorder` |

**未取得焦點的標題列按鈕： 將滑鼠停留狀態**

![未取得焦點的標題列按鈕，停留](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303年 099_TitleBarButtonUnfocusedHover")<br />暫留時顯示未取得焦點的標題列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonHoverInactive` |
| 前景 (字符) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Border | `Environment.ToolWindowButtonHoverInactiveBorder` |

**標題列按鈕已取得焦點： 按下狀態**

![標題列按鈕著重於按下](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303年 100_TitleBarButtonFocusedPressed")<br />按下的焦點的標題列按鈕

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonDown` |
| 前景 (字符) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Border | `Environment.ToolWindowButtonDownBorder` |

**未取得焦點的標題列按鈕： 按下狀態**

![未取得焦點的標題列按鈕按下](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303年 101_TitleBarButtonUnfocusedPressed")<br />未取得焦點的標題列按鈕按下

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonDown` |
| 前景 (字符) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Border | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>工具視窗索引標籤
![工具視窗索引標籤 （紅線）](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303年 102_ToolWindowTabRedline")<br />工具視窗索引標籤 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...您要建立 UI，您要尋找工具視窗的任何位置。 | ...您不想要時自動變更任何 ui 在 shell 具有佈景主題更新。 |

**已選取，已取得焦點的工具視窗索引標籤**

![選取、 工具視窗索引標籤已取得焦點](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303年 103_ToolWindowTabFocused")<br />已選取，已取得焦點的工具視窗索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabSelectedTab` |
| 前景 (文字) | `Environment.ToolWindowTabSelectedActiveText` |
| Border | `Environment.ToolWindowTabSelectedBorder`<br />（設定為相同的色彩，做為背景）。 |

**已選取，未取得焦點的工具視窗索引標籤**

![已選取，未取得焦點的工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303年 104_ToolWindowTabUnfocused")<br />已選取，未取得焦點的工具視窗索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabSelectedTab` |
| 前景 (文字) | `Environment.ToolWindowTabSelectedText` |
| Border | `Environment.ToolWindowTabSelectedBorder`<br />（設定為相同的色彩，做為背景）。 |

**背景工具視窗索引標籤： 預設狀態**

![預設背景工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303年 105_ToolWindowBackgroundTab")<br />預設背景工具視窗索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />（漸層停駐在 Visual Studio 2013 相同色彩值的集合。） |
| 前景 (文字) | `Environment.ToolWindowTabText` |
| Border | `Environment.ToolWindowTabBorder` |

**背景工具視窗索引標籤： 暫留狀態**

![暫留時的背景工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303年 106_ToolWindowBackgroundTabHover")<br />暫留時顯示背景工具視窗索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />（漸層停駐在 Visual Studio 2013 相同色彩值的集合。） |
| 前景 (文字) | `Environment.ToolWindowTabMouseOverText` |
| Border | `Environment.ToolWindowTabMouseOverBorder`<br />（設定為相同的色彩，做為背景）。 |

### <a name="auto-hide-tabs"></a>自動隱藏索引標籤

![自動隱藏索引標籤 （紅線）](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303年 107_AutoHideRedline")自動隱藏索引標籤 （紅線）

| 使用... | 請勿使用... |
| --- | --- |
| ...您要建立 UI，您想要符合自動隱藏工具視窗索引標籤的任何位置。 | ...您不想要時自動變更任何 ui 在 shell 具有佈景主題更新。 |

**自動隱藏索引標籤： 預設狀態**

![預設自動隱藏索引標籤](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303年 108_AutoHideTab")<br />預設自動隱藏索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.AutoHideTabBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.AutoHideTabText` |
| Border | `Environment.AutoHideTabBorder` |

**自動隱藏索引標籤： 暫留狀態**

![暫留時的自動隱藏索引標籤](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303年 109_AutoHideTabHover")<br />停留時顯示 [自動隱藏] 索引標籤

| 項目 | 權杖名稱：Category.color |
| --- | --- |
| 背景 | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />（漸層停駐配置其佈景主題的 UI 中不使用這個語彙基元。） |
| 前景 (文字) | `Environment.AutoHideTabMouseOverText` |
| Border | `Environment.AutoHideTabMouseOverBorder` |

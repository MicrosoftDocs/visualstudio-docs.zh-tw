---
title: Visual Studio 的共用色彩 |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b057803671f8add350e2d844b2697f60b2b8f1d
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181178"
---
# <a name="shared-colors-for-visual-studio"></a>Visual Studio 的共用色彩
當您設計使用通用 Visual Studio shell 元素的 UI，或您想要讓介面專案與類似的功能一致時，請使用套件定義檔中的現有 token 名稱來選擇並指派色彩。 這可確保您的 UI 與整體 Visual Studio 環境保持一致，而且會在加入或更新佈景主題時自動更新。

本文說明常見 UI 項目以及它們使用的語彙基元名稱，以在建置類似的 UI 時進行參考。 如需如何存取這些色彩語彙基元的特定資訊，請參閱 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。

請務必正確地使用語彙基元名稱：

- **使用以函式為基礎的標記名稱，而不是色彩本身。** 常見共用色彩是與特定介面項目相關聯，並且僅適用於相同或類似的功能。 例如，請不要只因為您喜歡微調進度動畫之已按下下拉式方塊的色彩，就重複使用該色彩。 下拉式方塊和動畫的功能不同，而且如果與下拉式方塊相關聯的色彩有所變更，則它可能不再是動畫元素的適當色彩。 一致地使用色彩可協助引導您的使用者並避免混淆。

- **使用正確組合的背景和文字色彩。** 要與文字搭配使用的背景色彩將有相關聯的文字色彩。 務必使用背景所指定的文字色彩。 如果沒有相關聯的文字色彩，請不要將該背景色彩用於您預期會顯示文字的任何介面。 其他文字和背景色彩的組合可能會導致無法讀取的介面。

- **使用適用于其位置的控制項色彩。** 在特定狀態中，某些 Visual Studio 控制項沒有個別的框線和背景色彩。 而是會選取其後介面的色彩。 務必根據控制項所放置的位置，而為其使用適合的語彙基元名稱。

> [!IMPORTANT]
> 請勿使用在 [起始頁] 或 [Cider] 類別中找到的權杖。

## <a name="common-shared-controls"></a>通用共用控制項

當您在功能中使用標準 Visual Studio 命令列時，您可以存取樣式化的 shell 控制項。 您不應該重新範本這些通用控制項。 不過，如果您需要建置自訂命令列，則可能也需要建置自訂控制項。 在該情況下，請務必針對下列每個控制項使用正確的語彙基元名稱，讓您的 UI 與 Visual Studio 的其餘部分一致。

### <a name="button-controls"></a>按鈕控制項

![Button 控制項紅線](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于檔中，您想要與 Visual Studio 主題（淺色、暗、藍色或系統高對比主題）整合的按鈕。 | ...針對將針對不屬於 Visual Studio 主題的自訂背景顯示的按鈕。 |

**按鈕：標準狀態**

![標準按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03。標準")<br />標準按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.Button` |
| 按鈕框線 | `CommonControls.ButtonBorder` |

**按鈕：預設狀態**

![預設按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03。預設值")<br />預設按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonDefault` |
| 按鈕框線 | `CommonControls.ButtonBorderDefault` |

**按鈕：停用狀態**

![已停用按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03。已停用")<br />已停用按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonDisabled` |
| 按鈕框線 | `CommonControls.ButtonBorderDisabled` |

**按鈕：暫留狀態**

![停留時顯示按鈕](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03. Button. 停留")<br />停留時顯示按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonHover` |
| 按鈕框線 | `CommonControls.ButtonBorderHover` |

**按鈕：按下狀態**

![已按下按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03。按下按鈕")<br />已按下按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonPressed` |
| 按鈕框線 | `CommonControls.ButtonBorderPressed` |

**按鈕：焦點狀態**

![焦點按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03。焦點")<br />焦點按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonFocused` |
| 按鈕框線 | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>核取方塊控制項
![核取方塊（紅線）](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />核取方塊（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于檔中包含的核取方塊控制項。 | ...適用于不屬於核取方塊控制項的任何 UI。 |

**核取方塊：預設狀態**

![核取方塊](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />預設核取方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackground` |
| 框線 | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| 圖像 | `CommonControls.CheckBoxGlyph` |

**核取方塊：停用狀態**

![已停用核取方塊](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />已停用核取方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundDisabled` |
| 框線 | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| 圖像 | `CommonControls.CheckBoxGlyphDisabled` |

**核取方塊：滑鼠停留狀態**

 ![停留時顯示覆選框](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />停留時顯示核取方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundHover` |
| 框線 | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| 圖像 | `CommonControls.CheckBoxGlyphHover` |

**核取方塊：已按下狀態**

![已按下核取方塊](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />已按下核取方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundPressed` |
| 框線 | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| 圖像 | `CommonControls.CheckBoxGlyphPressed` |

**核取方塊：焦點狀態**

![焦點核取方塊](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />焦點核取方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundFocused` |
| 框線 | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| 圖像 | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>下拉清單和下拉式方塊
![下拉式方塊（紅線）](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />下拉式方塊（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于檔中的下拉清單和下拉式方塊。 | ...適用于不是下拉或下拉式方塊的任何 UI。 |
| | ...適用于命令列下拉清單或[下拉式](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)[方塊](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)。 |

**下拉清單和下拉式方塊：預設狀態**

![預設下拉式方塊](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />預設下拉式方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackground` |
| 框線 | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| 分隔符號 | `CommonControls.ComboBoxSeparator` |
| 圖像 | `CommonControls.ComboBoxGlyph` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackground` |

**下拉清單和下拉式方塊：停用狀態**

![已停用下拉式方塊](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />已停用下拉式方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundDisabled` |
| 框線 | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| 分隔符號 | `CommonControls.ComboBoxSeparatorDisabled` |
| 圖像 | `CommonControls.ComboBoxGlyphDisabled` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**下拉清單和下拉式方塊：滑鼠停留狀態**

![停留時顯示下拉式方塊](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />停留時顯示下拉式方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundHover` |
| 框線 | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| 分隔符號 | `CommonControls.ComboBoxSeparatorHover` |
| 圖像 | `CommonControls.ComboBoxGlyphHover` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundHover` |

**下拉清單和下拉式方塊：已按下的狀態**

![已按下下拉式方塊](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />已按下下拉式方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundPressed` |
| 框線 | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| 分隔符號 | `CommonControls.ComboBoxSeparatorPressed` |
| 圖像 | `CommonControls.ComboBoxGlyphPressed` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**下拉清單和下拉式方塊列出專案視圖：按下狀態**

 ![已按下下拉式方塊的清單專案視圖](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />已按下下拉式方塊的清單專案視圖

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| 框線 | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| 項目文字 | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| 背景陰影 | `CommonControls.ComboBoxListBackgroundShadow` |

**下拉清單和下拉式方塊：焦點狀態**

![具有焦點的下拉式方塊](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />具有焦點的下拉式方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundFocused` |
| 框線 | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| 分隔符號 | `CommonControls.ComboBoxSeparatorFocused` |
| 圖像 | `CommonControls.ComboBoxGlyphFocused` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**下拉和下拉式方塊：文字輸入選取範圍**

![下拉式方塊文字輸入選取範圍](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />下拉式方塊文字輸入選取範圍

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 反白顯示 | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>表格式資料 (方格) 控制項
表格式資料控制項 (也稱為方格控制項) 是 Visual Studio 通用控制項，可用來在多個資料行中顯示大量資料。 標準表格式資料控制項可以位於 Visual Studio 的多個位置：[錯誤清單] 工具視窗、IntelliTrace 報告和記憶體堆積檢視等等。 請一律使用所提供的標準表格式資料控制項。 在一些罕見情況下，您可能無法存取標準表格式資料控制項。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他表格式資料控制項一致。

![表格式資料/方格控制項（紅線）](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />表格式資料/方格控制項（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于表格式或方格控制項。 | ...適用于不是表格式或方格控制項的任何 UI。 |

#### <a name="column-headers"></a>資料行標題
資料行標頭包含背景、框線、標題文字，以及通常在依該資料行排序方格時使用的選用字符。

**欄標題：預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Header.Default` |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (字符) | `Header.Glyph` |
| 框線 | `Header.SeparatorLine` |

**欄標題：暫留狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Header.MouseOver` |
| 前景 (文字) | `Environment.CommandBarTextHover` |
| 前景 (字符) | `Header.MouseOverGlyph` |
| 框線 | `Header.SeparatorLine` |

**欄標題：已按下狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundPressed` |
| 前景 (文字) | `CommonControls.CheckBoxBorderPressed` |
| 前景 (字符) | `CommonControls.CheckBoxTextPressed` |
| 框線 | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>清單檢視項目
 清單檢視項目包含背景和內容。 內容可以是文字及/或圖示。

**清單視圖專案：預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | 透明 |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 框線 | None |

**清單視圖專案： active 狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (文字) | `TreeView.SelectedItemActiveText` |
| 框線 | None |

**清單視圖專案：非使用中狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (文字) | `TreeView.SelectedItemInactiveText` |
| 框線 | None |

### <a name="ui-text"></a>UI 文字

#### <a name="instructional-text"></a>解說文字
解說文字提供了在對話或檔頁面中執行動作的主要說明。

![預設的解說文字](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText .png")<br />預設的解說文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>次要教學文字
在具有大量文字和控制項的檔頁面中，有些教學文字會使用不同的色彩值。 這有助於傳達最重要的資訊，並減少 UI 元素的整體密度。 （另請參閱下一節中的提示文字）。

![次要教學文字](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText .png")<br />次要教學文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>提示文字
提示文字會出現在空白控制項、控制項底下或空白檔介面上，以顯示使用者接下來要做什麼。 您可以搭配 [視窗] 或 [控制項背景] 使用提示文字。

**預設提示文字**

![預設提示文字](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText .png")<br />預設提示文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `Environment.ControlEditHintText` |

**必要的提示文字**

![必要的提示文字](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText .png")<br />必要的提示文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `Environment.ControlRequiredHintText` |
| 背景 | `Environment.ControlRequiredBackground` |

**搜尋方塊控制項文字**

> 請參閱[搜尋方塊](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes)，尋找與搜尋控制項相關的其他色彩標記。

![搜尋方塊控制項文字](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl .png")<br />搜尋方塊控制項文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
超連結是一個不具有前景/背景配對的控制項。 在所有情況下，請使用前景超連結色彩，這會在深色、灰階和白色背景上正確顯示。 如果您不使用超連結控制項的色彩標記，就會看到「已按下」的預設系統色彩，這會以紅色閃爍。 這就是控制項不會使用正確的環境色彩標記的信號。

![超連結（紅線）](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />超連結（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您需要建立自訂超連結時。 | ...針對不是超連結的任何專案。 |

**超連結：預設狀態**

![預設超連結](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />預設超連結

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlink` |

**超連結：滑鼠停留狀態**

![停留時顯示超連結](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />停留時顯示超連結

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlinkHover` |

**超連結：按下狀態**

![已按下超連結](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />已按下超連結

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlinkPressed` |

**超連結：停用狀態**

![已停用超連結](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />已停用超連結

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>資訊列
資訊列用來提供所指定內容的詳細資訊，而且一律會出現在文件視窗或工具視窗的頂端。

![資訊列（紅線）](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />資訊列（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...建立自訂資訊列時。 | ...適用于不類似資訊列的 UI 元素。 |

**資訊列：預設狀態**

![預設資訊列](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />預設資訊列

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.InfoBarBackground` |
| 前景 (文字) | `InfoBar.InfoBar` |
| 框線 | `InfoBar.InfoBarBorder` |

**資訊列關閉（&times;）按鈕：預設狀態**

![預設資訊列關閉（&times;）按鈕](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault .png")<br />預設資訊列關閉（&times;）按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButton` |
| 框線 | `InfoBar.CloseButtonBorder` |
| 圖像 | `InfoBar.CloseButtonGlyph` |

**資訊列關閉（&times;）按鈕：暫留狀態**

![停留時顯示資訊列關閉（&times;）按鈕](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover .png")<br />停留時顯示資訊列關閉（&times;）按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButtonHover` |
| 框線 | `InfoBar.CloseButtonHoverBorder` |
| 圖像 | `InfoBar.CloseButtonHoverGlyph` |

**資訊列關閉（&times;）按鈕：已按下狀態**

![按下的資訊列關閉（&times;）按鈕](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed .png")<br />按下的資訊列關閉（&times;）按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButtonDown` |
| 框線 | `InfoBar.CloseButtonDownBorder` |
| 圖像 | `InfoBar.CloseButtonDownGlyph` |

**資訊列超連結按鈕：預設狀態**

![預設資訊列的超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault .png")<br />預設資訊列的超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `InfoBar.Hyperlink` |

**資訊列超連結按鈕：暫留狀態**

![停留時顯示資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover .png")<br />停留時顯示資訊列超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `Infobar.HyperlinkMouseOver`<br />（加底線） |

**資訊列超連結按鈕：按下狀態**

![按下的資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed .png")<br />按下的資訊列超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `Infobar.HyperlinkMouseDown`<br />（加底線） |

**資訊列內嵌超連結（在句子內）：預設狀態**

![預設內嵌資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault .png")<br />預設內嵌資訊列超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `InfoBar.Hyperlink` |

**資訊列內嵌超連結（在句子內）：滑鼠停留狀態**

![停留時顯示資訊列的內嵌超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover .png")<br />停留時顯示資訊列的內嵌超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `Infobar.HyperlinkMouseOver`<br />（加底線） |

**資訊列內嵌超連結（在句子內）：已按下狀態**

![按下的 [資訊列] 內嵌超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed .png")<br />按下的 [資訊列] 內嵌超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景（文字） | `Infobar.HyperlinkMouseDown`<br />（加底線） |

**資訊列按鈕：預設狀態**

![預設資訊列列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault .png")<br />預設資訊列列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.Button` |
| 前景（文字） | `InfoBar.Button` |
| 框線 | `InfoBar.ButtonBorder` |

**資訊列按鈕：暫留狀態**

![停留時顯示資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover .png")<br />停留時顯示資訊列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonMouseOver` |
| 前景（文字） | `InfoBar.ButtonMouseOver` |
| 框線 | `InfoBar.ButtonMouseOverBorder` |

**資訊列按鈕：已按下狀態**

![已按下的資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed .png")<br />已按下的資訊列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonMouseDown` |
| 前景（文字） | `InfoBar.ButtonMouseDown` |
| 框線 | `InfoBar.ButtonMouseDownBorder` |

**資訊列按鈕：停用狀態**

![已停用資訊列列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled .png")<br />已停用資訊列列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonDisabled` |
| 前景（文字） | `InfoBar.ButtonDisabled` |
| 框線 | `InfoBar.ButtonDisabledBorder` |

**資訊列按鈕：焦點狀態**

![焦點的資訊列列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus .png")<br />焦點的資訊列列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonFocus` |
| 前景（文字） | `InfoBar.ButtonFocus` |
| 框線 | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>捲軸
捲軸是由 Visual Studio 環境所設計，而且不需要有主題。 不過，您可能會決定要利用捲軸中使用的色彩，讓您的 UI 一律會與 Visual Studio 環境的這個部分一致。

![捲軸（紅線）](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />捲軸（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您建立要比對的 UI 時 Visual Studio 捲軸。 | ...針對您不想要永遠符合捲軸 UI 的任何專案。 |

**捲軸：預設狀態**

![預設捲軸](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />預設捲軸

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 捲軸 | `Environment.ScrollBarBackground` |
| 前景 (捲動方塊) | `Environment.ScrollBarThumbBackground` |

**捲軸：暫留狀態**

![滑鼠停留時捲軸](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />停留時顯示捲軸

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 捲軸 | `Environment.ScrollBarBackground` |
| 前景 (捲動方塊) | `Environment.ScrollBarThumbMouseOverBackground` |

*捲軸：已按下的狀態**

![已按下捲軸](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />已按下捲軸

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 捲軸 | `Environment.ScrollBarBackground` |
| 前景 (捲動方塊) | `Environment.ScrollBarThumbPressedBackground` |

**捲軸箭號：預設狀態**

![預設捲軸箭號](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />預設捲軸箭號

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowBackground`<br />（設為與捲軸相同的色彩）。 |
| 前景 (字符) | `Environment.ScrollBarArrowGlyph` |

**捲軸箭號：滑鼠停留狀態**

![滑鼠停留時捲軸箭號](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />停留時顯示捲軸箭號

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowMouseOverBackground`<br />（設為與捲軸相同的色彩）。 |
| 前景 (字符) | `Environment.ScrollBarArrowGlyphMouseOver` |

**捲軸箭號：已按下狀態**

![按下的捲軸箭號](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />按下的捲軸箭號

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowPressedBackground`<br />（設為與捲軸相同的色彩）。 |
| 前景 (字符) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>搜尋方塊
可能的話，會使用 Visual Studio 環境所提供的通用搜尋控制項。 搜尋方塊色彩位於 **ShellColors.pkgdef** 檔案的 "SearchControl" 分類中，其中包含輸入欄位、動作按鈕、下拉式按鈕和下拉式功能表的語彙基元名稱。

搜尋方塊可以是數種狀態中的其中一種，但其中有一些互斥：

- 「已取得焦點」或「未取得焦點」指的是游標是否在文字方塊中。

- 「使用中」或「非使用中」指的是使用者是否已在文字方塊中輸入搜尋查詢。

- 「暫留」表示使用者已將滑鼠指標放在搜尋方塊上方 (這種狀態會覆寫所有其他狀態)。

- 「已停用」表示已關閉目前內容的搜尋功能。

![搜尋方塊（紅線）](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />搜尋方塊（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您要設計自訂搜尋方塊時。 | ...針對不是搜尋方塊的任何專案。 |
| | ...針對您不想要永遠符合搜尋方塊 UI 的任何專案。 |

**焦點搜尋輸入欄位**

![焦點搜尋輸入欄位](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />焦點搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.FocusedBackground` |
| 前景 (文字) | `SearchControl.FocusedBackground` |
| 框線 | `SearchControl.FocusedBorder` |
| 分隔符號 | `SearchControl.FocusedDropDownSeparator` |

**未取得焦點，現用搜尋輸入欄位**

![搜尋輸入欄位未取得焦點](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />未取得焦點，現用搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.SearchActiveBackground` |
| 前景 (文字) | `SearchControl.SearchActiveBackground` |
| 框線 | `SearchControl.UnfocusedBorder` |
| 分隔符號 | `SearchControl.DropDownSeparator` |

**未取得焦點，非使用中搜尋輸入欄位**

![未取得焦點，非使用中搜尋輸入欄位](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />未取得焦點，非使用中搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.Unfocused` |
| 前景 (文字) | `SearchControl.Unfocused` |
| 框線 | `SearchControl.UnfocusedBorder` |
| 分隔符號 | `SearchControl.DropDownSeparator` |

**反白顯示的搜尋輸入欄位（僅限文字）**

![反白顯示的搜尋輸入欄位](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />反白顯示的搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.Selection` |
| 前景 (文字) | `SearchControl.FocusedBackground` |
| 框線 | None |
| 分隔符號 | `SearchControl.FocusedDropDownSeparator` |

**停用的搜尋輸入欄位**

![停用的搜尋輸入欄位](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />停用的搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.Disabled` |
| 前景 (文字) | `SearchControl.Disabled` |
| 框線 | `SearchControl.DisabledBorder` |
| 分隔符號 | `SearchControl.DropDownSeparator` |

**焦點搜尋動作按鈕**

![搜尋動作按鈕的焦點](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />焦點搜尋動作按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (搜尋字符) | `SearchControl.SearchGlyph` |
| 前景 (停止字符) | `SearchControl.StopGlyph` |
| 前景 (清除字符) | `SearchControl.ClearGlyph` |
| 框線 | N/A |

**未取得焦點搜尋動作按鈕**

![未取得焦點搜尋動作按鈕](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />未取得焦點搜尋動作按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (搜尋字符) | `SearchControl.SearchGlyph` |
| 前景 (停止字符) | `SearchControl.StopGlyph` |
| 前景 (清除字符) | `SearchControl.ClearGlyph` |
| 框線 | N/A |

**已按下搜尋動作按鈕**

![已按下搜尋動作按鈕](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />已按下搜尋動作按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.ActionButtonMouseDown` |
| 前景 (字符) | `SearchControl.ActionButtonMouseDownGlyph` |
| 框線 | `SearchControl.ActionButtonMouseDownBorder` |

**停用的搜尋動作按鈕**

![[搜尋動作] 按鈕已停用](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />停用的搜尋動作按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `SearchControl.ActionButtonDisabledGlyph` |
| 框線 | None |

**焦點搜尋下拉式按鈕**

![焦點搜尋下拉式按鈕](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />焦點搜尋下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.FocusedDropDownButton` |
| 前景 (字符) | `SearchControl.FocusedDropDownButtonGlyph` |
| 框線 | `SearchControl.FocusedDropDownButtonBorder` |

**未取得焦點搜尋下拉式按鈕**

![未取得焦點搜尋下拉式按鈕](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />未取得焦點搜尋下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.UnfocusedDropDownButton` |
| 前景 (字符) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| 框線 | `SearchControl.UnfocusedDropDownButtonBorder` |

**已按下搜尋下拉式按鈕**

![已按下搜尋下拉式按鈕](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />已按下搜尋下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.MouseDownDropDownButton` |
| 前景 (字符) | `SearchControl.MouseDownDropDownButtonGlyph` |
| 框線 | `SearchControl.MouseDownDropDownButtonBorder` |

**停用的搜尋下拉式按鈕**

![停用的搜尋下拉式按鈕](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />停用的搜尋下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `SearchControl.DisabledDownButtonGlyph` |
| 框線 | None |

#### <a name="search-drop-down-lists"></a>搜尋下拉式清單
[搜尋方塊] 下拉式功能表可能會比 Visual Studio 中的其他下拉式功能表稍微複雜一點。 [建議的搜尋] 和 [搜尋選項] 區段可以單獨或一起出現在功能表中，而且每個區段會個別著色。 這兩個區段同時出現時，也會有一條線來區隔它們，而且會有框線括住整個下拉式功能表。

![搜尋下拉式清單（紅線）](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />搜尋下拉式清單（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您要建立自訂搜尋下拉式清單時。 | ...適用于出現在其他內容中的下拉式清單。 |
| ...正確清單元件的正確標記名稱。 | ...除了指定的任何背景/前景組合外。 |

**搜尋下拉式清單元素**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 框線 | `SearchControl.PopupBorder` |
| 分隔符號 | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**建議的搜尋：預設狀態**

![預設建議的搜尋](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />預設建議的搜尋

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `SearchControl.PopupItemText` |

**建議的搜尋：滑鼠停留狀態**

![停留時的建議搜尋](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />停留時的建議搜尋

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `SearchControl.PopupMouseOverItemText` |
| 框線 | `SearchControl.PopupControlMouseOverBorder` |

**搜尋選項：預設狀態**

![搜尋核取方塊](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />預設搜尋選項（核取方塊）

![搜尋選項](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />預設搜尋選項（連結）

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupSectionBackgroundGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (核取方塊文字) | `SearchControl.PopupCheckboxText` |
| 前景 (連結文字) | `SearchControl.PopupButtonText` |
| 頁首背景 | `SearchControl.PopupSectionHeaderGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (頁首文字) | `SearchControl.PopupSectionHeaderText` |

**搜尋選項：滑鼠停留狀態**

![停留時搜尋選項（核取方塊）](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />停留時搜尋選項（核取方塊）

![停留時搜尋選項（連結）](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />停留時搜尋選項（連結）

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (核取方塊文字) | `SearchControl.PopupCheckboxMouseDownText` |
| 前景 (連結文字) | `SearchControl.PopupButtonMouseDownText` |
| 框線 | `SearchControl.PopupControlMouseOverBorder` |

**搜尋選項：已按下狀態**

![已按下的搜尋選項（核取方塊）](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />已按下的搜尋選項（核取方塊）

![已按下的搜尋選項（連結）](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />已按下的搜尋選項（連結）

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 核取方塊背景 | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (核取方塊文字) | `SearchControl.PopupCheckboxMouseDownText` |
| 連結背景 | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (連結文字) | `SearchControl.PopupButtonMouseDownText` |

### <a name="BKMK_TreeView"></a>樹狀檢視
數個工具視窗（包括方案總管、伺服器總管和類別檢視）會執行階層式組織配置，其色彩是由 `TreeView` 分類中的色彩名稱所控制。 樹狀檢視中的所有項目都會有背景和文字色彩。 具有巢狀子項目的項目也具有字符可指出展開還是摺疊項目。

![樹狀檢視（紅線）](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />樹狀檢視（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...執行階層式組織視圖所需的任何位置。 | ...適用于不類似樹狀檢視的任何專案。 |
| | ...除了指定的任何背景/前景組合外。 |

**樹狀檢視專案：預設狀態**

![預設樹狀檢視專案](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />預設樹狀檢視專案

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.Background` |
| 前景 (文字) | `TreeView.Background` |
| 前景 (字符) | `TreeView.Glyph` |
| 框線 | None |

**樹狀檢視專案：暫留狀態**

![停留時顯示樹狀檢視專案](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />停留時顯示樹狀檢視專案

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.Background` |
| 前景 (文字) | `TreeView.Background` |
| 前景 (字符) | `TreeView.GlyphMouseOver` |
| 框線 | None |

**樹狀檢視專案：拖曳至狀態**

![拖曳上方的樹狀檢視專案](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />拖曳上方的樹狀檢視專案

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.DragOverItem` |
| 前景 (文字) | `TreeView.DragOverItem` |
| 前景 (字符) | `TreeView.DragOverItemGlyph` |
| 框線 | None |

**樹狀檢視專案：已選取，焦點狀態**

![選取和專注的樹狀檢視專案](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />選取和專注的樹狀檢視專案

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (文字) | `TreeView.SelectedItemActive` |
| 前景 (字符) | `TreeView.SelectedItemActiveGlyph` |
| 框線 | `TreeView.FocusVisualBorder` |

**樹狀檢視專案：已選取，未取得焦點狀態**

![選取的未取得焦點樹狀檢視專案](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />選取的未取得焦點樹狀檢視專案

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (文字) | `TreeView.SelectedItemInactive` |
| 前景 (字符) | `TreeView.SelectedItemInactiveGlyph` |
| 框線 | None |

**樹狀檢視專案：暫留、選取和聚焦狀態**

![停留時選取和專注的樹狀檢視專案](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />停留時選取和專注的樹狀檢視專案

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (文字) | `TreeView.SelectedItemActive` |
| 前景 (字符) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| 框線 | `TreeView.FocusVisualBorder` |

**樹狀檢視專案：懸停、選取和未取得焦點狀態**

![停留時選取並未取得焦點樹狀檢視專案](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />停留時選取並未取得焦點樹狀檢視專案

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (文字) | `TreeView.SelectedItemInactive` |
| 前景 (字符) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| 框線 | None |

## <a name="shell-appearance"></a>Shell 外觀

### <a name="background"></a>背景
環境背景包含兩個層級。 下層是涵蓋整個 IDE 的單色。 上層可放入命令櫃下方以及 IDE 左右兩側邊緣的工具視窗自動隱藏通道之間。 最上層和底部的背景圖層會設定為淺色和深色主題中的相同色彩。

![Visual Studio shell 背景（紅線）](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio shell 背景（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于您想要與 Visual Studio 環境背景進行比對的位置。 | ...作為不是背景表面位置的填滿。 |
| | ...做為放置前景元素的背景。 |

**下層 shell 的外觀**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.EnvironmentBackground` |

**最上層 shell 外觀**

> 設定為與 Visual Studio 2013 淺色調和暗色調佈景主題相同色彩值的漸層停駐點。

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>命令櫃
兩組語彙基元名稱用於命令櫃背景：一組用於功能表列所在的位置，一組用於命令列所在的位置。 個別命令列群組有其專屬背景色彩值 (會在＜命令列＞一節中詳細討論)。 功能表列和命令列文字分別會在功能表和命令列一節中進行討論。

![Visual Studio 命令架子（紅線）](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio 命令架子（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于放置功能表或工具列的區域。 | ...適用于不類似命令存放區的區域。 |
|...具有正確的背景/前景標記名稱組合。 | |

**命令貨位功能表列**

> 設定為與 Visual Studio 2013 淺色調和暗色調佈景主題相同色彩值的漸層停駐點。

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**命令架命令列**

> 設定為與 Visual Studio 2013 淺色調和暗色調佈景主題相同色彩值的漸層停駐點。

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>資訊清單設計工具
資訊清單設計工具的設計是用來輕鬆地編輯 Windows 8 和 Windows Phone 8 專案中的資訊清單檔。 雖然沒有任何共用架構可供取用，但是可能適合您比對方向/瀏覽索引標籤和整體結構的設計版面配置和色彩。 如需版面配置詳細資料的詳細資訊，請參閱 [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。

![資訊清單設計工具（紅線）](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />資訊清單設計工具（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于類似于資訊清單設計工具的設計工具。 | ...如果您有超過六個索引標籤。 |
| ...用來取代在檔中編輯器的頂端使用通用的索引標籤控制項。 | ...針對任何未結構化的 UI，不像資訊清單設計工具。 |

**資訊清單設計工具已選取索引標籤：預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.TabActive` |
| 框線 | None |

**資訊清單設計工具選取的描述窗格：預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.DescriptionPane` |

**資訊清單設計工具選取的內容頁面：預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Background` |
| 對話方塊 Helper 文字 | `ManifestDesigner.WatermarkText`<br />（此權杖名稱不符合其功能）。 |

**資訊清單設計工具索引標籤：未選取的狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Tab.Inactive` |

**資訊清單設計工具索引標籤：暫留狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>命令結構

### <a name="BKMK_CommandMenus"></a>彈出式
功能表可以在 Visual Studio 中的幾個位置發生：主要功能表列、內嵌在檔或工具視窗中，或在整個 IDE 的各種位置按一下滑鼠右鍵。 針對個別項目的一節中會討論與其他 UI 項目相關聯之功能表的實作。 您應該一律使用 Visual Studio 環境所提供的標準功能表實作。 不過，在一些罕見情況下，您可能無法存取標準 Visual Studio 功能表。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他功能表一致。

![Visual Studio 功能表（紅線）](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio 功能表（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您需要建立自訂功能表時。| ...單獨的背景色彩。 一律使用指定的背景/前景組合。 |
| ...當您有想要與 Visual Studio 功能表相符的新 UI 元件時。| |

#### <a name="menu-titles"></a>功能表標題
功能表標題包含背景、框線和標題文字，以及選用字符 (通常是在命令列中找到功能表時)。

![功能表標題（紅線）](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />功能表標題（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您建立自訂功能表標題時。 | ...針對您不想要一律符合功能表標題的任何專案。 |
| | ...除了指定的任何背景/前景組合外。 |

**功能表標題：預設狀態**

![預設功能表標題](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />預設功能表標題

![具有字型的預設功能表標題](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />具有字型的預設功能表標題

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景（文字） | `Environment.CommandBarTextActive` |
| 前景（圖像） | `Environment.CommandBarMenuGlyph` |
| 框線 | None |

**功能表標題：滑鼠停留狀態**

![停留時顯示功能表標題](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />停留時顯示功能表標題

![停留時顯示圖像的功能表標題](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />停留時顯示使用字符的功能表標題

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景（文字） | `Environment.CommandBarTextHover` |
| 前景（圖像） | `Environment.CommandBarMenuMouseOverGlyph` |
| 框線 | `Environment.CommandBarBorder` |

**功能表標題：已按下狀態**

![已按下功能表標題](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />已按下功能表標題

![具有圖像的已按下功能表標題](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />具有圖像的已按下功能表標題

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (字符) | `Environment.CommandBarMenuMouseDownGlyph` |
| 框線 | `Environment.CommandBarMenuBorder`<br />（只有 left、top 和 right）。 |

**功能表標題：停用狀態**

![具有圖像的已停用功能表標題](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />具有圖像的已停用功能表標題

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (文字) | `Environment.CommandBarTextInactive` |
| 前景 (字符) | `Environment.CommandBarTextInactive` |
| 框線 | None |

#### <a name="menu-items"></a>功能表項目
個別功能表項目包含功能表文字和選用圖示、核取方塊或子功能表字符。 其背景和文字色彩會在滑鼠游標暫留時變更。 這個色彩語彙基元是背景/前景配對。

![功能表項目紅線](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| 使用 。 | 不要使用 。 |
|---|---|
| ...從功能表列或命令列啟動的任何下拉式清單。 | ...針對另一個內容中的任何下拉式清單。 |
| | ...除了指定的任何背景/前景組合外。 |

**功能表項目：預設狀態**

![預設功能表項目](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />預設功能表項目

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuBackgroundGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (子功能表字符) | `Environment.CommandBarMenuSubmenuGlyph` |
| 框線 | `Environment.CommandBarMenuBorder` |
| 圖示通道背景 | `Environment.CommandBarMenuIconBackground` |
| 分隔符號 | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**功能表項目：已核取和選取的狀態**

![已核取功能表](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />已選取的功能表項目

![已選取功能表](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />選取的功能表項目

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 核取記號 | `Environment.CommandBarCheckBox` |
| 核取記號背景 | `Environment.CommandBarSelectedIcon` |
| 圖示背景 | `Environment.CommandBarSelected` |
| 圖示框線 | `Environment.CommandBarSelectedBorder` |

**功能表項目：滑鼠停留狀態**

![功能表停留](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />停留時顯示功能表項目

![已核取功能表游標](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />停留時選取的功能表項目

![已選取功能表游標](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />停留時選取的功能表項目

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuItemMouseOver` |
| 前景 (文字) | `Environment.CommandBarMenuItemMouseOverText` |
| 前景 (子功能表字符) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| 核取記號 | `Environment.CommandBarCheckBoxMouseOver` |
| 核取記號背景 | `Environment.CommandBarHoverOverSelectedIcon` |
| 圖示背景 | `Environment.CommandBarHoverOverSelected` |
| 圖示框線 | `Environment.CommandBarHoverOverSelectedIconBorder` |

**功能表項目：停用狀態**

![已停用功能表](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />停用的功能表項目

![已核取功能表](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />具有核取記號的已停用功能表項目

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.CommandBarTextInactive` |
| 前景 (子功能表字符) | `Environment.CommandBarMenuSubmenuGlyph` |
| 核取記號 | `Environment.CommandBarCheckBoxDisabled` |
| 核取記號背景 | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>命令列
命令列可以出現在 Visual Studio IDE 中的多個位置，最值得注意的是命令貨位和內嵌在工具或文件視窗中。

一般情況下，請一律使用 Visual Studio 環境所提供的標準命令列實作。 使用標準機制可確保正確地顯示所有視覺化詳細資料，而且互動式項目的行為會與其他 Visual Studio 命令列控制項一致。 不過，如果您需要建置專屬的命令列，請確定您使用下列語彙基元名稱正確地設定樣式。

![命令列紅線](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />命令列（紅線）

![溢位按鈕紅線](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />溢位按鈕（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...在您需要內嵌命令列，但無法使用標準 Visual Studio 命令列執行的位置。 | ...適用于與命令列不類似的 UI 元素。 |
| | ...用於指定標記名稱的命令列元件。 |

#### <a name="command-bar-groups"></a>命令列群組
命令列群組包含一組相關的命令列控制項，而且可能包含任意數目的按鈕，分割按鈕、下拉式功能表、下拉式方塊或功能表。 這些控制項的色彩受到個別的語彙基元名稱所規範，並且會在本指南的其他位置個別討論。 分隔線用來將命令列群組分成相關的子群組。

![命令列群組紅線](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />命令列群組（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...在您需要內嵌命令列，但無法使用標準 Visual Studio 命令列執行的位置。 | ...適用于與命令列不類似的 UI 元素。 |
| | ...用於指定標記名稱的命令列元件。 |

**命令列群組：預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 框線 | `Environment.CommandBarToolBarBorder` |
| 拖曳控點 | `Environment.CommandBarDragHandle` |
| 分隔符號 | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>命令圖示
![命令圖示紅線](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />命令圖示（紅線）

![具有文字紅線的命令圖示](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />含有文字的命令圖示（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于將放在命令列上的任何按鈕。 | ...適用于具有自已標幟名稱的控制項。 |
| | ...除了指定的任何背景/前景組合外。 |

**命令圖示：預設狀態**

![命令圖示預設值](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />預設命令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A (繼承自命令列背景) |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 框線 | N/A |

**命令圖示：預設狀態，已選取**

![預設，選取的命令圖示](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />預設，選取的命令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarSelected` |
| 前景 (文字) | `Environment.CommandBarTextSelected` |
| 框線 | `Environment.CommandBarSelectedBorder` |

**命令圖示：滑鼠停留或焦點狀態**

![滑鼠停留或焦點上的命令圖示](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />滑鼠停留或焦點上的命令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.CommandBarTextHover` |
| 框線 | `Environment.CommandBarBorder` |

**命令圖示：滑鼠停留或焦點狀態，已選取**

![滑鼠停留或焦點時選取的命令圖示](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />滑鼠停留或焦點時選取的命令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarHoverOverSelected` |
| 前景 (文字) | `Environment.CommandBarTextHoverOverSelected` |
| 框線 | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **命令圖示：已按下狀態**

![已按下的命令圖示](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />已按下的命令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseDownBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.CommandBarTextMouseDown` |
| 框線 | `Environment.CommandBarBorder` |

**命令圖示：停用狀態**

![停用的命令圖示](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />已停用的命令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A (繼承自命令列背景) |
| 前景 (文字) | `Environment.CommandBarTextInactive` |
| 框線 | N/A |

#### <a name="BKMK_CommandComboBox"></a>命令列下拉式方塊

> [!IMPORTANT]
> 下拉式方塊與下拉式清單類似，但包括可編輯的文字區域。 如果下拉式清單中沒有包含可編輯的文字區域，請使用 [[命令列](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)的色彩標記] 下拉式清單。

![命令列下拉式方塊紅線](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />命令列下拉式方塊（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...建立自訂下拉式方塊時。 | ...針對任何您不想要一律與命令列 UI 相符的專案。 |
| ...建立類似下拉式方塊的命令列控制項時。 | ...當您可以存取樣式的下拉式方塊時。 |

**命令列下拉式方塊輸入欄位：預設狀態**

![命令列下拉式方塊輸入欄位](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />命令列下拉式方塊輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxBackground` |
| 前景 (文字) | `Environment.ComboBoxText` |
| 框線 | `Environment.ComboBoxBorder` |
| 分隔符號 | 沒有分隔符號 |

**命令列下拉式按鈕：預設狀態**

![下拉式方塊下拉&#45;按鈕](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />命令列下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A (繼承自命令列背景) |
| 前景 (字符) | `Environment.ComboBoxGlyph` |

**命令列下拉式清單：預設狀態**

![命令列下拉式清單](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />命令列下拉式清單

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxPopupBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.ComboBoxItemText` |
| 框線 | `Environment.ComboBoxPopupBorder` |

**命令列下拉式方塊輸入欄位：暫留狀態**

![停留時顯示命令列下拉式方塊輸入欄位](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />停留時顯示命令列下拉式方塊輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxMouseOverBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.ComboBoxMouseOverText` |
| 框線 | `Environment.ComboBoxMouseOverBorder` |
| 分隔符號 | `Environment.ComboBoxMouseOverSeparator` |

 **命令列下拉式按鈕：滑鼠停留狀態**

![停留時顯示命令列下拉式按鈕](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />停留時顯示命令列下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxButtonMouseOverBackground` |
| 前景 (字符) | `Environment.ComboBoxMouseOverGlyph` |

**命令列下拉式清單：滑鼠停留狀態**

 ![停留時顯示命令列下拉式清單](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />停留時顯示命令列下拉式清單

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (功能表項目) | `Environment.ComboBoxItemMouseOverBackground` |
| 前景 (文字) | `Environment.ComboBoxItemMouseOverText` |
| 框線 (功能表項目) | `Environment.ComboBoxItemMouseOverBorder` |

 **命令列下拉式方塊輸入欄位：焦點狀態**

![焦點的命令列下拉式方塊輸入欄位](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />焦點的命令列下拉式方塊輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxFocusedBackground` |
| 前景 (文字) | `Environment.ComboBoxFocusedText` |
| 框線 | `Environment.ComboBoxFocusedBorder` |
| 分隔符號 | `Environment.ComboBoxFocusedButtonSeparator` |

**命令列下拉式按鈕：焦點狀態**

![焦點命令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />焦點命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxFocusedButtonBackground` |
| 前景 (字符) | `Environment.ComboBoxFocusedGlyph` |

 **命令列下拉式方塊輸入欄位：已按下的狀態**

![已按下的命令列下拉式方塊輸入欄位](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />已按下的命令列下拉式方塊輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxMouseDownBackground` |
| 前景 (文字) | `Environment.ComboBoxMouseDownText` |
| 框線 | `Environment.ComboBoxMouseDownBorder` |
| 分隔符號 | `Environment.ComboBoxMouseDownSeparator` |

**命令列下拉式按鈕：已按下的狀態**

![已按下的命令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />已按下的命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxButtonMouseDownBackground` |
| 前景 (字符) | `Environment.ComboBoxMouseDownGlyph` |

**命令列下拉式方塊輸入欄位：停用狀態**

![已停用的命令列下拉式方塊輸入欄位](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />已停用的命令列下拉式方塊輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxDisabledBackground` |
| 前景 (文字) | `Environment.ComboBoxDisabledText` |
| 框線 | `Environment.ComboBoxDisabledBorder` |
| 分隔符號 | 沒有分隔符號 |

**命令列下拉式按鈕：停用狀態**

![停用的命令列下拉式按鈕](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />停用的命令列下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="BKMK_CommandDropDown"></a>命令列下拉式清單

> [!IMPORTANT]
> 下拉式清單與下拉式方塊類似，但沒有可編輯的文字區域。 如果您的下拉式包含可編輯的文字區域，請使用 [命令列的色彩標記][下拉式方塊](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)。

![命令列下拉式（紅線）](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />命令列下拉式（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您要建立自訂下拉式清單控制項時。 | ...針對任何不類似下拉式清單的專案。 |
| | ...適用于下拉式方塊或分割按鈕。 |

**命令列下拉式選取範圍欄位：預設狀態**

![預設命令列下拉式選取欄位](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />預設命令列下拉式選取欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownBackground` |
| 前景 (文字) | `DropDownText` |
| 框線 | `DropDownBorder` |
| 分隔符號 | 沒有分隔符號 |

**命令列下拉式按鈕：預設狀態**

![預設命令列下拉式按鈕](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />預設命令列下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `Environment.DropDownGlyph` |

**命令列下拉式清單：預設狀態**

![預設命令列下拉式清單](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />預設命令列下拉式清單

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownPopupBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.ComboBoxItemText` |
| 框線 | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**命令列下拉式選取範圍欄位：暫留狀態**

![停留時顯示命令列下拉式選欄位](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />停留時顯示命令列下拉式選欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownMouseOverBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.DropDownMouseOverText` |
| 框線 | `Environment.DropDownMouseOverBorder` |
| 分隔符號 | `Environment.DropDownButtonMouseOverSeparator` |

**命令列下拉式按鈕：滑鼠停留狀態**

![停留時顯示命令列下拉式按鈕](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />停留時顯示命令列下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownButtonMouseOverBackground` |
| 前景 (字符) | `Environment.DropDownMouseOverGlyph` |

**命令列下拉式清單：滑鼠停留狀態**

![停留時顯示命令列下拉式清單](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />停留時顯示命令列下拉式清單

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (功能表項目) | `Environment.ComboBoxItemMouseOverBackground` |
| 前景 (文字) | `Environment.ComboBoxItemMouseOverText` |
| 框線 (功能表項目) | `Environment.ComboBoxItemMouseOverBorder` |

 **命令列下拉選取範圍欄位：已按下的狀態**

![已&#45;按下下拉選取範圍欄位](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />已按下的命令列下拉選取範圍欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownMouseDownBackground` |
| 前景 (文字) | `Environment.DropDownMouseDownText` |
| 框線 | `Environment.DropDownMouseDownBorder` |
| 分隔符號 | `Environment.DropDownButtonMouseDownSeparator` |

**命令列下拉式按鈕：已按下的狀態**

![已按下的命令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />已按下的命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownButtonMouseDownBackground` |
| 前景 (字符) | `Environment.DropDownMouseDownGlyph` |

**命令列下拉選取範圍欄位：停用狀態**

![已停用的命令列下拉式選欄位](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />已停用的命令列下拉式選欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownDisabledBackground` |
| 前景 (文字) | `Environment.DropDownDisabledText` |
| 框線 | `Environment.DropDownDisabledBorder` |
| 分隔符號 | 沒有分隔符號 |

**命令列下拉式按鈕：停用狀態**

![停用的命令列下拉式按鈕](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />停用的命令列下拉式按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>命令列分割按鈕
分割按鈕會與其他命令列控制項 (例如按鈕、 功能表和命令列文字) 共用許多語彙基元名稱。 基於使用方便，會在這裡重複所有必要的動作和下拉式按鈕語彙基元名稱。 分割按鈕下拉式清單是[命令列功能表](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)的執行方式。

![分割按鈕紅線](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />命令列分割按鈕（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您要建立自訂分割按鈕時。 | ...適用于其他類型的按鈕。 |
| | ...除了指定的任何背景/前景組合外。 |

**命令列分割按鈕：預設狀態**

![預設命令列分割按鈕](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />預設命令列分割按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (字符) | `Environment.CommandBarSplitButtonGlyph` |
| 框線 | N/A |
| 分隔符號 | N/A |

**命令列分割按鈕：暫留狀態**

![滑鼠停留時的命令列分割按鈕](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />滑鼠停留時的命令列分割按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.CommandBarTextHover` |
| 前景 (字符) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| 框線 | `Environment.CommandBarBorder` |
| 分隔符號 | `Environment.CommandBarSplitButtonSeparator` |

**命令列分割按鈕：按下狀態**

![已按下的命令列分割按鈕](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />已按下的命令列分割按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseDownBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.CommandBarTextMouseDown` |
| 前景 (字符) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| 框線 | `Environment.CommandBarBorder` |
| 分隔符號 | N/A |

**命令列分割按鈕：停用狀態**

![停用的命令列分割按鈕](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />停用的命令列分割按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (文字) | `Environment.ComboBoxItemTextInactive` |
| 前景 (字符) | `Environment.CommandBarTextInactive` |
| 框線 | N/A |
| 分隔符號 | N/A |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>命令列 [其他選項] 和 [溢位] 按鈕
可透過加入或移除相關命令列按鈕來自訂命令列群組時，會使用 [其他選項] 按鈕。 如果因水平空間不足而截斷命令列，以及按一下時顯示包含無法顯示之命令列按鈕的功能表，則會出現 [溢位] 按鈕。 這兩個按鈕的色彩是透過同一組語彙基元名稱所控制。

![命令列 [其他選項] 按鈕（紅線）](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />命令列 [其他選項] 按鈕（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于自訂的 [其他選項] 或 [溢位] 按鈕。 | ...針對沒有類似 [更多選項] 或 [溢位] 按鈕之功能的按鈕。 |

**命令列 [其他選項] 和 [溢位] 按鈕：預設狀態**

![預設命令列 [其他選項] 按鈕](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />預設命令列 [其他選項] 按鈕

![預設命令列 [溢位] 按鈕](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />預設命令列 [溢位] 按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsBackground` |
| 前景 (字符) | `Environment.CommandBarOptionsGlyph` |

**命令列 [其他選項] 和 [溢位] 按鈕：滑鼠停留狀態**

![停留時命令列的 [其他選項] 按鈕](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />停留時命令列的 [其他選項] 按鈕

![停留時顯示命令列 ' 溢位 ' 按鈕](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />停留時顯示命令列 ' 溢位 ' 按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (字符) | `Environment.CommandBarOptionsMouseDownGlyph` |

**命令列 [其他選項] 和 [溢位] 按鈕：已按下狀態**

![已按下的命令列 [其他選項] 按鈕](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />已按下的命令列 [其他選項] 按鈕

![已按下溢位](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />已按下的命令列 [溢位] 按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (字符) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>文件視窗
不需要複寫文件視窗，因為它們是由 Visual Studio 環境所提供。 不過，您可能會決定要利用文件視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。

使用文件視窗色彩標記時，請小心僅針對類似的元素使用它們，以及一律成對。 如果您沒有這麼做，您可能會在 UI 中收到非預期的結果。

### <a name="document-window-frames"></a>文件視窗框架
文件視窗可以停駐在 IDE 中或浮動為不同的視窗。 當文件視窗浮動于 IDE 外部時，它仍然會放在檔中，而且具有與 IDE 一部分相同的背景、框線、文字和索引標籤色彩。 不過，文件位在具有其專屬背景、框線和文字色彩的框架內。 工具視窗停駐在文件區域時，會從文件視窗語彙基元名稱繼承其索引標籤的行為和色彩。

![停駐的文件視窗（紅線）](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />停駐的文件視窗（紅線）

![浮動文件視窗（紅線）](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />浮動文件視窗（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...您要在其中建立 UI 的任何位置，以符合文件視窗。 | ... 針對您不想要在 shell 具有主題更新時自動變更的任何 UI。 |

**停駐或浮動文件視窗：預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | 根據文件類型 |
| 前景 (文字) | 根據文件類型 |
| 框線 | `Environment.ToolWindowBorder` |

**專注的浮動文件視窗框架：預設狀態**

![預設焦點的浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />預設焦點的浮動文件視窗框架

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowFloatingFrame` |
| 前景 (文字) | `Environment.ToolWindowFloatingFrame` |
| 前景 (字符) | `Environment.RaftedWindowButtonActiveGlyph` |
| 框線 | `Environment.MainWindowActiveDefaultBorder` |
| 框線 (字符) | `Environment.RaftedWindowButtonActiveBorder`<br />（設為透明） |

**未取得焦點，浮動文件視窗框架：預設狀態**

![預設未取得焦點，浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />預設未取得焦點，浮動文件視窗框架

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowFloatingFrameInactive` |
| 前景 (文字) | `Environment.ToolWindowFloatingFrameInactive` |
| 前景 (字符) | `Environment.RaftedWindowButtonInactiveGlyph` |
| 框線 | `Environment.MainWindowInactiveBorder` |
| 框線 (字符) | `Environment.RaftedWindowButtonInactiveBorder`<br />（設為透明） |

**專注的浮動文件視窗框架：滑鼠停留狀態**

![滑鼠停留時的焦點浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />滑鼠停留時的焦點浮動文件視窗框架

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (字符) | `Environment.RaftedWindowButtonHoverActive` |
| 前景 (字符) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| 框線 (字符) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**未取得焦點，浮動文件視窗框架：滑鼠停留狀態**

![未取得焦點，停留時浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />未取得焦點，停留時浮動文件視窗框架

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (字符) | `EnvironmentRaftedWindowButtonHoverInactive` |
| 前景 (字符) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| 框線 (字符) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**專注的浮動文件視窗框架：已按下的狀態**

![按下焦點的浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />按下焦點的浮動文件視窗框架

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (字符) | `Environment.RaftedWindowButtonDown` |
| 前景 (字符) | `Environment.RaftedWindowButtonDownGlyph` |
| 框線 (字符) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>文件索引標籤
文件索引標籤位在索引標籤通道中，表示目前開啟的文件以及目前選取的文件或使用中文件。 工具視窗也可以停駐在文件索引標籤通道中 (如果使用者將它們放在那裏)。 在此情況下，他們會使用與文件視窗相同的索引標籤色彩。 如果所建立的 UI 要一律符合文件視窗色彩 (包括佈景主題更新，或已安裝新的佈景主題時)，則請參考這些色彩語彙基元。

![檔索引標籤（紅線）](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />檔索引標籤（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...您正在建立 UI 的任何位置，都要與檔索引標籤比對，並自動挑選主題更新或新的主題色彩。 | ...適用于您不想在 shell 具有主題更新時自動變更的任何 UI。 |

#### <a name="open-document-tabs"></a>開啟文件索引標籤
每個開啟的文件都會有顯示其名稱之文件索引標籤通道中的索引標籤。 可以在背景中選取或開啟文件，而且它們的索引標籤會反映這些狀態：

- 選取的索引標籤代表目前顯示在文件區域中的文件。 選取的索引標籤會有可延伸至文件區域頂端的文件框線。

- 背景索引標籤是指任何不是目前所選取索引標籤的檔索引標籤。一旦按一下，它們就會變成選取的索引標籤，並從這些標記名稱取得所有的背景、框線和文字色彩。

![[開啟檔] 索引標籤（紅線）](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />[開啟檔] 索引標籤（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您要建立自訂檔索引標籤時。 | ...用於臨時（預覽）索引標籤。 |
| | ...適用于您不想要在 shell 具有主題更新時自動變更的任何 UI。 |

**選取的焦點檔索引標籤**

![選取的焦點檔索引標籤](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />選取的焦點檔索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabSelectedGradientTop`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.FileTabSelectedText` |
| 框線 | `Environment.FileTabSelectedBorder`<br />（設為與背景相同的色彩）。 |
| 文件框線 | `Environment.FileTabDocumentBorderBackground` |

**已選取，[未取得焦點檔] 索引標籤**

![已選取，[未取得焦點檔] 索引標籤](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />已選取，[未取得焦點檔] 索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabInactiveGradientTop`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.FileTabInactiveText` |
| 框線 | `Environment.FileTabInactiveBorder`<br />（設為與背景相同的色彩）。 |
| 文件框線 | `Environment.FileTabInactiveDocumentBorderBackground` |

**背景檔索引標籤：預設狀態**

![[預設背景檔] 索引標籤](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />[預設背景檔] 索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabBackground` |
| 前景 (文字) | `Environment.FileTabText` |
| 框線 | `Environment.FileTabBorder`<br />（設為與背景相同的色彩）。 |

**背景檔索引標籤：滑鼠停留狀態**

![停留時顯示背景檔索引標籤](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />停留時顯示背景檔索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabHotGradientTop`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.FileTabHotText` |
| 框線 | `Environment.FileTabHotBorder`<br />（設為與背景相同的色彩）。 |

#### <a name="preview-tab"></a>預覽索引標籤
也稱為「臨時」索引標籤。當使用者按一下 [方案總管工具] 視窗中的專案時，[預覽] 索引標籤會出現在 [檔] 索引標籤通道的右側。 它可作為文件的預覽，也可讓使用者選擇持續在文件索引標籤通道左側開啟文件。 一次只能開啟一個預覽索引標籤。 預覽索引標籤同時具有背景和選取的狀態 (例如開啟的索引標籤)，而且可以在其作用中狀態取得焦點或未取得焦點。

![預覽索引標籤（紅線）](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />預覽索引標籤（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...您正在建立臨時預覽的任何位置，以及想要讓某個元素符合目前的預覽索引標籤色彩。 | ...適用于任何一種非暫存檔案或索引標籤（預覽）。 |
| | ...適用于您不想要在 shell 具有主題更新時自動變更的任何 UI。 |

**焦點，選取的預覽索引標籤**

![焦點，選取的預覽索引標籤](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />焦點，選取的預覽索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalSelectedActive` |
| 前景 (文字) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| 框線 | `Environment.FileTabProvisionalSelectedActiveBorder`<br />（設為與背景相同的色彩）。 |
| 文件框線 | `Environment.FileTabProvisionalSelectedActiveBorder` |

**未取得焦點，選取的 [預覽] 索引標籤**

![未取得焦點，選取的 [預覽] 索引標籤](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />未取得焦點，選取的 [預覽] 索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalSelectedInactive` |
| 前景 (文字) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| 框線 | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| 文件框線 | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**背景預覽索引標籤：預設狀態**

![預設背景預覽索引標籤](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />預設背景預覽索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalInactive` |
| 前景 (文字) | `Environment.FileTabProvisionalInactiveForeground` |
| 框線 | `Environment.FileTabProvisionalInactiveBorder`<br />（設為與背景相同的色彩）。 |

**背景預覽索引標籤：暫留狀態**

![滑鼠停留時的背景預覽索引標籤](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />滑鼠停留時的背景預覽索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalHover` |
| 前景 (文字) | `Environment.FileTabProvisionalHoverForeground` |
| 框線 | `Environment.FileTabProvisionalHoverBorder`<br />（設為與背景相同的色彩）。 |

#### <a name="document-overflow-button"></a>文件溢位按鈕
如果開啟一個或多個文件 (不論目前組態中是否有垂直空間可放入所有文件索引標籤)，則會有文件溢位按鈕。 [檔溢位] 下拉式功能表（由 [[命令列] 功能表](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)色彩控制）會顯示所有開啟的檔案清單，其中包括 [可見] 和 [隱藏]，而溢點陣圖像會根據所有開啟的檔是否顯示在索引標籤通道中而變更。

![檔溢位按鈕（紅線）](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />檔溢位按鈕（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您正在建立自訂檔溢位按鈕時。 | ...適用于與溢位按鈕不類似的 UI。 |
| | ...適用于命令列溢位按鈕。 |

**檔溢位按鈕：預設狀態**

![預設檔溢位按鈕](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />預設檔溢位按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonBackground` |
| 前景 (字符) | `Environment.DocWellOverflowButtonGlyph` |
| 框線 | N/A |

**檔溢位按鈕：暫留狀態**

![停留時顯示檔溢位按鈕](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />暫留時顯示文件溢位按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonMouseOverBackground` |
| 前景 (字符) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| 框線 | `Environment.DocWellOverflowButtonMouseOverBorder` |

**檔溢位按鈕：已按下狀態**

![按下時的檔溢位按鈕](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />按下時的檔溢位按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonMouseDownBackground` |
| 前景 (字符) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| 框線 | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>標記
Visual Studio 支援標記，可讓使用者宣告可搜尋關鍵字，以進行追蹤。 例如，專案經理和開發人員可以使用 Team Foundation Server (TFS) 來標記工作項目。 下列表格提供以暫停和已選取狀態顯示之標記本身和「關閉圖示」字符的色彩名稱。

![在 Visual Studio 中標記（紅線）](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />在 Visual Studio 中標記（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于支援標記的 UI。 | ...適用于其他任何類型的 UI。 |

#### <a name="tags"></a>Tags

**標記：預設狀態**

![預設標記](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />預設標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.Background` |
| 前景 (文字) | `Tag.Background` |

**標記：暫留狀態**

![停留時標記](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />停留時顯示標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.HoverBackground` |
| 前景 (文字) | `Tag.HoverBackgroundText` |

**標記：已按下狀態**

![已按下的標記](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />已按下的標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.PressedBackground` |
| 前景 (文字) | `Tag.PressedBackgroundText` |

**標記：選取的狀態**

![選取的標記](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />選取的標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.SelectedBackground` |
| 前景 (文字) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>關閉（&times;）標記圖像

**關閉（&times;）標記圖像：預設狀態**

![預設關閉（&times;）標記圖像](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />預設關閉（&times;）標記圖像

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Tag.TagHoverGlyph` |

**關閉（&times;）標記圖像：滑鼠停留狀態**

![停留時關閉（&times;）標記圖像](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />停留時關閉（&times;）標記圖像

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagHoverGlyphHoverBackground` |
| 前景 (字符) | `Tag.TagHoverGlyphHover` |
| 框線 | `Tag.TagHoverGlyphHoverBorder` |

**關閉（&times;）標記圖像：已按下的狀態**

![已按下關閉（&times;）標記圖像](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />已按下關閉（&times;）標記圖像

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagHoverGlyphPressedBackground` |
| 前景 (字符) | `Tag.TagHoverGlyphPressed` |
| 框線 | `Tag.TagHoverGlyphPressedBorder` |

**具有關閉（&times;）字型的選取標記：預設狀態**

![具有關閉（&times;）字元的預設選取標記](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />具有關閉（&times;）字元的預設選取標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Tag.TagSelectedGlyph` |

**具有關閉（&times;）圖像的選取標記：滑鼠停留狀態**

![停留時使用關閉（&times;）圖像的選取標記](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />停留時使用關閉（&times;）圖像的選取標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagSelectedGlyphHoverBackground` |
| 前景 (字符) | `Tag.TagSelectedGlyphHover` |
| 框線 | `Tag.TagSelectedGlyphHoverBorder` |

**具有關閉（&times;）圖像的選取標記：已按下的狀態**

![選取的已按下標記與關閉（&times;）字元](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />選取的已按下標記與關閉（&times;）字元

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagSelectedGlyphPressedBackground` |
| 前景 (字符) | `Tag.TagSelectedGlyphPressed` |
| 框線 | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>工具視窗
不需要複製工具視窗，因為它們是由 Visual Studio 環境提供。 不過，您可能會決定要利用工具視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。

![工具視窗（紅線）](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />工具視窗（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...您正在建立 UI 的任何位置，都要與工具視窗相符。 | ...適用于您不想要在 shell 具有主題更新時自動變更的任何 UI。 |

### <a name="tool-window-frame"></a>工具視窗框架
Visual Studio 中的工具視窗用於許多不同的工作，而且可以存在於數種不同狀態的其中一種狀態。 如果開啟工具視窗，則可以將它指派至文件區域四邊的任何一邊。 工具視窗也可以浮動在 IDE 外面，讓它們可以重新定位在使用者螢幕內的任何位置。 浮動視窗一律位在 IDE 頂端。 最後，工具視窗可以停駐為文件視窗，以及顯示為文件區域中的索引標籤。 會使用文件視窗語彙基元名稱，將已停駐為文件視窗的工具視窗局部上色。

![工具視窗框架（紅線）](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />工具視窗框架（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ... 您正在建立 UI 的任何位置，都要與工具視窗相符。 | ...適用于您不想要在 shell 具有主題更新時自動變更的任何 UI。 |

**停駐的工具視窗**

![停駐的工具視窗](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />停駐的工具視窗

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| 框線 | `Environment.ToolWindowBorder` |

**浮動、專注的工具視窗**

![浮動、專注的工具視窗](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />浮動、專注的工具視窗

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| 框線 | `Environment.MainWindowActiveDefaultBorder` |

**浮動的未取得焦點工具視窗**

![浮動的未取得焦點工具視窗](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />浮動的未取得焦點工具視窗

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| 框線 | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>類似工具箱的視窗
[工具箱] 是 Visual Studio 中最常使用的其中一個通用工具視窗。 它基本上是已套用特殊主題和樣式的樹狀目錄控制項。

![類似工具箱的視窗（紅線）](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />類似工具箱的視窗（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...當您要設計的工具視窗時，一定要與 shell 工具箱一致。 | ...針對任何與 [工具箱] UI 不相似的專案，或如果您不確定 UI 是否會在 shell 工具箱色彩變更時遇到問題。 |

**工具箱節點：預設狀態**

![預設工具箱父節點](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />預設工具箱父節點

![預設工具箱子節點](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />預設工具箱子節點

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolboxContent`<br />放 |
| 背景 | `Environment.ToolWindowBackground`<br />（個別專案，如果沒有可用的控制項，則為整個視窗） |
| 框線 | None |
| 前景 (字符) | `Environment.ToolboxContent` |
| 前景 (文字) | `Environment.ToolboxContent` |

**工具箱子節點：滑鼠停留狀態**

![停留時顯示工具箱子節點](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />停留時顯示工具箱子節點

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolboxContentMouseOver`<br />（僅限個別專案） |
| 框線 | None |
| 前景 (文字) | `Environment.ToolboxContentMouseOver`<br />（僅限個別專案） |

**選取的工具箱節點：焦點狀態**

![焦點，選取的工具箱父節點](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />焦點，選取的工具箱父節點

![焦點選取的 [工具箱] 子節點](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />焦點選取的 [工具箱] 子節點

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 框線 | `TreeView.FocusVisualBorder`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 前景 (字符) | `TreeView.SelectedItemActive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 前景 (文字) | `TreeView.SelectedItemActive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |

**選取的工具箱節點：未取得焦點狀態**

![已選取，未取得焦點工具箱父節點](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />已選取，未取得焦點工具箱父節點

![已選取，未取得焦點工具箱子節點](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />已選取，未取得焦點工具箱子節點

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 框線 | None |
| 前景 (字符) | `TreeView.SelectedItemInactive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 前景 (文字) | `TreeView.SelectedItemInactive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |

### <a name="tool-window-title-bar"></a>工具視窗標題列
標題列框線不是真正的框線，而是在標題列頂端的粗線。 它的未取得焦點狀態沒有權杖名稱。

![工具視窗標題列（紅線）](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />工具視窗標題列（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...您正在建立 UI 的任何位置，都要與工具視窗相符。 | ...適用于您不想要在 shell 具有主題更新時自動變更的任何 UI。 |

**焦點標題列**

![焦點標題列](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />已取得焦點的標題列

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.TitleBarActiveGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.TitleBarActiveText` |
| 框線 | `Environment.TitleBarActiveBorder`<br />（設為與背景相同的色彩）。 |
| 拖曳控點 | `Environment.TitleBarDragHandleActive` |

**未取得焦點標題列**

![標題列未取得焦點](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />未取得焦點的標題列

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.TitleBarInactiveGradientBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.TitleBarInactiveText` |
| 框線 | N/A |
| 拖曳控點 | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>工具視窗標題列按鈕
![標題列按鈕（紅線）](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />標題列按鈕（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...適用于出現在 UI 中的按鈕，其使用工具視窗標題列的色彩標記。 | ...適用于出現在其他位置的按鈕。 |
| | ...除了指定的任何背景/前景組合外。 |

**焦點標題列按鈕：預設狀態**

![預設值，焦點標題列按鈕](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />預設值，焦點標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Environment.ToolWindowButtonActiveGlyph` |
| 框線 | N/A |

**未取得焦點標題列按鈕：預設狀態**

![預設值，未取得焦點標題列按鈕](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />預設值，未取得焦點標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Environment.ToolWindowButtonInactiveGlyph` |
| 框線 | N/A |

**焦點標題列按鈕：滑鼠停留狀態**

![停留時的焦點標題列按鈕](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />停留時的焦點標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonHoverActive` |
| 前景 (字符) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| 框線 | `Environment.ToolWindowButtonHoverActiveBorder` |

**未取得焦點標題列按鈕：暫留狀態**

![停留時未取得焦點標題列按鈕](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />停留時未取得焦點標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonHoverInactive` |
| 前景 (字符) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| 框線 | `Environment.ToolWindowButtonHoverInactiveBorder` |

**焦點標題列按鈕：已按下狀態**

![按下焦點的標題列按鈕](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />按下焦點的標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonDown` |
| 前景 (字符) | `Environment.ToolWindowButtonDownActiveGlyph` |
| 框線 | `Environment.ToolWindowButtonDownBorder` |

**未取得焦點標題列按鈕：已按下狀態**

![按下時的未取得焦點標題列按鈕](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />按下時的未取得焦點標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonDown` |
| 前景 (字符) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| 框線 | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>工具視窗索引標籤
![工具視窗索引標籤（紅線）](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />工具視窗索引標籤（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...您正在建立 UI 的任何位置，都要與工具視窗相符。 | ...適用于您不想要在 shell 具有主題更新時自動變更的任何 UI。 |

**已選取，焦點工具視窗索引標籤**

![已選取，焦點工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />已選取，已取得焦點的工具視窗索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabSelectedTab` |
| 前景 (文字) | `Environment.ToolWindowTabSelectedActiveText` |
| 框線 | `Environment.ToolWindowTabSelectedBorder`<br />（設為與背景相同的色彩）。 |

**已選取，未取得焦點工具視窗索引標籤**

![已選取，未取得焦點工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />已選取，未取得焦點的工具視窗索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabSelectedTab` |
| 前景 (文字) | `Environment.ToolWindowTabSelectedText` |
| 框線 | `Environment.ToolWindowTabSelectedBorder`<br />（設為與背景相同的色彩）。 |

**背景工具視窗索引標籤：預設狀態**

![預設背景工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />預設背景工具視窗索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />（漸層停駐點在 Visual Studio 2013 中設定為相同的色彩值）。 |
| 前景 (文字) | `Environment.ToolWindowTabText` |
| 框線 | `Environment.ToolWindowTabBorder` |

**背景工具視窗索引標籤：滑鼠停留狀態**

![滑鼠停留時的背景工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />暫留時顯示背景工具視窗索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />（漸層停駐點在 Visual Studio 2013 中設定為相同的色彩值）。 |
| 前景 (文字) | `Environment.ToolWindowTabMouseOverText` |
| 框線 | `Environment.ToolWindowTabMouseOverBorder`<br />（設為與背景相同的色彩）。 |

### <a name="auto-hide-tabs"></a>自動隱藏索引標籤

![自動隱藏索引標籤（紅線）](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline")自動隱藏索引標籤（紅線）

| 使用 。 | 不要使用 。 |
| --- | --- |
| ...您正在建立 UI 的任何位置，都要與自動隱藏工具視窗索引標籤相符。 | ...適用于您不想要在 shell 具有主題更新時自動變更的任何 UI。 |

**自動隱藏索引標籤：預設狀態**

![預設自動隱藏索引標籤](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />預設自動隱藏索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.AutoHideTabBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.AutoHideTabText` |
| 框線 | `Environment.AutoHideTabBorder` |

**自動隱藏索引標籤：滑鼠停留狀態**

![停留時自動隱藏索引標籤](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />停留時顯示 [自動隱藏] 索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />（未在主題 UI 中使用此標記的漸層停駐點）。 |
| 前景 (文字) | `Environment.AutoHideTabMouseOverText` |
| 框線 | `Environment.AutoHideTabMouseOverBorder` |

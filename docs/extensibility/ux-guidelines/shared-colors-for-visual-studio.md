---
title: 視覺工作室的共享顏色 |微軟文件
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699935"
---
# <a name="shared-colors-for-visual-studio"></a>視覺工作室的分享顏色
在設計使用通用 Visual Studio 外殼元素的 UI 時,或者希望介面元素與類似功能保持一致時,請使用包定義檔中的現有權杖名稱來選擇和分配顏色。 這可確保您的 UI 與整體 Visual Studio 環境保持一致，而且會在加入或更新佈景主題時自動更新。

本文說明常見 UI 項目以及它們使用的語彙基元名稱，以在建置類似的 UI 時進行參考。 如需如何存取這些色彩語彙基元的特定資訊，請參閱 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。

請務必正確地使用語彙基元名稱：

- **根據函式來使用語彙基元名稱，而不是色彩本身。** 常見共用色彩是與特定介面項目相關聯，並且僅適用於相同或類似的功能。 例如，請不要只因為您喜歡微調進度動畫之已按下下拉式方塊的色彩，就重複使用該色彩。 組合框和動畫的功能不同,如果與組合框關聯的顏色發生更改,則可能不再是動畫元素的適當顏色。 一致地使用色彩可協助引導您的使用者並避免混淆。

- **以正確的組合來使用背景和文字色彩。** 要與文字搭配使用的背景色彩將有相關聯的文字色彩。 務必使用背景所指定的文字色彩。 如果沒有關聯的文本顏色,則不要將該背景顏色用於預期要顯示文本的任何曲面。 文字和背景顏色的其他組合可能會導致無法讀的介面。

- **使用其位置適用的控制項色彩。** 在某些州,某些 Visual Studio 控件沒有單獨的邊框和背景顏色。 而是會選取其後介面的色彩。 務必根據控制項所放置的位置，而為其使用適合的語彙基元名稱。

> [!IMPORTANT]
> 不要使用"起始頁"或"蘋果"類別中的權杖。

## <a name="common-shared-controls"></a>通用共用控制項

當您在功能中使用標準 Visual Studio 命令列時,您將可以造取樣式的外殼控制項。 不應重新範本這些常見控制項。 不過，如果您需要建置自訂命令列，則可能也需要建置自訂控制項。 在該情況下，請務必針對下列每個控制項使用正確的語彙基元名稱，讓您的 UI 與 Visual Studio 的其餘部分一致。

### <a name="button-controls"></a>按鈕控制項

![按鈕控制項紅線](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| 使用。。。 | 不要使用... |
| --- | --- |
| ...對於要與 Visual Studio 主題(淺色、深色、藍色或系統高對比度主題)集成的文檔中的按鈕。 | ...用於在自定義背景上顯示的按鈕,該按鈕不是 Visual Studio 主題的一部分。 |

**按鈕:標準狀態**

![標準按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.標準")<br />標準按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.Button` |
| 按鈕框線 | `CommonControls.ButtonBorder` |

**按鈕:預設狀態**

![預設按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.按鈕.預設")<br />預設按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonDefault` |
| 按鈕框線 | `CommonControls.ButtonBorderDefault` |

**按鈕:關閉狀態**

![關閉按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.按鈕.禁用")<br />關閉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonDisabled` |
| 按鈕框線 | `CommonControls.ButtonBorderDisabled` |

**按鍵:移動狀態**

![停留時顯示按鈕](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />停留時顯示按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonHover` |
| 按鈕框線 | `CommonControls.ButtonBorderHover` |

**按鍵:按下狀態**

![按下按鈕](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.按鈕.壓榨")<br />按下按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonPressed` |
| 按鈕框線 | `CommonControls.ButtonBorderPressed` |

**按鍵:焦點狀態**

![焦點按鍵](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.聚焦")<br />焦點按鍵

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 按鈕 | `CommonControls.ButtonFocused` |
| 按鈕框線 | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>核取方塊控制項
![勾選方塊(紅線)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />勾選方塊(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...用於複選框控制件包含在文檔井中。 | ...對於不是複選框控件的任何 UI。 |

**勾選盒:預設狀態**

![核取方塊](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />預設選擇的欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackground` |
| 框線 | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| 圖像 | `CommonControls.CheckBoxGlyph` |

**勾選盒:關閉狀態**

![關閉選擇的方塊](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />關閉選擇的方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundDisabled` |
| 框線 | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| 圖像 | `CommonControls.CheckBoxGlyphDisabled` |

**勾選盒:懸停狀態**

 ![停留時顯示核取方塊](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />停留時顯示核取方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundHover` |
| 框線 | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| 圖像 | `CommonControls.CheckBoxGlyphHover` |

**勾選盒:按下狀態**

![按下複選方塊](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />按下複選方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundPressed` |
| 框線 | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| 圖像 | `CommonControls.CheckBoxGlyphPressed` |

**勾選盒:焦點狀態**

![焦點選擇](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />焦點選擇

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundFocused` |
| 框線 | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| 圖像 | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>下拉清單與組合框
![下拉/組合框(紅線)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />下拉/組合框(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...對於文檔中的下拉框和組合框。 | ...對於不是下拉框或組合框的任何 UI。 |
| | ...將命令列[下拉列表](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)或[組合框](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)。 |

**下拉清單與組合框:預設狀態**

![預設下拉/組合框](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />預設下拉/組合框

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackground` |
| 框線 | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| 分隔符號 | `CommonControls.ComboBoxSeparator` |
| 圖像 | `CommonControls.ComboBoxGlyph` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackground` |

**下拉清單與組合框:關閉狀態**

![關閉的下拉/ 組合框](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />關閉的下拉/ 組合框

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundDisabled` |
| 框線 | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| 分隔符號 | `CommonControls.ComboBoxSeparatorDisabled` |
| 圖像 | `CommonControls.ComboBoxGlyphDisabled` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**下拉清單與組合框:懸停狀態**

![停留時顯示下拉式方塊](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />停留時顯示下拉式方塊

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundHover` |
| 框線 | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| 分隔符號 | `CommonControls.ComboBoxSeparatorHover` |
| 圖像 | `CommonControls.ComboBoxGlyphHover` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundHover` |

**下拉清單與組合框:按下狀態**

![按下的下拉/ 組合框](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />按下的下拉/ 組合框

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundPressed` |
| 框線 | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| 分隔符號 | `CommonControls.ComboBoxSeparatorPressed` |
| 圖像 | `CommonControls.ComboBoxGlyphPressed` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**下拉清單項目檢視:按下狀態**

 ![下拉/組合框按下列表項目檢視](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />下拉/組合框按下列表項目檢視

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| 框線 | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| 項目文字 | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| 背景陰影 | `CommonControls.ComboBoxListBackgroundShadow` |

**下拉清單與組合框:焦點狀態**

![帶焦點的下拉/ 組合框](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />帶焦點的下拉/ 組合框

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundFocused` |
| 框線 | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| 分隔符號 | `CommonControls.ComboBoxSeparatorFocused` |
| 圖像 | `CommonControls.ComboBoxGlyphFocused` |
| 字符背景 | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**下拉清單與組合框:文字輸入選擇**

![下拉/組合框文字輸入選擇](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />下拉/組合框文字輸入選擇

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 反白顯示 | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>表格式資料 (方格) 控制項
表格式資料控制項 (也稱為方格控制項) 是 Visual Studio 通用控制項，可用來在多個資料行中顯示大量資料。 標準表格式資料控制項可以位於 Visual Studio 的多個位置：[錯誤清單] 工具視窗、IntelliTrace 報告和記憶體堆積檢視等等。 請一律使用所提供的標準表格式資料控制項。 在一些罕見情況下，您可能無法存取標準表格式資料控制項。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他表格式資料控制項一致。

![表格資料/網格控制(紅線)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />表格資料/網格控制(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...用於表格或網格控制項。 | ...對於不是表格或網格控制項的任何 UI。 |

#### <a name="column-headers"></a>資料行標題
資料行標頭包含背景、框線、標題文字，以及通常在依該資料行排序方格時使用的選用字符。

**列標題:預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Header.Default` |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (字符) | `Header.Glyph` |
| 框線 | `Header.SeparatorLine` |

**列標題:懸停狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Header.MouseOver` |
| 前景 (文字) | `Environment.CommandBarTextHover` |
| 前景 (字符) | `Header.MouseOverGlyph` |
| 框線 | `Header.SeparatorLine` |

**列標題:按下狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundPressed` |
| 前景 (文字) | `CommonControls.CheckBoxBorderPressed` |
| 前景 (字符) | `CommonControls.CheckBoxTextPressed` |
| 框線 | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>清單檢視項目
 清單檢視項目包含背景和內容。 內容可以是文字及/或圖示。

**清單檢視項目:預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | 透明 |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 框線 | None |

**清單檢視項目:動作狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (文字) | `TreeView.SelectedItemActiveText` |
| 框線 | None |

**清單檢視項目:非作用狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (文字) | `TreeView.SelectedItemInactiveText` |
| 框線 | None |

### <a name="ui-text"></a>UI 文字

#### <a name="instructional-text"></a>教學文字
教學文本對在對話框或文檔頁中應該怎麼做提供了顯著的主要說明。

![預設教學文字](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />預設教學文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>輔助教學文字
在包含大量文本和控件的文件頁中,某些指令性文本使用不同的顏色值。 這有助於傳達哪些資訊最重要,並降低 UI 元素的總體密度。 (另請參閱以下提示文本部分。

![輔助教學文字](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />輔助教學文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>提示文字
提示文本顯示在空控件、控件下方或空文檔表面上,以向用戶顯示下一步該怎麼做。 您可以使用具有視窗或控制項背景的提示文本。

**預設提示文字**

![預設提示文字](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />預設提示文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `Environment.ControlEditHintText` |

**需要的提示文字**

![需要的提示文字](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />需要的提示文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `Environment.ControlRequiredHintText` |
| 背景 | `Environment.ControlRequiredBackground` |

**搜尋方塊控制文字**

> 有關與搜尋控制件相關的其他顏色標記,請參閱[搜尋框](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes)。

![搜尋方塊控制文字](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />搜尋方塊控制文字

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
超連結是一個控件,沒有前景/背景對。 在所有情況下,使用前景超連結顏色,該顏色將在深色、灰色和白色背景上正確顯示。 如果不對超連結控制項使用顏色標記,您將看到"已按下"的預設系統顏色,該顏色將呈紅色閃爍。 這是控制項未使用正確的環境顏色標記的信號。

![超連結(紅線)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />超連結(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...當您需要創建自定義超連結時。 | ...對於不是超連結的任何內容。 |

**超連結:預設狀態**

![預設超連結](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />預設超連結

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlink` |

**超連結:懸停狀態**

![停留時顯示超連結](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />停留時顯示超連結

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlinkHover` |

**超連結:按下狀態**

![按下的超連結](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />按下的超連結

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlinkPressed` |

**超連結:停用狀態**

![關閉的超連結](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />關閉的超連結

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>資訊列
資訊列用來提供所指定內容的詳細資訊，而且一律會出現在文件視窗或工具視窗的頂端。

![資訊列(紅線)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />資訊列(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...創建自定義資訊列時。 | ...對於與資訊欄不類似的 UI 元素。 |

**資訊列:預設狀態**

![預設資訊列](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />預設資訊列

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.InfoBarBackground` |
| 前景 (文字) | `InfoBar.InfoBar` |
| 框線 | `InfoBar.InfoBarBorder` |

**資訊列&times;關閉( ) 按鈕: 預設狀態**

![預設資訊列&times;關閉( ) 按鈕](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />預設資訊列&times;關閉( ) 按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButton` |
| 框線 | `InfoBar.CloseButtonBorder` |
| 圖像 | `InfoBar.CloseButtonGlyph` |

**資訊列&times;關閉( ) 按鈕: 移動狀態**

![移動時的資訊列&times;關閉( ) 按鈕](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />移動時的資訊列&times;關閉( ) 按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButtonHover` |
| 框線 | `InfoBar.CloseButtonHoverBorder` |
| 圖像 | `InfoBar.CloseButtonHoverGlyph` |

**資訊列&times;關閉( ) 按鈕: 按下狀態**

![按下資訊列&times;關閉( ) 按鈕](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />按下資訊列&times;關閉( ) 按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButtonDown` |
| 框線 | `InfoBar.CloseButtonDownBorder` |
| 圖像 | `InfoBar.CloseButtonDownGlyph` |

**資訊列超連結按鈕:預設狀態**

![預設資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />預設資訊列超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `InfoBar.Hyperlink` |

**資訊列超連結按鈕:懸停狀態**

![移動的資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />移動的資訊列超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `Infobar.HyperlinkMouseOver`<br />(帶下劃線) |

**資訊列超連結按鈕:按下狀態**

![按下資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />按下資訊列超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `Infobar.HyperlinkMouseDown`<br />(帶下劃線) |

**資訊列內聯超連結(句子內):默認狀態**

![預設內聯資訊列超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />預設內聯資訊列超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `InfoBar.Hyperlink` |

**資訊列內聯超連結(在句子中):懸停狀態**

![移動的字列內聯超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />移動的字列內聯超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `Infobar.HyperlinkMouseOver`<br />(帶下劃線) |

**資訊列內聯超連結(在句子中):按下狀態**

![按下資訊列內聯超連結按鈕](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />按下資訊列內聯超連結按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景(文字) | `Infobar.HyperlinkMouseDown`<br />(帶下劃線) |

**資訊列按鈕:預設狀態**

![預設資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />預設資訊列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.Button` |
| 前景(文字) | `InfoBar.Button` |
| 框線 | `InfoBar.ButtonBorder` |

**資訊列按鈕:移動狀態**

![移動的資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />移動的資訊列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonMouseOver` |
| 前景(文字) | `InfoBar.ButtonMouseOver` |
| 框線 | `InfoBar.ButtonMouseOverBorder` |

**資訊列按鈕:按下狀態**

![按下資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />按下資訊列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonMouseDown` |
| 前景(文字) | `InfoBar.ButtonMouseDown` |
| 框線 | `InfoBar.ButtonMouseDownBorder` |

**資訊列按鈕:關閉狀態**

![關閉資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />關閉資訊列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonDisabled` |
| 前景(文字) | `InfoBar.ButtonDisabled` |
| 框線 | `InfoBar.ButtonDisabledBorder` |

**資訊列按鈕:聚焦狀態**

![焦點資訊列按鈕](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />焦點資訊列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonFocus` |
| 前景(文字) | `InfoBar.ButtonFocus` |
| 框線 | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>捲軸
滾動條由 Visual Studio 環境設置樣式,無需以主題為主題。 但是,您可能決定要利用滾動條中使用的顏色,以便 UI 始終與 Visual Studio 環境的這一部分保持一致。

![捲軸軸(紅線)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />捲軸軸(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...創建要匹配 Visual Studio 滾動條的 UI 時。 | ...對於不想始終匹配滾動條 UI 的任何內容。 |

**捲軸:預設狀態**

![預設捲軸列](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />預設捲軸列

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 捲軸 | `Environment.ScrollBarBackground` |
| 前景 (捲動方塊) | `Environment.ScrollBarThumbBackground` |

**捲軸列:移動狀態**

![停留時顯示捲軸](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />停留時顯示捲軸

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 捲軸 | `Environment.ScrollBarBackground` |
| 前景 (捲動方塊) | `Environment.ScrollBarThumbMouseOverBackground` |

*捲軸:按下狀態**

![按下捲軸列](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />按下捲軸列

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 捲軸 | `Environment.ScrollBarBackground` |
| 前景 (捲動方塊) | `Environment.ScrollBarThumbPressedBackground` |

**捲軸箭號:預設狀態**

![預設捲軸箭頭](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />預設捲軸箭頭

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowBackground`<br />(設置為與滾動條相同的顏色。 |
| 前景 (字符) | `Environment.ScrollBarArrowGlyph` |

**捲軸箭頭:懸停狀態**

![停留時顯示捲軸箭號](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />停留時顯示捲軸箭號

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowMouseOverBackground`<br />(設置為與滾動條相同的顏色。 |
| 前景 (字符) | `Environment.ScrollBarArrowGlyphMouseOver` |

**捲軸箭號:按下狀態**

![按下捲軸箭頭](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />按下捲軸箭頭

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowPressedBackground`<br />(設置為與滾動條相同的顏色。 |
| 前景 (字符) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>搜尋框
可能的話，會使用 Visual Studio 環境所提供的通用搜尋控制項。 搜尋方塊色彩位於 **ShellColors.pkgdef** 檔案的 "SearchControl" 分類中，其中包含輸入欄位、動作按鈕、下拉式按鈕和下拉式功能表的語彙基元名稱。

搜尋方塊可以是數種狀態中的其中一種，但其中有一些互斥：

- 「已取得焦點」或「未取得焦點」指的是游標是否在文字方塊中。

- 「使用中」或「非使用中」指的是使用者是否已在文字方塊中輸入搜尋查詢。

- 「暫留」表示使用者已將滑鼠指標放在搜尋方塊上方 (這種狀態會覆寫所有其他狀態)。

- 「已停用」表示已關閉目前內容的搜尋功能。

![搜尋框(紅線)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />搜尋框(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...設計自定義搜索框時。 | ...任何不是搜索框的東西。 |
| | ...對於不想始終匹配搜索框 UI 的任何內容。 |

**焦點搜尋輸入欄位**

![焦點搜尋輸入欄位](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />焦點搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.FocusedBackground` |
| 前景 (文字) | `SearchControl.FocusedBackground` |
| 框線 | `SearchControl.FocusedBorder` |
| 分隔符號 | `SearchControl.FocusedDropDownSeparator` |

**未聚焦、活動搜尋輸入欄位**

![搜尋輸入欄位未取得焦點](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />未聚焦、活動搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.SearchActiveBackground` |
| 前景 (文字) | `SearchControl.SearchActiveBackground` |
| 框線 | `SearchControl.UnfocusedBorder` |
| 分隔符號 | `SearchControl.DropDownSeparator` |

**未聚焦、非作用搜尋輸入欄位**

![未聚焦、非作用搜尋輸入欄位](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />未聚焦、非作用搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.Unfocused` |
| 前景 (文字) | `SearchControl.Unfocused` |
| 框線 | `SearchControl.UnfocusedBorder` |
| 分隔符號 | `SearchControl.DropDownSeparator` |

**突顯的搜尋輸入欄位(只有限制文字)**

![突顯的搜尋輸入欄位](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />突顯的搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.Selection` |
| 前景 (文字) | `SearchControl.FocusedBackground` |
| 框線 | None |
| 分隔符號 | `SearchControl.FocusedDropDownSeparator` |

**關閉搜尋輸入欄位**

![關閉搜尋輸入欄位](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />關閉搜尋輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.Disabled` |
| 前景 (文字) | `SearchControl.Disabled` |
| 框線 | `SearchControl.DisabledBorder` |
| 分隔符號 | `SearchControl.DropDownSeparator` |

**焦點搜尋操作按鈕**

![搜尋動作按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />焦點搜尋操作按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (搜尋字符) | `SearchControl.SearchGlyph` |
| 前景 (停止字符) | `SearchControl.StopGlyph` |
| 前景 (清除字符) | `SearchControl.ClearGlyph` |
| 框線 | N/A |

**沒有焦點搜尋操作按鈕**

![沒有焦點搜尋操作按鈕](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />沒有焦點搜尋操作按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (搜尋字符) | `SearchControl.SearchGlyph` |
| 前景 (停止字符) | `SearchControl.StopGlyph` |
| 前景 (清除字符) | `SearchControl.ClearGlyph` |
| 框線 | N/A |

**按下搜尋操作按鈕**

![按下搜尋操作按鈕](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />按下搜尋操作按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.ActionButtonMouseDown` |
| 前景 (字符) | `SearchControl.ActionButtonMouseDownGlyph` |
| 框線 | `SearchControl.ActionButtonMouseDownBorder` |

**關閉搜尋操作按鈕**

![已停用搜尋動作按鈕](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />關閉搜尋操作按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `SearchControl.ActionButtonDisabledGlyph` |
| 框線 | None |

**焦點搜尋下拉按鈕**

![焦點搜尋下拉按鈕](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />焦點搜尋下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.FocusedDropDownButton` |
| 前景 (字符) | `SearchControl.FocusedDropDownButtonGlyph` |
| 框線 | `SearchControl.FocusedDropDownButtonBorder` |

**沒有焦點搜尋下拉按鈕**

![沒有焦點搜尋下拉按鈕](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />沒有焦點搜尋下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.UnfocusedDropDownButton` |
| 前景 (字符) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| 框線 | `SearchControl.UnfocusedDropDownButtonBorder` |

**按下搜尋下拉按鈕**

![按下搜尋下拉按鈕](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />按下搜尋下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.MouseDownDropDownButton` |
| 前景 (字符) | `SearchControl.MouseDownDropDownButtonGlyph` |
| 框線 | `SearchControl.MouseDownDropDownButtonBorder` |

**關閉搜尋下拉按鈕**

![關閉搜尋下拉按鈕](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />關閉搜尋下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `SearchControl.DisabledDownButtonGlyph` |
| 框線 | None |

#### <a name="search-drop-down-lists"></a>搜尋下拉式清單
搜索框下拉菜單可能比 Visual Studio 中的其他下拉菜單稍微複雜一些。 「建議搜尋」和「搜尋選項」部分可以單獨或一起顯示在菜單中,並且每個部分分別著色。 這兩個區段同時出現時，也會有一條線來區隔它們，而且會有框線括住整個下拉式功能表。

![搜尋下拉清單(紅線)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />搜尋下拉清單(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...建立自定義搜索下拉清單時。 | ...用於出現在其他上下文中的下拉清單。 |
| ...正確的清單元件的正確權杖名稱。 | ...在指定以外的任何背景/前景組合中。 |

**搜尋下拉清單元素**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 框線 | `SearchControl.PopupBorder` |
| 分隔符號 | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**建議搜尋:預設狀態**

![預設建議搜尋](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />預設建議搜尋

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `SearchControl.PopupItemText` |

**建議搜尋:狀態狀態**

![低上列的建議搜尋](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />低上列的建議搜尋

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `SearchControl.PopupMouseOverItemText` |
| 框線 | `SearchControl.PopupControlMouseOverBorder` |

**搜尋選項:預設狀態**

![搜尋核取方塊](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />預設搜尋選項(選擇方選盒)

![搜尋選項](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />預設搜尋選項 (連結)

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (核取方塊文字) | `SearchControl.PopupCheckboxText` |
| 前景 (連結文字) | `SearchControl.PopupButtonText` |
| 頁首背景 | `SearchControl.PopupSectionHeaderGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (頁首文字) | `SearchControl.PopupSectionHeaderText` |

**搜尋選項:懸停狀態**

![懸停上的搜尋選項(選擇方選盒)](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />懸停上的搜尋選項(選擇方選盒)

![在下端搜尋選項(連結)](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />在下端搜尋選項(連結)

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (核取方塊文字) | `SearchControl.PopupCheckboxMouseDownText` |
| 前景 (連結文字) | `SearchControl.PopupButtonMouseDownText` |
| 框線 | `SearchControl.PopupControlMouseOverBorder` |

**搜尋選項:按下狀態**

![按下的搜尋選項(選擇方選盒)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />按下的搜尋選項(選擇方選盒)

![按下的搜尋選項(連結)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />按下的搜尋選項(連結)

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 核取方塊背景 | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (核取方塊文字) | `SearchControl.PopupCheckboxMouseDownText` |
| 連結背景 | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (連結文字) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>樹狀圖
多個工具視窗(包括解決方案資源管理員、伺服器資源管理員和類檢視)實現了一個分層組織方案,其顏色由`TreeView`類別中的顏色名稱控制。 樹狀檢視中的所有項目都會有背景和文字色彩。 具有巢狀子項目的項目也具有字符可指出展開還是摺疊項目。

![樹狀圖(紅線)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />樹狀圖(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...在需要實現分層組織視圖的任何地方。 | ...任何與樹視圖不相似的內容。 |
| | ...在指定以外的任何背景/前景組合中。 |

**樹狀圖:預設狀態**

![預設樹檢視項目](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />預設樹檢視項目

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.Background` |
| 前景 (文字) | `TreeView.Background` |
| 前景 (字符) | `TreeView.Glyph` |
| 框線 | None |

**樹狀圖:懸停狀態**

![懸停時樹檢視項](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />懸停時樹檢視項

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.Background` |
| 前景 (文字) | `TreeView.Background` |
| 前景 (字符) | `TreeView.GlyphMouseOver` |
| 框線 | None |

**樹狀圖:拖動狀態**

![拖動時樹檢視](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />拖動時樹檢視

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.DragOverItem` |
| 前景 (文字) | `TreeView.DragOverItem` |
| 前景 (字符) | `TreeView.DragOverItemGlyph` |
| 框線 | None |

**樹視圖項:選定、集中狀態**

![選定和重點突出的樹視圖項](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />選定和重點突出的樹視圖項

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (文字) | `TreeView.SelectedItemActive` |
| 前景 (字符) | `TreeView.SelectedItemActiveGlyph` |
| 框線 | `TreeView.FocusVisualBorder` |

**樹視圖項:選定、無焦點狀態**

![已選擇或未聚焦的樹檢視](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />已選擇或未聚焦的樹檢視

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (文字) | `TreeView.SelectedItemInactive` |
| 前景 (字符) | `TreeView.SelectedItemInactiveGlyph` |
| 框線 | None |

**樹狀圖:懸停、選擇和聚焦狀態**

![移動時選擇與聚焦樹檢視](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />移動時選擇與聚焦樹檢視

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (文字) | `TreeView.SelectedItemActive` |
| 前景 (字符) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| 框線 | `TreeView.FocusVisualBorder` |

**樹狀圖:懸停、選擇與未聚焦狀態**

![移動時選擇未聚焦的樹檢視](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />移動時選擇未聚焦的樹檢視

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (文字) | `TreeView.SelectedItemInactive` |
| 前景 (字符) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| 框線 | None |

## <a name="shell-appearance"></a>Shell 外觀

### <a name="background"></a>背景
環境背景包含兩個層級。 下層是涵蓋整個 IDE 的單色。 上層可放入命令櫃下方以及 IDE 左右兩側邊緣的工具視窗自動隱藏通道之間。 在"淺色"和"深色"主題中,頂部和底部背景圖層設置為相同的顏色。

![視覺工作室外殼背景(紅線)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />視覺工作室外殼背景(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...用於要匹配視覺工作室環境背景的位置。 | ...作為不是背景曲面的位置的填充。 |
| | ...作為放置前景元素的背景。 |

**底部層外殼外觀**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.EnvironmentBackground` |

**頂層外殼外觀**

> 設定為與 Visual Studio 2013 淺色調和暗色調佈景主題相同色彩值的漸層停駐點。

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>命令櫃
兩組語彙基元名稱用於命令櫃背景：一組用於功能表列所在的位置，一組用於命令列所在的位置。 個別命令列群組有其專屬背景色彩值 (會在＜命令列＞一節中詳細討論)。 功能表列和命令列文字分別會在功能表和命令列一節中進行討論。

![視覺化工作室命令架(紅線)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />視覺化工作室命令架(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...用於放置功能表或工具列的區域。 | ...對於與命令架子不類似的區域。 |
|...具有正確的背景/前景令牌名稱組合。 | |

**命令貨架選單列**

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

![清單設計器(紅線)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />清單設計器(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...用於類似於清單設計器的設計人員。 | ...如果您有六個以上的選項卡。 |
| ...代替在文件井編輯器頂部使用通用選項卡控制項。 | ...對於任何不像清單設計器那樣結構化的 UI。 |

**清單設計器選擇選項卡:預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.TabActive` |
| 框線 | None |

**清單設計器選取的描述窗格:預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.DescriptionPane` |

**清單設計器選定內容頁:預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Background` |
| 對話方塊 Helper 文字 | `ManifestDesigner.WatermarkText`<br />(此令牌名稱與其功能不匹配。 |

**清單設計器選項卡:未選擇狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Tab.Inactive` |

**清單設計器選項卡:懸停狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>命令結構

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>選單
功能表可以出現在 Visual Studio 中的多個位置:嵌入在文件或工具視窗中的主選單欄,或者在整個 IDE 的各個位置右鍵單擊。 針對個別項目的一節中會討論與其他 UI 項目相關聯之功能表的實作。 您應該一律使用 Visual Studio 環境所提供的標準功能表實作。 不過，在一些罕見情況下，您可能無法存取標準 Visual Studio 功能表。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他功能表一致。

![視覺工作室功能表(紅線)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />視覺工作室功能表(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...當您需要創建自定義功能表時。| ...僅背景顏色。 一律使用指定的背景/前景組合。 |
| ...當您有一個新的 UI 元件,您希望匹配 Visual Studio 選單時。| |

#### <a name="menu-titles"></a>選單標題
功能表標題包含背景、框線和標題文字，以及選用字符 (通常是在命令列中找到功能表時)。

![選單標題(紅線)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />選單標題(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...每當您創建自定義功能表標題時。 | ...任何您不想始終匹配功能表標題的。 |
| | ...在指定以外的任何背景/前景組合中。 |

**選單標題:預設狀態**

![預設選單標題](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />預設選單標題

![帶字形預設選單標題](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />帶字形預設選單標題

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景(文字) | `Environment.CommandBarTextActive` |
| 前景(字形) | `Environment.CommandBarMenuGlyph` |
| 框線 | None |

**選單標題:懸停狀態**

![停留時顯示功能表標題](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />停留時顯示功能表標題

![停留時顯示使用字符的功能表標題](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />停留時顯示使用字符的功能表標題

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景(文字) | `Environment.CommandBarTextHover` |
| 前景(字形) | `Environment.CommandBarMenuMouseOverGlyph` |
| 框線 | `Environment.CommandBarBorder` |

**選單標題:按下狀態**

![按下的選單標題](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />按下的選單標題

![標題字形按下選單標題](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />標題字形按下選單標題

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (字符) | `Environment.CommandBarMenuMouseDownGlyph` |
| 框線 | `Environment.CommandBarMenuBorder`<br />(僅左側、頂部和右側。 |

**選單標題:停用狀態**

![關閉帶字形的選單標題](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />關閉帶字形的選單標題

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (文字) | `Environment.CommandBarTextInactive` |
| 前景 (字符) | `Environment.CommandBarTextInactive` |
| 框線 | None |

#### <a name="menu-items"></a>功能表項目
個別功能表項目包含功能表文字和選用圖示、核取方塊或子功能表字符。 其背景和文字色彩會在滑鼠游標暫留時變更。 這個色彩語彙基元是背景/前景配對。

![功能表項目紅線](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| 使用。。。 | 不要使用... |
|---|---|
| ...從功能表列或命令列啟動的任何下拉清單。 | ...用於另一個上下文中的任何下拉清單。 |
| | ...在指定以外的任何背景/前景組合中。 |

**選單項目:預設狀態**

![預設選單項目](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />預設選單項目

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (子功能表字符) | `Environment.CommandBarMenuSubmenuGlyph` |
| 框線 | `Environment.CommandBarMenuBorder` |
| 圖示通道背景 | `Environment.CommandBarMenuIconBackground` |
| 分隔符號 | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**選單項目:已選擇狀態與選定狀態**

![已核取功能表](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />選取的選單項目

![已選取功能表](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />選取的選單項目

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 核取標記 | `Environment.CommandBarCheckBox` |
| 核取記號背景 | `Environment.CommandBarSelectedIcon` |
| 圖示背景 | `Environment.CommandBarSelected` |
| 圖示框線 | `Environment.CommandBarSelectedBorder` |

**選單項目:懸停狀態**

![功能表動態顯示](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />懸停上的選單項目

![已核取功能表動態顯示](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />暫停時選擇的選單項目

![已選取功能表動態顯示](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />移動時選擇選單項目

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuItemMouseOver` |
| 前景 (文字) | `Environment.CommandBarMenuItemMouseOverText` |
| 前景 (子功能表字符) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| 核取標記 | `Environment.CommandBarCheckBoxMouseOver` |
| 核取記號背景 | `Environment.CommandBarHoverOverSelectedIcon` |
| 圖示背景 | `Environment.CommandBarHoverOverSelected` |
| 圖示框線 | `Environment.CommandBarHoverOverSelectedIconBorder` |

**選單項目:停用狀態**

![已停用功能表](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />關閉的選單項目

![已核取停用的功能表](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />關閉時有複選標記的選單項目

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 前景 (文字) | `Environment.CommandBarTextInactive` |
| 前景 (子功能表字符) | `Environment.CommandBarMenuSubmenuGlyph` |
| 核取標記 | `Environment.CommandBarCheckBoxDisabled` |
| 核取記號背景 | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>命令列
命令列可以出現在 Visual Studio IDE 中的多個位置,其中最引人注目的是命令架,並嵌入在工具或文檔視窗中。

一般情況下，請一律使用 Visual Studio 環境所提供的標準命令列實作。 使用標準機制可確保正確地顯示所有視覺化詳細資料，而且互動式項目的行為會與其他 Visual Studio 命令列控制項一致。 不過，如果您需要建置專屬的命令列，請確定您使用下列語彙基元名稱正確地設定樣式。

![命令列紅線](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />命令列(紅線)

![溢位按鈕紅線](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />溢出按鈕(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...在需要嵌入式命令列但無法使用標準 Visual Studio 命令列實現的地方。 | ...對於與命令列不類似的 UI 元素。 |
| | ...對於指定權杖名稱以外的命令列元件。 |

#### <a name="command-bar-groups"></a>命令列群組
命令列群組包含一組相關的命令列控制項，而且可能包含任意數目的按鈕，分割按鈕、下拉式功能表、下拉式方塊或功能表。 這些控制項的色彩受到個別的語彙基元名稱所規範，並且會在本指南的其他位置個別討論。 分隔線用來將命令列群組分成相關的子群組。

![命令列群組紅線](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />命令列群組(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...在需要嵌入式命令列但無法使用標準 Visual Studio 命令列實現的地方。 | ...對於與命令列不類似的 UI 元素。 |
| | ...對於指定權杖名稱以外的命令列元件。 |

**命令列群組:預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 框線 | `Environment.CommandBarToolBarBorder` |
| 拖曳控點 | `Environment.CommandBarDragHandle` |
| 分隔符號 | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>命令圖示
![命令圖示紅線](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />命令圖示(紅線)

![以文字紅線的命令圖示](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />帶文字的命令圖示(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...用於將放置在命令列上的任何按鈕。 | ...具有其自己的權杖名稱的控制項。 |
| | ...在指定以外的任何背景/前景組合中。 |

**命令圖示:預設狀態**

![命令圖示預設值](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />預設指令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A (繼承自命令列背景) |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 框線 | N/A |

**命令圖示:預設狀態,已選擇**

![預設、選擇指令圖示](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />預設、選擇指令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarSelected` |
| 前景 (文字) | `Environment.CommandBarTextSelected` |
| 框線 | `Environment.CommandBarSelectedBorder` |

**命令圖示:移動或焦點狀態**

![移動或焦點的命令圖示](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />移動或焦點的命令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.CommandBarTextHover` |
| 框線 | `Environment.CommandBarBorder` |

**命令圖示:已選擇移動或焦點狀態**

![移動或焦點的選擇指令圖示](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />移動或焦點的選擇指令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarHoverOverSelected` |
| 前景 (文字) | `Environment.CommandBarTextHoverOverSelected` |
| 框線 | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **命令圖示:按下狀態**

![已按下的命令圖示](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />已按下的命令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseDownBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.CommandBarTextMouseDown` |
| 框線 | `Environment.CommandBarBorder` |

**命令圖示:關閉狀態**

![已停用的命令圖示](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />已停用的命令圖示

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A (繼承自命令列背景) |
| 前景 (文字) | `Environment.CommandBarTextInactive` |
| 框線 | N/A |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>命令列組合框

> [!IMPORTANT]
> 下拉式方塊與下拉式清單類似，但包括可編輯的文字區域。 如果下拉選單不包含可編輯的文字區域,請使用顏色標記進行[指令列下拉清單](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)。

![命令列組合框紅線](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />命令列組合框(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...構建自定義組合框時。 | ...對於不希望始終匹配命令欄 UI 的任何內容。 |
| ...創建類似於組合框的命令列控制項時。 | ...當您可以瀏覽樣式組合框時。 |

**命令列組合框輸入欄位:預設狀態**

![命令列組合框輸入欄位](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />命令列組合框輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxBackground` |
| 前景 (文字) | `Environment.ComboBoxText` |
| 框線 | `Environment.ComboBoxBorder` |
| 分隔符號 | 沒有分隔符號 |

**命令列下拉按鈕:預設狀態**

![組合框下拉&#45;下按鈕](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A (繼承自命令列背景) |
| 前景 (字符) | `Environment.ComboBoxGlyph` |

**命令列下拉清單:預設狀態**

![命令列下拉清單](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />命令列下拉清單

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxPopupBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.ComboBoxItemText` |
| 框線 | `Environment.ComboBoxPopupBorder` |

**命令列組合框輸入欄位:懸停狀態**

![將命令列的組合框輸入欄位](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />將命令列的組合框輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.ComboBoxMouseOverText` |
| 框線 | `Environment.ComboBoxMouseOverBorder` |
| 分隔符號 | `Environment.ComboBoxMouseOverSeparator` |

 **命令列下拉按鈕:懸停狀態**

![移動的命令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />移動的命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxButtonMouseOverBackground` |
| 前景 (字符) | `Environment.ComboBoxMouseOverGlyph` |

**命令列下拉清單:懸停狀態**

 ![標停的命令列下拉清單](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />標停的命令列下拉清單

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (功能表項目) | `Environment.ComboBoxItemMouseOverBackground` |
| 前景 (文字) | `Environment.ComboBoxItemMouseOverText` |
| 框線 (功能表項目) | `Environment.ComboBoxItemMouseOverBorder` |

 **命令列組合框輸入欄位:焦點狀態**

![焦點焦點框輸入欄位](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />焦點焦點框輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxFocusedBackground` |
| 前景 (文字) | `Environment.ComboBoxFocusedText` |
| 框線 | `Environment.ComboBoxFocusedBorder` |
| 分隔符號 | `Environment.ComboBoxFocusedButtonSeparator` |

**命令列下拉按鈕:焦點狀態**

![焦點命令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />焦點命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxFocusedButtonBackground` |
| 前景 (字符) | `Environment.ComboBoxFocusedGlyph` |

 **命令列組合框輸入欄位:按下狀態**

![按下指令列的組合框輸入欄位](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />按下指令列的組合框輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxMouseDownBackground` |
| 前景 (文字) | `Environment.ComboBoxMouseDownText` |
| 框線 | `Environment.ComboBoxMouseDownBorder` |
| 分隔符號 | `Environment.ComboBoxMouseDownSeparator` |

**命令列下拉按鈕:按下狀態**

![按下指令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />按下指令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxButtonMouseDownBackground` |
| 前景 (字符) | `Environment.ComboBoxMouseDownGlyph` |

**命令列組合框輸入欄位:關閉狀態**

![關閉指令列的組合框輸入欄位](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />關閉指令列的組合框輸入欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxDisabledBackground` |
| 前景 (文字) | `Environment.ComboBoxDisabledText` |
| 框線 | `Environment.ComboBoxDisabledBorder` |
| 分隔符號 | 沒有分隔符號 |

**命令列下拉按鈕:關閉狀態**

![關閉命令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />關閉命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>命令列下拉清單

> [!IMPORTANT]
> 下拉式清單與下拉式方塊類似，但沒有可編輯的文字區域。 如果下拉選單包含可編輯的文字區域,請使用顏色標記作為[指令列組合框](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)。

![命令列下拉(紅線)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />命令列下拉(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...建立自定義下拉清單控制項時。 | ...任何與下拉清單不類似的內容。 |
| | ...用於組合框或拆分按鈕。 |

**命令列下拉選擇欄位:預設狀態**

![預設命令列下拉選擇欄位](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />預設命令列下拉選擇欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownBackground` |
| 前景 (文字) | `DropDownText` |
| 框線 | `DropDownBorder` |
| 分隔符號 | 沒有分隔符號 |

**命令列下拉按鈕:預設狀態**

![預設命令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />預設命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (字符) | `Environment.DropDownGlyph` |

**命令列下拉清單:預設狀態**

![預設命令列下拉清單](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />預設命令列下拉清單

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownPopupBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.ComboBoxItemText` |
| 框線 | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**命令列下拉選擇欄位:懸停狀態**

![移動的指令列下拉選擇欄位](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />移動的指令列下拉選擇欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownMouseOverBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.DropDownMouseOverText` |
| 框線 | `Environment.DropDownMouseOverBorder` |
| 分隔符號 | `Environment.DropDownButtonMouseOverSeparator` |

**命令列下拉按鈕:懸停狀態**

![移動的命令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />移動的命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownButtonMouseOverBackground` |
| 前景 (字符) | `Environment.DropDownMouseOverGlyph` |

**命令列下拉清單:懸停狀態**

![標停的命令列下拉清單](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />標停的命令列下拉清單

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (功能表項目) | `Environment.ComboBoxItemMouseOverBackground` |
| 前景 (文字) | `Environment.ComboBoxItemMouseOverText` |
| 框線 (功能表項目) | `Environment.ComboBoxItemMouseOverBorder` |

 **命令列下拉選擇欄位:按下狀態**

![按下&#45;下拉選擇欄位](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />按下的指令列下拉選擇欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownMouseDownBackground` |
| 前景 (文字) | `Environment.DropDownMouseDownText` |
| 框線 | `Environment.DropDownMouseDownBorder` |
| 分隔符號 | `Environment.DropDownButtonMouseDownSeparator` |

**命令列下拉按鈕:按下狀態**

![按下指令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />按下指令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownButtonMouseDownBackground` |
| 前景 (字符) | `Environment.DropDownMouseDownGlyph` |

**命令列下拉選擇欄位:關閉狀態**

![關閉命令列下拉選擇欄位](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />關閉命令列下拉選擇欄位

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DropDownDisabledBackground` |
| 前景 (文字) | `Environment.DropDownDisabledText` |
| 框線 | `Environment.DropDownDisabledBorder` |
| 分隔符號 | 沒有分隔符號 |

**命令列下拉按鈕:關閉狀態**

![關閉命令列下拉按鈕](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />關閉命令列下拉按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>命令列分割按鈕
分割按鈕會與其他命令列控制項 (例如按鈕、 功能表和命令列文字) 共用許多語彙基元名稱。 基於使用方便，會在這裡重複所有必要的動作和下拉式按鈕語彙基元名稱。 拆分按鈕下拉清單是[命令欄菜單的](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)實現。

![分割按鈕紅線](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />命令列分割按鈕(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...創建自定義拆分按鈕時。 | ...用於其他類型的按鈕。 |
| | ...在指定以外的任何背景/前景組合中。 |

**命令列分割按鈕:預設狀態**

![預設命令列分割按鈕](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />預設命令列分割按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | None |
| 前景 (文字) | `Environment.CommandBarTextActive` |
| 前景 (字符) | `Environment.CommandBarSplitButtonGlyph` |
| 框線 | N/A |
| 分隔符號 | N/A |

**命令列分割按鈕:移動狀態**

![移動的命令列分割按鈕](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />移動的命令列分割按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.CommandBarTextHover` |
| 前景 (字符) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| 框線 | `Environment.CommandBarBorder` |
| 分隔符號 | `Environment.CommandBarSplitButtonSeparator` |

**命令列分割按鈕:按下狀態**

![按下指令列分割按鈕](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />按下指令列分割按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseDownBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.CommandBarTextMouseDown` |
| 前景 (字符) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| 框線 | `Environment.CommandBarBorder` |
| 分隔符號 | N/A |

**命令列分割按鈕:關閉狀態**

![關閉命令列分割按鈕](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />關閉命令列分割按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (文字) | `Environment.ComboBoxItemTextInactive` |
| 前景 (字符) | `Environment.CommandBarTextInactive` |
| 框線 | N/A |
| 分隔符號 | N/A |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>命令列「更多選項」和「溢出」按鈕
可透過加入或移除相關命令列按鈕來自訂命令列群組時，會使用 [其他選項] 按鈕。 如果因水平空間不足而截斷命令列，以及按一下時顯示包含無法顯示之命令列按鈕的功能表，則會出現 [溢位] 按鈕。 這兩個按鈕的色彩是透過同一組語彙基元名稱所控制。

![命令列「更多選項」按鈕(紅線)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />命令列「更多選項」按鈕(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...用於自訂「更多選項」或「溢出」按鈕。 | ...對於功能與「更多選項」或「溢出」按鈕沒有類似功能的按鈕。 |

**命令列「更多選項」和「溢出」按鈕:預設狀態**

![預設命令列「更多選項」按鈕](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />預設命令列「更多選項」按鈕

![預設命令列「溢出」按鈕](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />預設命令列「溢出」按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsBackground` |
| 前景 (字符) | `Environment.CommandBarOptionsGlyph` |

**命令列「更多選項」和「溢出」按鈕:懸停狀態**

![移動的指令列「更多選項」按鈕](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />移動的指令列「更多選項」按鈕

![移動的指令列「溢出」按鈕](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />移動的指令列「溢出」按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (字符) | `Environment.CommandBarOptionsMouseDownGlyph` |

**命令列「更多選項」和「溢出」按鈕:按下狀態**

![按下指令列「更多選項」按鈕](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />按下指令列「更多選項」按鈕

![已按下溢位](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />按下指令列「溢出」按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (字符) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>文件視窗
無需複製文檔視窗,因為它們由可視化工作室環境提供。 不過，您可能會決定要利用文件視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。

使用文檔視窗顏色標記時,請小心僅對類似元素使用它們,並且始終成對。 如果不執行此操作,則可能在 UI 中獲得意外的結果。

### <a name="document-window-frames"></a>文件視窗框架
文件視窗可以停駐在 IDE 中或浮動為不同的視窗。 當文件視窗漂浮在 IDE 外部時,它仍然位於文檔中,並且具有與 IDE 一部分相同的背景、邊框、文本和選項卡顏色。 不過，文件位在具有其專屬背景、框線和文字色彩的框架內。 工具視窗停駐在文件區域時，會從文件視窗語彙基元名稱繼承其索引標籤的行為和色彩。

![嵌入的文件視窗(紅線)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />嵌入的文件視窗(紅線)

![浮動文件視窗(紅線)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />浮動文件視窗(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...要與文件視窗匹配的任意位置創建 UI。 | ... 對於不希望自動更改的任何 UI(如果 shell 具有主題更新)。 |

**停靠或浮動文件視窗:預設狀態**

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | 根據文件類型 |
| 前景 (文字) | 根據文件類型 |
| 框線 | `Environment.ToolWindowBorder` |

**焦點、浮動文件視窗框架:預設狀態**

![預設焦點浮動文件視窗架構](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />預設焦點浮動文件視窗架構

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowFloatingFrame` |
| 前景 (文字) | `Environment.ToolWindowFloatingFrame` |
| 前景 (字符) | `Environment.RaftedWindowButtonActiveGlyph` |
| 框線 | `Environment.MainWindowActiveDefaultBorder` |
| 框線 (字符) | `Environment.RaftedWindowButtonActiveBorder`<br />( 設定為透明 ) |

**沒有焦點浮動文件視窗框架:預設狀態**

![預設未聚焦、浮動文件視窗框架](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />預設未聚焦、浮動文件視窗框架

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowFloatingFrameInactive` |
| 前景 (文字) | `Environment.ToolWindowFloatingFrameInactive` |
| 前景 (字符) | `Environment.RaftedWindowButtonInactiveGlyph` |
| 框線 | `Environment.MainWindowInactiveBorder` |
| 框線 (字符) | `Environment.RaftedWindowButtonInactiveBorder`<br />( 設定為透明 ) |

**焦點、浮動文件視窗框架:懸停狀態**

![移動時顯示浮動文件視窗架構](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />移動時顯示浮動文件視窗架構

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (字符) | `Environment.RaftedWindowButtonHoverActive` |
| 前景 (字符) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| 框線 (字符) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**沒有焦點浮動文件視窗框架: 移動狀態**

![移動的文件視窗框架](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />移動的文件視窗框架

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (字符) | `EnvironmentRaftedWindowButtonHoverInactive` |
| 前景 (字符) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| 框線 (字符) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**焦點、浮動文件視窗框架:按下狀態**

![按一時聚焦浮動文件視窗架構](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />按一時聚焦浮動文件視窗架構

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 (字符) | `Environment.RaftedWindowButtonDown` |
| 前景 (字符) | `Environment.RaftedWindowButtonDownGlyph` |
| 框線 (字符) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>文件索引標籤
文件索引標籤位在索引標籤通道中，表示目前開啟的文件以及目前選取的文件或使用中文件。 工具視窗也可以停駐在文件索引標籤通道中 (如果使用者將它們放在那裏)。 在此情況下，他們會使用與文件視窗相同的索引標籤色彩。 如果所建立的 UI 要一律符合文件視窗色彩 (包括佈景主題更新，或已安裝新的佈景主題時)，則請參考這些色彩語彙基元。

![文件選項卡(紅線)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />文件選項卡(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...在建立要匹配文件選項卡並自動選取主題更新或新主題顏色的 UI 的任意位置。 | ...對於在 shell 具有主題更新時不希望自動更改的任何 UI。 |

#### <a name="open-document-tabs"></a>開啟文件索引標籤
每個開啟的文件都會有顯示其名稱之文件索引標籤通道中的索引標籤。 可以在背景中選取或開啟文件，而且它們的索引標籤會反映這些狀態：

- 選取的索引標籤代表目前顯示在文件區域中的文件。 選取的索引標籤會有可延伸至文件區域頂端的文件框線。

- 背景選項卡不是當前選擇的選項卡的任何文件選項卡。按下後,它們將成為所選選項卡,並從這些權杖名稱中獲取所有背景、邊框和文字顏色。

![開啟文件選項卡(紅線)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />開啟文件選項卡(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...建立自定義文件選項卡時。 | ...臨時(預覽)選項卡。 |
| | ...對於不希望自動更改的任何 UI(如果 shell 具有主題更新)。 |

**選取的重點文件選項卡**

![選取的重點文件選項卡](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />選取的重點文件選項卡

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabSelectedGradientTop`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.FileTabSelectedText` |
| 框線 | `Environment.FileTabSelectedBorder`<br />(設置為與背景相同的顏色。 |
| 文件框線 | `Environment.FileTabDocumentBorderBackground` |

**已選擇、未聚焦的文件選項卡**

![已選擇、未聚焦的文件選項卡](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />已選擇、未聚焦的文件選項卡

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabInactiveGradientTop`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.FileTabInactiveText` |
| 框線 | `Environment.FileTabInactiveBorder`<br />(設置為與背景相同的顏色。 |
| 文件框線 | `Environment.FileTabInactiveDocumentBorderBackground` |

**背景文件選項卡:預設狀態**

![預設背景文件選項卡](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />預設背景文件選項卡

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabBackground` |
| 前景 (文字) | `Environment.FileTabText` |
| 框線 | `Environment.FileTabBorder`<br />(設置為與背景相同的顏色。 |

**背景文件選項卡:懸停狀態**

![懸停的背景文件選項卡](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />懸停的背景文件選項卡

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabHotGradientTop`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.FileTabHotText` |
| 框線 | `Environment.FileTabHotBorder`<br />(設置為與背景相同的顏色。 |

#### <a name="preview-tab"></a>預覽索引標籤
也稱為"臨時"選項卡。當用戶按下「解決方案資源管理器」工具視窗中的專案時,預覽選項卡將顯示在文檔選項卡通道的右側。 它可作為文件的預覽，也可讓使用者選擇持續在文件索引標籤通道左側開啟文件。 一次只能開啟一個預覽索引標籤。 預覽索引標籤同時具有背景和選取的狀態 (例如開啟的索引標籤)，而且可以在其作用中狀態取得焦點或未取得焦點。

![預覽選項卡(紅線)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />預覽選項卡(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...無論在哪裡,您創建臨時預覽,並希望某些元素匹配當前預覽選項卡顏色。 | ...對於不是臨時(預覽)的任何類型的文件或選項卡。 |
| | ...對於不希望自動更改的任何 UI(如果 shell 具有主題更新)。 |

**焦點、選擇預覽選項卡**

![焦點、選擇預覽選項卡](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />焦點、選擇預覽選項卡

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalSelectedActive` |
| 前景 (文字) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| 框線 | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(設置為與背景相同的顏色。 |
| 文件框線 | `Environment.FileTabProvisionalSelectedActiveBorder` |

**未聚焦、選擇預覽選項卡**

![未聚焦、選擇預覽選項卡](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />未聚焦、選擇預覽選項卡

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalSelectedInactive` |
| 前景 (文字) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| 框線 | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| 文件框線 | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**背景預覽選項卡:預設狀態**

![預設背景預覽選項卡](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />預設背景預覽選項卡

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalInactive` |
| 前景 (文字) | `Environment.FileTabProvisionalInactiveForeground` |
| 框線 | `Environment.FileTabProvisionalInactiveBorder`<br />(設置為與背景相同的顏色。 |

**背景預覽選項卡:懸停狀態**

![在滑鼠時的背景預覽選項卡](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />在滑鼠時的背景預覽選項卡

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalHover` |
| 前景 (文字) | `Environment.FileTabProvisionalHoverForeground` |
| 框線 | `Environment.FileTabProvisionalHoverBorder`<br />(設置為與背景相同的顏色。 |

#### <a name="document-overflow-button"></a>文件溢位按鈕
如果開啟一個或多個文件 (不論目前組態中是否有垂直空間可放入所有文件索引標籤)，則會有文件溢位按鈕。 文件溢出下拉選單由[命令列選單](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)顏色控制,顯示所有打開的文檔的清單(可見和隱藏)以及溢出字形會更改,具體取決於所有打開的文檔是否顯示在選項卡通道中。

![文件溢出按鈕(紅線)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />文件溢出按鈕(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...創建自定義文檔溢出按鈕時。 | ...對於與溢出按鈕不類似的 UI。 |
| | ...用於命令欄溢出按鈕。 |

**文件溢出按鈕:預設狀態**

![預設文件的溢出按鈕](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />預設文件的溢出按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonBackground` |
| 前景 (字符) | `Environment.DocWellOverflowButtonGlyph` |
| 框線 | N/A |

**文件溢出按鈕:移動狀態**

![暫留時顯示文件溢位按鈕](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />暫留時顯示文件溢位按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonMouseOverBackground` |
| 前景 (字符) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| 框線 | `Environment.DocWellOverflowButtonMouseOverBorder` |

**文件溢出按鈕:按下狀態**

![按下時的文件溢出按鈕](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />按下時的文件溢出按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonMouseDownBackground` |
| 前景 (字符) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| 框線 | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>標記
Visual Studio 支援標記，可讓使用者宣告可搜尋關鍵字，以進行追蹤。 例如，專案經理和開發人員可以使用 Team Foundation Server (TFS) 來標記工作項目。 下列表格提供以暫停和已選取狀態顯示之標記本身和「關閉圖示」字符的色彩名稱。

![在視覺工作室中標記(紅線)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />在視覺工作室中標記(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...用於支援標記的 UI。 | ...用於任何其他類型的 UI。 |

#### <a name="tags"></a>Tags

**標記:預設狀態**

![預設標記](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />預設標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.Background` |
| 前景 (文字) | `Tag.Background` |

**標記:懸停狀態**

![停留時顯示標記](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />停留時顯示標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.HoverBackground` |
| 前景 (文字) | `Tag.HoverBackgroundText` |

**標記:按下狀態**

![按下標籤](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />按下標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.PressedBackground` |
| 前景 (文字) | `Tag.PressedBackgroundText` |

**標記:選擇狀態**

![選取標記](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />選取標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.SelectedBackground` |
| 前景 (文字) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>關閉&times;( ) 標記字型

**關閉&times;( ) 標記字型: 預設狀態**

![預設關閉&times;( ) 標記字型](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />預設關閉&times;( ) 標記字型

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Tag.TagHoverGlyph` |

**關閉&times;( ) 標記字型: 移動狀態**

![關閉&times;( ) 移動標記字形](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />關閉&times;( ) 移動標記字形

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagHoverGlyphHoverBackground` |
| 前景 (字符) | `Tag.TagHoverGlyphHover` |
| 框線 | `Tag.TagHoverGlyphHoverBorder` |

**關閉&times;( ) 標記字型: 按下狀態**

![按下關閉&times;( ) 標記字形](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />按下關閉&times;( ) 標記字形

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagHoverGlyphPressedBackground` |
| 前景 (字符) | `Tag.TagHoverGlyphPressed` |
| 框線 | `Tag.TagHoverGlyphPressedBorder` |

**具有「關閉」&times;字形的選擇標記:預設狀態**

![預設選擇帶有「關閉&times;」 字型標記](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />預設選擇帶有「關閉&times;」 字型標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Tag.TagSelectedGlyph` |

**具有「關閉&times;」 字形的選擇標記:懸停狀態**

![在移動時選擇 「&times;關閉 」 字形的標記](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />在移動時選擇 「&times;關閉 」 字形的標記

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagSelectedGlyphHoverBackground` |
| 前景 (字符) | `Tag.TagSelectedGlyphHover` |
| 框線 | `Tag.TagSelectedGlyphHoverBorder` |

**具有「關閉&times;」 字形的選擇標記:按下狀態**

![已選擇,按下標籤與關閉&times;( ) 字形](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />已選擇,按下標籤與關閉&times;( ) 字形

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Tag.TagSelectedGlyphPressedBackground` |
| 前景 (字符) | `Tag.TagSelectedGlyphPressed` |
| 框線 | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>工具視窗
無需複製工具視窗,因為它們由可視化工作室環境提供。 不過，您可能會決定要利用工具視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。

![工具視窗(紅線)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />工具視窗(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...在要符合工具視窗的任意位置創建 UI。 | ...對於不希望自動更改的任何 UI(如果 shell 具有主題更新)。 |

### <a name="tool-window-frame"></a>工具視窗框架
Visual Studio 中的工具視窗用於許多不同的工作，而且可以存在於數種不同狀態的其中一種狀態。 如果開啟工具視窗，則可以將它指派至文件區域四邊的任何一邊。 工具視窗也可以浮動在 IDE 外面，讓它們可以重新定位在使用者螢幕內的任何位置。 浮動視窗一律位在 IDE 頂端。 最後，工具視窗可以停駐為文件視窗，以及顯示為文件區域中的索引標籤。 會使用文件視窗語彙基元名稱，將已停駐為文件視窗的工具視窗局部上色。

![工具視窗框架(紅線)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />工具視窗框架(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ... 在要符合工具視窗的任意位置創建 UI。 | ...對於不希望自動更改的任何 UI(如果 shell 具有主題更新)。 |

**停駐工具視窗**

![停駐工具視窗](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />停駐工具視窗

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| 框線 | `Environment.ToolWindowBorder` |

**浮動、焦點的工具視窗**

![浮動、焦點的工具視窗](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />浮動、焦點的工具視窗

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| 框線 | `Environment.MainWindowActiveDefaultBorder` |

**浮動、無焦點工具視窗**

![浮動、無焦點工具視窗](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />浮動、無焦點工具視窗

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| 框線 | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>工具盒視窗
該工具箱是可視化工作室中最常用的常用工具視窗之一。 它本質上是一個樹控件,應用了特殊的主題和樣式。

![工具箱樣視窗(紅線)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />工具箱樣視窗(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...當您設計要始終與外殼工具箱保持一致的工具視窗時。 | ...對於與工具箱 UI 不類似的任何內容,或者如果您不確定您的 UI 是否會出現問題,則外殼工具箱顏色是否發生變化。 |

**工具箱節點:預設狀態**

![預設工具箱父節點](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />預設工具箱父節點

![預設工具箱子節點](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />預設工具箱子節點

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolboxContent`<br />( 標題 ) |
| 背景 | `Environment.ToolWindowBackground`<br />(單個項目,或整個視窗(如果沒有可用的控制項) |
| 框線 | None |
| 前景 (字符) | `Environment.ToolboxContent` |
| 前景 (文字) | `Environment.ToolboxContent` |

**工具箱子節點:懸停狀態**

![停留時顯示工具箱子節點](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />停留時顯示工具箱子節點

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolboxContentMouseOver`<br />(僅限單個專案) |
| 框線 | None |
| 前景 (文字) | `Environment.ToolboxContentMouseOver`<br />(僅限單個專案) |

**選取的工具箱節點:聚焦狀態**

![焦點、選擇的工具箱父節點](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />焦點、選擇的工具箱父節點

![焦點、選擇的工具箱子節點](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />焦點、選擇的工具箱子節點

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 框線 | `TreeView.FocusVisualBorder`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 前景 (字符) | `TreeView.SelectedItemActive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 前景 (文字) | `TreeView.SelectedItemActive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |

**選取的工具箱節點:無焦點狀態**

![已選擇、未聚焦工具箱父節點](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />已選擇、未聚焦工具箱父節點

![已選擇、未聚焦工具箱子節點](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />已選擇、未聚焦工具箱子節點

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 框線 | None |
| 前景 (字符) | `TreeView.SelectedItemInactive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |
| 前景 (文字) | `TreeView.SelectedItemInactive`<br />從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類 |

### <a name="tool-window-title-bar"></a>工具視窗標題列
標題列邊框不是真正的邊框,它是標題欄頂部的粗線。 它沒有其未聚焦狀態的權杖名稱。

![工具視窗標題列(紅線)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />工具視窗標題列(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...在要符合工具視窗的任意位置創建 UI。 | ...對於不希望自動更改的任何 UI(如果 shell 具有主題更新)。 |

**已取得焦點的標題列**

![已取得焦點的標題列](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />已取得焦點的標題列

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.TitleBarActiveGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.TitleBarActiveText` |
| 框線 | `Environment.TitleBarActiveBorder`<br />(設置為與背景相同的顏色。 |
| 拖曳控點 | `Environment.TitleBarDragHandleActive` |

**未取得焦點的標題列**

![標題列未取得焦點](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />未取得焦點的標題列

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.TitleBarInactiveGradientBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.TitleBarInactiveText` |
| 框線 | N/A |
| 拖曳控點 | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>工具視窗標題列按鈕
![標題列按鈕(紅線)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />標題列按鈕(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...用於使用工具視窗標題列中的顏色標記顯示在 UI 中的按鈕。 | ...用於出現在其他位置的按鈕。 |
| | ...在指定以外的任何背景/前景組合中。 |

**聚焦標題列按鈕:預設狀態**

![預設、聚焦標題列按鈕](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />預設、聚焦標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Environment.ToolWindowButtonActiveGlyph` |
| 框線 | N/A |

**沒有焦點標題列按鈕:預設狀態**

![預設、未聚焦的標題列按鈕](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />預設、未聚焦的標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (字符) | `Environment.ToolWindowButtonInactiveGlyph` |
| 框線 | N/A |

**聚焦標題列按鈕:懸停狀態**

![移動上的焦點的焦點按鈕](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />移動上的焦點的焦點按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonHoverActive` |
| 前景 (字符) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| 框線 | `Environment.ToolWindowButtonHoverActiveBorder` |

**沒有焦點標題列按鈕:移動狀態**

![移動上未聚焦的標題列按鍵](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />移動上未聚焦的標題列按鍵

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonHoverInactive` |
| 前景 (字符) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| 框線 | `Environment.ToolWindowButtonHoverInactiveBorder` |

**聚焦標題列按鈕:按下狀態**

![按下時聚焦標題列按鈕](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />按下時聚焦標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonDown` |
| 前景 (字符) | `Environment.ToolWindowButtonDownActiveGlyph` |
| 框線 | `Environment.ToolWindowButtonDownBorder` |

**沒有焦點標題列按鈕:按下狀態**

![按下時未聚焦的標題列按鈕](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />按下時未聚焦的標題列按鈕

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonDown` |
| 前景 (字符) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| 框線 | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>工具視窗索引標籤
![工具視窗選項卡(紅線)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />工具視窗選項卡(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...在要符合工具視窗的任意位置創建 UI。 | ...對於不希望自動更改的任何 UI(如果 shell 具有主題更新)。 |

**已選取，已取得焦點的工具視窗索引標籤**

![已選取，已取得焦點的工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />已選取，已取得焦點的工具視窗索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabSelectedTab` |
| 前景 (文字) | `Environment.ToolWindowTabSelectedActiveText` |
| 框線 | `Environment.ToolWindowTabSelectedBorder`<br />(設置為與背景相同的顏色。 |

**已選取，未取得焦點的工具視窗索引標籤**

![已選取，未取得焦點的工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />已選取，未取得焦點的工具視窗索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabSelectedTab` |
| 前景 (文字) | `Environment.ToolWindowTabSelectedText` |
| 框線 | `Environment.ToolWindowTabSelectedBorder`<br />(設置為與背景相同的顏色。 |

**背景工具視窗選項卡:預設狀態**

![預設背景工具選項卡](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />預設背景工具選項卡

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(漸變停止設定為 Visual Studio 2013 中相同的顏色值。 |
| 前景 (文字) | `Environment.ToolWindowTabText` |
| 框線 | `Environment.ToolWindowTabBorder` |

**背景工具選項:懸停狀態**

![暫留時顯示背景工具視窗索引標籤](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />暫留時顯示背景工具視窗索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(漸變停止設定為 Visual Studio 2013 中相同的顏色值。 |
| 前景 (文字) | `Environment.ToolWindowTabMouseOverText` |
| 框線 | `Environment.ToolWindowTabMouseOverBorder`<br />(設置為與背景相同的顏色。 |

### <a name="auto-hide-tabs"></a>自動隱藏索引標籤

![自動隱藏選項卡(紅線)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline")自動隱藏選項卡(紅線)

| 使用。。。 | 不要使用... |
| --- | --- |
| ...要匹配自動隱藏工具視窗選項卡的任意位置。 | ...對於不希望自動更改的任何 UI(如果 shell 具有主題更新)。 |

**自動隱藏選項卡:預設狀態**

![預設自動隱藏索引標籤](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />預設自動隱藏索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.AutoHideTabBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.AutoHideTabText` |
| 框線 | `Environment.AutoHideTabBorder` |

**自動隱藏選項卡:懸停狀態**

![停留時顯示 [自動隱藏] 索引標籤](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />停留時顯示 [自動隱藏] 索引標籤

| 元素 | 語彙基元名稱：Category.color |
| --- | --- |
| 背景 | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(此令牌的漸變停止,這些令牌未在主題 UI 中使用。 |
| 前景 (文字) | `Environment.AutoHideTabMouseOverText` |
| 框線 | `Environment.AutoHideTabMouseOverBorder` |

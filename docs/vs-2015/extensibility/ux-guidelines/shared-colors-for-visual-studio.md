---
title: 共用色彩
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 87520a7e17d194d7f5cc28665a6f23466bface65
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086425"
---
# <a name="shared-colors-for-visual-studio"></a>適用於 Visual Studio 的共用的色彩

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

如果您設計的 UI 使用通用 Visual Studio Shell 項目，或您想要介面項目與類似的功能一致，請在封裝定義檔中使用現有的語彙基元名稱，以選擇並指派色彩。 這可確保您的 UI 與整體 Visual Studio 環境保持一致，而且會在加入或更新佈景主題時自動更新。

本文說明常見 UI 項目以及它們使用的語彙基元名稱，以在建置類似的 UI 時進行參考。 如需如何存取這些色彩語彙基元的特定資訊，請參閱 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。

請務必正確地使用語彙基元名稱：

- **使用根據函式，不是色彩本身的語彙基元名稱。** 常見共用色彩是與特定介面項目相關聯，並且僅適用於相同或類似的功能。 例如，請不要只因為您喜歡微調進度動畫之已按下下拉式方塊的色彩，就重複使用該色彩。 下拉式方塊和動畫的功能不同，而且，如果與下拉式方塊相關聯的色彩變更，則可能不再是動畫項目的適當色彩。 一致地使用色彩可協助引導您的使用者並避免混淆。

- **以正確的組合來使用背景和文字色彩。** 要與文字搭配使用的背景色彩將有相關聯的文字色彩。 務必使用背景所指定的文字色彩。 如果沒有相關聯的文字色彩，請不要將該背景色彩用於您希望顯示文字的任何介面。 用其他方式組合文字和背景色彩可能會導致介面無法讀取。

- **使用其位置適用的控制項色彩。** 在特定狀態中，部分 Visual Studio 控制項沒有個別框線和背景色彩。 而是會選取其後介面的色彩。 務必根據控制項所放置的位置，而為其使用適合的語彙基元名稱。

> [!IMPORTANT]
> 請勿使用 「 起始頁 」 或"Cider"。 類別目錄中的權杖

## <a name="command-structures"></a>命令結構

### <a name="BKMK_CommandMenus"></a> 功能表

功能表可能會發生在 Visual Studio 的數個位置： 主要功能表列、 內嵌在文件或工具視窗中，或以滑鼠右鍵按一下 IDE 各位置上。 針對個別項目的一節中會討論與其他 UI 項目相關聯之功能表的實作。 您應該一律使用 Visual Studio 環境所提供的標準功能表實作。 不過，在一些罕見情況下，您可能無法存取標準 Visual Studio 功能表。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他功能表一致。

![功能表紅線](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303年 000_MenuRedline")

請使用於…
- 任何需要建立自訂功能表的時機。

- 當您有想要與 Visual Studio 功能表相符的新 UI 元件時。

請勿使用於…
單一背景色彩。 一律使用指定的背景/前景組合。

#### <a name="menu-title"></a>功能表標題

功能表標題包含背景、框線和標題文字，以及選用字符 (通常是在命令列中找到功能表時)。

![功能表標題紅線](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303年 001_MenuTitleRedline")

請使用於…
任何需要建立自訂功能表標題的時機。

請勿使用於…
- 任何不想要其一律與功能表標題相符的項目。

- 任何非指定的背景/前景組合。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![功能表標題預設值](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303年 002_MenuTitleDefault")

  **功能表標題**

  背景

  None

  前景 (文字)

  `Environment.CommandBarTextActive`

  ![使用字符預設值的功能表標題](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303年 003_MenuTitleWithGlyphDefault")

  **使用字符的功能表標題**

  前景 (字符)

  `Environment.CommandBarMenuGlyph`

  Border

  None

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![暫留時顯示的功能表標題](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303年 004_MenuTitleHover")

  **功能表標題**

  背景

  `Environment.CommandBarMouseOverBackgroundBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.CommandBarTextHover`

  ![使用暫留時的字符的功能表標題](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303年 005_MenuTitleWithGlyphHover")

  **使用字符的功能表標題**

  前景 (字符)

  `Environment.CommandBarMenuMouseOverGlyph`

  Border

  `Environment.CommandBarBorder`

  **按下**

  元件

  項目

  權杖名稱：Category.color

  ![按下功能表標題](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303年 006_MenuTitlePressed")

  **功能表標題**

  背景

  `Environment.CommandBarMenuBackgroundGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.CommandBarTextActive`

  ![使用已按下的字符的功能表標題](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303年 007_MenuTitleWithGlyphPressed")

  **使用字符的功能表標題**

  前景 (字符)

  `Environment.CommandBarMenuMouseDownGlyph`

  Border

  `Environment.CommandBarMenuBorder`

  只有左側、上方和右側。

  **已停用**

  元件

  項目

  權杖名稱：Category.color

  ![使用停用的字符的功能表標題](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303年 008_MenuTitleWithGlyphDisabled")

  **使用字符的功能表標題**

  背景

  None

  前景 (文字)

  `Environment.CommandBarTextInactive`

  前景 (字符)

  `Environment.CommandBarTextInactive`

  Border

  None

#### <a name="menu"></a>功能表

個別功能表項目包含功能表文字和選用圖示、核取方塊或子功能表字符。 其背景和文字色彩會在滑鼠游標暫留時變更。 這個色彩語彙基元是背景/前景配對。

![功能表項目紅線](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303年 009_MenuItemRedline")

請使用於…
任何從功能表列或命令列啟動的下拉式清單。

請勿使用於…
- 任何其他內容中發生的下拉式清單。

- 任何非指定的背景/前景組合。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![功能表預設值](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303年 010_MenuDefault")

  **Menu**

  背景

  `Environment.CommandBarMenuBackgroundGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.CommandBarTextActive`

  前景 (子功能表字符)

  `Environment.CommandBarMenuSubmenuGlyph`

  Border

  `Environment.CommandBarMenuBorder`

  圖示通道背景

  `Environment.CommandBarMenuIconBackground`

  Separator

  `Environment.CommandBarMenuSeparator`

  陰影

  `Environment.DropShadowBackground`

  ![已核取功能表](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303年 011_MenuChecked")

  **已核取**

  核取標記

  `Environment.CommandBarCheckBox`

  核取記號背景

  `Environment.CommandBarSelectedIcon`

  ![選取 [功能表]](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303年 012_MenuSelected")

  **選取**

  圖示背景

  `Environment.CommandBarSelected`

  圖示框線

  `Environment.CommandBarSelectedBorder`

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![Menu hover](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")

  **功能表項目**

  背景

  `Environment.CommandBarMenuItemMouseOver`

  前景 (文字)

  `Environment.CommandBarMenuItemMouseOver`

  前景 (子功能表字符)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![核取功能表動態顯示](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303年 014_MenuHoverChecked")

  **已核取**

  核取標記

  `Environment.CommandBarCheckBoxMouseOver`

  核取記號背景

  `Environment.CommandBarHoverOverSelectedIcon`

  ![已選取功能表動態顯示](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303年 015_MenuHoverSelected")

  **選取**

  圖示背景

  `Environment.CommandBarHoverOverSelected`

  圖示框線

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **已停用**

  元件

  項目

  權杖名稱：Category.color

  ![已停用功能表](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303年 016_MenuDisabled")

  Menu item

  前景 (文字)

  `Environment.CommandBarTextInactive`

  前景 (子功能表字符)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![停用的功能表已核取](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303年 017_MenuDisabledChecked")

  已核取

  核取標記

  `Environment.CommandBarCheckBoxDisabled`

  核取記號背景

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>命令列

命令列可以出現在 Visual Studio IDE 的多個位置中，最值得注意的是命令櫃並內嵌在工具或文件視窗中。

一般情況下，請一律使用 Visual Studio 環境所提供的標準命令列實作。 使用標準機制可確保正確地顯示所有視覺化詳細資料，而且互動式項目的行為會與其他 Visual Studio 命令列控制項一致。 不過，如果您需要建置專屬的命令列，請確定您使用下列語彙基元名稱正確地設定樣式。

![命令列紅線](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303年 018_CommandBarRedline")

![溢位按鈕紅線](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303年 019_OverflowButtonRedline")

請使用於…
任何需要內嵌命令列，但無法使用標準 Visual Studio 命令列實作的位置。

請勿使用於…
- 任何未與命令列類似的 UI 項目。

- 不屬於語彙基元名稱所指定的命令列元件。

#### <a name="command-bar-group"></a>命令列群組

命令列群組包含一組相關的命令列控制項，而且可能包含任意數目的按鈕，分割按鈕、下拉式功能表、下拉式方塊或功能表。 這些控制項的色彩受到個別的語彙基元名稱所規範，並且會在本指南的其他位置個別討論。 分隔線用來將命令列群組分成相關的子群組。

![命令列群組紅線](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303年 020_CommandBarGroupRedline")

請使用於…
任何需要內嵌命令列，但無法使用標準 Visual Studio 命令列實作的位置。

請勿使用於…
- 任何未與命令列類似的 UI 項目。

- 不屬於語彙基元名稱所指定的命令列元件。

  **預設值** (沒有其他狀態)

  項目

  權杖名稱：Category.color

  背景

  `Environment.CommandBarGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  Border

  `Environment.CommandBarToolBarBorder`

  拖曳控點

  `Environment.CommandBarDragHandle`

  Separator

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>命令圖示

![命令圖示紅線](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303年 021_CommandIconRedline1")

![命令圖示紅線](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303年 022_CommandIconRedline2")

請使用於…
任何將放在命令列上的按鈕。

請勿使用於…
- 已具有專屬語彙基元名稱的控制項。

- 任何非指定的背景/前景組合。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![命令圖示預設值](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303年 023_CommandIconDefault")

  **Default**

  背景

  N/A (繼承自命令列背景)

  前景 (文字)

  `Environment.CommandBarTextActive`

  Border

  N/A

  ![命令圖示預設的已選取](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303年 024_CommandIconDefaultSelected")

  **選取**

  背景

  `Environment.CommandBarSelected`

  前景 (文字)

  `Environment.CommandBarTextSelected`

  Border

  `Environment.CommandBarSelectedBorder`

  **暫留和鍵盤已取得焦點**

  元件

  項目

  權杖名稱：Category.color

  ![命令圖示動態顯示](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303年 025_CommandIconHover")

  **暫留時的標準**

  背景

  `Environment.CommandBarMouseOverBackgroundBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.CommandBarTextHover`

  Border

  `Environment.CommandBarBorder`

  ![命令圖示動態顯示選取](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303年 026_CommandIconHoverSelected")

  **選取暫留時顯示**

  背景

  `Environment.CommandBarHoverOverSelected`

  前景 (文字)

  `Environment.CommandBarTextHoverOverSelected`

  Border

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **按下**

  元件

  項目

  權杖名稱：Category.color

  ![按下命令圖示](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303年 027_CommandIconPressed")

  **已按下的命令圖示**

  背景

  `Environment.CommandBarMouseDownBackgroundBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.CommandBarTextMouseDown`

  Border

  `Environment.CommandBarBorder`

  **已停用**

  元件

  項目

  權杖名稱：Category.color

  ![停用的命令圖示](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303年 028_CommandIconDisabled")

  **已停用的命令圖示**

  背景

  N/A (繼承自命令列背景)

  前景 (文字)

  `Environment.CommandBarTextInactive`

  Border

  N/A

#### <a name="BKMK_CommandComboBox"></a> 下拉式方塊

> [!IMPORTANT]
> 下拉式方塊與下拉式清單類似，但包括可編輯的文字區域。 如果下拉式清單未包括可編輯的文字區域，請使用 [Drop-down](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)下找到的色彩語彙基元。

![Combo box redline](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")

請使用於…
- 建置自訂下拉式方塊時。

- 建立與下拉式方塊類似的命令列控制項時。

  請勿使用於…
  - 任何不想要其一律與符合命令列 UI 相符的項目。

- 您能存取已設定樣式的下拉式方塊時。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![下拉式方塊輸入的欄位](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303年 030_ComboBoxInputField")

  **輸入的欄位**

  背景

  `Environment.ComboBoxBackground`

  前景 (文字)

  `Environment.ComboBoxText`

  Border

  `Environment.ComboBoxBorder`

  Separator

  沒有分隔符號

  ![下拉式方塊&#45;向下按鈕](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303年 031_ComboBoxDropdownButton")

  **下拉式按鈕**

  背景

  N/A (繼承)

  前景 (字符)

  `Environment.ComboBoxGlyph`

  ![下拉式方塊&#47;drop&#45;下拉式清單](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303年 032_ComboBoxDropdownList")

  **下拉式清單**

  背景

  `Environment.ComboBoxPopupBackgroundBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.ComboBoxItemText`

  Border

  `Environment.ComboBoxPopupBorder`

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![暫留時顯示下拉式方塊輸入的欄位](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303年 033_ComboBoxInputFieldHover")

  **輸入的欄位**

  背景

  `Environment.ComboBoxMouseOverBackgroundBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.ComboBoxMouseOverText`

  Border

  `Environment.ComboBoxMouseOverBorder`

  Separator

  `Environment.ComboBoxMouseOverSeparator`

  ![下拉式方塊&#47;drop&#45;向下按鈕，停留](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303年 034_ComboBoxDropdownButtonHover")

  **下拉式按鈕**

  背景

  `Environment.ComboBoxButtonMouseOverBackground`

  前景 (字符)

  `Environment.ComboBoxMouseOverGlyph`

  ![下拉式方塊&#47;drop&#45;下拉式清單上暫留](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303年 035_ComboBoxDropdownListHover")

  **下拉式清單**

  背景 (功能表項目)

  `Environment.ComboBoxItemMouseOverBackground`

  前景 (文字)

  `Environment.ComboBoxItemMouseOverText`

  框線 (功能表項目)

  `Environment.ComboBoxItemMouseOverBorder`

  **已取得焦點**

  元件

  項目

  權杖名稱：Color.category

  ![下拉式方塊輸入的欄位已取得焦點](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303年 036_ComboBoxInputFieldFocused")

  **輸入的欄位**

  背景

  `Environment.ComboBoxFocusedBackground`

  前景 (文字)

  `Environment.ComboBoxFocusedText`

  Border

  `Environment.ComboBoxFocusedBorder`

  Separator

  `Environment.ComboBoxFocusedButtonSeparator`

  ![下拉式方塊&#47;drop&#45;向下按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303年 037_ComboBoxDropdownButtonFocused")

  **下拉式按鈕**

  背景

  `Environment.ComboBoxFocusedButtonBackground`

  前景 (字符)

  `Environment.ComboBoxFocusedGlyph`

  **按下**

  元件

  項目

  權杖名稱：Color.category

  ![按下下拉式方塊輸入的欄位](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303年 038_ComboBoxInputFieldPressed")

  **輸入的欄位**

  背景

  `Environment.ComboBoxMouseDownBackground`

  前景 (文字)

  `Environment.ComboBoxMouseDownText`

  Border

  `Environment.ComboBoxMouseDownBorder`

  Separator

  `Environment.ComboBoxMouseDownSeparator`

  ![下拉式方塊&#47;drop&#45;向下按鈕按下](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303年 039_ComboBoxDropdownButtonPressed")

  **下拉式按鈕**

  背景

  `Environment.ComboBoxButtonMouseDownBackground`

  前景 (字符)

  `Environment.ComboBoxMouseDownGlyph`

  **已停用**

  ![停用下拉式方塊輸入的欄位](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303年 041_ComboBoxInputFieldDisabled")

  **輸入的欄位**

  背景

  `Environment.ComboBoxDisabledBackground`

  前景 (文字)

  `Environment.ComboBoxDisabledText`

  Border

  `Environment.ComboBoxDisabledBorder`

  Separator

  沒有分隔符號

  ![下拉式方塊&#47;drop&#45;向下按鈕已停用](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303年 040_ComboBoxDropdownButtonDisabled")

  **下拉式按鈕**

  背景

  None

  前景 (字符)

  `Environment.ComboBoxDisabledGlyph`

#### <a name="BKMK_CommandDropDown"></a> 下拉式清單

> [!IMPORTANT]
> 下拉式清單與下拉式方塊類似，但沒有可編輯的文字區域。 如果下拉式清單包括可編輯的文字區域，請使用 [Combo box](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)下找到的色彩語彙基元。

![卸除&#45;向下紅線](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303年 042_DropdownRedline")

請使用於…
建立自訂下拉式清單控制項時。

請勿使用於…
- 任何未與下拉式清單類似的項目。

- 下拉式方塊或分割按鈕。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![卸除&#45;下選取項目欄位](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303年 043_DropdownSelectionField")

  **選取項目欄位**

  背景

  `Environment.DropDownBackground`

  前景 (文字)

  `DropDownText`

  Border

  `DropDownBorder`

  Separator

  沒有分隔符號

  ![卸除&#45;向下按鈕](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303年 044_DropdownButton")

  **下拉式按鈕**

  背景

  None

  前景 (字符)

  `Environment.DropDownGlyph`

  ![卸除&#45;下拉式清單](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303年 045_DropdownList")

  **下拉式清單**

  背景

  `Environment.DropDownPopupBackgroundBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.ComboBoxItemText`

  Border

  `Environment.DropDownPopupBorder`

  陰影

  `Environment.DropShadowBackground`

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![卸除&#45;下暫留時的選取項目欄位](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303年 046_DropdownSelectionFieldHover")

  **選取項目欄位**

  背景

  `Environment.DropDownMouseOverBackgroundBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.DropDownMouseOverText`

  Border

  `Environment.DropDownMouseOverBorder`

  Separator

  `Environment.DropDownButtonMouseOverSeparator`

  ![卸除&#45;向下按鈕，停留](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303年 047_DropdownButtonHover")

  **下拉式按鈕**

  背景

  `Environment.DropDownButtonMouseOverBackground`

  前景 (字符)

  `Environment.DropDownMouseOverGlyph`

  ![卸除&#45;暫留時顯示的清單中向下](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303年 048_DropdownListHover")

  **下拉式清單**

  背景 (功能表項目)

  `Environment.ComboBoxItemMouseOverBackground`

  前景 (文字)

  `Environment.ComboBoxItemMouseOverText`

  框線 (功能表項目)

  `Environment.ComboBoxItemMouseOverBorder`

  **按下**

  元件

  項目

  權杖名稱：Category.color

  ![卸除&#45;下按下的選取項目欄位](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303年 049_DropdownSelectionFieldPressed")

  **選取項目欄位**

  背景

  `Environment.DropDownMouseDownBackground`

  前景 (文字)

  `Environment.DropDownMouseDownText`

  Border

  `Environment.DropDownMouseDownBorder`

  Separator

  `Environment.DropDownButtonMouseDownSeparator`

  ![卸除&#45;向下按鈕按下](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303年 050_DropdownButtonPressed")

  **下拉式按鈕**

  背景

  `Environment.DropDownButtonMouseDownBackground`

  前景 (字符)

  `Environment.DropDownMouseDownGlyph`

  **已停用**

  元件

  項目

  權杖名稱：Category.color

  ![卸除&#45;下已停用的選取項目欄位](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303年 051_DropdownSelectionFieldDisabled")

  背景

  `Environment.DropDownDisabledBackground`

  前景 (文字)

  `Environment.DropDownDisabledText`

  Border

  `Environment.DropDownDisabledBorder`

  Separator

  沒有分隔符號

  ![卸除&#45;向下按鈕已停用](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303年 052_DropdownButtonDisabled")

  背景

  N/A

  前景 (字符)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Split 按鈕

分割按鈕會與其他命令列控制項 (例如按鈕、 功能表和命令列文字) 共用許多語彙基元名稱。 基於使用方便，會在這裡重複所有必要的動作和下拉式按鈕語彙基元名稱。 分割按鈕下拉式清單是命令列 [Menus](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)的實作。

![分割按鈕紅線](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303年 053_SplitButtonRedline")

請使用於…
建置自訂分割按鈕時。

請勿使用於…
- 其他種類的按鈕。

- 任何非指定的背景/前景組合。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![分割按鈕](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303年 054_SplitButton")

  **分割按鈕 （預設值）**

  背景

  None

  前景 (文字)

  `Environment.CommandBarTextActive`

  前景 (字符)

  `Environment.CommandBarSplitButtonGlyph`

  Border

  N/A

  Separator

  N/A

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![分割按鈕，停留](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303年 055_SplitButtonHover")

  **分割按鈕 （暫留）**

  背景

  `Environment.CommandBarMouseOverBackgroundBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.CommandBarTextHover`

  前景 (字符)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Border

  `Environment.CommandBarBorder`

  Separator

  `Environment.CommandBarSplitButtonSeparator`

  **按下**

  元件

  項目

  權杖名稱：Category.color

  ![按下的 [分割] 按鈕](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303年 056_SplitButtonPressed")

  **（按下） 的 [分割] 按鈕**

  背景

  `Environment.CommandBarMouseDownBackgroundBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `Environment.CommandBarTextMouseDown`

  前景 (字符)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Border

  `Environment.CommandBarBorder`

  Separator

  N/A

  **已停用**

  元件

  項目

  權杖名稱：Category.color

  ![已停用分割按鈕](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303年 057_SplitButtonDisabled")

  **分割按鈕 （停用）**

  背景

  N/A

  前景 (文字)

  `Environment.ComboBoxItemTextInactive`

  前景 (字符)

  `Environment.CommandBarTextInactive`

  Border

  N/A

  Separator

  N/A

#### <a name="more-options-and-overflow-buttons"></a>[其他選項] 和 [溢位] 按鈕
 可透過加入或移除相關命令列按鈕來自訂命令列群組時，會使用 [其他選項] 按鈕。 如果因水平空間不足而截斷命令列，以及按一下時顯示包含無法顯示之命令列按鈕的功能表，則會出現 [溢位] 按鈕。 這兩個按鈕的色彩是透過同一組語彙基元名稱所控制。

 ![更多選項紅線](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303年 058_MoreOptionsRedline")

 請使用於…
針對自訂 [其他選項] 或 [溢位] 按鈕。

 請勿使用於…
針對沒有與 [其他選項] 或 [溢位] 按鈕類似之功能的按鈕。

 **Default**

 元件

 項目

 權杖名稱：Category.color

 ![更多選項](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303年 059_MoreOptions")

 **更多選項**

 ![溢位按鈕](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303年 060_Overflow")

 **Overflow**

 背景

 `Environment.CommandBarOptionsBackground`

 前景 (字符)

 `Environment.CommandBarOptionsGlyph`

 **Hover**

 元件

 項目

 權杖名稱：Category.color

 ![暫留時的更多選項](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303年 061_MoreOptionsHover")

 **更多選項**

 ![暫留時顯示溢位](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303年 062_OverflowOptions")

 **Overflow**

 背景

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

 前景 (字符)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **按下**

 元件

 項目

 權杖名稱：Category.color

 ![更多選項按下](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303年 063_MoreOptionsPressed")

 **更多選項**

 ![按下溢位](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303年 064_OverflowPressed")

 **Overflow**

 背景

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

 前景 (字符)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>文件視窗
 文件視窗是由 Visual Studio 環境所提供，因此不需要進行複寫。 不過，您可能會決定要利用文件視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。

 使用文件視窗色彩語彙基元時，必須小心只針對類似的項目使用這些資料，而且一定成對。 如果您沒有這麼做，則 UI 中會有未預期的結果。

### <a name="document-window-frame"></a>文件視窗框架
 文件視窗可以停駐在 IDE 中或浮動為不同的視窗。 文件視窗在 IDE 外部浮動時，還是停留在文件區域中，並且具有為 IDE 一部分時的相同背景、框線、文字和索引標籤色彩。 不過，文件位在具有其專屬背景、框線和文字色彩的框架內。 工具視窗停駐在文件區域時，會從文件視窗語彙基元名稱繼承其索引標籤的行為和色彩。

 ![停駐文件視窗紅線](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303年 065_DockedDocumentWindowRedline")

 **停駐文件視窗**

 ![浮動文件視窗紅線](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303年 066_FloatingDocumentWindowRedline")

 **浮動文件視窗**

 請使用於…
任何要建立符合文件視窗之 UI 的位置。

 請勿使用於…
針對您不想在 Shell 具有佈景主題更新時自動變更的任何 UI。

 **Default**

 元件

 項目

 權杖名稱：Category.color

 文件：停駐或浮動

 背景

 根據文件類型

 前景 (文字)

 根據文件類型

 Border

 `Environment.ToolWindowBorder`

 ![框架已取得焦點](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303年 067_FrameFocused")

 **框架： 浮動，已取得焦點**

 背景

 `Environment.ToolWindowFloatingFrame`

 前景 (文字)

 `Environment.ToolWindowFloatingFrame`

 前景 (字符)

 `Environment.RaftedWindowButtonActiveGlyph`

 Border

 `Environment.MainWindowActiveDefaultBorder`

 框線 (字符)

 `Environment.RaftedWindowButtonActiveBorder`

 設定為透明

 ![未取得焦點的框架](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303年 068_FrameUnfocused")

 **框架： 浮動，未取得焦點**

 背景

 `Environment.ToolWindowFloatingFrameInactive`

 前景 (文字)

 `Environment.ToolWindowFloatingFrameInactive`

 前景 (字符)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Border

 `Environment.MainWindowInactiveBorder`

 框線 (字符)

 `Environment.RaftedWindowButtonInactiveBorder`

 設定為透明

 **Hover**

 元件

 項目

 權杖名稱：Category.color

 ![暫留時顯示取得焦點的框架](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303年 069_FrameFocusedHover")

 **框架： 浮動，已取得焦點**

 背景 (字符)

 `Environment.RaftedWindowButtonHoverActive`

 前景 (字符)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 框線 (字符)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![框架未取得焦點停留](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303年 070_FrameUnfocusedHover")

 **框架： 浮動，未取得焦點**

 背景 (字符)

 `EnvironmentRaftedWindowButtonHoverInactive`

 前景 (字符)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 框線 (字符)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **按下**

 元件

 項目

 權杖名稱：Category.color

 ![取得焦點的框架已按下](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303年 071_FrameFocusedPressed")

 **框架： 浮動，已取得焦點**

 背景 (字符)

 `Environment.RaftedWindowButtonDown`

 前景 (字符)

 `Environment.RaftedWindowButtonDownGlyph`

 框線 (字符)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>文件索引標籤
 文件索引標籤位在索引標籤通道中，表示目前開啟的文件以及目前選取的文件或使用中文件。 工具視窗也可以停駐在文件索引標籤通道中 (如果使用者將它們放在那裏)。 在此情況下，他們會使用與文件視窗相同的索引標籤色彩。 如果所建立的 UI 要一律符合文件視窗色彩 (包括佈景主題更新，或已安裝新的佈景主題時)，則請參考這些色彩語彙基元。

 ![文件索引標籤紅線](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303年 072_DocumentTabRedline")

 請使用於…
任何要建立與文件索引標籤相符並自動選取佈景主題更新或新佈景主題色彩之 UI 的位置。

 請勿使用於…
任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。

#### <a name="open-document-tabs"></a>開啟文件索引標籤
 每個開啟的文件都會有顯示其名稱之文件索引標籤通道中的索引標籤。 可以在背景中選取或開啟文件，而且它們的索引標籤會反映這些狀態：

- 選取的索引標籤代表目前顯示在文件區域中的文件。 選取的索引標籤會有可延伸至文件區域頂端的文件框線。

- 背景索引標籤是任何非目前選取之索引標籤的文件索引標籤。按一下之後，它們會成為選取的索引標籤，並從這些語彙基元名稱取得所有背景、框線和文字色彩。

  ![開啟的文件 索引標籤紅線](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303年 073_OpenDocumentTabRedline")

  請使用於…
  建立自訂文件索引標籤時。

  請勿使用於…
  - 暫時 (預覽) 索引標籤。

- 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。

#### <a name="selected-tab"></a>選取的索引標籤
 **已取得焦點**

 元件

 項目

 權杖名稱：Category.color

 ![選取的索引標籤已取得焦點](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303年 074_SelectedTabFocused")

 **選取的文件索引標籤上，已取得焦點**

 背景

 `Environment.FileTabSelectedGradientTop`

 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

 前景 (文字)

 `Environment.FileTabSelectedText`

 Border

 `Environment.FileTabSelectedBorder`

 設定為與背景相同的色彩。

 文件框線

 `Environment.FileTabDocumentBorderBackground`

 **未取得焦點**

 元件

 項目

 權杖名稱：Category.color

 ![選取的索引標籤未取得焦點](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303年 075_SelectedTabUnfocused")

 **選取的文件索引標籤上，未取得焦點**

 背景

 `Environment.FileTabInactiveGradientTop`

 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

 前景 (文字)

 `Environment.FileTabInactiveText`

 Border

 `Environment.FileTabInactiveBorder`

 設定為與背景相同的色彩。

 文件框線

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>背景索引標籤
 **Default**

 ![背景索引標籤](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303年 076_BackgroundTab")

 **背景索引標籤的預設值**

 背景

 `Environment.FileTabBackground`

 前景 (文字)

 `Environment.FileTabText`

 Border

 `Environment.FileTabBorder`

 設定為與背景相同的色彩。

 **Hover**

 ![暫留時背景索引標籤](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303年 077_BackgroundTabHover")

 **暫留時背景索引標籤**

 背景

 `Environment.FileTabHotGradientTop`

 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

 前景 (文字)

 `Environment.FileTabHotText`

 Border

 `Environment.FileTabHotBorder`

 設定為與背景相同的色彩。

#### <a name="preview-tab"></a>預覽索引標籤

使用者按一下方案總管工具視窗中的項目時，預覽索引標籤會出現在文件索引標籤通道右側。 它可作為文件的預覽，也可讓使用者選擇持續在文件索引標籤通道左側開啟文件。 一次只能開啟一個預覽索引標籤。 預覽索引標籤同時具有背景和選取的狀態 (例如開啟的索引標籤)，而且可以在其作用中狀態取得焦點或未取得焦點。

![預覽索引標籤紅線](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303年 078_PreviewTabRedline")

請使用於…
任何要建立暫時預覽且想要某個項目符合目前預覽索引標籤色彩的位置。

請勿使用於…
- 於任何非暫時 (非預覽) 的文件種類或索引標籤種類。

- 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。

  **選取的預覽索引標籤：已取得焦點**

  元件

  項目

  權杖名稱：Category.color

  ![已取得焦點的預覽索引標籤](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303年 079_PreviewTabFocused")

  **具有焦點的預覽索引標籤**

  背景

  `Environment.FileTabProvisionalSelectedActive`

  前景 (文字)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Border

  `Environment.FileTabProvisionalSelectedActiveBorder`

  設定為與背景相同的色彩。

  文件框線

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **選取的預覽索引標籤：未取得焦點**

  元件

  項目

  權杖名稱：Category.color

  ![預覽索引標籤未取得焦點](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303年 080_PreviewTabUnfocused")

  **未取得焦點的預覽索引標籤**

  背景

  `Environment.FileTabProvisionalSelectedInactive`

  前景 (文字)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Border

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  文件框線

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **背景預覽索引標籤：預設值**

  元件

  項目

  權杖名稱：Category.color

  ![預覽 背景索引標籤](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303年 081_PreviewBackgroundTab")

  **預覽索引標籤背景索引標籤**

  背景

  `Environment.FileTabProvisionalInactive`

  前景 (文字)

  `Environment.FileTabProvisionalInactiveForeground`

  Border

  `Environment.FileTabProvisionalInactiveBorder`

  設定為與背景相同的色彩。

  **背景預覽索引標籤：Hover**

  元件

  項目

  權杖名稱：Category.color

  ![暫留時顯示 [預覽] 背景索引標籤](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303年 082_PreviewBackgroundTabHover")

  **暫留時的預覽索引標籤背景索引標籤**

  背景

  `Environment.FileTabProvisionalHover`

  前景 (文字)

  `Environment.FileTabProvisionalHoverForeground`

  Border

  `Environment.FileTabProvisionalHoverBorder`

  設定為與背景相同的色彩。

#### <a name="document-overflow-button"></a>文件溢位按鈕

如果開啟一個或多個文件 (不論目前組態中是否有垂直空間可放入所有文件索引標籤)，則會有文件溢位按鈕。 透過 **CommandBarMenu** 色彩控制的文件溢位下拉式功能表 (請參閱 [Menus](../../misc/shared-colors.md#BKMK_CommandMenus))，會顯示一份所有開啟的文件 (顯示和隱藏)，並根據是否在索引標籤通道中顯示所有開啟的文件來變更溢位字符。

![溢位紅線](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303年 083_OverflowRedline")

請使用於…
建立自訂文件溢位按鈕時。

請勿使用於…
- 針對未與溢位按鈕類似的 UI。

- 命令列溢位按鈕。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![Overflow](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")

  **文件溢位按鈕**

  背景

  `Environment.DocWellOverflowButtonBackground`

  前景 (字符)

  `Environment.DocWellOverflowButtonGlyph`

  Border

  N/A

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![暫留時顯示溢位](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303年 085_OverflowHover")

  **暫留時的文件溢位按鈕**

  背景

  `Environment.DocWellOverflowButtonMouseOverBackground`

  前景 (字符)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Border

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **按下**

  元件

  項目

  權杖名稱：Category.color

  ![按下溢位](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303年 086_OverflowPressed")

  **已按下的文件溢位按鈕**

  背景

  `Environment.DocWellOverflowButtonMouseDownBackground`

  前景 (字符)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Border

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>工具視窗
 工具視窗是由 Visual Studio 環境所提供，因此不需要進行複寫。 不過，您可能會決定要利用工具視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。

 ![工具視窗紅線](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303年 087_ToolWindowRedline")

 請使用於…
任何要建立符合工具視窗之 UI 的位置。

 請勿使用於…
任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。

### <a name="tool-window-frame"></a>工具視窗框架
 Visual Studio 中的工具視窗用於許多不同的工作，而且可以存在於數種不同狀態的其中一種狀態。 如果開啟工具視窗，則可以將它指派至文件區域四邊的任何一邊。 工具視窗也可以浮動在 IDE 外面，讓它們可以重新定位在使用者螢幕內的任何位置。 浮動視窗一律位在 IDE 頂端。 最後，工具視窗可以停駐為文件視窗，以及顯示為文件區域中的索引標籤。 會使用文件視窗語彙基元名稱，將已停駐為文件視窗的工具視窗局部上色。

 ![工具視窗框架紅線](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303年 088_ToolWindowFrameRedline")

 請使用於…
任何要建立符合工具視窗之 UI 的位置。

 請勿使用於…
任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。

 **Docked**

 元件

 項目

 權杖名稱：Category.color

 ![工具視窗停駐](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303年 089_ToolWindowDocked")

 背景

 `Environment.ToolWindowBackground`

 Border

 `Environment.ToolWindowBorder`

 **浮動： 已取得焦點**

 元件

 項目

 權杖名稱：Category.color

 ![工具視窗已取得焦點](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303年 090_ToolWindowFocused")

 背景

 `Environment.ToolWindowBackground`

 Border

 `Environment.MainWindowActiveDefaultBorder`

 **浮動： 未取得焦點**

 元件

 項目

 權杖名稱：Category.color

 ![未取得焦點的工具視窗](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303年 091_ToolWindowUnfocused")

 背景

 `Environment.ToolWindowBackground`

 Border

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>工具視窗標題列
 標題列框線不是真正的框線，而是跨標題列頂端的粗線。 它並沒有其未取得焦點狀態的語彙基元名稱。

 ![工具視窗標題列紅線](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303年 092_ToolWindowTitleBarRedline")

 請使用於…
任何要建立符合工具視窗之 UI 的位置。

 請勿使用於…
任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。

 **已取得焦點**

 元件

 項目

 權杖名稱：Category.color

 ![標題列著重](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303年 093_TitleBarFocused")

 **具有焦點的標題列**

 背景

 `Environment.TitleBarActiveGradientBegin`

 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

 前景 (文字)

 `Environment.TitleBarActiveText`

 Border

 `Environment.TitleBarActiveBorder`

 設定為與背景相同的色彩。

 拖曳控點

 `Environment.TitleBarDragHandleActive`

 **未取得焦點**

 元件

 項目

 權杖名稱：Category.color

 ![未取得焦點的標題列](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303年 094_TitleBarUnfocused")

 **未取得焦點的標題列**

 背景

 `Environment.TitleBarInactiveGradientBegin`

 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

 前景 (文字)

 `Environment.TitleBarInactiveText`

 Border

 N/A

 拖曳控點

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>標題列按鈕

![標題列按鈕紅線](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303年 095_TitleBarButtonRedline")

請使用於…
UI 中所顯示的按鈕 (當 UI 使用了來自工具視窗標題列的色彩語彙基元時)。

請勿使用於…
- 出現在其他位置的按鈕。

- 任何非指定的背景/前景組合。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![標題列按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303年 096_TitleBarButtonFocused")

  **已取得焦點**

  背景

  N/A

  前景 (字符)

  `Environment.ToolWindowButtonActiveGlyph`

  Border

  N/A

  ![標題列按鈕未取得焦點](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303年 097_TitleBarButtonUnfocused")

  **未取得焦點**

  背景

  N/A

  前景 (字符)

  `Environment.ToolWindowButtonInactiveGlyph`

  Border

  N/A

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![暫留時顯示的標題列按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303年 098_TitleBarButtonFocusedHover")

  **已取得焦點**

  背景

  `Environment.ToolWindowButtonHoverActive`

  前景 (字符)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Border

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![標題列按鈕未取得焦點停留](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303年 099_TitleBarButtonUnfocusedHover")

  **未取得焦點**

  背景

  `Environment.ToolWindowButtonHoverInactive`

  前景 (字符)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Border

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **按下**

  元件

  項目

  權杖名稱：Category.color

  ![標題列按鈕已取得焦點且按下](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303年 100_TitleBarButtonFocusedPressed")

  **已取得焦點**

  背景

  `Environment.ToolWindowButtonDown`

  前景 (字符)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Border

  `Environment.ToolWindowButtonDownBorder`

  ![標題列按鈕未取得焦點且按下](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303年 101_TitleBarButtonUnfocusedPressed")

  **未取得焦點**

  背景

  `Environment.ToolWindowButtonDown`

  前景 (字符)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Border

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>工具視窗索引標籤
 ![工具視窗索引標籤紅線](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303年 102_ToolWindowTabRedline")

 請使用於…
任何要建立符合工具視窗之 UI 的位置。

 請勿使用於…
任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。

 **選取的索引標籤**

 元件

 項目

 權杖名稱：Category.color

 ![工具視窗索引標籤已取得焦點](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303年 103_ToolWindowTabFocused")

 **已選取，已取得焦點的工具視窗索引標籤**

 背景

 `Environment.ToolWindowTabSelectedTab`

 前景 (文字)

 `Environment.ToolWindowTabSelectedActiveText`

 Border

 `Environment.ToolWindowTabSelectedBorder`

 設定為與背景相同的色彩。

 元件

 項目

 權杖名稱：Category.color

 ![工具視窗索引標籤未取得焦點](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303年 104_ToolWindowTabUnfocused")

 **已選取，未取得焦點的工具視窗索引標籤**

 背景

 `Environment.ToolWindowTabSelectedTab`

 前景 (文字)

 `Environment.ToolWindowTabSelectedText`

 Border

 `Environment.ToolWindowTabSelectedBorder`

 設定為與背景相同的色彩。

 **背景索引標籤**

 元件

 項目

 權杖名稱：Category.color

 ![工具視窗背景索引標籤](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303年 105_ToolWindowBackgroundTab")

 **背景工具視窗索引標籤**

 背景

 `Environment.ToolWindowTabGradientBegin`

 設定為與 Visual Studio 2013 相同色彩值的漸層停駐點。

 `Environment.ToolWindowTabGradientEnd`

 設定為與 Visual Studio 2013 相同色彩值的漸層停駐點。

 前景 (文字)

 `Environment.ToolWindowTabText`

 Border

 `Environment.ToolWindowTabBorder`

 元件

 項目

 權杖名稱：Category.color

 ![暫留時的工具視窗背景索引標籤](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303年 106_ToolWindowBackgroundTabHover")

 **暫留時的背景工具視窗索引標籤**

 背景

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 設定為與 Visual Studio 2013 相同色彩值的漸層停駐點。

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 設定為與 Visual Studio 2013 相同色彩值的漸層停駐點。

 前景 (文字)

 `Environment.ToolWindowTabMouseOverText`

 Border

 `Environment.ToolWindowTabMouseOverBorder`

 設定為與背景相同的色彩。

### <a name="auto-hide-tabs"></a>自動隱藏索引標籤
 ![自動&#45;隱藏紅線](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303年 107_AutoHideRedline")

 請使用於…
任何要建立符合自動隱藏工具視窗索引標籤之 UI 的位置。

 請勿使用於…
任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。

 **Default**

 元件

 項目

 權杖名稱：Category.color

 ![自動&#45;隱藏 索引標籤](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303年 108_AutoHideTab")

 **預設自動隱藏索引標籤**

 背景

 `Environment.AutoHideTabBackgroundBegin`

 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

 前景 (文字)

 `Environment.AutoHideTabText`

 Border

 `Environment.AutoHideTabBorder`

 **Hover**

 元件

 項目

 權杖名稱：Category.color

 ![自動&#45;隱藏 索引標籤上暫留](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303年 109_AutoHideTabHover")

 **暫留時的自動隱藏索引標籤**

 背景

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

 前景 (文字)

 `Environment.AutoHideTabMouseOverText`

 Border

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>通用共用控制項
 在您的功能中使用標準 Visual Studio 命令列時，您可以存取已設定樣式的 Shell 控制項，而且不應該重新設定這些通用控制項的樣板。 不過，如果您需要建置自訂命令列，則可能也需要建置自訂控制項。 在該情況下，請務必針對下列每個控制項使用正確的語彙基元名稱，讓您的 UI 與 Visual Studio 的其餘部分一致。

### <a name="search-box"></a>搜尋方塊
 可能的話，會使用 Visual Studio 環境所提供的通用搜尋控制項。 搜尋方塊色彩位於 **ShellColors.pkgdef** 檔案的 "SearchControl" 分類中，其中包含輸入欄位、動作按鈕、下拉式按鈕和下拉式功能表的語彙基元名稱。

 搜尋方塊可以是數種狀態中的其中一種，但其中有一些互斥：

- 「已取得焦點」或「未取得焦點」指的是游標是否在文字方塊中。

- 「使用中」或「非使用中」指的是使用者是否已在文字方塊中輸入搜尋查詢。

- 「暫留」表示使用者已將滑鼠指標放在搜尋方塊上方 (這種狀態會覆寫所有其他狀態)。

- 「已停用」表示已關閉目前內容的搜尋功能。

  ![搜尋方塊紅線](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303年 110_SearchBoxRedline")

  請使用於…
  設計自訂搜尋方塊時。

  請勿使用於…
  - 針對不是搜尋方塊的任何項目。

- 任何不想要其一律與搜尋方塊 UI 相符的項目。

  **已取得焦點**

  元件

  項目

  權杖名稱：Category.color

  ![搜尋輸入的欄位已取得焦點](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303年 111_SearchInputFieldFocused")

  **輸入的欄位**

  背景

  `SearchControl.FocusedBackground`

  前景 (文字)

  `SearchControl.FocusedBackground`

  Border

  `SearchControl.FocusedBorder`

  Separator

  `SearchControl.FocusedDropDownSeparator`

  ![搜尋動作按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303年 112_SearchActionButtonFocused")

  **動作按鈕**

  背景

  None

  前景 (搜尋字符)

  `SearchControl.SearchGlyph`

  前景 (停止字符)

  `SearchControl.StopGlyph`

  前景 (清除字符)

  `SearchControl.ClearGlyph`

  Border

  N/A

  ![搜尋下拉式&#45;向下按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303年 113_SearchDropdownButtonFocused")

  **下拉式按鈕**

  背景

  `SearchControl.FocusedDropDownButton`

  前景 (字符)

  `SearchControl.FocusedDropDownButtonGlyph`

  Border

  `SearchControl.FocusedDropDownButtonBorder`

  **未取得焦點**

  元件

  項目

  權杖名稱：Category.color

  ![搜尋輸入的欄位未取得焦點](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303年 114_SearchInputFieldUnfocused")

  **作用中的輸入的欄位**

  背景

  `SearchControl.SearchActiveBackground`

  前景 (文字)

  `SearchControl.SearchActiveBackground`

  Border

  `SearchControl.UnfocusedBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![搜尋輸入的欄位未取得焦點且非作用中](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303年-114-1_SearchInputFieldUnfocusedInactive")

  **非使用中的輸入的欄位**

  背景

  `SearchControl.Unfocused`

  前景 (文字)

  `SearchControl.Unfocused`

  Border

  `SearchControl.UnfocusedBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![搜尋動作按鈕未取得焦點](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303年 115_SearchActionButtonUnfocused")

  **動作按鈕**

  背景

  N/A

  前景 (搜尋字符)

  `SearchControl.SearchGlyph`

  前景 (停止字符)

  `SearchControl.StopGlyph`

  前景 (清除字符)

  `SearchControl.ClearGlyph`

  Border

  N/A

  ![搜尋下拉式&#45;向下按鈕未取得焦點](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303年 116_SearchDropdownButtonUnfocused")

  **下拉式按鈕**

  背景

  `SearchControl.UnfocusedDropDownButton`

  前景 (字符)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Border

  `SearchControl.UnfocusedDropDownButtonBorder`

  **按下**

  元件

  項目

  權杖名稱：Category.color

  ![按下搜尋動作按鈕](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303年-116-1_SearchActionButtonPressed")

  **動作按鈕**

  背景

  `SearchControl.ActionButtonMouseDown`

  前景 (字符)

  `SearchControl.ActionButtonMouseDownGlyph`

  Border

  `SearchControl.ActionButtonMouseDownBorder`

  ![搜尋下拉式&#45;向下按鈕按下](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303年-116-2_SearchDropdownButtonPressed")

  **下拉式按鈕**

  背景

  `SearchControl.MouseDownDropDownButton`

  前景 (字符)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Border

  `SearchControl.MouseDownDropDownButtonBorder`

  **反白顯示 （僅顯示文字）**

  元件

  項目

  權杖名稱：Category.color

  ![搜尋輸入的欄位反白](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303年 120_SearchInputFieldHighlight")

  **反白顯示的文字輸入的欄位**

  背景

  `SearchControl.Selection`

  前景 (文字)

  `SearchControl.FocusedBackground`

  Border

  None

  Separator

  `SearchControl.FocusedDropDownSeparator`

  **已停用**

  元件

  項目

  權杖名稱：Category.color

  ![已停用搜尋輸入的欄位](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303年 121_SearchInputFieldDisabled")

  **輸入的欄位**

  背景

  `SearchControl.Disabled`

  前景 (文字)

  `SearchControl.Disabled`

  Border

  `SearchControl.DisabledBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![已停用搜尋動作按鈕](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303年 122_SearchActionButtonDisabled")

  **動作按鈕**

  背景

  None

  前景 (字符)

  `SearchControl.ActionButtonDisabledGlyph`

  Border

  None

  ![搜尋下拉式&#45;向下按鈕已停用](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303年 123_SearchDropdownButtonDisabled")

  **下拉式按鈕**

  背景

  None

  前景 (字符)

  `SearchControl.DisabledDownButtonGlyph`

  Border

  None

#### <a name="search-drop-down-lists"></a>搜尋下拉式清單

搜尋方塊下拉式功能表可能會比 Visual Studio 中的其他下拉式功能表稍微更為複雜。 [建議的搜尋] 和 [搜尋選項] 區段可以單獨或一起出現在功能表上，而且各區段會個別著色。 這兩個區段同時出現時，也會有一條線來區隔它們，而且會有框線括住整個下拉式功能表。

![搜尋下拉式&#45;向下紅線](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303年 124_SearchDropdownRedline")

請使用於…
- 建立自訂搜尋下拉式清單時。

- 正確清單元件的正確語彙基元名稱。

  請勿使用於…
  - 針對出現在其他內容中的下拉式清單。

- 任何非指定的背景/前景組合。

  **預設值 （沒有其他狀態）**

  項目

  權杖名稱：Category.color

  Border

  `SearchControl.PopupBorder`

  Separator

  `SearchControl.PopupSectionHeaderSeparator`

  陰影

  `Environment.DropShadowBackground`

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![搜尋建議](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303年 125_SearchSuggested")

  **建議的搜尋**

  背景

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `SearchControl.PopupItemText`

  ![搜尋核取方塊](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303年 126_SearchCheckbox")

  **搜尋選項 （核取方塊）**

  ![搜尋選項](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303年 127_SearchOptions")

  **搜尋選項 （連結）**

  背景

  `SearchControl.PopupSectionBackgroundGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (核取方塊文字)

  `SearchControl.PopupCheckboxText`

  前景 (連結文字)

  `SearchControl.PopupButtonText`

  頁首背景

  `SearchControl.PopupSectionHeaderGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (頁首文字)

  `SearchControl.PopupSectionHeaderText`

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![搜尋建議停留](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303年 128_SearchSuggestedHover")

  **建議的搜尋**

  背景

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (文字)

  `SearchControl.PopupMouseOverItemText`

  Border

  `SearchControl.PopupControlMouseOverBorder`

  ![暫留時顯示搜尋核取方塊](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303年 129_SearchCheckboxHover")

  **建議的搜尋 （核取方塊）**

  ![搜尋選項停留](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303年 130_SearchOptionsHover")

  **搜尋選項**

  背景

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (核取方塊文字)

  `SearchControl.PopupCheckboxMouseDownText`

  前景 (連結文字)

  `SearchControl.PopupButtonMouseDownText`

  Border

  `SearchControl.PopupControlMouseOverBorder`

  **按下**

  元件

  項目

  權杖名稱：Category.color

  ![搜尋建議的按下](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303年 131_SearchSuggestedPressed")

  **建議的搜尋 （核取方塊）**

  ![搜尋已按下選項](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303年 132_SearchOptionsPressed")

  **搜尋選項**

  核取方塊背景

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (核取方塊文字)

  `SearchControl.PopupCheckboxMouseDownText`

  連結背景

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。

  前景 (連結文字)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>超連結
 超連結是一個沒有前景/背景配對的控制項。 在所有情況下，都會使用前景超連結色彩，以正確地顯示在深色、灰色和白色背景上。 如果您未使用超連結控制項的色彩語彙基元，則會看到「已按下」的預設系統色彩 (即閃爍紅色)。 這是控制項未使用正確環境色彩語彙基元的訊號。

 ![超連結紅線](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303年 133_HyperlinkRedline")

 請使用於…
需要建立自訂超連結時。

 請勿使用於…
針對不是超連結的任何項目。

 **Default**

 元件

 項目

 權杖名稱：Category.color

 ![超連結預設值](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303年 134_Hyperlink")

 前景 (文字)

 `Environment.PanelHyperlink`

 **Hover**

 元件

 項目

 權杖名稱：Category.color

 ![暫留時的超連結](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303年 135_HyperlinkHover")

 前景 (文字)

 `Environment.PanelHyperlinkHover`

 **按下**

 元件

 項目

 權杖名稱：Category.color

 ![按下的超連結](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303年 136_HyperlinkPressed")

 前景 (文字)

 `Environment.PanelHyperlinkPressed`

 **已停用**

 元件

 項目

 權杖名稱：Category.color

 ![停用的超連結](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303年 137_HyperlinkDisabled")

 前景 (文字)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>資訊列
 資訊列用來提供所指定內容的詳細資訊，而且一律會出現在文件視窗或工具視窗的頂端。

 ![資訊列紅線](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303年 138_InfobarRedline")

 請使用於…
建立自訂資訊列時。

 請勿使用於…
任何未與資訊列類似的 UI 項目。

 元件

 項目

 權杖名稱：Category.color

 ![Infobar](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")

 **Infobar**

 背景

 `Environment.InfoBackground`

 前景 (文字)

 `Environment.InfoText`

 Border

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>捲軸
 捲軸的樣式是由 Visual Studio 環境所設定，因此不需要設定佈景主題。 不過，您可能會決定您想要利用捲軸中使用時，您的 UI 一律會顯示與 Visual Studio 環境的這個部分一致的色彩。

 ![捲軸紅線](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303年 140_ScrollbarRedline")

 請使用於…
建立要符合 Visual Studio 捲軸的 UI 時。

 請勿使用於...針對任何項目，您不想要一律與捲軸 UI 相符。

 **Default**

 元件

 項目

 權杖名稱：Category.color

 ![捲軸](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303年 141_Scrollbar")

 **Scrollbar**

 捲軸

 `Environment.ScrollBarBackground`

 前景 (捲動方塊)

 `Environment.ScrollBarThumbBackground`

 ![捲軸箭號](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303年 142_ScrollbarArrow")

 **捲動箭號**

 背景

 `Environment.ScrollBarArrowBackground`

 設定為與捲軸相同的色彩。

 前景 (字符)

 `Environment.ScrollBarArrowGlyph`

 **Hover**

 元件

 項目

 權杖名稱：Category.color

 ![暫留時顯示捲軸](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303年 143_ScrollbarHover")

 **Scrollbar**

 捲軸

 `Environment.ScrollBarBackground`

 前景 (捲動方塊)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![捲軸箭號暫留時](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303年 144_ScrollbarArrowHover")

 **捲動箭號**

 背景

 `Environment.ScrollBarArrowMouseOverBackground`

 設定為與捲軸相同的色彩。

 前景 (字符)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **按下**

 元件

 項目

 權杖名稱：Category.color

 ![按下捲軸](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303年 145_ScrollbarPressed")

 **Scrollbar**

 捲軸

 `Environment.ScrollBarBackground`

 前景 (捲動方塊)

 `Environment.ScrollBarThumbPressedBackground`

 ![捲軸箭號，按下](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303年 146_ScrollbarArrowPressed")

 **捲動箭號**

 背景

 `Environment.ScrollBarArrowPressedBackground`

 設定為與捲軸相同的色彩。

 前景 (字符)

 `Environment.ScrollBarArrowGlyphPressed`

### <a name="BKMK_TreeView"></a> 樹狀檢視

數個工具視窗 (包括方案總管、伺服器總管和類別檢視) 會實作階層式組織配置，其色彩受到 TreeView 類別中的色彩名稱所控制。 樹狀檢視中的所有項目都會有背景和文字色彩。 具有巢狀子項目的項目也具有字符可指出展開還是摺疊項目。

![樹狀檢閱紅線](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303年 147_TreeViewRedline")

請使用於…
任何您需要實作階層式組織檢視的位置。

請勿使用於…
- 任何未與樹狀檢視類似的項目。

- 任何非指定的背景/前景組合。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![樹狀檢視](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303年 148_TreeView")

  背景

  `TreeView.Background`

  前景 (文字)

  `TreeView.Background`

  前景 (字符)

  `TreeView.Glyph`

  Border

  None

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![樹狀檢視停留](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303年 149_TreeViewHover")

  背景

  `TreeView.Background`

  前景 (文字)

  `TreeView.Background`

  前景 (字符)

  `TreeView.GlyphMouseOver`

  Border

  None

  **拖曳至上方**

  元件

  項目

  權杖名稱：Category.color

  ![樹狀檢視拖曳經過時顯示](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303年 150_TreeViewDragOver")

  背景

  `TreeView.DragOverItem`

  前景 (文字)

  `TreeView.DragOverItem`

  前景 (字符)

  `TreeView.DragOverItemGlyph`

  Border

  None

  **選取**

  元件

  項目

  權杖名稱：Category.color

  ![樹狀檢閱已取得焦點](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303年 151_TreeViewFocused")

  **已取得焦點**

  背景

  `TreeView.SelectedItemActive`

  前景 (文字)

  `TreeView.SelectedItemActive`

  前景 (字符)

  `TreeView.SelectedItemActiveGlyph`

  Border

  `TreeView.FocusVisualBorder`

  ![樹狀檢視未取得焦點](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303年 152_TreeViewUnfocused")

  **未取得焦點**

  背景

  `TreeView.SelectedItemInactive`

  前景 (文字)

  `TreeView.SelectedItemInactive`

  前景 (字符)

  `TreeView.SelectedItemInactiveGlyph`

  Border

  None

  **將滑鼠停在選取**

  元件

  項目

  權杖名稱：Category.color

  ![樹狀檢閱已取得焦點停留](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303年 153_TreeViewFocusedHover")

  **已取得焦點**

  背景

  `TreeView.SelectedItemActive`

  前景 (文字)

  `TreeView.SelectedItemActive`

  前景 (字符)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Border

  無`TreeView.FocusVisualBorder`

  ![樹狀檢閱未取得焦點停留](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303年 154_TreeViewUnfocusedHover")

  **未取得焦點**

  背景

  `TreeView.SelectedItemInactive`

  前景 (文字)

  `TreeView.SelectedItemInactive`

  前景 (字符)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Border

  None

### <a name="button-controls"></a>按鈕控制項
 ![按鈕控制項紅線](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303年 155_ButtonControlRedline")

 請使用於…
文件區域中，您想要與 Visual Studio 佈景主題 (淺色調、暗色調、藍色或系統高對比佈景主題) 整合的按鈕。

 請勿使用於…
將針對自訂背景 (不屬於 Visual Studio 的佈景主題) 而顯示的按鈕。

 **Default**

 元件

 項目

 權杖名稱：Category.color

 ![Button](../../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")

 按鈕

 `CommonControls.Button`

 按鈕框線

 `CommonControls.ButtonBorder`

 **已停用**

 元件

 項目

 權杖名稱：Category.color

 ![按鈕已停用](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303年 157_ButtonDisabled")

 按鈕

 `CommonControls.ButtonDisabled`

 按鈕框線

 `CommonControls.ButtonBorderDisabled`

 **Hover**

 元件

 項目

 權杖名稱：Category.color

 ![動態顯示按鈕](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303年 158_ButtonHover")

 按鈕

 `CommonControls.ButtonHover`

 按鈕框線

 `CommonControls.ButtonBorderHover`

 **按下**

 元件

 項目

 權杖名稱：Category.color

 ![已按下按鈕](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303年 159_ButtonPressed")

 按鈕

 `CommonControls.ButtonPressed`

 按鈕框線

 `CommonControls.ButtonBorderPressed`

 **已取得焦點**

 元件

 項目

 權杖名稱：Category.color

 ![按鈕已取得焦點](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303年 160_ButtonFocused")

 按鈕

 `CommonControls.ButtonFocused`

 按鈕框線

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>核取方塊控制項
 ![核取方塊紅線](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303年 161_CheckboxRedline")

 請使用於…
文件區域內所包含的核取方塊控制項。

 請勿使用於…
任何不是核取方塊控制項的 UI。

 **Default**

 元件

 項目

 權杖名稱：Category.color

 ![Check box](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")

 背景

 `CommonControls.CheckBoxBackground`

 Border

 `CommonControls.CheckBoxBorder`

 文字

 `CommonControls.CheckBoxText`

 圖像

 `CommonControls.CheckBoxGlyph`

 **已停用**

 元件

 項目

 權杖名稱：Category.color

 ![已停用的核取方塊](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303年 163_CheckboxDisabled")

 背景

 `CommonControls.CheckBoxBackgroundDisabled`

 Border

 `CommonControls.CheckBoxBorderDisabled`

 文字

 `CommonControls.CheckBoxTextDisabled`

 圖像

 `CommonControls.CheckBoxGlyphDisabled`

 **Hover**

 元件

 項目

 權杖名稱：Category.color

 ![暫留時的核取方塊](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303年 164_CheckboxHover")

 背景

 `CommonControls.CheckBoxBackgroundHover`

 Border

 `CommonControls.CheckBoxBorderHover`

 文字

 `CommonControls.CheckBoxTextHover`

 圖像

 `CommonControls.CheckBoxGlyphHover`

 **按下**

 元件

 項目

 權杖名稱：Category.color

 ![按下的核取方塊](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303年 165_CheckboxPressed")

 背景

 `CommonControls.CheckBoxBackgroundPressed`

 Border

 `CommonControls.CheckBoxBorderPressed`

 文字

 `CommonControls.CheckBoxTextPressed`

 圖像

 `CommonControls.CheckBoxGlyphPressed`

 **已取得焦點**

 元件

 項目

 權杖名稱：Category.color

 ![核取方塊已取得焦點](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303年 166_CheckboxFocused")

 背景

 `CommonControls.CheckBoxBackgroundFocused`

 Border

 `CommonControls.CheckBoxBorderFocused`

 文字

 `CommonControls.CheckBoxTextFocused`

 圖像

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>下拉式方塊控制項

![卸除&#45;關閉&#47;下拉式方塊紅線](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303年 167_DropDownComboBoxRedline")

請使用於…
針對屬於文件區域一部分的下拉式清單和下拉式方塊。

請勿使用於…
- 任何不是下拉式清單或下拉式方塊的 UI。

- 針對命令列中的 [Drop-down](../../misc/shared-colors.md#BKMK_CommandDropDown) 或 [Combo box](../../misc/shared-colors.md#BKMK_CommandComboBox) 。

  **Default**

  元件

  項目

  權杖名稱：Category.color

  ![Drop&#45;down&#47;combo box](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")

  背景

  `CommonControls.ComboBoxBackground`

  Border

  `CommonControls.ComboBoxBorder`

  文字

  `CommonControls.ComboBoxText`

  Separator

  `CommonControls.ComboBoxSeparator`

  圖像

  `CommonControls.ComboBoxGlyph`

  字符背景

  `CommonControls.ComboBoxGlyphBackground`

  **已停用**

  元件

  項目

  權杖名稱：Category.color

  ![卸除&#45;關閉&#47;下拉式方塊已停用](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303年 169_DropDownComboBoxDisabled")

  背景

  `CommonControls.ComboBoxBackgroundDisabled`

  Border

  `CommonControls.ComboBoxBorderDisabled`

  文字

  `CommonControls.ComboBoxTextDisabled`

  Separator

  `CommonControls.ComboBoxSeparatorDisabled`

  圖像

  `CommonControls.ComboBoxGlyphDisabled`

  字符背景

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Hover**

  元件

  項目

  權杖名稱：Category.color

  ![卸除&#45;關閉&#47;動態顯示下拉式方塊](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303年 170_DropDownComboBoxHover")

  背景

  `CommonControls.ComboBoxBackgroundHover`

  Border

  `CommonControls.ComboBoxBorderHover`

  文字

  `CommonControls.ComboBoxTextHover`

  Separator

  `CommonControls.ComboBoxSeparatorHover`

  圖像

  `CommonControls.ComboBoxGlyphHover`

  字符背景

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **按下**

  元件

  項目

  權杖名稱：Category.color

  ![卸除&#45;關閉&#47;下拉式方塊，按下](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303年 171_DropDownComboBoxPressed")

  背景

  `CommonControls.ComboBoxBackgroundPressed`

  Border

  `CommonControls.ComboBoxBorderPressed`

  文字

  `CommonControls.ComboBoxTextPressed`

  Separator

  `CommonControls.ComboBoxSeparatorPressed`

  圖像

  `CommonControls.ComboBoxGlyphPressed`

  字符背景

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **已取得焦點**

  元件

  項目

  權杖名稱：Category.color

  ![卸除&#45;關閉&#47;下拉式方塊已取得焦點](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303年 172_DropDownComboBoxFocused")

  背景

  `CommonControls.ComboBoxBackgroundFocused`

  Border

  `CommonControls.ComboBoxBorderFocused`

  文字

  `CommonControls.ComboBoxTextFocused`

  Separator

  `CommonControls.ComboBoxSeparatorFocused`

  圖像

  `CommonControls.ComboBoxGlyphFocused`

  字符背景

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **文字輸入選取範圍**

  元件

  項目

  權杖名稱：Category.color

  ![卸除&#45;關閉&#47;下拉式方塊的文字輸入](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303年 173_DropDownComboBoxTextInput")

  反白顯示

  `CommonControls.ComboBoxTextInputSelection`

  **已按下 – 清單項目檢視**

  ![卸除&#45;關閉&#47;下拉式方塊清單檢視](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303年 174_DropDownComboBoxListView")

  背景

  `CommonControls.ComboBoxListBackground`

  `CommonControls.ComboBoxListBackgroundHover`

  `CommonControls.ComboBoxListItemBackgroundPressed`

  `CommonControls.ComboBoxListItemBackgroundFocused`

  Border

  `CommonControls.ComboBoxListBorder`

  `CommonControls.ComboBoxListBorderHover`

  `CommonControls.ComboBoxListBorderPressed`

  `CommonControls.ComboBoxListBorderFocused`

  項目文字

  `CommonControls.ComboBoxListItemText`

  `CommonControls.ComboBoxListItemTextHover`

  `CommonControls.ComboBoxListItemTextPressed`

  `CommonControls.ComboBoxListItemTextFocused`

  背景陰影

  `CommonControls.ComboBoxListBackgroundShadow`

### <a name="tabular-data-grid-controls"></a>表格式資料 (方格) 控制項
 表格式資料控制項 (也稱為方格控制項) 是 Visual Studio 通用控制項，可用來在多個資料行中顯示大量資料。 標準表格式資料控制項可以位於 Visual Studio 的多個位置：[錯誤清單] 工具視窗、IntelliTrace 報告和記憶體堆積檢視等等。 請一律使用所提供的標準表格式資料控制項。 在一些罕見情況下，您可能無法存取標準表格式資料控制項。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他表格式資料控制項一致。

 ![表格式資料&#40;方格控制項&#41;紅線](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303年 197_TabularDataGridControlRedline")

 請使用於…
針對表格式或方格控制項。

 請勿使用於…
任何不是表格式或方格控制項的 UI。

#### <a name="column-headers"></a>資料行標頭
 資料行標頭包含背景、框線、標題文字，以及通常在依該資料行排序方格時使用的選用字符。

 狀況

 項目

 權杖名稱：Category.color

 預設

 背景

 `Header.Default`

 前景 (文字)

 `Environment.CommandBarTextActive`

 前景 (字符)

 `Header.Glyph`

 Border

 `Header.SeparatorLine`

 暫留

 背景

 `Header.MouseOver`

 前景 (文字)

 `Environment.CommandBarTextHover`

 前景 (字符)

 `Header.MouseOverGlyph`

 Border

 `Header.SeparatorLine`

 按下

 背景

 `CommonControls.CheckBoxBackgroundPressed`

 前景 (文字)

 `CommonControls.CheckBoxBorderPressed`

 前景 (字符)

 `CommonControls.CheckBoxTextPressed`

 Border

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>清單檢視項目
 清單檢視項目包含背景和內容。 內容可以是文字及/或圖示。

 狀況

 項目

 權杖名稱：Category.color

 預設

 背景

 透明

 前景 (文字)

 `Environment.CommandBarTextActive`

 Border

 None

 已選取 (使用中)

 背景

 `TreeView.SelectedItemActive`

 前景 (文字)

 `TreeView.SelectedItemActiveText`

 Border

 None

 已選取 (非使用中)

 背景

 `TreeView.SelectedItemInactive`

 前景 (文字)

 `TreeView.SelectedItemInactiveText`

 Border

 None

## <a name="manifest-designer"></a>資訊清單設計工具

資訊清單設計工具的設計是用來輕鬆地編輯 Windows 8 和 Windows Phone 8 專案中的資訊清單檔。 雖然沒有任何共用架構可供取用，但是可能適合您比對方向/瀏覽索引標籤和整體結構的設計版面配置和色彩。 如需版面配置詳細資料的詳細資訊，請參閱 [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。

![資訊清單設計工具紅線](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303年 175_ManifestDesignerRedline")

請使用於…
- 針對與資訊清單設計工具類似的設計工具。

- 改為使用文件區域內的編輯器頂端的通用索引標籤控制項。

請勿使用於…
- 如果您有六個以上的索引標籤。

- 任何未結構化的 UI (例如資訊清單設計工具)。

  狀況

  元件

  項目

  權杖名稱：Category.color

  預設值 (已選取)

  索引標籤

  背景

  `ManifestDesigner.TabActive`

  Border

  None

  描述窗格

  背景

  `ManifestDesigner.DescriptionPane`

  內容頁面

  背景

  `ManifestDesigner.Background`

  對話方塊 Helper 文字

  `ManifestDesigner.WatermarkText`

  這個語彙基元名稱不符合其功能。

  未選取

  索引標籤

  背景

  `ManifestDesigner.Tab.Inactive`

  暫留

  索引標籤

  背景

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>標記
 Visual Studio 支援標記，可讓使用者宣告可搜尋關鍵字，以進行追蹤。 例如，專案經理和開發人員可以使用 Team Foundation Server (TFS) 來標記工作項目。 下列表格提供以暫停和已選取狀態顯示之標記本身和「關閉圖示」字符的色彩名稱。

 ![標記紅線](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303年 176_TaggingRedline")

 請使用於…
針對支援標記的 UI。

 請勿使用於…
任何其他類型的 UI。

### <a name="tag"></a>標記
 元件

 項目

 權杖名稱：Category.color

 ![Tag](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")

 **Default**

 背景

 `Tag.Background`

 前景 (文字)

 `Tag.Background`

 ![暫留時顯示標記](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303年 178_TagHover")

 **Hover**

 背景

 `Tag.HoverBackground`

 前景 (文字)

 `Tag.HoverBackgroundText`

 ![已按下標記](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303年 179_TagPressed")

 **按下**

 背景

 `Tag.PressedBackground`

 前景 (文字)

 `Tag.PressedBackgroundText`

 ![已選取標記](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303年 180_TagSelected")

 **選取**

 背景

 `Tag.SelectedBackground`

 前景 (文字)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>字符 (關閉圖示)
 **Default**

 元件

 項目

 權杖名稱：Category.color

 ![Tag &#40;glyph&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")

 **預設值 （標記預設值）**

 背景

 N/A

 前景 (字符)

 `Tag.TagHoverGlyph`

 **Hover**

 元件

 項目

 權杖名稱：Category.color

 ![標記&#40;圖像 （glyph)&#41;停留](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303年 182_TagGlyphHover")

 **暫留 （標記預設值）**

 背景

 `Tag.TagHoverGlyphHoverBackground`

 前景 (字符)

 `Tag.TagHoverGlyphHover`

 Border

 `Tag.TagHoverGlyphHoverBorder`

 **按下**

 元件

 項目

 權杖名稱：Category.color

 ![標記&#40;圖像 （glyph)&#41;按下](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303年 183_TagGlyphPressed")

 **按下 （標記預設值）**

 背景

 `Tag.TagHoverGlyphPressedBackground`

 前景 (字符)

 `Tag.TagHoverGlyphPressed`

 Border

 `Tag.TagHoverGlyphPressedBorder`

 **標記選取/字符預設值**

 元件

 項目

 權杖名稱：Category.color

 ![已選取標記](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303年 184_TagSelected")

 **預設值 （已選取標記）**

 背景

 N/A

 前景 (字符)

 `Tag.TagSelectedGlyph`

 **標記選取/字符暫留**

 元件

 項目

 權杖名稱：Category.color

 ![暫留時已選取標記](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303年 185_TagSelectedHover")

 **暫留 （已選取標記）**

 背景

 `Tag.TagSelectedGlyphHoverBackground`

 前景 (字符)

 `Tag.TagSelectedGlyphHover`

 Border

 `Tag.TagSelectedGlyphHoverBorder`

 **標記選取/字符按下**

 元件

 項目

 權杖名稱：Category.color

 ![已選取標記已按下](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303年 186_TagSelectedPressed")

 **已按下 （已選取標記）**

 背景

 `Tag.TagSelectedGlyphPressedBackground`

 前景 (字符)

 `Tag.TagSelectedGlyphPressed`

 Border

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Shell

### <a name="background"></a>背景

環境背景包含兩個層級。 下層是涵蓋整個 IDE 的單色。 上層可放入命令櫃下方以及 IDE 左右兩側邊緣的工具視窗自動隱藏通道之間。 從 Visual Studio 2013 開始，在淺色調和暗色調佈景主題中，背景上層和下層會設定為相同的色彩。

![殼層背景紅線](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303年 187_ShellBackgroundRedline")

請使用於…
針對您想要符合 Visual Studio 環境背景的位置。

請勿使用於…
- 作為非背景表面之位置的填色。

- 作為您要放置前景項目的背景。

  元件

  項目

  權杖名稱：Category.color

  下層

  背景

  `Environment.EnvironmentBackground`

  元件

  項目

  權杖名稱：Category.color

  上層

  背景

  *漸層停駐在 Visual Studio 2013 淺色調和暗色調佈景主題中的相同色彩值的集合。*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>命令櫃

兩組語彙基元名稱用於命令櫃背景：一組用於功能表列所在的位置，一組用於命令列所在的位置。 個別命令列群組有其專屬背景色彩值 (會在＜命令列＞一節中詳細討論)。 功能表列和命令列文字分別會在功能表和命令列一節中進行討論。

![命令櫃紅線](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303年 188_CommandShelfRedline")

請使用於…
- 針對您放置功能表或工具列的區域。

- 具有正確的背景 /？ 前景語彙基元名稱組合。

請勿使用於…
針對未與命令櫃類似的區域。

  元件

  項目

  權杖名稱：Category.color

  功能表列

  背景

  *漸層停駐在 Visual Studio 2013 淺色調和暗色調佈景主題中的相同色彩值的集合。*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  命令列

  背景

  *漸層停駐在 Visual Studio 2013 淺色調和暗色調佈景主題中的相同色彩值的集合。*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>工具箱
 工具箱是其中一個最常用於 Visual Studio 的通用工具視窗。 它基本上是已套用特殊佈景主題和樣式的樹狀控制項。

 ![工具箱紅線](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303年 189_ToolboxRedline")

 請使用於…
設計要一律與 Shell 工具箱一致的工具視窗時。

 請勿使用於…
針對未與工具箱 UI 類似的任何項目，或者，如果您不確定 UI 是否會在 Shell 工具箱色彩變更時發生問題。

 **Default**

 元件

 項目

 權杖名稱：Category.color

 ![工具箱父節點](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303年 190_ToolboxParentNode")

 **父節點**

 ![工具箱子節點](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303年 191_ToolboxChildNode")

 **子節點**

 背景

 `Environment.ToolboxContent`

 標題

 `Environment.ToolWindowBackground`

 個別項目或整個視窗 (沒有可用控制項時)

 Border

 None

 前景 (字符)

 `Environment.ToolboxContent`

 前景 (文字)

 `Environment.ToolboxContent`

 **Hover**

 元件

 項目

 權杖名稱：Category.color

 ![暫留時顯示工具箱子節點](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303年 192_ToolboxChildNodeHover")

 **子節點上的工具箱暫留**

 背景

 `Environment.ToolboxContentMouseOver`

 僅限個別項目

 Border

 None

 前景 (文字)

 `Environment.ToolboxContentMouseOver`

 僅限個別項目

 **選取**

 元件

 項目

 權杖名稱：Category.color

 ![工具箱父節點已取得焦點](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303年 193_ToolboxParentNodeFocused")

 **具有焦點的父節點**

 ![工具箱子節點已取得焦點](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303年 194_ToolboxChildNodeFocused")

 **具有焦點的子節點**

 背景

 `TreeView.SelectedItemActive`

 從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類

 Border

 `TreeView.FocusVisualBorder`

 從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類

 前景 (字符)

 `TreeView.SelectedItemActive`

 從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類

 前景 (文字)

 `TreeView.SelectedItemActive`

 從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類

 ![工具箱父節點未取得焦點](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303年 195_ToolboxParentNodeUnfocused")

 **未取得焦點的父節點**

 ![工具箱子節點未取得焦點](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303年 196_ToolboxChildNodeUnfocused")

 **未取得焦點的子節點**

 背景

 `TreeView.SelectedItemInactive`

 從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類

 Border

 None

 前景 (字符)

 `TreeView.SelectedItemInactive`

 從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類

 前景 (文字)

 `TreeView.SelectedItemInactive`

 從 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 分類

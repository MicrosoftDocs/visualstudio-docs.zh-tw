---
title: 共用色彩 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 421ff85831bb611b655de2bc35f01423b61921a2
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410090"
---
# <a name="shared-colors"></a>共用色彩
在這裡插入簡介。  
  
## <a name="shared-colors"></a>共用色彩  
 如果您設計的 UI 使用通用 Visual Studio Shell 項目，或您想要介面項目與類似的功能一致，請在封裝定義檔中使用現有的語彙基元名稱，以選擇並指派色彩。 這可確保您的 UI 與整體 Visual Studio 環境保持一致，而且會在加入或更新佈景主題時自動更新。  
  
 本文說明常見 UI 項目以及它們使用的語彙基元名稱，以在建置類似的 UI 時進行參考。 如需如何存取這些色彩語彙基元的特定資訊，請參閱 [The VSColor Service](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。  
  
 請務必正確地使用語彙基元名稱：  
  
- **使用以函式為基礎的標記名稱，而不是色彩本身。** 常見共用色彩是與特定介面項目相關聯，並且僅適用於相同或類似的功能。 例如，請不要只因為您喜歡微調進度動畫之已按下下拉式方塊的色彩，就重複使用該色彩。 下拉式方塊和動畫的功能不同，而且，如果與下拉式方塊相關聯的色彩變更，則可能不再是動畫項目的適當色彩。 一致地使用色彩可協助引導您的使用者並避免混淆。  
  
- **使用正確組合的背景和文字色彩。** 要與文字搭配使用的背景色彩將有相關聯的文字色彩。 務必使用背景所指定的文字色彩。 如果沒有相關聯的文字色彩，請不要將該背景色彩用於您希望顯示文字的任何介面。 用其他方式組合文字和背景色彩可能會導致介面無法讀取。  
  
- **使用適用于其位置的控制項色彩。** 在特定狀態中，部分 Visual Studio 控制項沒有個別框線和背景色彩。 而是會選取其後介面的色彩。 務必根據控制項所放置的位置，而為其使用適合的語彙基元名稱。  
  
> [!IMPORTANT]
> 請勿使用「起始頁」或 "Cider" 類別中找到的語彙基元！  
  
### <a name="command-structures"></a>命令結構  
  
#### <a name="BKMK_CommandMenus"></a>彈出式  
 功能表可能會發生在 Visual Studio 2013 的數個位置：主要功能表列、內嵌在文件或工具視窗中，或 IDE 各位置的滑鼠右鍵功能表上。 針對個別項目的一節中會討論與其他 UI 項目相關聯之功能表的實作。 您應該一律使用 Visual Studio 環境所提供的標準功能表實作。 不過，在一些罕見情況下，您可能無法存取標準 Visual Studio 功能表。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他功能表一致。  
  
 ![功能表紅線](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
請使用於…  
- 任何需要建立自訂功能表的時機。  
  
- 當您有想要與 Visual Studio 功能表相符的新 UI 元件時。  
  
請勿使用於…  
單一背景色彩。 一律使用指定的背景/前景組合。  
  
##### <a name="menu-title"></a>功能表標題  
 功能表標題包含背景、框線和標題文字，以及選用字符 (通常是在命令列中找到功能表時)。  
  
 ![功能表標題紅線](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
請使用於…  
任何需要建立自訂功能表標題的時機。  
  
請勿使用於…  
- 任何不想要其一律與功能表標題相符的項目。  
  
- 任何非指定的背景/前景組合。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![功能表標題預設值](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **功能表標題**|背景|無|  
|![功能表標題預設值](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **功能表標題**|前景 (文字)|`Environment.CommandBarTextActive`|  
|![具有字型預設值的功能表標題](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **具有字型的功能表標題**|前景 (字符)|`Environment.CommandBarMenuGlyph`|  
|![具有字型預設值的功能表標題](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **具有字型的功能表標題**|Border|無|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時顯示功能表標題](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **功能表標題**|背景|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留時顯示功能表標題](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **功能表標題**|前景 (文字)|`Environment.CommandBarTextHover`|  
|![停留時顯示圖像的功能表標題](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **具有字型的功能表標題**|前景 (字符)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![停留時顯示圖像的功能表標題](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **具有字型的功能表標題**|Border|`Environment.CommandBarBorder`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下功能表標題](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **功能表標題**|背景|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![已按下功能表標題](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **功能表標題**|前景 (文字)|`Environment.CommandBarTextActive`|  
|![已按下圖示的功能表標題](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **具有字型的功能表標題**|前景 (字符)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![已按下圖示的功能表標題](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **具有字型的功能表標題**|Border|`Environment.CommandBarMenuBorder`<br /><br /> 只有左側、上方和右側。|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已停用字元的功能表標題](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **具有字型的功能表標題**|背景|無|  
|![已停用字元的功能表標題](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **具有字型的功能表標題**|前景 (文字)|`Environment.CommandBarTextInactive`|  
|![已停用字元的功能表標題](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **具有字型的功能表標題**|前景 (字符)|`Environment.CommandBarTextInactive`|  
|![已停用字元的功能表標題](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **具有字型的功能表標題**|Border|無|  
  
##### <a name="menu"></a>功能表  
 個別功能表項目包含功能表文字和選用圖示、核取方塊或子功能表字符。 其背景和文字色彩會在滑鼠游標暫留時變更。 這個色彩語彙基元是背景/前景配對。  
  
 ![功能表項目紅線](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 請使用於…  
 任何從功能表列或命令列啟動的下拉式清單。  
  
請勿使用於…  
- 任何其他內容中發生的下拉式清單。  

- 任何非指定的背景/前景組合。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![功能表預設值](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|背景|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![功能表預設值](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|前景 (文字)|`Environment.CommandBarTextActive`|  
|![功能表預設值](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|前景 (子功能表字符)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![功能表預設值](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Border|`Environment.CommandBarMenuBorder`|  
|![功能表預設值](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|圖示通道背景|`Environment.CommandBarMenuIconBackground`|  
|![功能表預設值](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|分隔符號|`Environment.CommandBarMenuSeparator`|  
|![功能表預設值](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|陰影|`Environment.DropShadowBackground`|  
|![已核取功能表](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **已核取**|核取記號|`Environment.CommandBarCheckBox`|  
|![已核取功能表](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **已核取**|核取記號背景|`Environment.CommandBarSelectedIcon`|  
|![已選取功能表](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **已選取**|圖示背景|`Environment.CommandBarSelected`|  
|![已選取功能表](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **已選取**|圖示框線|`Environment.CommandBarSelectedBorder`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![功能表停留](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **功能表項目**|背景|`Environment.CommandBarMenuItemMouseOver`|  
|![功能表停留](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **功能表項目**|前景 (文字)|`Environment.CommandBarMenuItemMouseOver`|  
|![功能表停留](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **功能表項目**|前景 (子功能表字符)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![已核取功能表游標](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **已核取**|核取記號|`Environment.CommandBarCheckBoxMouseOver`|  
|![已核取功能表游標](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **已核取**|核取記號背景|`Environment.CommandBarHoverOverSelectedIcon`|  
|![已選取功能表游標](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **已選取**|圖示背景|`Environment.CommandBarHoverOverSelected`|  
|![已選取功能表游標](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **已選取**|圖示框線|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已停用功能表](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> 功能表項目|前景 (文字)|`Environment.CommandBarTextInactive`|  
|![已停用功能表](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> 功能表項目|前景 (子功能表字符)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![已核取功能表](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> 已檢查|核取記號|`Environment.CommandBarCheckBoxDisabled`|  
|![已核取功能表](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> 已檢查|核取記號背景|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>命令列  
 命令列可以出現在 Visual Studio IDE 的多個位置中，最值得注意的是命令櫃並內嵌在工具或文件視窗中。  
  
 一般情況下，請一律使用 Visual Studio 環境所提供的標準命令列實作。 使用標準機制可確保正確地顯示所有視覺化詳細資料，而且互動式項目的行為會與其他 Visual Studio 命令列控制項一致。 不過，如果您需要建置專屬的命令列，請確定您使用下列語彙基元名稱正確地設定樣式。  
  
 ![命令列紅線](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![溢位按鈕紅線](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 請使用於…  
 任何需要內嵌命令列，但無法使用標準 Visual Studio 命令列實作的位置。  
  
請勿使用於…  
- 任何未與命令列類似的 UI 項目。  

- 不屬於語彙基元名稱所指定的命令列元件。  
  
##### <a name="command-bar-group"></a>命令列群組  
 命令列群組包含一組相關的命令列控制項，而且可能包含任意數目的按鈕，分割按鈕、下拉式功能表、下拉式方塊或功能表。 這些控制項的色彩受到個別的語彙基元名稱所規範，並且會在本指南的其他位置個別討論。 分隔線用來將命令列群組分成相關的子群組。  
  
 ![命令列群組紅線](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 請使用於…  
 任何需要內嵌命令列，但無法使用標準 Visual Studio 命令列實作的位置。  
  
請勿使用於…  
- 任何未與命令列類似的 UI 項目。  

- 不屬於語彙基元名稱所指定的命令列元件。  
  
  **預設值** (沒有其他狀態)  
  
|元素|語彙基元名稱：Category.color|  
|-------------|--------------------------------|  
|背景|`Environment.CommandBarGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|Border|`Environment.CommandBarToolBarBorder`|  
|拖曳控點|`Environment.CommandBarDragHandle`|  
|分隔符號|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>命令圖示  
 ![命令圖示紅線](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![命令圖示紅線](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 請使用於…  
 任何將放在命令列上的按鈕。  
  
請勿使用於…  
- 已具有專屬語彙基元名稱的控制項。  

- 任何非指定的背景/前景組合。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![命令圖示預設值](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **預設值**|背景|N/A (繼承自命令列背景)|  
|![命令圖示預設值](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **預設值**|前景 (文字)|`Environment.CommandBarTextActive`|  
|![命令圖示預設值](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **預設值**|Border|N/A|  
|![已選取命令圖示預設值](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **已選取**|背景|`Environment.CommandBarSelected`|  
|![已選取命令圖示預設值](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **已選取**|前景 (文字)|`Environment.CommandBarTextSelected`|  
|![已選取命令圖示預設值](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **已選取**|Border|`Environment.CommandBarSelectedBorder`|  
  
 **滑鼠停留和鍵盤焦點**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![命令圖示停留](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **停留時標準**|背景|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![命令圖示停留](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **停留時標準**|前景 (文字)|`Environment.CommandBarTextHover`|  
|![命令圖示停留](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **停留時標準**|Border|`Environment.CommandBarBorder`|  
|![已選取命令圖示游標](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **停留時選取**|背景|`Environment.CommandBarHoverOverSelected`|  
|![已選取命令圖示游標](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **停留時選取**|前景 (文字)|`Environment.CommandBarTextHoverOverSelected`|  
|![已選取命令圖示游標](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **停留時選取**|Border|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下命令圖示](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **已按下的命令圖示**|背景|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![已按下命令圖示](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **已按下的命令圖示**|前景 (文字)|`Environment.CommandBarTextMouseDown`|  
|![已按下命令圖示](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **已按下的命令圖示**|Border|`Environment.CommandBarBorder`|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已停用命令圖示](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **停用的命令圖示**|背景|N/A (繼承自命令列背景)|  
|![已停用命令圖示](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **停用的命令圖示**|前景 (文字)|`Environment.CommandBarTextInactive`|  
|![已停用命令圖示](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **停用的命令圖示**|Border|N/A|  
  
##### <a name="BKMK_CommandComboBox"></a>下拉式方塊  
  
> [!IMPORTANT]
> 下拉式方塊與下拉式清單類似，但包括可編輯的文字區域。 如果下拉式清單未包括可編輯的文字區域，請使用 [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown)下找到的色彩語彙基元。  
  
 ![下拉式方塊紅線](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
請使用於…  
- 建置自訂下拉式方塊時。  

- 建立與下拉式方塊類似的命令列控制項時。  

請勿使用於…  
- 任何不想要其一律與符合命令列 UI 相符的項目。  

- 您能存取已設定樣式的下拉式方塊時。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **輸入欄位**|背景|`Environment.ComboBoxBackground`|  
|![下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **輸入欄位**|前景 (文字)|`Environment.ComboBoxText`|  
|![下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **輸入欄位**|Border|`Environment.ComboBoxBorder`|  
|![下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **輸入欄位**|分隔符號|沒有分隔符號|  
|![下拉式方塊下拉&#45;按鈕](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **下拉按鈕**|背景|N/A (繼承)|  
|![下拉式方塊下拉&#45;按鈕](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **下拉按鈕**|前景 (字符)|`Environment.ComboBoxGlyph`|  
|![&#47;下拉式方塊下拉&#45;清單](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **下拉式清單**|背景|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![&#47;下拉式方塊下拉&#45;清單](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **下拉式清單**|前景 (文字)|`Environment.ComboBoxItemText`|  
|![&#47;下拉式方塊下拉&#45;清單](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **下拉式清單**|Border|`Environment.ComboBoxPopupBorder`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時顯示下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **輸入欄位**|背景|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留時顯示下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **輸入欄位**|前景 (文字)|`Environment.ComboBoxMouseOverText`|  
|![停留時顯示下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **輸入欄位**|Border|`Environment.ComboBoxMouseOverBorder`|  
|![停留時顯示下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **輸入欄位**|分隔符號|`Environment.ComboBoxMouseOverSeparator`|  
|![停留時&#47;顯示&#45;下拉式方塊下拉按鈕](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **下拉按鈕**|背景|`Environment.ComboBoxButtonMouseOverBackground`|  
|![停留時&#47;顯示&#45;下拉式方塊下拉按鈕](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **下拉按鈕**|前景 (字符)|`Environment.ComboBoxMouseOverGlyph`|  
|![停留時&#47;顯示&#45;下拉式方塊下拉清單](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **下拉式清單**|背景 (功能表項目)|`Environment.ComboBoxItemMouseOverBackground`|  
|![停留時&#47;顯示&#45;下拉式方塊下拉清單](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **下拉式清單**|前景 (文字)|`Environment.ComboBoxItemMouseOverText`|  
|![停留時&#47;顯示&#45;下拉式方塊下拉清單](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **下拉式清單**|框線 (功能表項目)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **作用**  
  
|元件|元素|語彙基元名稱：Color.category|  
|---------------|-------------|--------------------------------|  
|![下拉式方塊輸入欄位已獲得焦點](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **輸入欄位**|背景|`Environment.ComboBoxFocusedBackground`|  
|![下拉式方塊輸入欄位已獲得焦點](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **輸入欄位**|前景 (文字)|`Environment.ComboBoxFocusedText`|  
|![下拉式方塊輸入欄位已獲得焦點](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **輸入欄位**|Border|`Environment.ComboBoxFocusedBorder`|  
|![下拉式方塊輸入欄位已獲得焦點](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **輸入欄位**|分隔符號|`Environment.ComboBoxFocusedButtonSeparator`|  
|![&#47;下拉式方塊下拉&#45;按鈕的焦點](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **下拉按鈕**|背景|`Environment.ComboBoxFocusedButtonBackground`|  
|![&#47;下拉式方塊下拉&#45;按鈕的焦點](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **下拉按鈕**|前景 (字符)|`Environment.ComboBoxFocusedGlyph`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Color.category|  
|---------------|-------------|--------------------------------|  
|![已按下下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **輸入欄位**|背景|`Environment.ComboBoxMouseDownBackground`|  
|![已按下下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **輸入欄位**|前景 (文字)|`Environment.ComboBoxMouseDownText`|  
|![已按下下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **輸入欄位**|Border|`Environment.ComboBoxMouseDownBorder`|  
|![已按下下拉式方塊輸入欄位](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **輸入欄位**|分隔符號|`Environment.ComboBoxMouseDownSeparator`|  
|![已按&#47;下&#45;下拉式方塊下拉按鈕](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **下拉按鈕**|背景|`Environment.ComboBoxButtonMouseDownBackground`|  
|![已按&#47;下&#45;下拉式方塊下拉按鈕](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **下拉按鈕**|前景 (字符)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Color.category|  
|---------------|-------------|--------------------------------|  
|![下拉式方塊輸入欄位已停用](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **輸入欄位**|背景|`Environment.ComboBoxDisabledBackground`|  
|![下拉式方塊輸入欄位已停用](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **輸入欄位**|前景 (文字)|`Environment.ComboBoxDisabledText`|  
|![下拉式方塊輸入欄位已停用](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **輸入欄位**|Border|`Environment.ComboBoxDisabledBorder`|  
|![下拉式方塊輸入欄位已停用](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **輸入欄位**|分隔符號|沒有分隔符號|  
|![&#47;下拉式方塊下拉&#45;按鈕已停用](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **下拉按鈕**|背景|無|  
|![&#47;下拉式方塊下拉&#45;按鈕已停用](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **下拉按鈕**|前景 (字符)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="BKMK_CommandDropDown"></a>下拉式  
  
> [!IMPORTANT]
> 下拉式清單與下拉式方塊類似，但沒有可編輯的文字區域。 如果下拉式清單包括可編輯的文字區域，請使用 [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox)下找到的色彩語彙基元。  
  
 ![下拉&#45;紅線](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 請使用於…  
 建立自訂下拉式清單控制項時。  
  
請勿使用於…  
- 任何未與下拉式清單類似的項目。  

- 下拉式方塊或分割按鈕。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![下拉&#45;選取範圍欄位](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **選取範圍欄位**|背景|`Environment.DropDownBackground`|  
|![下拉&#45;選取範圍欄位](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **選取範圍欄位**|前景 (文字)|`DropDownText`|  
|![下拉&#45;選取範圍欄位](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **選取範圍欄位**|Border|`DropDownBorder`|  
|![下拉&#45;選取範圍欄位](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **選取範圍欄位**|分隔符號|沒有分隔符號|  
|![下拉&#45;按鈕](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **下拉按鈕**|背景|無|  
|![下拉&#45;按鈕](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **下拉按鈕**|前景 (字符)|`Environment.DropDownGlyph`|  
|![下拉式&#45;清單](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **下拉式清單**|背景|`Environment.DropDownPopupBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![下拉式&#45;清單](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **下拉式清單**|前景 (文字)|`Environment.ComboBoxItemText`|  
|![下拉式&#45;清單](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **下拉式清單**|Border|`Environment.DropDownPopupBorder`|  
|![下拉式&#45;清單](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **下拉式清單**|陰影|`Environment.DropShadowBackground`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留&#45;時下拉選取欄位](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **選取範圍欄位**|背景|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留&#45;時下拉選取欄位](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **選取範圍欄位**|前景 (文字)|`Environment.DropDownMouseOverText`|  
|![停留&#45;時下拉選取欄位](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **選取範圍欄位**|Border|`Environment.DropDownMouseOverBorder`|  
|![停留&#45;時下拉選取欄位](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **選取範圍欄位**|分隔符號|`Environment.DropDownButtonMouseOverSeparator`|  
|![停留&#45;時顯示下拉式按鈕](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **下拉按鈕**|背景|`Environment.DropDownButtonMouseOverBackground`|  
|![停留&#45;時顯示下拉式按鈕](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **下拉按鈕**|前景 (字符)|`Environment.DropDownMouseOverGlyph`|  
|![停留&#45;時顯示下拉式清單](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **下拉式清單**|背景 (功能表項目)|`Environment.ComboBoxItemMouseOverBackground`|  
|![停留&#45;時顯示下拉式清單](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **下拉式清單**|前景 (文字)|`Environment.ComboBoxItemMouseOverText`|  
|![停留&#45;時顯示下拉式清單](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **下拉式清單**|框線 (功能表項目)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已&#45;按下下拉選取範圍欄位](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **選取範圍欄位**|背景|`Environment.DropDownMouseDownBackground`|  
|![已&#45;按下下拉選取範圍欄位](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **選取範圍欄位**|前景 (文字)|`Environment.DropDownMouseDownText`|  
|![已&#45;按下下拉選取範圍欄位](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **選取範圍欄位**|Border|`Environment.DropDownMouseDownBorder`|  
|![已&#45;按下下拉選取範圍欄位](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **選取範圍欄位**|分隔符號|`Environment.DropDownButtonMouseDownSeparator`|  
|![已&#45;按下下拉式按鈕](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **下拉按鈕**|背景|`Environment.DropDownButtonMouseDownBackground`|  
|![已&#45;按下下拉式按鈕](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **下拉按鈕**|前景 (字符)|`Environment.DropDownMouseDownGlyph`|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![下拉&#45;選取範圍欄位已停用](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|背景|`Environment.DropDownDisabledBackground`|  
|![下拉&#45;選取範圍欄位已停用](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|前景 (文字)|`Environment.DropDownDisabledText`|  
|![下拉&#45;選取範圍欄位已停用](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Border|`Environment.DropDownDisabledBorder`|  
|![下拉&#45;選取範圍欄位已停用](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|分隔符號|沒有分隔符號|  
|![下拉&#45;按鈕已停用](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|背景|N/A|  
|![下拉&#45;按鈕已停用](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|前景 (字符)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Split 按鈕  
 分割按鈕會與其他命令列控制項 (例如按鈕、 功能表和命令列文字) 共用許多語彙基元名稱。 基於使用方便，會在這裡重複所有必要的動作和下拉式按鈕語彙基元名稱。 分割按鈕下拉式清單是命令列 [Menus](../misc/shared-colors.md#BKMK_CommandMenus)的實作。  
  
 ![分割按鈕紅線](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 請使用於…  
 建置自訂分割按鈕時。  
  
請勿使用於…  
- 其他種類的按鈕。  

- 任何非指定的背景/前景組合。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![分割按鈕](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **分割按鈕（預設值）**|背景|無|  
|![分割按鈕](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **分割按鈕（預設值）**|前景 (文字)|`Environment.CommandBarTextActive`|  
|![分割按鈕](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **分割按鈕（預設值）**|前景 (字符)|`Environment.CommandBarSplitButtonGlyph`|  
|![分割按鈕](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **分割按鈕（預設值）**|Border|N/A|  
|![分割按鈕](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **分割按鈕（預設值）**|分隔符號|N/A|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時顯示分割按鈕](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **分割按鈕（停留時）**|背景|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留時顯示分割按鈕](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **分割按鈕（停留時）**|前景 (文字)|`Environment.CommandBarTextHover`|  
|![停留時顯示分割按鈕](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **分割按鈕（停留時）**|前景 (字符)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![停留時顯示分割按鈕](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **分割按鈕（停留時）**|Border|`Environment.CommandBarBorder`|  
|![停留時顯示分割按鈕](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **分割按鈕（停留時）**|分隔符號|`Environment.CommandBarSplitButtonSeparator`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下分割按鈕](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **分割按鈕（已按下）**|背景|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![已按下分割按鈕](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **分割按鈕（已按下）**|前景 (文字)|`Environment.CommandBarTextMouseDown`|  
|![已按下分割按鈕](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **分割按鈕（已按下）**|前景 (字符)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![已按下分割按鈕](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **分割按鈕（已按下）**|Border|`Environment.CommandBarBorder`|  
|![已按下分割按鈕](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **分割按鈕（已按下）**|分隔符號|N/A|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![分割按鈕已停用](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **分割按鈕（已停用）**|背景|N/A|  
|![分割按鈕已停用](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **分割按鈕（已停用）**|前景 (文字)|`Environment.ComboBoxItemTextInactive`|  
|![分割按鈕已停用](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **分割按鈕（已停用）**|前景 (字符)|`Environment.CommandBarTextInactive`|  
|![分割按鈕已停用](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **分割按鈕（已停用）**|Border|N/A|  
|![分割按鈕已停用](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **分割按鈕（已停用）**|分隔符號|N/A|  
  
##### <a name="more-options-and-overflow-buttons"></a>[其他選項] 和 [溢位] 按鈕  
 可透過加入或移除相關命令列按鈕來自訂命令列群組時，會使用 [其他選項] 按鈕。 如果因水平空間不足而截斷命令列，以及按一下時顯示包含無法顯示之命令列按鈕的功能表，則會出現 [溢位] 按鈕。 這兩個按鈕的色彩是透過同一組語彙基元名稱所控制。  
  
 ![其他選項紅線](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 請使用於…  
 針對自訂 [其他選項] 或 [溢位] 按鈕。  
  
 請勿使用於…  
 針對沒有與 [其他選項] 或 [溢位] 按鈕類似之功能的按鈕。  
  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![更多選項](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **更多選項**|背景|`Environment.CommandBarOptionsBackground`|  
|![更多選項](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **更多選項**|前景 (字符)|`Environment.CommandBarOptionsGlyph`|  
|![溢位按鈕](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **溢出**|背景|`Environment.CommandBarOptionsBackground`|  
|![溢位按鈕](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **溢出**|前景 (字符)|`Environment.CommandBarOptionsGlyph`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時顯示更多選項](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **更多選項**|背景|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留時顯示更多選項](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **更多選項**|前景 (字符)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![停留時溢位](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **溢出**|背景|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留時溢位](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **溢出**|前景 (字符)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下更多選項](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **更多選項**|背景|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![已按下更多選項](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **更多選項**|前景 (字符)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![已按下溢位](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **溢出**|背景|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![已按下溢位](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **溢出**|前景 (字符)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>文件視窗  
 文件視窗是由 Visual Studio 環境所提供，因此不需要進行複寫。 不過，您可能會決定要利用文件視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。  
  
 使用文件視窗色彩語彙基元時，必須小心只針對類似的項目使用這些資料，而且一定成對。 如果您沒有這麼做，則 UI 中會有未預期的結果。  
  
#### <a name="document-window-frame"></a>文件視窗框架  
 文件視窗可以停駐在 IDE 中或浮動為不同的視窗。 文件視窗在 IDE 外部浮動時，還是停留在文件區域中，並且具有為 IDE 一部分時的相同背景、框線、文字和索引標籤色彩。 不過，文件位在具有其專屬背景、框線和文字色彩的框架內。 工具視窗停駐在文件區域時，會從文件視窗語彙基元名稱繼承其索引標籤的行為和色彩。  
  
 ![停駐的文件視窗紅線](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **停駐的文件視窗**  
  
 ![浮動文件視窗紅線](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **浮動文件視窗**  
  
 請使用於…  
 任何要建立符合文件視窗之 UI 的位置。  
  
 請勿使用於…  
 針對您不想在 Shell 具有佈景主題更新時自動變更的任何 UI。  
  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|文件：停駐或浮動|背景|根據文件類型|  
|文件：停駐或浮動|前景 (文字)|根據文件類型|  
|文件：停駐或浮動|Border|`Environment.ToolWindowBorder`|  
|![框架焦點](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **框架：浮動、聚焦**|背景|`Environment.ToolWindowFloatingFrame`|  
|![框架焦點](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **框架：浮動、聚焦**|前景 (文字)|`Environment.ToolWindowFloatingFrame`|  
|![框架焦點](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **框架：浮動、聚焦**|前景 (字符)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![框架焦點](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **框架：浮動、聚焦**|Border|`Environment.MainWindowActiveDefaultBorder`|  
|![框架焦點](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **框架：浮動、聚焦**|框線 (字符)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> 設定為透明|  
|![框架未取得焦點](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame：浮動、未取得焦點**|背景|`Environment.ToolWindowFloatingFrameInactive`|  
|![框架未取得焦點](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame：浮動、未取得焦點**|前景 (文字)|`Environment.ToolWindowFloatingFrameInactive`|  
|![框架未取得焦點](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame：浮動、未取得焦點**|前景 (字符)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![框架未取得焦點](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame：浮動、未取得焦點**|Border|`Environment.MainWindowInactiveBorder`|  
|![框架未取得焦點](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Frame：浮動、未取得焦點**|框線 (字符)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> 設定為透明|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![滑鼠停留時的框架焦點](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **框架：浮動、聚焦**|背景 (字符)|`Environment.RaftedWindowButtonHoverActive`|  
|![滑鼠停留時的框架焦點](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **框架：浮動、聚焦**|前景 (字符)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![滑鼠停留時的框架焦點](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **框架：浮動、聚焦**|框線 (字符)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![停留時顯示框架未取得焦點](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Frame：浮動、未取得焦點**|背景 (字符)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![停留時顯示框架未取得焦點](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Frame：浮動、未取得焦點**|前景 (字符)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![停留時顯示框架未取得焦點](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Frame：浮動、未取得焦點**|框線 (字符)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下的框架焦點](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **框架：浮動、聚焦**|背景 (字符)|`Environment.RaftedWindowButtonDown`|  
|![已按下的框架焦點](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **框架：浮動、聚焦**|前景 (字符)|`Environment.RaftedWindowButtonDownGlyph`|  
|![已按下的框架焦點](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **框架：浮動、聚焦**|框線 (字符)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>文件索引標籤  
 文件索引標籤位在索引標籤通道中，表示目前開啟的文件以及目前選取的文件或使用中文件。 工具視窗也可以停駐在文件索引標籤通道中 (如果使用者將它們放在那裏)。 在此情況下，他們會使用與文件視窗相同的索引標籤色彩。 如果所建立的 UI 要一律符合文件視窗色彩 (包括佈景主題更新，或已安裝新的佈景主題時)，則請參考這些色彩語彙基元。  
  
 ![檔索引標籤紅線](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 請使用於…  
 任何要建立與文件索引標籤相符並自動選取佈景主題更新或新佈景主題色彩之 UI 的位置。  
  
 請勿使用於…  
 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。  
  
##### <a name="open-document-tabs"></a>開啟文件索引標籤  
 每個開啟的文件都會有顯示其名稱之文件索引標籤通道中的索引標籤。 可以在背景中選取或開啟文件，而且它們的索引標籤會反映這些狀態：  
  
- 選取的索引標籤代表目前顯示在文件區域中的文件。 選取的索引標籤會有可延伸至文件區域頂端的文件框線。  
  
- 背景索引標籤是指任何不是目前所選取索引標籤的檔索引標籤。一旦按一下，它們就會變成選取的索引標籤，並從這些標記名稱取得所有的背景、框線和文字色彩。  
  
  ![[開啟檔] 索引標籤紅線](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  請使用於…  
  建立自訂文件索引標籤時。  
  
  請勿使用於…  
  - 暫時 (預覽) 索引標籤。  
  
- 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。  
  
##### <a name="selected-tab"></a>選取的索引標籤  
 **作用**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![選取的索引標籤焦點](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **選取的檔索引標籤，焦點**|背景|`Environment.FileTabSelectedGradientTop`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![選取的索引標籤焦點](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **選取的檔索引標籤，焦點**|前景 (文字)|`Environment.FileTabSelectedText`|  
|![選取的索引標籤焦點](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **選取的檔索引標籤，焦點**|Border|`Environment.FileTabSelectedBorder`<br /><br /> 設定為與背景相同的色彩。|  
|![選取的索引標籤焦點](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **選取的檔索引標籤，焦點**|文件框線|`Environment.FileTabDocumentBorderBackground`|  
  
 **未取得焦點**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![選取的索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **選取的檔索引標籤，未取得焦點**|背景|`Environment.FileTabInactiveGradientTop`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![選取的索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **選取的檔索引標籤，未取得焦點**|前景 (文字)|`Environment.FileTabInactiveText`|  
|![選取的索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **選取的檔索引標籤，未取得焦點**|Border|`Environment.FileTabInactiveBorder`<br /><br /> 設定為與背景相同的色彩。|  
|![選取的索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **選取的檔索引標籤，未取得焦點**|文件框線|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>背景索引標籤  
 **預設值**  
  
|元件|元素|語彙基元名稱：Color.category|  
|---------------|-------------|--------------------------------|  
|![背景索引標籤](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **背景索引標籤預設值**|背景|`Environment.FileTabBackground`|  
|![背景索引標籤](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **背景索引標籤預設值**|前景 (文字)|`Environment.FileTabText`|  
|![背景索引標籤](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **背景索引標籤預設值**|Border|`Environment.FileTabBorder`<br /><br /> 設定為與背景相同的色彩。|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Color.category|  
|---------------|-------------|--------------------------------|  
|![停留時顯示背景索引標籤](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **停留時顯示背景索引標籤**|背景|`Environment.FileTabHotGradientTop`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留時顯示背景索引標籤](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **停留時顯示背景索引標籤**|前景 (文字)|`Environment.FileTabHotText`|  
|![停留時顯示背景索引標籤](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **停留時顯示背景索引標籤**|Border|`Environment.FileTabHotBorder`<br /><br /> 設定為與背景相同的色彩。|  
  
##### <a name="preview-tab"></a>預覽索引標籤  
 使用者按一下方案總管工具視窗中的項目時，預覽索引標籤會出現在文件索引標籤通道右側。 它可作為文件的預覽，也可讓使用者選擇持續在文件索引標籤通道左側開啟文件。 一次只能開啟一個預覽索引標籤。 預覽索引標籤同時具有背景和選取的狀態 (例如開啟的索引標籤)，而且可以在其作用中狀態取得焦點或未取得焦點。  
  
 ![預覽索引標籤紅線](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 請使用於…  
 任何要建立暫時預覽且想要某個項目符合目前預覽索引標籤色彩的位置。  
  
請勿使用於…  
- 於任何非暫時 (非預覽) 的文件種類或索引標籤種類。  

- 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。  
  
  **選取的 [預覽] 索引標籤：焦點**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![預覽索引標籤焦點](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **專注的預覽索引標籤**|背景|`Environment.FileTabProvisionalSelectedActive`|  
|![預覽索引標籤焦點](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **專注的預覽索引標籤**|前景 (文字)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![預覽索引標籤焦點](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **專注的預覽索引標籤**|Border|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> 設定為與背景相同的色彩。|  
|![預覽索引標籤焦點](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **專注的預覽索引標籤**|文件框線|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **選取的預覽索引標籤：未取得焦點**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![預覽索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **未取得焦點預覽索引標籤**|背景|`Environment.FileTabProvisionalSelectedInactive`|  
|![預覽索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **未取得焦點預覽索引標籤**|前景 (文字)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![預覽索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **未取得焦點預覽索引標籤**|Border|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![預覽索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **未取得焦點預覽索引標籤**|文件框線|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **背景預覽索引標籤：預設**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![預覽背景索引標籤](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **預覽索引標籤背景索引標籤**|背景|`Environment.FileTabProvisionalInactive`|  
|![預覽背景索引標籤](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **預覽索引標籤背景索引標籤**|前景 (文字)|`Environment.FileTabProvisionalInactiveForeground`|  
|![預覽背景索引標籤](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **預覽索引標籤背景索引標籤**|Border|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> 設定為與背景相同的色彩。|  
  
 **背景預覽索引標籤：滑鼠停留**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時預覽背景索引標籤](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **滑鼠停留時的預覽索引標籤背景索引標籤**|背景|`Environment.FileTabProvisionalHover`|  
|![停留時預覽背景索引標籤](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **滑鼠停留時的預覽索引標籤背景索引標籤**|前景 (文字)|`Environment.FileTabProvisionalHoverForeground`|  
|![停留時預覽背景索引標籤](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **滑鼠停留時的預覽索引標籤背景索引標籤**|Border|`Environment.FileTabProvisionalHoverBorder`<br /><br /> 設定為與背景相同的色彩。|  
  
##### <a name="document-overflow-button"></a>文件溢位按鈕  
 如果開啟一個或多個文件 (不論目前組態中是否有垂直空間可放入所有文件索引標籤)，則會有文件溢位按鈕。 透過 **CommandBarMenu** 色彩控制的文件溢位下拉式功能表 (請參閱 [Menus](../misc/shared-colors.md#BKMK_CommandMenus))，會顯示一份所有開啟的文件 (顯示和隱藏)，並根據是否在索引標籤通道中顯示所有開啟的文件來變更溢位字符。  
  
 ![溢位紅線](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
請使用於…  
建立自訂文件溢位按鈕時。  

請勿使用於…  
- 針對未與溢位按鈕類似的 UI。  

- 命令列溢位按鈕。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![溢出](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **檔溢位按鈕**|背景|`Environment.DocWellOverflowButtonBackground`|  
|![溢出](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **檔溢位按鈕**|前景 (字符)|`Environment.DocWellOverflowButtonGlyph`|  
|![溢出](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **檔溢位按鈕**|Border|N/A|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時溢位](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **停留時顯示檔溢位按鈕**|背景|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![停留時溢位](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **停留時顯示檔溢位按鈕**|前景 (字符)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![停留時溢位](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **停留時顯示檔溢位按鈕**|Border|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下溢位](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **已按下的檔溢位按鈕**|背景|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![已按下溢位](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **已按下的檔溢位按鈕**|前景 (字符)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![已按下溢位](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **已按下的檔溢位按鈕**|Border|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>工具視窗  
 工具視窗是由 Visual Studio 環境所提供，因此不需要進行複寫。 不過，您可能會決定要利用工具視窗中所使用的色彩，讓您的 UI 一律與 Visual Studio 環境的這個部分一致。  
  
 ![工具視窗紅線](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 請使用於…  
 任何要建立符合工具視窗之 UI 的位置。  
  
 請勿使用於…  
 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。  
  
#### <a name="tool-window-frame"></a>工具視窗框架  
 Visual Studio 中的工具視窗用於許多不同的工作，而且可以存在於數種不同狀態的其中一種狀態。 如果開啟工具視窗，則可以將它指派至文件區域四邊的任何一邊。 工具視窗也可以浮動在 IDE 外面，讓它們可以重新定位在使用者螢幕內的任何位置。 浮動視窗一律位在 IDE 頂端。 最後，工具視窗可以停駐為文件視窗，以及顯示為文件區域中的索引標籤。 會使用文件視窗語彙基元名稱，將已停駐為文件視窗的工具視窗局部上色。  
  
 ![工具視窗框架紅線](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 請使用於…  
 任何要建立符合工具視窗之 UI 的位置。  
  
 請勿使用於…  
 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。  
  
 **連接**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停靠的工具視窗](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|背景|`Environment.ToolWindowBackground`|  
|![停靠的工具視窗](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Border|`Environment.ToolWindowBorder`|  
  
 **浮動：焦點**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![工具視窗已聚焦](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|背景|`Environment.ToolWindowBackground`|  
|![工具視窗已聚焦](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Border|`Environment.MainWindowActiveDefaultBorder`|  
  
 **浮動：未取得焦點**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![工具視窗未取得焦點](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|背景|`Environment.ToolWindowBackground`|  
|![工具視窗未取得焦點](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Border|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>工具視窗標題列  
 標題列框線不是真正的框線，而是跨標題列頂端的粗線。 它並沒有其未取得焦點狀態的語彙基元名稱。  
  
 ![工具視窗標題列紅線](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 請使用於…  
 任何要建立符合工具視窗之 UI 的位置。  
  
 請勿使用於…  
 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。  
  
 **作用**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![標題列焦點](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **焦點標題列**|背景|`Environment.TitleBarActiveGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![標題列焦點](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **焦點標題列**|前景 (文字)|`Environment.TitleBarActiveText`|  
|![標題列焦點](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **焦點標題列**|Border|`Environment.TitleBarActiveBorder`<br /><br /> 設定為與背景相同的色彩。|  
|![標題列焦點](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **焦點標題列**|拖曳控點|`Environment.TitleBarDragHandleActive`|  
  
 **未取得焦點**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![標題列未取得焦點](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **未取得焦點標題列**|背景|`Environment.TitleBarInactiveGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![標題列未取得焦點](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **未取得焦點標題列**|前景 (文字)|`Environment.TitleBarInactiveText`|  
|![標題列未取得焦點](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **未取得焦點標題列**|Border|N/A|  
|![標題列未取得焦點](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **未取得焦點標題列**|拖曳控點|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>標題列按鈕  
 ![標題列按鈕紅線](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 請使用於…  
 UI 中所顯示的按鈕 (當 UI 使用了來自工具視窗標題列的色彩語彙基元時)。  
  
請勿使用於…  
- 出現在其他位置的按鈕。  

- 任何非指定的背景/前景組合。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![標題列按鈕已獲得焦點](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **作用**|背景|N/A|  
|![標題列按鈕已獲得焦點](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **作用**|前景 (字符)|`Environment.ToolWindowButtonActiveGlyph`|  
|![標題列按鈕已獲得焦點](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **作用**|Border|N/A|  
|![標題列按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **未取得焦點**|背景|N/A|  
|![標題列按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **未取得焦點**|前景 (字符)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![標題列按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **未取得焦點**|Border|N/A|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![標題列按鈕著重于停留](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **作用**|背景|`Environment.ToolWindowButtonHoverActive`|  
|![標題列按鈕著重于停留](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **作用**|前景 (字符)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![標題列按鈕著重于停留](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **作用**|Border|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![停留時顯示標題列按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **未取得焦點**|背景|`Environment.ToolWindowButtonHoverInactive`|  
|![停留時顯示標題列按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **未取得焦點**|前景 (字符)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![停留時顯示標題列按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **未取得焦點**|Border|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![焦點和按下的標題列按鈕](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **作用**|背景|`Environment.ToolWindowButtonDown`|  
|![焦點和按下的標題列按鈕](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **作用**|前景 (字符)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![焦點和按下的標題列按鈕](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **作用**|Border|`Environment.ToolWindowButtonDownBorder`|  
|![標題列按鈕未取得焦點和按下](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **未取得焦點**|背景|`Environment.ToolWindowButtonDown`|  
|![標題列按鈕未取得焦點和按下](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **未取得焦點**|前景 (字符)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![標題列按鈕未取得焦點和按下](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **未取得焦點**|Border|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>工具視窗索引標籤  
 ![工具視窗索引標籤紅線](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 請使用於…  
 任何要建立符合工具視窗之 UI 的位置。  
  
 請勿使用於…  
 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。  
  
 **選取的索引標籤**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![焦點為工具視窗索引標籤](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **已選取，焦點工具視窗索引標籤**|背景|`Environment.ToolWindowTabSelectedTab`|  
|![焦點為工具視窗索引標籤](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **已選取，焦點工具視窗索引標籤**|前景 (文字)|`Environment.ToolWindowTabSelectedActiveText`|  
|![焦點為工具視窗索引標籤](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **已選取，焦點工具視窗索引標籤**|Border|`Environment.ToolWindowTabSelectedBorder`<br /><br /> 設定為與背景相同的色彩。|  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![工具視窗索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **已選取，未取得焦點工具視窗索引標籤**|背景|`Environment.ToolWindowTabSelectedTab`|  
|![工具視窗索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **已選取，未取得焦點工具視窗索引標籤**|前景 (文字)|`Environment.ToolWindowTabSelectedText`|  
|![工具視窗索引標籤未取得焦點](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **已選取，未取得焦點工具視窗索引標籤**|Border|`Environment.ToolWindowTabSelectedBorder`<br /><br /> 設定為與背景相同的色彩。|  
  
 **背景索引標籤**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![工具視窗背景索引標籤](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **背景工具視窗索引標籤**|背景|`Environment.ToolWindowTabGradientBegin`<br /><br /> 設定為與 Visual Studio 2013 相同色彩值的漸層停駐點。<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> 設定為與 Visual Studio 2013 相同色彩值的漸層停駐點。|  
|![工具視窗背景索引標籤](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **背景工具視窗索引標籤**|前景 (文字)|`Environment.ToolWindowTabText`|  
|![工具視窗背景索引標籤](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **背景工具視窗索引標籤**|Border|`Environment.ToolWindowTabBorder`|  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![滑鼠停留時的工具視窗背景索引標籤](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **滑鼠停留時的背景工具視窗索引標籤**|背景|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> 設定為與 Visual Studio 2013 相同色彩值的漸層停駐點。<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> 設定為與 Visual Studio 2013 相同色彩值的漸層停駐點。|  
|![滑鼠停留時的工具視窗背景索引標籤](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **滑鼠停留時的背景工具視窗索引標籤**|前景 (文字)|`Environment.ToolWindowTabMouseOverText`|  
|![滑鼠停留時的工具視窗背景索引標籤](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **滑鼠停留時的背景工具視窗索引標籤**|Border|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> 設定為與背景相同的色彩。|  
  
#### <a name="auto-hide-tabs"></a>自動隱藏索引標籤  
 ![自動&#45;隱藏紅線](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 請使用於…  
 任何要建立符合自動隱藏工具視窗索引標籤之 UI 的位置。  
  
 請勿使用於…  
 任何您不想在 Shell 具有佈景主題更新時自動變更的 UI。  
  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![自動&#45;隱藏索引標籤](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **預設自動隱藏索引標籤**|背景|`Environment.AutoHideTabBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![自動&#45;隱藏索引標籤](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **預設自動隱藏索引標籤**|前景 (文字)|`Environment.AutoHideTabText`|  
|![自動&#45;隱藏索引標籤](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **預設自動隱藏索引標籤**|Border|`Environment.AutoHideTabBorder`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留&#45;時自動隱藏索引標籤](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **停留時自動隱藏索引標籤**|背景|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留&#45;時自動隱藏索引標籤](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **停留時自動隱藏索引標籤**|前景 (文字)|`Environment.AutoHideTabMouseOverText`|  
|![停留&#45;時自動隱藏索引標籤](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **停留時自動隱藏索引標籤**|Border|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>通用共用控制項  
 在您的功能中使用標準 Visual Studio 命令列時，您可以存取已設定樣式的 Shell 控制項，而且不應該重新設定這些通用控制項的樣板。 不過，如果您需要建置自訂命令列，則可能也需要建置自訂控制項。 在該情況下，請務必針對下列每個控制項使用正確的語彙基元名稱，讓您的 UI 與 Visual Studio 的其餘部分一致。  
  
#### <a name="search-box"></a>搜尋方塊  
 可能的話，會使用 Visual Studio 環境所提供的通用搜尋控制項。 搜尋方塊色彩位於 **ShellColors.pkgdef** 檔案的 "SearchControl" 分類中，其中包含輸入欄位、動作按鈕、下拉式按鈕和下拉式功能表的語彙基元名稱。  
  
 搜尋方塊可以是數種狀態中的其中一種，但其中有一些互斥：  
  
- 「已取得焦點」或「未取得焦點」指的是游標是否在文字方塊中。  
  
- 「使用中」或「非使用中」指的是使用者是否已在文字方塊中輸入搜尋查詢。  
  
- 「暫留」表示使用者已將滑鼠指標放在搜尋方塊上方 (這種狀態會覆寫所有其他狀態)。  
  
- 「已停用」表示已關閉目前內容的搜尋功能。  
  
  ![搜尋方塊紅線](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  請使用於…  
  設計自訂搜尋方塊時。  
  
  請勿使用於…  
  - 針對不是搜尋方塊的任何項目。  
  
- 任何不想要其一律與搜尋方塊 UI 相符的項目。  
  
  **作用**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![搜尋輸入欄位的焦點](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **輸入欄位**|背景|`SearchControl.FocusedBackground`|  
|![搜尋輸入欄位的焦點](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **輸入欄位**|前景 (文字)|`SearchControl.FocusedBackground`|  
|![搜尋輸入欄位的焦點](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **輸入欄位**|Border|`SearchControl.FocusedBorder`|  
|![搜尋輸入欄位的焦點](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **輸入欄位**|分隔符號|`SearchControl.FocusedDropDownSeparator`|  
|![搜尋動作按鈕的焦點](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **動作按鈕**|背景|無|  
|![搜尋動作按鈕的焦點](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **動作按鈕**|前景 (搜尋字符)|`SearchControl.SearchGlyph`|  
|![搜尋動作按鈕的焦點](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **動作按鈕**|前景 (停止字符)|`SearchControl.StopGlyph`|  
|![搜尋動作按鈕的焦點](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **動作按鈕**|前景 (清除字符)|`SearchControl.ClearGlyph`|  
|![搜尋動作按鈕的焦點](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **動作按鈕**|Border|N/A|  
|![搜尋下拉式&#45;按鈕的焦點](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **下拉按鈕**|背景|`SearchControl.FocusedDropDownButton`|  
|![搜尋下拉式&#45;按鈕的焦點](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **下拉按鈕**|前景 (字符)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![搜尋下拉式&#45;按鈕的焦點](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **下拉按鈕**|Border|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **未取得焦點**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![搜尋輸入欄位未取得焦點](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **現用輸入欄位**|背景|`SearchControl.SearchActiveBackground`|  
|![搜尋輸入欄位未取得焦點](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **現用輸入欄位**|前景 (文字)|`SearchControl.SearchActiveBackground`|  
|![搜尋輸入欄位未取得焦點](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **現用輸入欄位**|Border|`SearchControl.UnfocusedBorder`|  
|![搜尋輸入欄位未取得焦點](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **現用輸入欄位**|分隔符號|`SearchControl.DropDownSeparator`|  
|![搜尋輸入欄位未取得焦點和非作用中](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **非使用中輸入欄位**|背景|`SearchControl.Unfocused`|  
|![搜尋輸入欄位未取得焦點和非作用中](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **非使用中輸入欄位**|前景 (文字)|`SearchControl.Unfocused`|  
|![搜尋輸入欄位未取得焦點和非作用中](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **非使用中輸入欄位**|Border|`SearchControl.UnfocusedBorder`|  
|![搜尋輸入欄位未取得焦點和非作用中](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **非使用中輸入欄位**|分隔符號|`SearchControl.DropDownSeparator`|  
|![搜尋動作按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **動作按鈕**|背景|N/A|  
|![搜尋動作按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **動作按鈕**|前景 (搜尋字符)|`SearchControl.SearchGlyph`|  
|![搜尋動作按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **動作按鈕**|前景 (停止字符)|`SearchControl.StopGlyph`|  
|![搜尋動作按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **動作按鈕**|前景 (清除字符)|`SearchControl.ClearGlyph`|  
|![搜尋動作按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **動作按鈕**|Border|N/A|  
|![搜尋下拉式&#45;按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **下拉按鈕**|背景|`SearchControl.UnfocusedDropDownButton`|  
|![搜尋下拉式&#45;按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **下拉按鈕**|前景 (字符)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![搜尋下拉式&#45;按鈕未取得焦點](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **下拉按鈕**|Border|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下搜尋動作按鈕](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **動作按鈕**|背景|`SearchControl.ActionButtonMouseDown`|  
|![已按下搜尋動作按鈕](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **動作按鈕**|前景 (字符)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![已按下搜尋動作按鈕](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **動作按鈕**|Border|`SearchControl.ActionButtonMouseDownBorder`|  
|![已按&#45;下 [搜尋] 下拉按鈕](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **下拉按鈕**|背景|`SearchControl.MouseDownDropDownButton`|  
|![已按&#45;下 [搜尋] 下拉按鈕](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **下拉按鈕**|前景 (字符)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![已按&#45;下 [搜尋] 下拉按鈕](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **下拉按鈕**|Border|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **反白顯示（僅限文字）**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![搜尋輸入欄位反白顯示](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **已反白顯示文字的輸入欄位**|背景|`SearchControl.Selection`|  
|![搜尋輸入欄位反白顯示](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **已反白顯示文字的輸入欄位**|前景 (文字)|`SearchControl.FocusedBackground`|  
|![搜尋輸入欄位反白顯示](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **已反白顯示文字的輸入欄位**|Border|無|  
|![搜尋輸入欄位反白顯示](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **已反白顯示文字的輸入欄位**|分隔符號|`SearchControl.FocusedDropDownSeparator`|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已停用搜尋輸入欄位](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **輸入欄位**|背景|`SearchControl.Disabled`|  
|![已停用搜尋輸入欄位](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **輸入欄位**|前景 (文字)|`SearchControl.Disabled`|  
|![已停用搜尋輸入欄位](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **輸入欄位**|Border|`SearchControl.DisabledBorder`|  
|![已停用搜尋輸入欄位](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **輸入欄位**|分隔符號|`SearchControl.DropDownSeparator`|  
|![[搜尋動作] 按鈕已停用](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **動作按鈕**|背景|無|  
|![[搜尋動作] 按鈕已停用](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **動作按鈕**|前景 (字符)|`SearchControl.ActionButtonDisabledGlyph`|  
|![[搜尋動作] 按鈕已停用](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **動作按鈕**|Border|無|  
|![[搜尋&#45;] 下拉按鈕已停用](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **下拉按鈕**|背景|無|  
|![[搜尋&#45;] 下拉按鈕已停用](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **下拉按鈕**|前景 (字符)|`SearchControl.DisabledDownButtonGlyph`|  
|![[搜尋&#45;] 下拉按鈕已停用](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **下拉按鈕**|Border|無|  
  
##### <a name="search-drop-down-lists"></a>搜尋下拉式清單  
 搜尋方塊下拉式功能表可能會比 Visual Studio 中的其他下拉式功能表稍微更為複雜。 [建議的搜尋] 和 [搜尋選項] 區段可以單獨或一起出現在功能表上，而且各區段會個別著色。 這兩個區段同時出現時，也會有一條線來區隔它們，而且會有框線括住整個下拉式功能表。  
  
 ![搜尋下拉&#45;紅線](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
請使用於…  
- 建立自訂搜尋下拉式清單時。  

- 正確清單元件的正確語彙基元名稱。  

請勿使用於…  
- 針對出現在其他內容中的下拉式清單。  

- 任何非指定的背景/前景組合。  
  
  **預設值（沒有其他狀態）**  
  
|元素|語彙基元名稱：Category.color|  
|-------------|--------------------------------|  
|Border|`SearchControl.PopupBorder`|  
|分隔符號|`SearchControl.PopupSectionHeaderSeparator`|  
|陰影|`Environment.DropShadowBackground`|  
  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![搜尋建議](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **建議的搜尋**|背景|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![搜尋建議](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **建議的搜尋**|前景 (文字)|`SearchControl.PopupItemText`|  
|![搜尋核取方塊](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **搜尋選項（核取方塊）**|背景|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![搜尋選項](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **搜尋選項（連結）**|背景|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![搜尋核取方塊](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **搜尋選項（核取方塊）**|前景 (核取方塊文字)|`SearchControl.PopupCheckboxText`|  
|![搜尋選項](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **搜尋選項（連結）**|前景 (核取方塊文字)|`SearchControl.PopupCheckboxText`|  
|![搜尋核取方塊](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **搜尋選項（核取方塊）**|前景 (連結文字)|`SearchControl.PopupButtonText`|  
|![搜尋選項](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **搜尋選項（連結）**|前景 (連結文字)|`SearchControl.PopupButtonText`|  
|![搜尋核取方塊](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **搜尋選項（核取方塊）**|頁首背景|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![搜尋選項](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **搜尋選項（連結）**|頁首背景|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![搜尋核取方塊](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **搜尋選項（核取方塊）**|前景 (頁首文字)|`SearchControl.PopupSectionHeaderText`|  
|![搜尋選項](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **搜尋選項（連結）**|前景 (頁首文字)|`SearchControl.PopupSectionHeaderText`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時搜尋建議](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **建議的搜尋**|背景|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留時搜尋建議](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **建議的搜尋**|前景 (文字)|`SearchControl.PopupMouseOverItemText`|  
|![停留時搜尋建議](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **建議的搜尋**|Border|`SearchControl.PopupControlMouseOverBorder`|  
|![停留時搜尋核取方塊](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **建議的搜尋（核取方塊）**|背景|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留時搜尋選項](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **搜尋選項**|背景|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![停留時搜尋核取方塊](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **建議的搜尋（核取方塊）**|前景 (核取方塊文字)|`SearchControl.PopupCheckboxMouseDownText`|  
|![停留時搜尋選項](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **搜尋選項**|前景 (核取方塊文字)|`SearchControl.PopupCheckboxMouseDownText`|  
|![停留時搜尋核取方塊](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **建議的搜尋（核取方塊）**|前景 (連結文字)|`SearchControl.PopupButtonMouseDownText`|  
|![停留時搜尋選項](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **搜尋選項**|前景 (連結文字)|`SearchControl.PopupButtonMouseDownText`|  
|![停留時搜尋核取方塊](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **建議的搜尋（核取方塊）**|Border|`SearchControl.PopupControlMouseOverBorder`|  
|![停留時搜尋選項](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **搜尋選項**|Border|`SearchControl.PopupControlMouseOverBorder`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![搜尋建議按下的](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **建議的搜尋（核取方塊）**|核取方塊背景|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![已按下搜尋選項](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **搜尋選項**|核取方塊背景|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![搜尋建議按下的](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **建議的搜尋（核取方塊）**|核取方塊背景|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![已按下搜尋選項](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **搜尋選項**|核取方塊背景|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![搜尋建議按下的](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **建議的搜尋（核取方塊）**|前景 (核取方塊文字)|`SearchControl.PopupCheckboxMouseDownText`|  
|![已按下搜尋選項](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **搜尋選項**|前景 (核取方塊文字)|`SearchControl.PopupCheckboxMouseDownText`|  
|![搜尋建議按下的](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **建議的搜尋（核取方塊）**|連結背景|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![已按下搜尋選項](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **搜尋選項**|連結背景|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> 雖然未使用在現代佈景主題 UI 中，但是會有這個背景的漸層停駐點和值。|  
|![搜尋建議按下的](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **建議的搜尋（核取方塊）**|前景 (連結文字)|`SearchControl.PopupButtonMouseDownText`|  
|![已按下搜尋選項](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **搜尋選項**|前景 (連結文字)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hyperlink  
 超連結是一個沒有前景/背景配對的控制項。 在所有情況下，都會使用前景超連結色彩，以正確地顯示在深色、灰色和白色背景上。 如果您未使用超連結控制項的色彩語彙基元，則會看到「已按下」的預設系統色彩 (即閃爍紅色)。 這是控制項未使用正確環境色彩語彙基元的訊號。  
  
 ![超連結紅線](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 請使用於…  
 需要建立自訂超連結時。  
  
 請勿使用於…  
 針對不是超連結的任何項目。  
  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![超連結預設值](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|前景 (文字)|`Environment.PanelHyperlink`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時顯示超連結](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|前景 (文字)|`Environment.PanelHyperlinkHover`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下超連結](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|前景 (文字)|`Environment.PanelHyperlinkPressed`|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![超連結已停用](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|前景 (文字)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>資訊列  
 資訊列用來提供所指定內容的詳細資訊，而且一律會出現在文件視窗或工具視窗的頂端。  
  
 ![資訊列紅線](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 請使用於…  
 建立自訂資訊列時。  
  
 請勿使用於…  
 任何未與資訊列類似的 UI 項目。  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![頂部](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **頂部**|背景|`Environment.InfoBackground`|  
|![頂部](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **頂部**|前景 (文字)|`Environment.InfoText`|  
|![頂部](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **頂部**|Border|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>捲軸  
 捲軸的樣式是由 Visual Studio 環境所設定，因此不需要設定佈景主題。 不過，您可能會決定要利用捲軸中使用的色彩，讓您的 UI 一律會與 Visual Studio 環境的這個部分一致。  
  
 ![捲軸紅線](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 請使用於…  
 建立要符合 Visual Studio 捲軸的 UI 時。  
  
 不要使用…  
 任何不想要其一律與捲軸 UI 相符的項目。  
  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![捲軸](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **滾動**|捲軸|`Environment.ScrollBarBackground`|  
|![捲軸](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **滾動**|前景 (捲動方塊)|`Environment.ScrollBarThumbBackground`|  
|![捲軸箭號](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **滾動箭號**|背景|`Environment.ScrollBarArrowBackground`<br /><br /> 設定為與捲軸相同的色彩。|  
|![捲軸箭號](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **滾動箭號**|前景 (字符)|`Environment.ScrollBarArrowGlyph`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![滑鼠停留時捲軸](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **滾動**|捲軸|`Environment.ScrollBarBackground`|  
|![滑鼠停留時捲軸](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **滾動**|前景 (捲動方塊)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![滑鼠停留時捲軸箭號](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **滾動箭號**|背景|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> 設定為與捲軸相同的色彩。|  
|![滑鼠停留時捲軸箭號](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **滾動箭號**|前景 (字符)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下捲軸](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **滾動**|捲軸|`Environment.ScrollBarBackground`|  
|![已按下捲軸](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **滾動**|前景 (捲動方塊)|`Environment.ScrollBarThumbPressedBackground`|  
|![已按下捲軸箭號](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **滾動箭號**|背景|`Environment.ScrollBarArrowPressedBackground`<br /><br /> 設定為與捲軸相同的色彩。|  
|![已按下捲軸箭號](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **滾動箭號**|前景 (字符)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="BKMK_TreeView"></a>樹狀檢視  
 數個工具視窗 (包括方案總管、伺服器總管和類別檢視) 會實作階層式組織配置，其色彩受到 TreeView 類別中的色彩名稱所控制。 樹狀檢視中的所有項目都會有背景和文字色彩。 具有巢狀子項目的項目也具有字符可指出展開還是摺疊項目。  
  
 ![樹狀檢視紅線](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 請使用於…  
 任何您需要實作階層式組織檢視的位置。  
  
請勿使用於…  
- 任何未與樹狀檢視類似的項目。  

- 任何非指定的背景/前景組合。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![樹狀檢視](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|背景|`TreeView.Background`|  
|![樹狀檢視](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|前景 (文字)|`TreeView.Background`|  
|![樹狀檢視](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|前景 (字符)|`TreeView.Glyph`|  
|![樹狀檢視](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Border|無|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時顯示樹狀檢視](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|背景|`TreeView.Background`|  
|![停留時顯示樹狀檢視](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|前景 (文字)|`TreeView.Background`|  
|![停留時顯示樹狀檢視](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|前景 (字符)|`TreeView.GlyphMouseOver`|  
|![停留時顯示樹狀檢視](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Border|無|  
  
 **拖曳至上方**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![樹狀檢視 system.windows.dragdrop.dragover>](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|背景|`TreeView.DragOverItem`|  
|![樹狀檢視 system.windows.dragdrop.dragover>](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|前景 (文字)|`TreeView.DragOverItem`|  
|![樹狀檢視 system.windows.dragdrop.dragover>](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|前景 (字符)|`TreeView.DragOverItemGlyph`|  
|![樹狀檢視 system.windows.dragdrop.dragover>](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Border|無|  
  
 **已選取**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![樹狀檢視聚焦](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **作用**|背景|`TreeView.SelectedItemActive`|  
|![樹狀檢視聚焦](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **作用**|前景 (文字)|`TreeView.SelectedItemActive`|  
|![樹狀檢視聚焦](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **作用**|前景 (字符)|`TreeView.SelectedItemActiveGlyph`|  
|![樹狀檢視聚焦](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **作用**|Border|`TreeView.FocusVisualBorder`|  
|![樹狀檢視未取得焦點](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **未取得焦點**|背景|`TreeView.SelectedItemInactive`|  
|![樹狀檢視未取得焦點](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **未取得焦點**|前景 (文字)|`TreeView.SelectedItemInactive`|  
|![樹狀檢視未取得焦點](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **未取得焦點**|前景 (字符)|`TreeView.SelectedItemInactiveGlyph`|  
|![樹狀檢視未取得焦點](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **未取得焦點**|Border|無|  
  
 **將滑鼠停留在選取的上方**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![滑鼠停留時的樹狀檢視](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **作用**|背景|`TreeView.SelectedItemActive`|  
|![滑鼠停留時的樹狀檢視](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **作用**|前景 (文字)|`TreeView.SelectedItemActive`|  
|![滑鼠停留時的樹狀檢視](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **作用**|前景 (字符)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![滑鼠停留時的樹狀檢視](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **作用**|Border|無`TreeView.FocusVisualBorder`|  
|![停留時未取得焦點樹狀檢視](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **未取得焦點**|背景|`TreeView.SelectedItemInactive`|  
|![停留時未取得焦點樹狀檢視](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **未取得焦點**|前景 (文字)|`TreeView.SelectedItemInactive`|  
|![停留時未取得焦點樹狀檢視](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **未取得焦點**|前景 (字符)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![停留時未取得焦點樹狀檢視](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **未取得焦點**|Border|無|  
  
#### <a name="button-controls"></a>按鈕控制項  
 ![Button 控制項紅線](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 請使用於…  
 文件區域中，您想要與 Visual Studio 佈景主題 (淺色調、暗色調、藍色或系統高對比佈景主題) 整合的按鈕。  
  
 請勿使用於…  
 將針對自訂背景 (不屬於 Visual Studio 的佈景主題) 而顯示的按鈕。  
  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![Button](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|按鈕|`CommonControls.Button`|  
|![Button](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|按鈕框線|`CommonControls.ButtonBorder`|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已停用按鈕](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|按鈕|`CommonControls.ButtonDisabled`|  
|![已停用按鈕](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|按鈕框線|`CommonControls.ButtonBorderDisabled`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時顯示按鈕](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|按鈕|`CommonControls.ButtonHover`|  
|![停留時顯示按鈕](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|按鈕框線|`CommonControls.ButtonBorderHover`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下按鈕](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|按鈕|`CommonControls.ButtonPressed`|  
|![已按下按鈕](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|按鈕框線|`CommonControls.ButtonBorderPressed`|  
  
 **作用**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![按鈕焦點](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|按鈕|`CommonControls.ButtonFocused`|  
|![按鈕焦點](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|按鈕框線|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>核取方塊控制項  
 ![核取方塊紅線](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 請使用於…  
 文件區域內所包含的核取方塊控制項。  
  
 請勿使用於…  
 任何不是核取方塊控制項的 UI。  
  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![核取方塊](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|背景|`CommonControls.CheckBoxBackground`|  
|![核取方塊](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Border|`CommonControls.CheckBoxBorder`|  
|![核取方塊](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Text|`CommonControls.CheckBoxText`|  
|![核取方塊](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|圖像|`CommonControls.CheckBoxGlyph`|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![核取方塊已停用](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|背景|`CommonControls.CheckBoxBackgroundDisabled`|  
|![核取方塊已停用](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Border|`CommonControls.CheckBoxBorderDisabled`|  
|![核取方塊已停用](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Text|`CommonControls.CheckBoxTextDisabled`|  
|![核取方塊已停用](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|圖像|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時顯示覆選框](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|背景|`CommonControls.CheckBoxBackgroundHover`|  
|![停留時顯示覆選框](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Border|`CommonControls.CheckBoxBorderHover`|  
|![停留時顯示覆選框](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Text|`CommonControls.CheckBoxTextHover`|  
|![停留時顯示覆選框](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|圖像|`CommonControls.CheckBoxGlyphHover`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下核取方塊](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|背景|`CommonControls.CheckBoxBackgroundPressed`|  
|![已按下核取方塊](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Border|`CommonControls.CheckBoxBorderPressed`|  
|![已按下核取方塊](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Text|`CommonControls.CheckBoxTextPressed`|  
|![已按下核取方塊](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|圖像|`CommonControls.CheckBoxGlyphPressed`|  
  
 **作用**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![核取方塊焦點](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|背景|`CommonControls.CheckBoxBackgroundFocused`|  
|![核取方塊焦點](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Border|`CommonControls.CheckBoxBorderFocused`|  
|![核取方塊焦點](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Text|`CommonControls.CheckBoxTextFocused`|  
|![核取方塊焦點](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|圖像|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>下拉式方塊控制項  
 ![&#47;下拉式&#45;方塊紅線](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
請使用於…  
針對屬於文件區域一部分的下拉式清單和下拉式方塊。  

請勿使用於…  
- 任何不是下拉式清單或下拉式方塊的 UI。  

- 針對命令列中的 [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown) 或 [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox) 。  
  
  **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![&#47;下拉&#45;下拉式方塊](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|背景|`CommonControls.ComboBoxBackground`|  
|![&#47;下拉&#45;下拉式方塊](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Border|`CommonControls.ComboBoxBorder`|  
|![&#47;下拉&#45;下拉式方塊](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Text|`CommonControls.ComboBoxText`|  
|![&#47;下拉&#45;下拉式方塊](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|分隔符號|`CommonControls.ComboBoxSeparator`|  
|![&#47;下拉&#45;下拉式方塊](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|圖像|`CommonControls.ComboBoxGlyph`|  
|![&#47;下拉&#45;下拉式方塊](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|字符背景|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Disabled**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已停用下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|背景|`CommonControls.ComboBoxBackgroundDisabled`|  
|![已停用下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Border|`CommonControls.ComboBoxBorderDisabled`|  
|![已停用下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Text|`CommonControls.ComboBoxTextDisabled`|  
|![已停用下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|分隔符號|`CommonControls.ComboBoxSeparatorDisabled`|  
|![已停用下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|圖像|`CommonControls.ComboBoxGlyphDisabled`|  
|![已停用下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|字符背景|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時下拉下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|背景|`CommonControls.ComboBoxBackgroundHover`|  
|![停留時下拉下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Border|`CommonControls.ComboBoxBorderHover`|  
|![停留時下拉下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Text|`CommonControls.ComboBoxTextHover`|  
|![停留時下拉下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|分隔符號|`CommonControls.ComboBoxSeparatorHover`|  
|![停留時下拉下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|圖像|`CommonControls.ComboBoxGlyphHover`|  
|![停留時下拉下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|字符背景|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|背景|`CommonControls.ComboBoxBackgroundPressed`|  
|![已按下下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Border|`CommonControls.ComboBoxBorderPressed`|  
|![已按下下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Text|`CommonControls.ComboBoxTextPressed`|  
|![已按下下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|分隔符號|`CommonControls.ComboBoxSeparatorPressed`|  
|![已按下下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|圖像|`CommonControls.ComboBoxGlyphPressed`|  
|![已按下下拉式&#45;&#47;](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|字符背景|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **作用**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![&#47;下拉&#45;下拉式方塊的焦點](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|背景|`CommonControls.ComboBoxBackgroundFocused`|  
|![&#47;下拉&#45;下拉式方塊的焦點](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Border|`CommonControls.ComboBoxBorderFocused`|  
|![&#47;下拉&#45;下拉式方塊的焦點](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Text|`CommonControls.ComboBoxTextFocused`|  
|![&#47;下拉&#45;下拉式方塊的焦點](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|分隔符號|`CommonControls.ComboBoxSeparatorFocused`|  
|![&#47;下拉&#45;下拉式方塊的焦點](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|圖像|`CommonControls.ComboBoxGlyphFocused`|  
|![&#47;下拉&#45;下拉式方塊的焦點](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|字符背景|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **文字輸入選取範圍**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![&#47;下拉式&#45;方塊文字輸入](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|反白顯示|`CommonControls.ComboBoxTextInputSelection`|  
  
 **已按下–列出專案視圖**  
  
|元件|元素|語彙基元名稱：Color.category|  
|---------------|-------------|--------------------------------|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|背景|`CommonControls.ComboBoxListBackground`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|背景|`CommonControls.ComboBoxListBackgroundHover`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|背景|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|背景|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Border|`CommonControls.ComboBoxListBorder`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Border|`CommonControls.ComboBoxListBorderHover`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Border|`CommonControls.ComboBoxListBorderPressed`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Border|`CommonControls.ComboBoxListBorderFocused`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|項目文字|`CommonControls.ComboBoxListItemText`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|項目文字|`CommonControls.ComboBoxListItemTextHover`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|項目文字|`CommonControls.ComboBoxListItemTextPressed`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|項目文字|`CommonControls.ComboBoxListItemTextFocused`|  
|![下拉&#45;&#47;下拉式列示方塊清單視圖](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|背景陰影|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>表格式資料 (方格) 控制項  
 表格式資料控制項 (也稱為方格控制項) 是 Visual Studio 通用控制項，可用來在多個資料行中顯示大量資料。 標準表格式資料控制項可以位於 Visual Studio 的多個位置：[錯誤清單] 工具視窗、IntelliTrace 報告和記憶體堆積檢視等等。 請一律使用所提供的標準表格式資料控制項。 在一些罕見情況下，您可能無法存取標準表格式資料控制項。 在這些情況下，請使用下列語彙基元名稱，確保您的 UI 與 Visual Studio 中的其他表格式資料控制項一致。  
  
 ![表格式資料&#40;格控制項&#41;紅線](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 請使用於…  
 針對表格式或方格控制項。  
  
 請勿使用於…  
 任何不是表格式或方格控制項的 UI。  
  
##### <a name="column-headers"></a>資料行標題  
 資料行標頭包含背景、框線、標題文字，以及通常在依該資料行排序方格時使用的選用字符。  
  
|狀態|元素|語彙基元名稱：Category.color|  
|-----------|-------------|--------------------------------|  
|預設|背景|`Header.Default`|  
|預設|前景 (文字)|`Environment.CommandBarTextActive`|  
|預設|前景 (字符)|`Header.Glyph`|  
|預設|Border|`Header.SeparatorLine`|  
|暫留|背景|`Header.MouseOver`|  
|暫留|前景 (文字)|`Environment.CommandBarTextHover`|  
|暫留|前景 (字符)|`Header.MouseOverGlyph`|  
|暫留|Border|`Header.SeparatorLine`|  
|按下|背景|`CommonControls.CheckBoxBackgroundPressed`|  
|按下|前景 (文字)|`CommonControls.CheckBoxBorderPressed`|  
|按下|前景 (字符)|`CommonControls.CheckBoxTextPressed`|  
|按下|Border|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>清單檢視項目  
 清單檢視項目包含背景和內容。 內容可以是文字及/或圖示。  
  
|狀態|元素|語彙基元名稱：Category.color|  
|-----------|-------------|--------------------------------|  
|預設|背景|透明|  
|預設|前景 (文字)|`Environment.CommandBarTextActive`|  
|預設|Border|無|  
|已選取 (使用中)|背景|`TreeView.SelectedItemActive`|  
|已選取 (使用中)|前景 (文字)|`TreeView.SelectedItemActiveText`|  
|已選取 (使用中)|Border|無|  
|已選取 (非使用中)|背景|`TreeView.SelectedItemInactive`|  
|已選取 (非使用中)|前景 (文字)|`TreeView.SelectedItemInactiveText`|  
|已選取 (非使用中)|Border|無|  
  
### <a name="manifest-designer"></a>資訊清單設計工具  
 資訊清單設計工具的設計是用來輕鬆地編輯 Windows 8 和 Windows Phone 8 專案中的資訊清單檔。 雖然沒有任何共用架構可供取用，但是可能適合您比對方向/瀏覽索引標籤和整體結構的設計版面配置和色彩。 如需版面配置詳細資料的詳細資訊，請參閱 [Layout for Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md)。  
  
 ![資訊清單設計工具紅線](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
請使用於…  
- 針對與資訊清單設計工具類似的設計工具。  

- 改為使用文件區域內的編輯器頂端的通用索引標籤控制項。  

請勿使用於…  
- 如果您有六個以上的索引標籤。  

- 任何未結構化的 UI (例如資訊清單設計工具)。  
  
|狀態|元件|元素|語彙基元名稱：Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|預設值 (已選取)|索引標籤|背景|`ManifestDesigner.TabActive`|  
|預設值 (已選取)|索引標籤|Border|無|  
|預設值 (已選取)|描述窗格|背景|`ManifestDesigner.DescriptionPane`|  
|預設值 (已選取)|內容頁面|背景|`ManifestDesigner.Background`|  
|預設值 (已選取)|內容頁面|對話方塊 Helper 文字|`ManifestDesigner.WatermarkText`<br /><br /> 這個語彙基元名稱不符合其功能。|  
|未選取|索引標籤|背景|`ManifestDesigner.Tab.Inactive`|  
|暫留|索引標籤|背景|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>標記  
 Visual Studio 支援標記，可讓使用者宣告可搜尋關鍵字，以進行追蹤。 例如，專案經理和開發人員可以使用 Team Foundation Server (TFS) 來標記工作項目。 下列表格提供以暫停和已選取狀態顯示之標記本身和「關閉圖示」字符的色彩名稱。  
  
 ![標記紅線](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 請使用於…  
 針對支援標記的 UI。  
  
 請勿使用於…  
 任何其他類型的 UI。  
  
#### <a name="tag"></a>Tag  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **預設值**|背景|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **預設值**|前景 (文字)|`Tag.Background`|  
|![停留時標記](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **逐個**|背景|`Tag.HoverBackground`|  
|![停留時標記](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **逐個**|前景 (文字)|`Tag.HoverBackgroundText`|  
|![已按下標記](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **原裝**|背景|`Tag.PressedBackground`|  
|![已按下標記](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **原裝**|前景 (文字)|`Tag.PressedBackgroundText`|  
|![已選取標記](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **已選取**|背景|`Tag.SelectedBackground`|  
|![已選取標記](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **已選取**|前景 (文字)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>字符 (關閉圖示)  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![標記&#40;圖像&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **預設值（標記預設值）**|背景|N/A|  
|![標記&#40;圖像&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **預設值（標記預設值）**|前景 (字符)|`Tag.TagHoverGlyph`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留&#40; &#41;時標記圖像](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **暫留（標記預設值）**|背景|`Tag.TagHoverGlyphHoverBackground`|  
|![停留&#40; &#41;時標記圖像](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **暫留（標記預設值）**|前景 (字符)|`Tag.TagHoverGlyphHover`|  
|![停留&#40; &#41;時標記圖像](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **暫留（標記預設值）**|Border|`Tag.TagHoverGlyphHoverBorder`|  
  
 **原裝**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已&#40; &#41;按下標記圖像](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **已按下（標記預設值）**|背景|`Tag.TagHoverGlyphPressedBackground`|  
|![已&#40; &#41;按下標記圖像](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **已按下（標記預設值）**|前景 (字符)|`Tag.TagHoverGlyphPressed`|  
|![已&#40; &#41;按下標記圖像](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **已按下（標記預設值）**|Border|`Tag.TagHoverGlyphPressedBorder`|  
  
 **已選取標記/字元預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已選取標記](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **預設值（已選取標記）**|背景|N/A|  
|![已選取標記](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **預設值（已選取標記）**|前景 (字符)|`Tag.TagSelectedGlyph`|  
  
 **已選取標記/圖像停留**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時選取標記](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **暫留（已選取標記）**|背景|`Tag.TagSelectedGlyphHoverBackground`|  
|![停留時選取標記](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **暫留（已選取標記）**|前景 (字符)|`Tag.TagSelectedGlyphHover`|  
|![停留時選取標記](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **暫留（已選取標記）**|Border|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **已選取標記/已按下的字元**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![已按下選取的標記](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **已按下（已選取標記）**|背景|`Tag.TagSelectedGlyphPressedBackground`|  
|![已按下選取的標記](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **已按下（已選取標記）**|前景 (字符)|`Tag.TagSelectedGlyphPressed`|  
|![已按下選取的標記](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **已按下（已選取標記）**|Border|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>殼層  
  
#### <a name="background"></a>背景  
 環境背景包含兩個層級。 下層是涵蓋整個 IDE 的單色。 上層可放入命令櫃下方以及 IDE 左右兩側邊緣的工具視窗自動隱藏通道之間。 從 Visual Studio 2013 開始，在淺色調和暗色調佈景主題中，背景上層和下層會設定為相同的色彩。  
  
 ![Shell 背景紅線](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 請使用於…  
 針對您想要符合 Visual Studio 環境背景的位置。  
  
請勿使用於…  
- 作為非背景表面之位置的填色。  

- 作為您要放置前景項目的背景。  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|下層|背景|`Environment.EnvironmentBackground`|  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|上層|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.EnvironmentBackgroundGradientBegin`|  
|上層|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.EnvironmentBackgroundGradientEnd`|  
|上層|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|上層|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>命令櫃  
 兩組語彙基元名稱用於命令櫃背景：一組用於功能表列所在的位置，一組用於命令列所在的位置。 個別命令列群組有其專屬背景色彩值 (會在＜命令列＞一節中詳細討論)。 功能表列和命令列文字分別會在功能表和命令列一節中進行討論。  
  
 ![命令貨位紅線](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
請使用於…  
- 針對您放置功能表或工具列的區域。  

- 具有正確的背景/前景標記名稱組合。  
  
  請勿使用於…  
  針對未與命令櫃類似的區域。  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|功能表列|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.CommandShelfHighlightGradientBegin`|  
|功能表列|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.CommandShelfHighlightGradientMiddle`|  
|功能表列|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.CommandShelfHighlightGradientEnd`|  
|命令列|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.CommandShelfBackgroundGradientBegin`|  
|命令列|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|命令列|背景<br /><br /> *漸層停駐點在 Visual Studio 2013 淺色和深色主題中設定為相同的色彩值。*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>工具箱  
 工具箱是其中一個最常用於 Visual Studio 的通用工具視窗。 它基本上是已套用特殊佈景主題和樣式的樹狀控制項。  
  
 ![工具箱紅線](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 請使用於…  
 設計要一律與 Shell 工具箱一致的工具視窗時。  
  
 請勿使用於…  
 針對未與工具箱 UI 類似的任何項目，或者，如果您不確定 UI 是否會在 Shell 工具箱色彩變更時發生問題。  
  
 **預設值**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![工具箱父節點](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **父節點**|背景|`Environment.ToolboxContent`<br /><br /> 標題<br /><br /> `Environment.ToolWindowBackground`<br /><br /> 個別項目或整個視窗 (沒有可用控制項時)|  
|![工具箱子節點](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **子節點**|背景|`Environment.ToolboxContent`<br /><br /> 標題<br /><br /> `Environment.ToolWindowBackground`<br /><br /> 個別項目或整個視窗 (沒有可用控制項時)|  
|![工具箱父節點](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **父節點**|Border|無|  
|![工具箱子節點](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **子節點**|Border|無|  
|![工具箱父節點](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **父節點**|前景 (字符)|`Environment.ToolboxContent`|  
|![工具箱子節點](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **子節點**|前景 (字符)|`Environment.ToolboxContent`|  
|![工具箱父節點](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **父節點**|前景 (文字)|`Environment.ToolboxContent`|  
|![工具箱子節點](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **子節點**|前景 (文字)|`Environment.ToolboxContent`|  
  
 **逐個**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![停留時顯示工具箱子節點](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **子節點上的工具箱停留**|背景|`Environment.ToolboxContentMouseOver`<br /><br /> 僅限個別項目|  
|![停留時顯示工具箱子節點](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **子節點上的工具箱停留**|Border|無|  
|![停留時顯示工具箱子節點](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **子節點上的工具箱停留**|前景 (文字)|`Environment.ToolboxContentMouseOver`<br /><br /> 僅限個別項目|  
  
 **已選取**  
  
|元件|元素|語彙基元名稱：Category.color|  
|---------------|-------------|--------------------------------|  
|![工具箱父節點已獲得焦點](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **焦點父節點**|背景|`TreeView.SelectedItemActive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![[工具箱] 子節點已獲得焦點](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **焦點的子節點**|背景|`TreeView.SelectedItemActive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![工具箱父節點已獲得焦點](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **焦點父節點**|Border|`TreeView.FocusVisualBorder`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![[工具箱] 子節點已獲得焦點](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **焦點的子節點**|Border|`TreeView.FocusVisualBorder`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![工具箱父節點已獲得焦點](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **焦點父節點**|前景 (字符)|`TreeView.SelectedItemActive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![[工具箱] 子節點已獲得焦點](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **焦點的子節點**|前景 (字符)|`TreeView.SelectedItemActive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![工具箱父節點已獲得焦點](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **焦點父節點**|前景 (文字)|`TreeView.SelectedItemActive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![[工具箱] 子節點已獲得焦點](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **焦點的子節點**|前景 (文字)|`TreeView.SelectedItemActive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![工具箱父節點未取得焦點](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **未取得焦點父節點**|背景|`TreeView.SelectedItemInactive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![[工具箱] 子節點未取得焦點](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **未取得焦點子節點**|背景|`TreeView.SelectedItemInactive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![工具箱父節點未取得焦點](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **未取得焦點父節點**|Border|無|  
|![[工具箱] 子節點未取得焦點](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **未取得焦點子節點**|Border|無|  
|![工具箱父節點未取得焦點](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **未取得焦點父節點**|前景 (字符)|`TreeView.SelectedItemInactive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![[工具箱] 子節點未取得焦點](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **未取得焦點子節點**|前景 (字符)|`TreeView.SelectedItemInactive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![工具箱父節點未取得焦點](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **未取得焦點父節點**|前景 (文字)|`TreeView.SelectedItemInactive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
|![[工具箱] 子節點未取得焦點](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **未取得焦點子節點**|前景 (文字)|`TreeView.SelectedItemInactive`<br /><br /> 從 [Tree view](../misc/shared-colors.md#BKMK_TreeView) 分類|  
  
## <a name="color-value-reference"></a>色彩值參考  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|元件|部分|元素|狀態|淺色|暗色調|藍色|高對比|  
|分割線|||預設|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|展開器字符||前景|預設|||||  
|展開器字符||前景|暫留|||||  
|展開器字符||背景|預設|||||  
|展開器字符||背景|暫留|||||  
|展開器字符||Border|預設|||||  
|展開器字符||Border|暫留|||||
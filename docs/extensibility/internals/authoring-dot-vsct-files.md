---
title: 製作..Vsct 檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82960de02c43a7c4002e189d573a914bb2a73f20
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186661"
---
# <a name="author-vsct-files"></a>撰寫 .vsct 檔案
本檔說明如何撰寫 *.vsct*檔案，以將功能表項目、工具列和其他使用者介面（UI）元素新增至 Visual Studio 的整合式開發環境（IDE）。 當您將 UI 元素新增至尚未擁有 *.vsct*檔案的 Visual Studio 封裝（VSPackage）時，請使用下列步驟。

 針對新的專案，建議您使用 [Visual Studio 封裝] 範本，因為它會產生 *.vsct*檔案，根據您的選擇，已經有功能表命令、工具視窗或自訂編輯器的必要元素。 您可以修改這個 *.vsct*檔案，以符合 VSPackage 的需求。 如需如何修改 *.vsct*檔的詳細資訊，請參閱[擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)中的範例。

## <a name="author-the-file"></a>撰寫檔案
 在下列階段中撰寫 *.vsct*檔案：建立檔案和資源的結構、宣告 ui 元素、將 ui 元素放在 IDE 中，以及新增任何特殊行為。

### <a name="file-structure"></a>檔案結構
 *.Vsct*檔案的基本結構是[CommandTable](../../extensibility/commandtable-element.md)根項目，其中包含[命令](../../extensibility/commands-element.md)元素和[符號](../../extensibility/symbols-element.md)元素。

#### <a name="to-create-the-file-structure"></a>若要建立檔案結構

1. 遵循[如何：建立 .vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)檔案中的步驟，將 *.vsct*檔案新增至您的專案。

2. 將必要的命名空間新增至 `CommandTable` 元素，如下列範例所示：

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. 在 `CommandTable` 元素中，新增 `Commands` 元素，以裝載您的所有自訂功能表、工具列、命令群組和命令。 為了讓您的自訂 UI 元素可以載入，`Commands` 元素必須將其 `Package` 屬性設定為封裝的名稱。

     在 `Commands` 專案之後，加入 `Symbols` 元素以定義封裝的 Guid，以及 UI 元素的名稱和命令識別碼。

### <a name="include-visual-studio-resources"></a>包含 Visual Studio 資源
 使用[Extern](../../extensibility/extern-element.md)元素來存取定義 Visual Studio 命令的檔案，以及將 UI 元素放在 IDE 中所需的功能表。 如果您將使用在封裝外部定義的命令，請使用[UsedCommands](../../extensibility/usedcommands-element.md)元素來通知 Visual Studio。

#### <a name="to-include-visual-studio-resources"></a>包含 Visual Studio 資源

1. 在 `CommandTable` 專案的頂端，為每個要參考的外部檔案加入一個 `Extern` 元素，然後將 `href` 屬性設定為檔案的名稱。 您可以參考下列標頭檔來存取 Visual Studio 資源：

   - *Stdidcmd*：定義 Visual Studio 所公開之所有命令的識別碼。

   - *Vsshlids .h*：包含 Visual Studio 功能表的命令識別碼。

2. 如果您的封裝會呼叫 Visual Studio 或其他封裝所定義的任何命令，請在 `Commands` 元素後面加入 `UsedCommands` 元素。 針對您所呼叫且不屬於套件的每個命令，使用[UsedCommand](../../extensibility/usedcommand-element.md)元素填入此元素。 將 `UsedCommand` 元素的 `guid` 和 `id` 屬性，設定為要呼叫之命令的 GUID 和識別碼值。

   如需如何尋找 Visual Studio 命令之 Guid 和識別碼的詳細資訊，請參閱[Visual Studio 命令的 guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)。 若要從其他套件呼叫命令，請使用命令的 GUID 和識別碼，如這些封裝的 *.vsct*檔案中所定義。

### <a name="declare-ui-elements"></a>宣告 UI 元素
 在 *.vsct*檔案的 `Symbols` 區段中，宣告所有新的 UI 元素。

#### <a name="to-declare-ui-elements"></a>宣告 UI 元素

1. 在 `Symbols` 元素中，新增三個[GuidSymbol](../../extensibility/guidsymbol-element.md)元素。 每個 `GuidSymbol` 元素都具有 `name` 屬性和 `value` 屬性。 設定 `name` 屬性，使其反映元素的目的。 `value` 屬性會採用 GUID。 （若要產生 GUID，請在 [**工具**] 功能表上，選取 [**建立 guid**]，然後選取 [登錄**格式**]）。

     第一個 `GuidSymbol` 元素代表您的封裝，而且通常沒有任何子系。 第二個 `GuidSymbol` 元素代表命令集，而且會包含定義您的功能表、群組和命令的所有符號。 第三個 `GuidSymbol` 元素代表您的映射存放區，並包含命令的所有圖示的符號。 如果您沒有使用圖示的命令，您可以省略第三個 `GuidSymbol` 元素。

2. 在代表命令集的 `GuidSymbol` 元素中，新增一或多個[IDSymbol](../../extensibility/idsymbol-element.md)元素。 其中每一個都代表您要加入至 UI 的功能表、工具列、群組或命令。

     針對每個 `IDSymbol` 專案，將 `name` 屬性設定為您將用來參考對應功能表、群組或命令的名稱，然後將 `value` 元素設定為十六進位數位，以表示其命令識別碼。 沒有兩個具有相同父系的 `IDSymbol` 元素可以具有相同的值。

3. 如果您的任何 UI 元素需要圖示，請將每個圖示的 `IDSymbol` 專案新增至代表映射存放區的 `GuidSymbol` 元素。

### <a name="put-ui-elements-in-the-ide"></a>將 UI 元素放在 IDE 中
 [[功能表](../../extensibility/menus-element.md)]、[[群組](../../extensibility/groups-element.md)] 和 [[按鈕](../../extensibility/buttons-element.md)] 元素包含封裝中定義之所有功能表、群組和命令的定義。 使用[父](../../extensibility/parent-element.md)元素（屬於 UI 專案定義的一部分），或使用其他位置所定義的[CommandPlacement](../../extensibility/commandplacement-element.md)元素，將這些功能表、群組和命令放在 IDE 中。

 每個 `Menu`、`Group`和 `Button` 元素都有一個 `guid` 屬性和一個 `id` 屬性。 請一律設定 `guid` 屬性，使其符合代表命令集之 `GuidSymbol` 元素的名稱，並將 `id` 屬性設定為代表您在 `Symbols` 區段中的功能表、群組或命令之 `IDSymbol` 元素的名稱。

#### <a name="to-define-ui-elements"></a>若要定義 UI 元素

1. 如果您要定義任何新的功能表、子功能表、快捷方式功能表或工具列，請將 `Menus` 專案加入 `Commands` 元素。 然後，針對要建立的每個功能表，將 [ [menu](../../extensibility/menu-element.md) ] 專案新增至 [`Menus`] 元素。

    設定 `Menu` 元素的 `guid` 和 `id` 屬性，然後將 `type` 屬性設為您想要的功能表類型。 您也可以設定 `priority` 屬性，以建立父群組中功能表的相對位置。

   > [!NOTE]
   > `priority` 屬性不適用於工具列和內容功能表。

2. Visual Studio IDE 中的所有命令都必須由命令群組裝載，這些是功能表和工具列的直接子系。 如果您要在 IDE 中加入新的功能表或工具列，這些就必須包含新的命令群組。 您也可以將命令群組新增至現有的功能表和工具列，讓您能夠以視覺化方式將命令分組。

    當您新增新的命令群組時，必須先建立一個 `Groups` 專案，然後將每個命令群組的[group](../../extensibility/group-element.md)元素新增至該元素。

    設定每個 `Group` 專案的 `guid` 和 `id` 屬性，然後設定 `priority` 屬性，以在父功能表上建立群組的相對位置。 如需詳細資訊，請參閱[建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。

3. 如果您要將新的命令加入至 IDE，請將 `Buttons` 專案加入至 `Commands` 元素。 然後，針對每個命令，將[Button](../../extensibility/button-element.md)元素新增至 `Buttons` 元素。

   1. 設定每個 `Button` 元素的 `guid` 和 `id` 屬性，然後將 `type` 屬性設定為您想要的按鈕類型。 您也可以設定 `priority` 屬性，以在父群組中建立命令的相對位置。

       > [!NOTE]
       > 在工具列上使用標準功能表命令和按鈕的 `type="button"`。

   2. 在 `Button` 元素中，新增包含[ButtonText](../../extensibility/buttontext-element.md)元素和[CommandName](../../extensibility/commandname-element.md)元素的[string](../../extensibility/strings-element.md)元素。 `ButtonText` 元素提供功能表項目的文字標籤，或工具列按鈕的工具提示。 `CommandName` 元素會提供命令中要使用的命令名稱。

   3. 如果您的命令會有圖示，請在 `Button` 元素中建立[圖示](../../extensibility/icon-element.md)專案，並將其 `guid` 和 `id` 屬性設定為圖示的 `Bitmap` 元素。

       > [!NOTE]
       > 工具列按鈕必須有圖示。

   如需詳細資訊，請參閱[menucommand 對比與 OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)。

4. 如果您的任何命令都需要圖示，請將[點陣圖](../../extensibility/bitmaps-element.md)元素新增至 `Commands` 元素。 然後，針對每個圖示，將[Bitmap](../../extensibility/bitmap-element.md)元素新增至 `Bitmaps` 元素。 這是您指定點陣圖資源位置的位置。 如需詳細資訊，請參閱[將圖示新增至功能表命令](../../extensibility/adding-icons-to-menu-commands.md)。

   您可以依賴父結構，正確地放置大部分的功能表、群組和命令。 對於非常大型的命令集，或當功能表、群組或命令必須出現在多個位置時，我們建議您指定命令位置。

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>依賴父代將 UI 元素放在 IDE 中

1. 針對一般的父代，請在封裝中定義的每個 `Menu`、`Group`和 `Command` 專案中，建立一個 `Parent` 元素。

    `Parent` 元素的目標是將包含功能表、群組或命令的功能表或群組。

   1. 將 `guid` 屬性設定為定義命令集之 `GuidSymbol` 元素的名稱。 如果目標元素不屬於您的封裝，請使用該命令集的 guid，如對應的 *.vsct*檔案中所定義。

   2. 設定 `id` 屬性，使其符合目標功能表或群組的 `id` 屬性。 如需 Visual Studio 所公開的功能表和群組清單，請參閱[Visual Studio 功能表的 guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)[和 Visual Studio 工具列的 guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)。

   如果您有大量的 UI 元素要放在 IDE 中，或如果您有應出現在多個位置中的專案，請在[CommandPlacements](../../extensibility/commandplacements-element.md)元素中定義其放置，如下列步驟所示。

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>若要使用命令位置將 UI 元素放在 IDE 中

1. 在 `Commands` 元素後面，加入 `CommandPlacements` 元素。

2. 在 `CommandPlacements` 元素中，為要放置的每個功能表、群組或命令加入 `CommandPlacement` 專案。

    每個 `CommandPlacement` 專案或 `Parent` 元素都會在一個 IDE 位置中放置一個功能表、群組或命令。 UI 元素只能有一個父代，但可以有多個命令放置。 若要將 UI 元素放在多個位置，請為每個位置加入一個 `CommandPlacement` 元素。

3. 將每個 `CommandPlacement` 專案的 [`guid`] 和 [`id` 屬性] 設定為 [主控] 功能表或群組，就像您針對 `Parent` 元素所做的一樣。 您也可以設定 `priority` 屬性，以建立 UI 元素的相對位置。

   您可以透過父和命令放置來混合放置。 不過，對於非常大型的命令集，我們建議您只使用命令位置。

### <a name="add-specialized-behaviors"></a>新增特殊行為
 例如，您可以使用[CommandFlag](../../extensibility/command-flag-element.md)元素來修改功能表和命令的行為，以變更其外觀和可見度。 您也可以使用[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)元素來影響命令的顯示時間，或使用[KeyBindings](../../extensibility/keybindings-element.md)專案加入鍵盤快速鍵。 某些類型的功能表和命令已經內建特定行為。

#### <a name="to-add-specialized-behaviors"></a>新增特殊行為

1. 若要讓 UI 元素僅在特定 UI 內容中可見，例如，載入方案時，請使用可見度條件約束。

   1. 在 `Commands` 元素後面，加入 `VisibilityConstraints` 元素。

   2. 針對每個要限制的 UI 專案，新增[VisibilityItem](../../extensibility/visibilityitem-element.md)元素。

   3. 針對每個 `VisibilityItem` 元素，將 `guid` 和 `id` 屬性設定為功能表、群組或命令，然後將 `context` 屬性設定為您想要的 UI 內容，如 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 類別中所定義。

2. 若要在程式碼中設定 UI 專案的可見度或可用性，請使用下列一個或多個命令旗標：

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   如需詳細資訊，請參閱[CommandFlag](../../extensibility/command-flag-element.md)元素。

3. 若要變更元素的顯示方式，或動態變更其外觀，請使用下列一或多個命令旗標：

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   如需詳細資訊，請參閱[CommandFlag](../../extensibility/command-flag-element.md)元素。

4. 若要變更元素收到命令時的回應方式，請使用下列一個或多個命令旗標：

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   如需詳細資訊，請參閱[CommandFlag](../../extensibility/command-flag-element.md)元素。

5. 若要將功能表相關的鍵盤快速鍵附加至功能表或功能表上的專案，請在功能表或功能表項目的 `ButtonText` 元素中加入連字號（&）。 當父功能表開啟時，符號後面的字元就是現用鍵盤快速鍵。

6. 若要將功能表獨立的鍵盤快速鍵附加至命令，請使用[KeyBindings](../../extensibility/keybindings-element.md)元素。 如需詳細資訊，請參閱[KeyBinding](../../extensibility/keybinding-element.md)元素。

7. 若要將功能表文字當地語系化，請使用 `LocCanonicalName` 元素。 如需詳細資訊，請參閱[字串](../../extensibility/strings-element.md)元素。

   某些功能表和按鈕類型包含特殊行為。 下列清單說明一些特殊的功能表和按鈕類型。 如需其他類型，請參閱[功能表](../../extensibility/menu-element.md)、[按鈕](../../extensibility/button-element.md)和[組合](../../extensibility/combo-element.md)元素中的 `types` 屬性描述。

   - 下拉式方塊：下拉式方塊是可以在工具列上使用的下拉式清單。 若要在 UI 中加入下拉式方塊，請在 `Commands` 元素中建立[Combos](../../extensibility/combos-element.md)專案。 然後，將每個下拉式方塊的 `Combo` 元素新增至 `Combos` 元素。 `Combo` 元素與 `Button` 元素具有相同的屬性和子系，而且也有 `DefaultWidth` 和 `idCommandList` 屬性。 `DefaultWidth` 屬性會設定寬度（以圖元為單位），而 `idCommandList` 屬性會指向用來填入下拉式方塊的命令識別碼。

   - 功能表控制器：功能表控制器是一個按鈕，它旁邊有箭號。 按一下箭號就會開啟清單。 若要將功能表控制器加入至 UI，請根據您想要的行為，建立 `Menu` 專案，並將其 `type` 屬性設定為 [`MenuController`] 或 [`MenuControllerLatched`]。 若要填入功能表控制器，請將它設定為 `Group` 元素的父系。 功能表控制器會在下拉式清單中顯示該群組的所有子系。

## <a name="see-also"></a>請參閱
- [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)
- [Visual Studio 命令資料表（. .vsct）檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [.VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)
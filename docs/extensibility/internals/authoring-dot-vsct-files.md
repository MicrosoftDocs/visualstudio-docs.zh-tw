---
title: 創作。.Vsct Files |Microsoft Docs
description: 瞭解如何撰寫 .vsct 檔案，以將功能表項目、工具列和其他 UI 元素新增至 Visual Studio 整合式開發環境 (IDE) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c484c08b3335d51283f1f6e1a7b29757a2271aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906062"
---
# <a name="author-vsct-files"></a>撰寫 .vsct 檔案
本檔說明如何撰寫 *.vsct* 檔案，以將功能表項目、工具列和其他使用者介面 (UI) 專案加入至 Visual Studio 整合式開發環境 (IDE) 。 當您將 UI 專案加入至沒有 *.vsct* 檔案的 Visual Studio 封裝 (VSPackage) 時，請使用這些步驟。

 針對新的專案，建議您使用 Visual Studio 套件範本，因為它會產生 *.vsct* 檔案，視您的選取專案而定，已有功能表命令的必要元素、工具視窗或自訂編輯器。 您可以修改這個 *.vsct* 檔案，以符合您的 VSPackage 需求。 如需有關如何修改 *.vsct* 檔案的詳細資訊，請參閱 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)中的範例。

## <a name="author-the-file"></a>撰寫檔
 在這些階段中撰寫 *.vsct* 檔案：建立檔案和資源的結構、宣告 ui 元素、將 ui 元素放在 IDE 中，然後新增任何特製化的行為。

### <a name="file-structure"></a>檔案結構
 *.Vsct* 檔案的基本結構是 [CommandTable](../../extensibility/commandtable-element.md)根項目，其中包含 [命令](../../extensibility/commands-element.md)元素和 [符號](../../extensibility/symbols-element.md)元素。

#### <a name="to-create-the-file-structure"></a>若要建立檔案結構

1. 遵循 how [to：建立 .vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)檔案中的步驟，將 *.vsct* 檔案新增至您的專案。

2. 將必要的命名空間新增至 `CommandTable` 元素，如下列範例所示：

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. 在專案中 `CommandTable` 加入專案， `Commands` 以裝載您所有的自訂功能表、工具列、命令群組和命令。 為了讓您的自訂 UI 元素可以載入， `Commands` 元素的 `Package` 屬性必須設定為封裝的名稱。

     在專案之後 `Commands` ，加入 `Symbols` 元素來定義封裝的 guid，以及 UI 元素的名稱和命令識別碼。

### <a name="include-visual-studio-resources"></a>包含 Visual Studio 資源
 您可以使用 [Extern](../../extensibility/extern-element.md) 元素來存取定義 Visual Studio 命令的檔案，以及在 IDE 中放置 UI 元素所需的功能表。 如果您要使用在封裝之外定義的命令，請使用 [UsedCommands](../../extensibility/usedcommands-element.md) 元素來通知 Visual Studio。

#### <a name="to-include-visual-studio-resources"></a>包含 Visual Studio 資源

1. 在專案的頂端 `CommandTable` ，為 `Extern` 要參考的每個外部檔案加入一個元素，並將屬性設定為檔案的 `href` 名稱。 您可以參考下列標頭檔以存取 Visual Studio 資源：

   - *Stdidcmd*：定義 Visual Studio 所公開之所有命令的識別碼。

   - *Vsshlids*：包含 Visual Studio 功能表的命令識別碼。

2. 如果您的封裝呼叫由 Visual Studio 或由其他封裝所定義的任何命令，請在專案 `UsedCommands` 之後加入元素 `Commands` 。 針對您所呼叫且不是套件一部分的每個命令，將 [UsedCommand](../../extensibility/usedcommand-element.md) 元素填入此元素。 將 `guid` 元素的和 `id` 屬性設定 `UsedCommand` 為要呼叫的命令的 GUID 和識別碼值。

   如需有關如何尋找 Visual Studio 命令之 Guid 和識別碼的詳細資訊，請參閱 [Visual Studio 命令的 guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)。 若要從其他封裝呼叫命令，請使用這些封裝的 *.vsct* 檔案中所定義的 GUID 和命令識別碼。

### <a name="declare-ui-elements"></a>宣告 UI 元素
 在 .vsct 檔案的區段中宣告所有新的 UI 元素 `Symbols` 。 

#### <a name="to-declare-ui-elements"></a>宣告 UI 元素

1. 在 `Symbols` 元素中，加入三個 [GuidSymbol](../../extensibility/guidsymbol-element.md) 專案。 每個 `GuidSymbol` 元素都有 `name` 屬性和 `value` 屬性。 設定 `name` 屬性，使其反映元素的用途。 `value`屬性會採用 GUID。  (若要產生 GUID，請在 [ **工具** ] 功能表上選取 [ **建立 guid**]，然後選取 [登錄 **格式**]。 ) 

     第一個 `GuidSymbol` 元素代表您的封裝，且通常沒有任何子系。 第二個 `GuidSymbol` 元素代表命令集，且會包含定義您的功能表、群組和命令的所有符號。 第三個 `GuidSymbol` 元素代表您的映射存放區，並包含命令所有圖示的符號。 如果您沒有使用圖示的命令，您可以省略第三個 `GuidSymbol` 元素。

2. 在 `GuidSymbol` 代表命令集的元素中，加入一或多個 [IDSymbol](../../extensibility/idsymbol-element.md) 元素。 其中每個都代表您要加入至 UI 的功能表、工具列、群組或命令。

     針對每個專案 `IDSymbol` ，將 `name` 屬性設定為您將用來參考對應功能表、群組或命令的名稱，然後將 `value` 元素設定為十六進位數位，以代表其命令識別碼。 沒有相同父系的兩個 `IDSymbol` 元素可以有相同的值。

3. 如果任何 UI 元素需要圖示，請將 `IDSymbol` 每個圖示的專案新增至 `GuidSymbol` 代表影像存放區的元素。

### <a name="put-ui-elements-in-the-ide"></a>在 IDE 中放置 UI 元素
 [ [功能表](../../extensibility/menus-element.md)]、[ [群組](../../extensibility/groups-element.md)] 和 [ [按鈕](../../extensibility/buttons-element.md) ] 元素包含封裝中定義之所有功能表、群組和命令的定義。 使用 [父](../../extensibility/parent-element.md) 元素（屬於 UI 元素定義的一部分），或使用在其他位置定義的 [CommandPlacement](../../extensibility/commandplacement-element.md) 元素，將這些功能表、群組和命令放入 IDE 中。

 每個 `Menu` 、 `Group` 和 `Button` 元素都有 `guid` 屬性和 `id` 屬性。 務必將 `guid` 屬性設定為符合您的命令集的專案名稱 `GuidSymbol` ，並將 `id` 屬性設定為 `IDSymbol` 代表區段中之功能表、群組或命令的元素名稱 `Symbols` 。

#### <a name="to-define-ui-elements"></a>若要定義 UI 元素

1. 如果您要定義任何新的功能表、子功能表、快捷方式功能表或工具列，請將 `Menus` 元素加入至專案 `Commands` 。 然後，針對每個要建立的功能表，將 [功能表](../../extensibility/menu-element.md) 元素加入至專案 `Menus` 。

    設定 `guid` 元素的和 `id` 屬性 `Menu` ，然後將屬性設定 `type` 為您想要的功能表類型。 您也可以設定 `priority` 屬性，以建立父群組中功能表的相對位置。

   > [!NOTE]
   > `priority`屬性不適用於工具列和內容功能表。

2. Visual Studio IDE 中的所有命令都必須由命令群組主控，這些是功能表和工具列的直接子系。 如果您要在 IDE 中加入新的功能表或工具列，這些都必須包含新的命令群組。 您也可以將命令群組新增至現有的功能表和工具列，讓您可以用視覺化方式將命令分組。

    當您加入新的命令群組時，您必須先建立專案 `Groups` ，然後將每個命令群組的 [群組](../../extensibility/group-element.md) 專案加入其中。

    設定 `guid` `id` 每個元素的和屬性 `Group` ，然後設定屬性， `priority` 以在父功能表上建立群組的相對位置。 如需詳細資訊，請參閱 [建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。

3. 如果您要將新的命令加入至 IDE，請將 `Buttons` 元素加入至專案 `Commands` 。 然後，針對每個命令，將 [Button](../../extensibility/button-element.md) 元素加入至專案 `Buttons` 。

   1. 設定 `guid` `id` 每個元素的和屬性 `Button` ，然後將屬性設定 `type` 為您想要的按鈕類型。 您也可以設定 `priority` 屬性，以在父群組中建立命令的相對位置。

       > [!NOTE]
       > 用於 `type="button"` 工具列上的標準功能表命令和按鈕。

   2. 在專案中 `Button` ，加入包含[ButtonText](../../extensibility/buttontext-element.md)元素和[CommandName](../../extensibility/commandname-element.md)元素的[Strings](../../extensibility/strings-element.md)元素。 `ButtonText`元素提供功能表項目的文字標籤，或工具列按鈕的工具提示。 專案會 `CommandName` 提供命令中要使用之命令的名稱。

   3. 如果您的命令會有圖示，請在專案中建立一個 [icon](../../extensibility/icon-element.md) 元素 `Button` ，並將其 `guid` 和屬性設定 `id` 為圖示的 `Bitmap` 元素。

       > [!NOTE]
       > 工具列按鈕必須有圖示。

   如需詳細資訊，請參閱 [menucommand 對比與 OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)。

4. 如果您的任何命令都需要圖示，請將 [點陣圖](../../extensibility/bitmaps-element.md) 元素加入至 `Commands` 元素。 然後，針對每個圖示，將 [Bitmap](../../extensibility/bitmap-element.md) 元素加入至專案 `Bitmaps` 。 這是您指定點陣圖資源位置的位置。 如需詳細資訊，請參閱 [將圖示新增至功能表命令](../../extensibility/adding-icons-to-menu-commands.md)。

   您可以依賴父結構來正確放置大部分的功能表、群組和命令。 針對非常大型的命令集，或當功能表、群組或命令必須出現在多個位置時，建議您指定命令放置。

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>依賴父代將 UI 元素放置在 IDE 中

1. 若為一般的父代，請 `Parent` 在封裝中定義的每一個、和專案中建立一個元素 `Menu` `Group` `Command` 。

    元素的目標 `Parent` 是將包含功能表、群組或命令的功能表或群組。

   1. 將 `guid` 屬性（attribute）設定為 `GuidSymbol` 定義命令集之元素的名稱。 如果目標專案不是封裝的一部分，請使用該命令集的 guid，如對應的 *.vsct* 檔中所定義。

   2. 將 `id` 屬性設定為符合 `id` 目標功能表或群組的屬性。 如需 Visual Studio 所公開之功能表和群組的清單，請參閱 [Visual Studio 功能表的 guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ，或 [Visual Studio 工具列的 guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)。

   如果您有大量的 UI 元素要放置在 IDE 中，或如果您有應該出現在多個位置的元素，請在 [CommandPlacements](../../extensibility/commandplacements-element.md) 元素中定義其位置，如下列步驟所示。

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>使用命令放置將 UI 元素放置在 IDE 中

1. 在 `Commands` 元素後方加入 `CommandPlacements` 元素。

2. 在 `CommandPlacements` 元素中，為 `CommandPlacement` 要放置的每個功能表、群組或命令新增專案。

    每個專案 `CommandPlacement` 或 `Parent` 元素都會在一個 IDE 位置中放入一個功能表、群組或命令。 UI 元素只能有一個父代，但它可以有多個命令放置。 若要將 UI 元素放置在多個位置，請 `CommandPlacement` 為每個位置新增專案。

3. 將 `guid` 每個專案的和 `id` 屬性設定 `CommandPlacement` 為裝載功能表或群組，就像您對專案所 `Parent` 做的一樣。 您也可以設定 `priority` 屬性，以建立 UI 元素的相對位置。

   您可以透過父項和命令位置來混合放置。 不過，對於非常大型的命令集，我們建議您只使用命令放置。

### <a name="add-specialized-behaviors"></a>新增特殊行為
 您可以使用 [CommandFlag](../../extensibility/command-flag-element.md) 元素來修改功能表和命令的行為，例如變更其外觀和可見度。 您也可以在使用 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) 專案來顯示命令時影響，或使用 [keybindings.json](../../extensibility/keybindings-element.md) 元素來新增鍵盤快速鍵。 某些種類的功能表和命令已經內建特定的行為。

#### <a name="to-add-specialized-behaviors"></a>新增特殊行為

1. 若要讓 UI 元素只在特定的 UI 內容中顯示，例如，載入解決方案時，請使用可見度條件約束。

   1. 在 `Commands` 元素後方加入 `VisibilityConstraints` 元素。

   2. 針對要限制的每個 UI 專案，加入 [VisibilityItem](../../extensibility/visibilityitem-element.md) 元素。

   3. 針對每個 `VisibilityItem` 元素，將 `guid` 和 `id` 屬性設定為功能表、群組或命令，然後將 `context` 屬性設定為您想要的 UI 內容，如類別中所定義 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 。

2. 若要在程式碼中設定 UI 專案的可見度或可用性，請使用下列一或多個命令旗標：

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   如需詳細資訊，請參閱 [CommandFlag](../../extensibility/command-flag-element.md) 元素。

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

   如需詳細資訊，請參閱 [CommandFlag](../../extensibility/command-flag-element.md) 元素。

4. 若要變更元素收到命令時的回應方式，請使用下列一或多個命令旗標：

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

   如需詳細資訊，請參閱 [CommandFlag](../../extensibility/command-flag-element.md) 元素。

5. 若要將功能表相依的鍵盤快速鍵附加至功能表或功能表上的專案，請在 `ButtonText` 功能表或功能表項目的元素中，新增符號字元 ( # A0) 。 當上層功能表開啟時，連字號後面的字元是使用中的鍵盤快速鍵。

6. 若要將功能表獨立的鍵盤快速鍵附加至命令，請使用 [keybindings.json](../../extensibility/keybindings-element.md) 元素。 如需詳細資訊，請參閱 [KeyBinding](../../extensibility/keybinding-element.md) 元素。

7. 若要將功能表文字當地語系化，請使用 `LocCanonicalName` 元素。 如需詳細資訊，請參閱 [Strings](../../extensibility/strings-element.md) 元素。

   某些功能表和按鈕類型包含特殊行為。 下列清單說明某些特殊的功能表和按鈕類型。 針對其他類型，請參閱 `types` [功能表](../../extensibility/menu-element.md)、 [按鈕](../../extensibility/button-element.md)和 [組合](../../extensibility/combo-element.md) 元素中的屬性描述。

   - 下拉式方塊：下拉式方塊是可在工具列上使用的下拉式清單。 若要將下拉式方塊加入至 UI，請在專案中建立 [Combos](../../extensibility/combos-element.md) 元素 `Commands` 。 然後，將每個下拉式方塊的元素加入至專案， `Combos` `Combo` 以加入。 `Combo` 專案的屬性和子系與元素相同， `Button` 而且也具有 `DefaultWidth` 和 `idCommandList` 屬性。 `DefaultWidth`屬性會設定以圖元為單位的寬度，而 `idCommandList` 屬性會指向用來填入下拉式方塊的命令識別碼。

   - 功能表控制器：功能表控制器是按鈕旁邊有箭號的按鈕。 按一下箭號會開啟清單。 若要將功能表控制器加入至 UI，請建立專案， `Menu` 並 `type` `MenuController` `MenuControllerLatched` 根據您想要的行為，將其屬性設定為或。 若要填入功能表控制器，請將它設定為元素的父系 `Group` 。 功能表控制器會在下拉式清單中顯示該群組的所有子系。

## <a name="see-also"></a>另請參閱
- [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)
- [Visual Studio 命令表格 (. .vsct) 檔](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [.VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)
---
title: "撰寫。Vsct 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bad1a8cbd8bc0369d405bf0a0c26c4285e143e46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="authoring-vsct-files"></a>撰寫。Vsct 檔案
本文件示範如何撰寫.vsct 檔加入 Visual Studio 整合式的開發環境 (IDE) 中的功能表項目、 工具列和其他使用者介面 (UI) 項目。 UI 項目加入 Visual Studio Package (VSPackage) 已經沒有.vsct 檔時，請使用下列步驟。  
  
 對於新專案，我們建議您使用 Visual Studio Package 範本，因為它會產生.vsct 檔會根據您的選項，已有必要的項目，功能表命令、 工具視窗，或自訂編輯器。 您可以修改此.vsct 檔案，以符合需求的 VSPackage。 如需如何修改.vsct 檔的詳細資訊，請參閱中的範例[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## <a name="authoring-the-file"></a>撰寫檔案  
 撰寫.vsct 檔中這三個階段： 建立檔案和資源的結構、 宣告的 UI 項目，將 UI 項目放在 IDE 中，並加入任何特殊的行為。  
  
### <a name="file-structure"></a>檔案結構  
 .Vsct 檔的基本結構是[CommandTable](../../extensibility/commandtable-element.md)根項目，其中包含[命令](../../extensibility/commands-element.md)項目和[符號](../../extensibility/symbols-element.md)項目。  
  
##### <a name="to-create-the-file-structure"></a>若要建立的檔案結構  
  
1.  專案中加入.vsct 檔案中步驟[How to： 建立。Vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。  
  
2.  加入必要的命名空間`CommandTable`項目，如下列範例所示。  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  在`CommandTable`項目，加入`Commands`来裝載您的自訂功能表、 工具列、 命令群組和命令的所有項目。 這樣可以載入自訂的 UI 項目，`Commands`項目必須具有其`Package`屬性設定為封裝的名稱。  
  
     之後`Commands`項目，加入`Symbols`項目來定義封裝，以及名稱為 Guid，以及 UI 項目的命令 Id。  
  
### <a name="including-visual-studio-resources"></a>包含 Visual Studio 資源  
 使用[Extern](../../extensibility/extern-element.md)項目，以存取 Visual Studio 命令和功能表，才能將您的 UI 項目放在 IDE 中定義的檔案。 如果您將使用您的封裝之外定義的命令，使用[UsedCommands](../../extensibility/usedcommands-element.md)通知 Visual Studio 的項目。  
  
##### <a name="to-include-visual-studio-resources"></a>包含 Visual Studio 資源  
  
1.  在頂端`CommandTable`項目，加入一個`Extern`項目，每個外部檔案參考，並設定`href`屬性加入檔案的名稱。 您可以參考下列標頭檔，以存取 Visual Studio 資源：  
  
    -   Stdidcmd.h，會定義為 Visual Studio 所公開的所有命令識別碼。  
  
    -   Vsshlids.h，包含 Visual Studio 功能表的命令識別碼。  
  
2.  如果您的封裝呼叫會由 Visual Studio 或其他封裝所定義的任何命令，新增`UsedCommands`之後的項目`Commands`項目。 填入此項目[UsedCommand](../../extensibility/usedcommand-element.md)每個命令呼叫也就不是屬於您的封裝。 設定`guid`和`id`屬性`UsedCommand`呼叫命令的 GUID 和 ID 值的項目。 如需如何尋找 Guid 和 Id Visual Studio 命令的詳細資訊，請參閱[Guid 和 Id 的 Visual Studio 命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)。 若要呼叫從其他封裝的命令，使用的 GUID，以及這些封裝的.vsct 檔案中所定義的命令識別碼。  
  
### <a name="declaring-ui-elements"></a>宣告的 UI 項目  
 宣告中的所有新 UI 元素`Symbols`.vsct 檔的區段。  
  
##### <a name="to-declare-ui-elements"></a>若要宣告 UI 項目  
  
1.  在`Symbols`項目，將三個[GuidSymbol](../../extensibility/guidsymbol-element.md)項目。 每個`GuidSymbol`項目具有`name`屬性和`value`屬性。 設定`name`屬性使其反映之元素的目的。 `value`屬性，不需要是 GUID。 (在產生的 GUID，**工具**功能表上，按一下**建立 GUID**，然後選取**登錄格式**。)  
  
     第一個`GuidSymbol`元素代表您的封裝，通常沒有子系。 第二個`GuidSymbol`元素代表命令集，並將包含所有定義您的功能表、 群組和命令的符號。 第三個`GuidSymbol`元素代表您的映像存放區，並包含符號所有的命令圖示。 如果您有使用圖示沒有命令時，您可以省略第三個`GuidSymbol`項目。  
  
2.  在`GuidSymbol`項目，表示您的命令集，新增一或多個[IDSymbol](../../extensibility/idsymbol-element.md)項目。 每一種代表功能表、 工具列、 群組或您要加入至 UI 的命令。  
  
     每個`IDSymbol`項目，設定`name`屬性設定為您的名稱會用來參考對應的功能表、 群組或命令，然後設定`value`十六進位的數字表示其命令識別碼的項目。任兩個`IDSymbol`具有相同父系的項目可以有相同的值。  
  
3.  如果任何您的 UI 項目需要圖示，將`IDSymbol`至每個圖示的項目`GuidSymbol`項目，表示您的映像存放區。  
  
### <a name="putting-ui-elements-in-the-ide"></a>將 UI 項目放在 IDE 中  
 [功能表](../../extensibility/menus-element.md)項目，[群組](../../extensibility/groups-element.md)項目，和[按鈕](../../extensibility/buttons-element.md)項目包含所有的功能表、 群組及您的封裝中所定義的命令定義。 這些功能表、 群組和命令置於使用 IDE[父](../../extensibility/parent-element.md)項目，這是組件的 UI 項目定義，或使用[CommandPlacement](../../extensibility/commandplacement-element.md)項目，其他位置所定義。  
  
 每個`Menu`， `Group`，和`Button`項目具有`guid`屬性和`id`屬性。 一定會設定`guid`要比對的名稱屬性`GuidSymbol`項目，表示您的命令集，並設定`id`屬性的名稱`IDSymbol`項目，表示您的功能表、 群組或命令中`Symbols`> 一節。  
  
##### <a name="to-define-ui-elements"></a>若要定義 UI 元素  
  
1.  如果您要定義任何新的功能表、 子功能表、 捷徑功能表或工具列，新增`Menus`元素`Commands`項目。 然後，針對要建立每個功能表，加入[功能表](../../extensibility/menu-element.md)元素`Menus`項目。  
  
     設定`guid`和`id`屬性`Menu`項目，並將其設定`type`屬性設定為想要的類型。 您可能也會設定`priority`屬性，以建立父群組中的功能表的相對位置。  
  
    > [!NOTE]
    >  `priority`屬性不適用於工具列和操作功能表。  
  
2.  Visual Studio IDE 中的所有命令都必須由命令群組功能表和工具列的直接子系都裝載。 如果您要加入新的功能表或工具列 ide，這些必須包含新的命令群組。 您也可以新增命令群組至現有的功能表和工具列，讓您以視覺化方式可以群組您的命令。  
  
     當您新增新的命令群組時，您必須先建立`Groups`項目，並將加入[群組](../../extensibility/group-element.md)每個命令群組的項目。  
  
     設定`guid`和`id`每個屬性`Group`項目，並將其設定`priority`屬性，以建立父功能表上的群組的相對位置。 如需詳細資訊，請參閱[建立可重複使用群組的按鈕](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
3.  如果您要將新的命令加入 IDE，新增`Buttons`元素`Commands`項目。 然後，針對每個命令中，加入[按鈕](../../extensibility/button-element.md)元素`Buttons`項目。  
  
    1.  設定`guid`和`id`每個屬性`Button`項目，並將其設定`type`屬性設定為想要的按鈕類型。 您可能也會設定`priority`屬性，以建立父群組中之命令的相對位置。  
  
        > [!NOTE]
        >  使用`type="button"`標準功能表命令和工具列上的按鈕。  
  
    2.  在`Button`項目，加入[字串](../../extensibility/strings-element.md)包含項目[ButtonText](../../extensibility/buttontext-element.md)項目和[CommandName](../../extensibility/commandname-element.md)項目。 `ButtonText`項目提供的文字標籤功能表項目或工具列按鈕的工具提示。 `CommandName`項目會提供要在命令中也使用的命令名稱。  
  
    3.  如果您的命令將會有圖示，建立[圖示](../../extensibility/icon-element.md)中的項目`Button`項目，並設定其`guid`和`id`屬性至`Bitmap`圖示的項目。  
  
        > [!NOTE]
        >  工具列按鈕必須有圖示。  
  
     如需詳細資訊，請參閱[MenuCommands Vs。OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)。  
  
4.  如果您命令的任何要求圖示，將[點陣圖](../../extensibility/bitmaps-element.md)元素`Commands`項目。 然後，針對每個圖示，加入[點陣圖](../../extensibility/bitmap-element.md)元素`Bitmaps`項目。 這是您用來指定點陣圖資源的位置。 如需詳細資訊，請參閱[將圖示加入功能表命令](../../extensibility/adding-icons-to-menu-commands.md)。  
  
 您可以依賴正確放置大部分功能表、 群組和命令的父代結構。 對於非常大的命令集，或當功能表、 群組或命令必須出現在多個位置中，我們建議您指定的命令位置。  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>依賴將 UI 項目放在 IDE 中的父代  
  
1.  典型的父代，對於建立`Parent`中每個項目`Menu`， `Group`，和`Command`定義在封裝中的項目。  
  
     目標`Parent`項目是功能表或群組將包含功能表、 群組或命令。  
  
    1.  設定`guid`屬性的名稱`GuidSymbol`定義命令集的項目。 如果目標項目不屬於您的封裝，使用 guid 該命令集，對應的.vsct 檔中所定義。  
  
    2.  設定`id`屬性，以符合`id`目標功能表或群組的屬性。 如需功能表和 Visual Studio 所公開的群組的清單，請參閱[Guid 和 Id 的 Visual Studio 功能表](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)或[Guid 和 Id 的 Visual Studio 工具列](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)。  
  
 如果您有大量要放置在 ide 中的 UI 項目，或是如果您有多個位置中應該顯示的項目，定義其放置在[CommandPlacements](../../extensibility/commandplacements-element.md)項目，如下列步驟所示。  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>若要使用命令位置，將 UI 項目放在 IDE 中  
  
1.  之後`Commands`項目，加入`CommandPlacements`項目。  
  
2.  在`CommandPlacements`項目，加入`CommandPlacement`針對每個功能表、 群組或命令將項目。  
  
     每個`CommandPlacement`項目或`Parent`項目會將一個功能表、 群組或命令放在一個 IDE 位置。 UI 項目只能有一個父代，但它可以有多個命令位置。 若要在多個位置中放置 UI 項目，將`CommandPlacement`針對每個位置的項目。  
  
3.  設定`guid`和`id`每個屬性`CommandPlacement`項目至裝載的功能表或群組，就像您對`Parent`項目。 您也可以設定`priority`屬性，以建立 UI 項目相對位置。  
  
 您可以混合的父代的位置和命令位置。 不過，對於非常大的命令集，我們建議您使用只命令位置。  
  
### <a name="adding-specialized-behaviors"></a>加入特殊的行為  
 您可以使用[CommandFlag](../../extensibility/command-flag-element.md)若要修改的行為的功能表和命令，例如，若要變更其外觀和可見性的項目。 您也可以影響命令看到時使用[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)，或藉由加入鍵盤快速鍵[按鍵組合](../../extensibility/keybindings-element.md)。 特定種類的功能表和命令已經有專門內建的行為。  
  
##### <a name="to-add-specialized-behaviors"></a>若要加入特殊的行為  
  
1.  若要顯示 UI 項目只在特定 UI 內容，例如，在載入方案時，使用可見性條件約束。  
  
    1.  之後`Commands`項目，加入`VisibilityConstraints`項目。  
  
    2.  若要限制每個 UI 項目，加入[VisibilityItem](../../extensibility/visibilityitem-element.md)項目。  
  
    3.  每個`VisibilityItem`項目，設定`guid`和`id`給功能表、 群組，或命令，並將其設定的屬性`context`屬性至您想，UI 內容中所定義<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>類別。 如需詳細資訊，請參閱[VisibilityItem 元素](../../extensibility/visibilityitem-element.md)。  
  
2.  若要在程式碼中設定的可見性或可用性的 UI 項目，使用一或多個下列的命令旗標：  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     如需詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)。  
  
3.  若要變更項目隨即出現，或動態變更其外觀的方式，使用一或多個下列的命令旗標：  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   Pict  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   文字變更  
  
    -   TextOnly  
  
     如需詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)。  
  
4.  若要變更項目如何反應收到命令時，使用一或多個下列的命令旗標：  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   篩選鍵  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     如需詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)。  
  
5.  要附加功能表相關的快速鍵功能表或功能表上的項目，請新增連字號字元 ('& ') 在`ButtonText`項目，功能表或功能表項目。 在父功能表開啟時，後面的連字號的字元是作用中的鍵盤快速鍵。  
  
6.  若要將獨立於功能表的鍵盤快速鍵附加至命令，使用[按鍵組合](../../extensibility/keybindings-element.md)。 如需詳細資訊，請參閱[KeyBinding 元素](../../extensibility/keybinding-element.md)。  
  
7.  若要當地語系化功能表文字，請使用`LocCanonicalName`項目。 如需詳細資訊，請參閱[字串項目](../../extensibility/strings-element.md)。  
  
 某些功能表和按鈕的型別包含特殊的行為。 下表描述一些特殊的功能表和按鈕類型。 對於其他類型，請參閱`types`屬性中的描述[功能表項目](../../extensibility/menu-element.md)，[按鈕項目](../../extensibility/button-element.md)，和[下拉式項目](../../extensibility/combo-element.md)。  
  
 下拉式方塊  
 下拉式方塊是可以使用工具列的下拉式清單。 若要加入至 UI 的下拉式方塊，建立[組合](../../extensibility/combos-element.md)中的項目`Commands`項目。 將新增到`Combos`元素`Combo`新增每個下拉式方塊項目。 `Combo`項目擁有相同的屬性和子系為`Button`項目，也有`DefaultWidth`和`idCommandList`屬性。 `DefaultWidth`屬性設定的寬度，以像素和`idCommandList`屬性指向用來填入下拉式方塊的命令識別碼。 如需詳細資訊，請參閱`Combo`項目文件。  
  
 MenuController  
 功能表控制器是具有旁邊的箭頭的按鈕。 按一下箭頭，即可開啟清單。 若要將功能表控制器加入至 UI 中，建立`Menu`項目並設定其`type`屬性**MenuController**或**MenuControllerLatched**，取決於您想要的行為。 若要填入功能表控制器，將它設為父代`Group`項目。 功能表控制器將會顯示該群組的所有子系的下拉式清單上。  
  
## <a name="see-also"></a>另請參閱  
 [擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 命令表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
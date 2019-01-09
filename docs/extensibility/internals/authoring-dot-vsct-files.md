---
title: 撰寫。Vsct 檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b39cd97bca9ee88628d064f917686d2a7f45aaa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945258"
---
# <a name="author-vsct-files"></a>撰寫.vsct 檔案
本文件說明如何撰寫 *.vsct*將功能表項目、 工具列和其他使用者介面 (UI) 項目新增至 Visual Studio 整合式的開發環境 (IDE) 的檔案。 當您將 UI 項目新增到還沒有 Visual Studio 封裝 (VSPackage) 使用這些步驟 *.vsct*檔案。  
  
 對於新專案，我們建議您使用 Visual Studio package 範本，因為它會產生 *.vsct*檔案，根據您的選擇，已經有必要的項目，功能表命令、 工具視窗，或自訂編輯器. 您可以修改這 *.vsct*檔案，以符合需求的 VSPackage。 如需有關如何修改 *.vsct*檔案，請參閱中的範例[擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## <a name="author-the-file"></a>製作檔案  
 作者 *.vsct*這些階段中的檔案：建立檔案和資源的結構、 宣告的 UI 項目，將 UI 項目放在 IDE 中，並加入任何特殊的行為。  
  
### <a name="file-structure"></a>檔案結構  
 基本結構 *.vsct*檔案[CommandTable](../../extensibility/commandtable-element.md)包含的根項目[命令](../../extensibility/commands-element.md)元素和[符號](../../extensibility/symbols-element.md)項目。  
  
#### <a name="to-create-the-file-structure"></a>若要建立的檔案結構  
  
1.  新增 *.vsct*檔案，以您的專案中的步驟[How to:建立.vsct 檔](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。  
  
2. 新增必要的命名空間，以`CommandTable`項目，如下列範例所示：  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  在 `CommandTable`項目，新增`Commands`來裝載您的自訂功能表、 工具列、 命令群組和命令的所有項目。 以便載入自訂的 UI 項目，`Commands`項目必須具有其`Package`屬性設為封裝的名稱。  
  
     在後`Commands`項目，新增`Symbols`來定義封裝，以及的名稱 Guid 和您的 UI 項目的命令 Id 的項目。  
  
### <a name="include-visual-studio-resources"></a>包含 Visual Studio 資源  
 使用[Extern](../../extensibility/extern-element.md)来存取 Visual Studio 的命令和功能表，才能將您的 UI 項目放在 IDE 中定義的檔案項目。 如果您將使用您的套件之外定義的命令，使用[UsedCommands](../../extensibility/usedcommands-element.md)項目，告知 Visual Studio。  
  
#### <a name="to-include-visual-studio-resources"></a>包含 Visual Studio 資源  
  
1. 在頂端`CommandTable`項目，加入一個`Extern`參考，並設定每個外部檔案的項目`href`屬性加入檔案的名稱。 您可以參考下列標頭檔來存取 Visual Studio 資源：  
  
   -   *Stdidcmd.h*:定義識別碼針對 Visual Studio 所公開的所有命令。  
  
   -   *Vsshlids.h*:包含 Visual Studio 功能表的命令識別碼。  
  
2. 如果您的封裝呼叫由 Visual Studio 或其他套件會定義任何命令，新增`UsedCommands`之後的項目`Commands`項目。 填入此項目[UsedCommand](../../extensibility/usedcommand-element.md)每個命令呼叫也就是不屬於您套件的一部分。 設定`guid`並`id`屬性的`UsedCommand`呼叫命令的 GUID 和 ID 值的項目。 

   如需如何尋找 [Guid] 和 Visual Studio 的識別碼命令的詳細資訊，請參閱[Guid 和 Visual Studio 的識別碼命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)。 若要從其他套件呼叫的命令，使用 GUID 和命令的識別碼中所定義 *.vsct*這些套件的檔案。
  
### <a name="declare-ui-elements"></a>宣告 UI 項目  
 將所有新的 UI 項目，在宣告`Symbols`一節 *.vsct*檔案。  
  
#### <a name="to-declare-ui-elements"></a>若要宣告 UI 項目  
  
1.  在 `Symbols`項目，新增三個[GuidSymbol](../../extensibility/guidsymbol-element.md)項目。 每個`GuidSymbol`項目具有`name`屬性和`value`屬性。 設定`name`屬性，讓它反映出之項目的用途。 `value`屬性會是 GUID。 (若要在產生的 GUID，**工具**功能表上，選取**建立 GUID**，然後選取**登錄格式**。)  
  
     第一個`GuidSymbol`項目代表您的套件，且通常沒有子系。 第二個`GuidSymbol`命令集，並將包含的所有符號定義您的功能表、 群組和命令的項目表示。 第三個`GuidSymbol`項目代表您的映像存放區，並包含符號所有的圖示為您的命令。 如果您有沒有使用圖示的命令時，您可以省略第三個`GuidSymbol`項目。  
  
2.  在 `GuidSymbol`項目，表示您的命令集，新增一或多個[IDSymbol](../../extensibility/idsymbol-element.md)項目。 每一種代表功能表、 工具列、 群組或您要加入至 UI 的命令。  
  
     每個`IDSymbol`項目，設定`name`屬性設定為您的名稱會用來表示對應的功能表、 群組或命令，然後設定`value`項目為十六進位的數字表示其命令識別碼。 任兩個`IDSymbol`有相同的父代的項目可以有相同的值。  
  
3.  如果任何您的 UI 項目需要圖示，新增`IDSymbol`針對至每個圖示的項目`GuidSymbol`項目，表示您的映像存放區。  
  
### <a name="put-ui-elements-in-the-ide"></a>將 UI 項目放在 IDE 中  
 [功能表](../../extensibility/menus-element.md)，[群組](../../extensibility/groups-element.md)，並[按鈕](../../extensibility/buttons-element.md)項目中包含的所有功能表、 群組和您的套件中所定義的命令定義。 將這些功能表、 群組和命令放在 IDE 中使用[父代](../../extensibility/parent-element.md)項目，這是組件的 UI 項目定義，或使用[CommandPlacement](../../extensibility/commandplacement-element.md)項目，是定義在其他位置。  
  
 每個`Menu`， `Group`，並`Button`項目具有`guid`屬性和`id`屬性。 一律設`guid`要比對的名稱屬性`GuidSymbol`項目，表示您的命令集，並設定`id`屬性的名稱`IDSymbol`項目，表示您的功能表、 群組或命令`Symbols`一節。  
  
#### <a name="to-define-ui-elements"></a>若要定義 UI 元素  
  
1. 如果您正在定義任何新的功能表、 子功能表、 捷徑功能表或工具列，新增`Menus`項目`Commands`項目。 然後，針對要建立每個功能表，新增[ 功能表](../../extensibility/menu-element.md)項目`Menus`項目。  
  
    設定`guid`並`id`屬性`Menu`項目，然後再把`type`屬性設定為您想要的類型。 您也可以設定`priority`屬性，以在父群組中建立功能表的相對位置。  
  
   > [!NOTE]
   >  `priority`屬性不適用於工具列和快顯功能表。  
  
2. 命令群組功能表和工具列的直接子系所都必須裝載 Visual Studio IDE 中的所有命令。 如果您要新增新的功能表或工具列的 ide，這些必須包含新的命令群組。 您也可以新增至現有的功能表和工具列命令群組，以便您可以以視覺化方式分組您的命令。  
  
    當您新增新的命令群組時，您必須先建立`Groups`項目，然後將它加入[群組](../../extensibility/group-element.md)針對每個命令群組的項目。  
  
    設定`guid`並`id`每個屬性`Group`項目，然後再把`priority`屬性，以建立父功能表上的群組的相對位置。 如需詳細資訊，請參閱 <<c0> [ 建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
3. 如果您要新增新的命令加入 IDE，新增`Buttons`項目`Commands`項目。 然後，針對每個命令中，新增[ 按鈕](../../extensibility/button-element.md)項目`Buttons`項目。  
  
   1.  設定`guid`並`id`每個屬性`Button`項目，然後再把`type`屬性設定為想要的按鈕類型。 您也可以設定`priority`屬性，以在父群組中建立命令的相對位置。  
  
       > [!NOTE]
       >  使用`type="button"`標準功能表命令和工具列上的按鈕。  
  
   2.  在 `Button`項目，新增[字串](../../extensibility/strings-element.md)包含的項目[ButtonText](../../extensibility/buttontext-element.md)項目和[CommandName](../../extensibility/commandname-element.md)項目。 `ButtonText`項目 功能表項目或工具列按鈕的工具提示中提供的文字標籤。 `CommandName`項目會提供要在命令中也使用的命令名稱。  
  
   3.  如果您的命令將會有圖示，建立[ 圖示](../../extensibility/icon-element.md)中的項目`Button`項目，並將其`guid`並`id`屬性加入`Bitmap`圖示的項目。  
  
       > [!NOTE]
       >  工具列按鈕必須有圖示。  
  
   如需詳細資訊，請參閱[Menucommand 對比。OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)。  
  
4. 如果任何您命令需要圖示，新增[點陣圖](../../extensibility/bitmaps-element.md)項目`Commands`項目。 然後，針對每個圖示，新增[點陣圖](../../extensibility/bitmap-element.md)項目`Bitmaps`項目。 這是您用來指定點陣圖資源的位置。 如需詳細資訊，請參閱 <<c0> [ 將圖示加入至功能表命令](../../extensibility/adding-icons-to-menu-commands.md)。  
  
   您可以依賴正確放置大部分的功能表、 群組和命令的父結構。 對於非常大的命令集，或當功能表、 群組或命令必須出現在多個位置中，我們建議您指定命令位置。  
  
#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>若要依賴將 UI 項目放在 IDE 中的父代  
  
1. 針對典型的父代，建立`Parent`中每個項目`Menu`， `Group`，和`Command`您封裝中定義的項目。  
  
    目標`Parent`項目是功能表或群組將包含功能表、 群組或命令。  
  
   1.  設定`guid`屬性的名稱`GuidSymbol`定義的命令集的項目。 如果目標項目不是套件的一部分，用於 guid 在設定該命令後，所定義之對應 *.vsct*檔案。  
  
   2.  設定`id`屬性，以符合`id`目標 功能表或群組的屬性。 如需功能表和 Visual Studio 所公開的群組的清單，請參閱 < [Visual Studio 識別碼和 Guid 功能表](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)或[Guid] 和 [Visual Studio 的識別碼工具列](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)。  
  
   如果您有大量 UI 項目放在 IDE 中，或如果您有應該會出現在多個位置的項目，定義中的其配置[CommandPlacements](../../extensibility/commandplacements-element.md)項目，如下列步驟中所示。  
  
#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>若要使用命令位置來將 UI 項目放在 IDE 中  
  
1. 在後`Commands`項目，新增`CommandPlacements`項目。  
  
2. 在 `CommandPlacements`項目，新增`CommandPlacement`的每個功能表、 群組或命令，將項目。  
  
    每個`CommandPlacement`項目或`Parent`項目會將一個功能表、 群組或命令放在一個 IDE 的位置。 UI 項目只能有一個父代，但它可以有多個命令的位置。 若要將 UI 項目放在多個位置中，新增`CommandPlacement`針對每個位置的項目。  
  
3. 設定`guid`並`id`每個屬性`CommandPlacement`至裝載的功能表或群組，就如同您的項目會針對`Parent`項目。 您也可以設定`priority`屬性，以建立的 UI 元素的相對位置。  
  
   您可以混合的父代的位置和命令位置。 不過，對於非常大的命令集，我們建議您使用只有命令位置。  
  
### <a name="add-specialized-behaviors"></a>新增特殊的行為  
 您可以使用[CommandFlag](../../extensibility/command-flag-element.md)項目來修改行為的功能表和命令，例如，若要變更其外觀和可見性。 您也可以影響時使用的命令會顯示[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)項目，或藉由加入鍵盤快速鍵[按鍵繫結關係](../../extensibility/keybindings-element.md)項目。 特定種類的功能表和命令已經有專用的內建的行為。  
  
#### <a name="to-add-specialized-behaviors"></a>將特製化的行為  
  
1. 若要顯示的 UI 項目只在特定 UI 內容，例如，載入方案時，使用 可見性的條件約束。  
  
   1.  在後`Commands`項目，新增`VisibilityConstraints`項目。  
  
   2.  每個 UI 項目來限制，加入[VisibilityItem](../../extensibility/visibilityitem-element.md)項目。  
  
   3.  每個`VisibilityItem`項目，設定`guid`並`id` 功能表、 群組或命令，然後將設定的屬性`context`屬性設定為您想，UI 內容中所定義<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>類別。   
  
2. 若要在程式碼中設定的可見性或可用性的 UI 項目，使用一或多個下列的命令旗標：  
  
   -   `DefaultDisabled`
  
   -   `DefaultInvisible`
  
   -   `DynamicItemStart` 
  
   -   `DynamicVisibility`
  
   -   `NoShowOnMenuController`
  
   -   `NotInTBList`
  
   如需詳細資訊，請參閱 < [CommandFlag](../../extensibility/command-flag-element.md)項目。  
  
3. 若要變更項目隨即出現，或以動態方式變更其外觀的方式，使用一或多個下列的命令旗標：  
  
   -   `AlwaysCreate`  
  
   -   `CommandWellOnly`  
  
   -   `DefaultDocked`  
  
   -   `DontCache`  
  
   -   `DynamicItemStart`  
  
   -   `FixMenuController`  
  
   -   `IconAndText`  
  
   -   `Pict`  
  
   -   `StretchHorizontally`  
  
   -   `TextMenuUseButton`  
  
   -   `TextChanges`  
  
   -   `TextOnly`  
  
   如需詳細資訊，請參閱 < [CommandFlag](../../extensibility/command-flag-element.md)項目。  
  
4. 若要變更項目如何回應收到命令時，使用一或多個下列的命令旗標：  
  
   -   `AllowParams`  
  
   -   `CaseSensitive`  
  
   -   `CommandWellOnly`  
  
   -   `FilterKeys`  
  
   -   `NoAutoComplete`  
  
   -   `NoButtonCustomize`  
  
   -   `NoKeyCustomize`  
  
   -   `NoToolbarClose`  
  
   -   `PostExec`  
  
   -   `RouteToDocs`  
  
   -   `TextIsAnchorCommand`  
  
   如需詳細資訊，請參閱 < [CommandFlag](../../extensibility/command-flag-element.md)項目。  
  
5. 若要附加功能表相關的快速鍵功能表或功能表上的項目，加上連字號字元 (&) 在`ButtonText`功能表或功能表項目的項目。 父功能表開啟時，遵循連字號字元會是作用中的鍵盤快速鍵。  
  
6. 若要將獨立於功能表的鍵盤快速鍵附加至命令中，使用[按鍵繫結關係](../../extensibility/keybindings-element.md)項目。 如需詳細資訊，請參閱 <<c0> [ 按鍵繫結關係](../../extensibility/keybinding-element.md)項目。  
  
7. 若要當地語系化的功能表文字，請使用`LocCanonicalName`項目。 如需詳細資訊，請參閱 <<c0> [ 字串](../../extensibility/strings-element.md)項目。  
  
   某些功能表和按鈕的類型包括特製化的行為。 下列清單說明一些特殊的功能表和按鈕類型。 對於其他類型，請參閱`types`屬性中的描述[ 功能表](../../extensibility/menu-element.md)， [ 按鈕](../../extensibility/button-element.md)，和[組合](../../extensibility/combo-element.md)項目。  
  
   - 下拉式方塊：  
   下拉式方塊是可以使用工具列的下拉式清單。 若要加入的 UI 中的下拉式方塊，建立[Combos](../../extensibility/combos-element.md)中的項目`Commands`項目。 然後加入`Combos`項目`Combo`將每個下拉式方塊的項目。 `Combo` 項目有相同的屬性和子系作為`Button`項目，也有`DefaultWidth`和`idCommandList`屬性。 `DefaultWidth`屬性設定的寬度，單位為像素和`idCommandList`屬性指向用來填入下拉式方塊的命令識別碼。 
  
   - 功能表控制器：  
   功能表控制器是具有它旁邊的箭號按鈕。 按一下箭號會開啟清單。 若要將功能表控制器加入至 UI 中，建立`Menu`項目並將其`type`屬性設定為`MenuController`或`MenuControllerLatched`，取決於您想要的行為。 若要填入功能表控制器，將它設為父代`Group`項目。 功能表控制器將會顯示該群組的所有子系，在它的下拉式清單。  
  
## <a name="see-also"></a>另請參閱  
 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 命令表檔案 (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
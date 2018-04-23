---
title: Vspackage 如何新增使用者介面項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 930ab9e741b2fd5bbc0ca2954192fe5e2c4313d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-vspackages-add-user-interface-elements"></a>Vspackage 如何新增使用者介面項目
VSPackage 可以加入使用者介面 (UI) 項目，例如，功能表、 工具列和工具視窗，來透過.vsct 檔的 Visual Studio。  
  
 您可以找到設計指導方針的 UI 項目在[Visual Studio 使用者經驗指導方針](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio 命令表架構  
 如前所述，命令資料表架構支援前述架構的原則。 抽象概念，資料結構和工具的命令資料表架構背後的原則如下所示：  
  
-   有三種基本項目： 功能表、 命令及群組。 功能表可以公開在 UI 中，為功能表、 子功能表、 工具列或工具視窗。 命令是使用者可以執行在 IDE 中，而且它們可以公開為功能表項目、 按鈕、 清單方塊或其他控制項的程序。 群組是功能表和命令的容器。  
  
-   描述項目，其優先權，相對於其他項目，並修改其行為的旗標的定義被指定每個項目。  
  
-   每個項目具有描述項目的父代的位置。 項目可以有多個父代，使它可以出現在 UI 中的多個位置。  
  
     每個命令必須為其父系，擁有的群組，即使它是該群組中唯一的子系。 每個標準功能表也必須有父群組。 工具列和工具視窗做為其本身的父系。 群組可以有為其父代 Visual Studio 功能表列中，或任何功能表、 工具列或工具視窗。  
  
### <a name="how-items-are-defined"></a>項目定義的方式  
 .Vsct 檔案是以 XML 格式。 .Vsct 檔會定義封裝的 UI 項目，並決定這些項目出現在 IDE 中的位置。 每個功能表、 群組或封裝中的命令會先指派的 GUID 和 ID `Symbols` > 一節。 接下來在.vsct 檔案、 每個功能表、 命令和群組來識別其 GUID 和 ID 的組合。 下列範例示範典型`Symbols`區段所產生的 Visual Studio Package 範本時**功能表命令**範本中已選取。  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 最上層元素`Symbols`區段是[GuidSymbol 元素](../../extensibility/guidsymbol-element.md)。 `GuidSymbol` 元素會對應至 Guid IDE 所用來識別封裝和其元件部分的名稱。  
  
> [!NOTE]
>  在 Visual Studio 封裝範本所自動產生的 Guid。 您也可以按一下來建立唯一的 GUID**建立 GUID**上**工具**功能表。  
  
 第一個`GuidSymbol`項目"guid [PackageName] Byok-kek-pkg 」，是封裝本身的 GUID。 這是由 Visual Studio 用來載入封裝的 GUID。 通常，它並沒有子項目。  
  
 依照慣例，功能表和命令在底下的分組第二個`GuidSymbol`項目"guid [PackageName] CmdSet 」，和點陣圖是在第三個`GuidSymbol`元素中，「 guidImages"。 您沒有遵循這個慣例，但每個功能表、 群組、 命令和點陣圖必須是子系`GuidSymbol`項目。  
  
 在第二個`GuidSymbol`元素，其代表封裝命令集，幾`IDSymbol`項目。 每個[IDSymbol 元素](../../extensibility/idsymbol-element.md)名稱對應到數值，而且可能呈現功能表、 群組或命令的命令集的一部分。 `IDSymbol`第三個中的項目`GuidSymbol`可能做為命令圖示的項目代表點陣圖。 因為必須是唯一的應用程式中，沒有相同的兩個小孩的 GUID/識別碼組`GuidSymbol`元素可能具有相同的值。  
  
### <a name="menus-groups-and-commands"></a>功能表、 群組和命令  
 當功能表、 群組或命令具有 GUID 和 ID 時，它會加入 ide。 每個 UI 項目必須具有下列動作：  
  
-   A`guid`符合名稱的屬性`GuidSymbol`之下的 UI 項目定義的項目。  
  
-   `id`符合相關聯的名稱屬性`IDSymbol`項目。  
  
     在一起，`guid`和`id`屬性撰寫*簽章*UI 項目。  
  
-   A`priority`決定其父功能表或群組中的 UI 項目位置的屬性。  
  
-   A[父項目](../../extensibility/parent-element.md)具有`guid`和`id`父功能表或群組的簽章指定的屬性。  
  
#### <a name="menus"></a>Menus  
 每個功能表會定義為[功能表項目](../../extensibility/menu-element.md)中`Menus`> 一節。 必須有功能表`guid`， `id`，和`priority`屬性和`Parent`項目，也下列的其他屬性和子系：  
  
-   A`type`指定功能表是否應該出現在 IDE 中，為一種功能表或工具列中的屬性。  
  
-   A[字串項目](../../extensibility/strings-element.md)包含[ButtonText 元素](../../extensibility/buttontext-element.md)，在 IDE 中，指定功能表的標題和[CommandName 元素](../../extensibility/commandname-element.md)，以指定的名稱。用於**命令**視窗來存取功能表。  
  
-   選擇性的旗標。 A[命令旗標的項目](../../extensibility/command-flag-element.md)可能出現在功能表定義中，以變更其外觀或行為，在 IDE 中的。  
  
 每個`Menu`項目都必須有群組做為其父系，除非它是可停駐的項目，例如工具列。 可停駐的功能表是其本身的父系。 如需功能表和值`type`屬性，請參閱[功能表項目](../../extensibility/menu-element.md)文件。  
  
 下列範例顯示旁會顯示在 Visual Studio 功能表列的功能表**工具**功能表。  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>群組  
 群組是定義中的項目`Groups`.vsct 檔的區段。 群組是只是容器。 它們不會出現除了在 IDE 中的功能表上的分隔線。 因此，[群組元素](../../extensibility/group-element.md)由其簽章、 優先權和父代所定義。  
  
 群組可以有功能表、 另一個群組，或本身為父系。 不過，父系通常是功能表或工具列。 在前面範例中的功能表是子系的`IDG_VS_MM_TOOLSADDINS`群組與該群組是在 Visual Studio 功能表列的子系。 在下列範例中的群組是功能表的在前面範例中的子系。  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 因為它是功能表的一部分，此群組通常會包含命令。 不過，它也可以包含其他功能表。 這是定義子功能表的方式，如下列範例所示。  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>命令  
 提供給 IDE 的命令定義為[按鈕項目](../../extensibility/button-element.md)或[下拉式項目](../../extensibility/combo-element.md)。 若要出現在功能表或工具列上，命令必須群組做為其父系。  
  
##### <a name="buttons"></a>按鈕  
 中所定義的按鈕`Buttons`> 一節。 任何功能表項目、 按鈕或其他項目，使用者按一下來執行單一命令，會被視為一個按鈕。 某些按鈕類型也可以包含清單功能。 按鈕會有相同的必要和選擇性屬性，有功能表，也會造成[圖示的項目](../../extensibility/icon-element.md)指定的 GUID 和 ID 的點陣圖，表示在 IDE 中的按鈕。 如需按鈕和其屬性的詳細資訊，請參閱[按鈕項目](../../extensibility/buttons-element.md)文件。  
  
 下列範例中的按鈕是在較早的範例中，群組的子系，並為該群組的父功能表上的功能表項目會出現在 IDE 中。  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>組合  
 組合中所定義`Combos`> 一節。 每個`Combo`元素代表在 IDE 中的下拉式清單方塊。 清單方塊可能或可能不是可由使用者，根據的值寫入`type`屬性的組合。 組合具有相同的項目和按鈕的行為，也可以有下列的其他屬性：  
  
-   A`defaultWidth`屬性來指定像素寬度。  
  
-   `idCommandList`屬性，指定清單，其中包含顯示在清單方塊中的項目。 必須在同一個宣告命令清單`GuidSymbol`包含在下拉式方塊的節點。  
  
 下列範例會定義下拉式項目。  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>點陣圖  
 將的圖示一起顯示的命令必須包含`Icon`點陣圖使用其 GUID 和 id。 參考的項目 每個點陣圖定義為[點陣圖項目](../../extensibility/bitmap-element.md)中`Bitmaps`> 一節。 唯一必要的屬性`Bitmap`定義是`guid`和`href`，指向原始程式檔。 如果來源檔案的資源區域， **usedList**屬性也是必要項，列出可用的映像區域中的索引。 如需詳細資訊，請參閱[點陣圖項目](../../extensibility/bitmap-element.md)文件。  
  
### <a name="parenting"></a>父代  
 下列規則可控制如何項目可以呼叫另一個做為其父系的項目。  
  
|項目|在本節中的命令資料表定義|可能包含 (父代，或放置在`CommandPlacements` 區段中，或兩者)|可能包含 （稱為父代）|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|群組|[群組項目](../../extensibility/groups-element.md)、 IDE、 其他 Vspackage|功能表上，為群組，請在項目本身|功能表、 群組和命令|  
|功能表|[功能表項目](../../extensibility/menus-element.md)、 IDE、 其他 Vspackage|1 到*n*群組|0 到*n*群組|  
|工具列|[功能表項目](../../extensibility/menus-element.md)、 IDE、 其他 Vspackage|在項目本身|0 到*n*群組|  
|功能表項目|[按鈕項目](../../extensibility/buttons-element.md)、 IDE、 其他 Vspackage|1 到*n*群組、 項目本身|-0 以*n*群組|  
|按鈕|[按鈕項目](../../extensibility/buttons-element.md)、 IDE、 其他 Vspackage|1 到*n*群組、 項目本身||  
|組合|[組合的項目](../../extensibility/combos-element.md)、 IDE、 其他 Vspackage|1 到*n*群組、 項目本身||  
  
### <a name="menu-command-and-group-placement"></a>功能表、 命令和群組放置  
 功能表、 群組或命令可以出現在 IDE 中的多個位置中。 對於多個位置中出現的項目，它必須新增至`CommandPlacements`區段為[CommandPlacement 元素](../../extensibility/commandplacement-element.md)。 可以加入任何功能表、 群組或命令當做命令位置。 不過，工具列無法定位，以這種方式因為它們不能出現在多個內容相關性的位置。  
  
 命令位置，擁有`guid`， `id`，和`priority`屬性。 GUID 和 ID 必須符合位於與項目。 `priority`屬性可控制的其他項目相關的項目位置。 IDE 會合併兩個或多個具有相同優先順序的項目，則因為 IDE 不保證，封裝資源會讀取相同的順序建置封裝每次，會有未定義其位置。  
  
 如果功能表或群組出現在多個位置，該功能表或群組的所有子系會出現在每個執行個體。  
  
## <a name="command-visibility-and-context"></a>命令的可見性和內容  
 多個 Vspackage 安裝時，功能表、 功能表項目和工具列的難題可能干擾 IDE。 若要避免這個問題，您可以控制個別的 UI 項目的可見性，使用*可見性限制式*和命令旗標。  
  
##### <a name="visibility-constraints"></a>可見性條件約束  
 可見性條件約束設定為[VisibilityItem 元素](../../extensibility/visibilityitem-element.md)中`VisibilityConstraints`> 一節。 可見性條件約束定義的目標項目會顯示特定 UI 內容。 功能表或包含本節中的命令可見時才會定義內容的其中一個使用中。 如果這一節中未參考的功能表或命令，則永遠預設為可見。 本節不適用於群組。  
  
 `VisibilityItem` 項目必須有三種屬性，如下所示：`guid`和`id`目標 UI 項目和`context`。 `context`屬性會指定當目標項目會顯示，而且會當做其值的任何有效 UI 內容。 適用於 Visual Studio UI 內容常數屬於<xref:Microsoft.VisualStudio.VSConstants>類別。 每個`VisibilityItem`項目可接受一個內容值。 若要套用的第二個內容，建立第二個`VisibilityItem`指向相同的項目，如下列範例所示的項目。  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
##### <a name="command-flags"></a>命令旗標  
 下列命令旗標可能會影響功能表和命令套用至可見的性。  
  
 AlwaysCreate  
 即使它沒有任何群組或按鈕時，會建立功能表。  
  
 適用於： `Menu`  
  
 CommandWellOnly  
 這個旗標，如果套用命令未出現在最上層功能表上，而且您想要使其可供其他殼層自訂，比方說，繫結至索引鍵。 VSPackage 安裝之後，使用者可以自訂這些命令開啟**選項**對話方塊，然後編輯下的命令位置**鍵盤環境**類別目錄。 不會影響在快顯功能表、 工具列、 功能表控制器或子功能表上的位置。  
  
 適用於： `Button`， `Combo`  
  
 DefaultDisabled  
 根據預設，如果尚未載入 VSPackage 實作命令，或尚未呼叫 QueryStatus 方法，會停用的命令。  
  
 適用於： `Button`， `Combo`  
  
 DefaultInvisible  
 根據預設，此命令為不可見的如果 VSPackage 實作命令就不會載入或尚未呼叫 QueryStatus 方法。  
  
 應與結合`DynamicVisibility`旗標。  
  
 適用於： `Button`， `Combo`， `Menu`  
  
 DynamicVisibility  
 命令的可見性可以透過使用 QueryStatus 方法或內容中隨附的 GUID 被變更`VisibilityConstraints`> 一節。  
  
 適用於不在工具列上的功能表出現的命令。 可以停用，但不是能隱藏 OLECMDF_INVISIBLE 旗標從 QueryStatus 方法傳回時的最上層工具列項目。  
  
 在功能表上，此旗標也會指出，它應該會自動隱藏隱藏它的成員時。 這個旗標通常會指派給子功能表，因為最上層功能表已經有這個行為。  
  
 應與結合`DefaultInvisible`旗標。  
  
 適用於： `Button`， `Combo`， `Menu`  
  
 NoShowOnMenuController  
 如果具有此旗標的命令位於功能表控制站上，命令就不會出現在下拉式清單。  
  
 適用於： `Button`  
  
 如需命令旗標的詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)文件。  
  
##### <a name="general-requirements"></a>一般需求  
 您的命令必須通過一系列如下的測試可以顯示和啟用：  
  
-   此命令是正確的位置。  
  
-   `DefaultInvisible`未設定旗標。  
  
-   父功能表或工具列是可見的。  
  
-   此命令不是不可見因為中的內容項目[VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)> 一節。  
  
-   VSPackage 實作的程式碼<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面顯示，並讓您的命令。 沒有介面程式碼攔截它，並對其進行動作。  
  
-   當使用者按一下您的命令時，它會變成受限於中所述的程序[路由演算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
## <a name="calling-pre-defined-commands"></a>呼叫預先定義的命令  
 [UsedCommands 元素](../../extensibility/usedcommands-element.md)Vspackage 可以存取其他 Vspackage 或 IDE 所提供的命令。 若要這樣做，請建立[UsedCommand 元素](../../extensibility/usedcommand-element.md)，其具有 GUID 和 ID 的命令，以使用。 這可確保命令將會載入由 Visual Studio 中，即使它不是目前的 Visual Studio 組態的一部分。 如需詳細資訊，請參閱[UsedCommand 元素](../../extensibility/usedcommand-element.md)。  
  
## <a name="interface-element-appearance"></a>介面項目外觀  
 以下是考量選擇及定位命令項目：  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供許多 UI 項目顯示的方式會視位置而定。  
  
-   定義所使用的 UI 項目`DefaultInvisible`旗標不會顯示在 IDE 中除非它是 顯示它的 VSPackage 實作<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>方法，或在特定 UI 內容相關聯`VisibilityConstraints`> 一節。  
  
-   不會顯示成功定位的命令。 這是因為 IDE 會自動隱藏或顯示一些命令，根據 VSPackage 已經 （或尚未） 的介面實作。 例如，某些 VSPackage 實作建置介面原因與建置相關的功能表項目會自動顯示。  
  
-   套用`CommandWellOnly`命令可以新增只能透過自訂的 UI 元素的定義中的旗標表示。  
  
-   IDE 會在設計檢視中時，顯示對話方塊時，才可能僅適用於特定 UI 內容，例如，命令。  
  
-   若要讓特定的 UI 項目顯示在 IDE 中，您必須實作一或多個介面，或撰寫一些程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)
---
title: Vspackage 如何新增消費者介面元素 |Microsoft Docs
description: 瞭解 Vspackage 如何將使用者介面 (UI) 元素（例如功能表、工具列和工具視窗）新增至 Visual Studio。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f1d01c2ed91a5f4aad55c196dfb2e689aeea288a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086036"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Vspackage 如何新增使用者介面元素
VSPackage 可以新增使用者介面 (UI) 專案，例如功能表、工具列和工具視窗），透過 .vsct 檔案來 Visual Studio *。*

您可以在 [Visual Studio 使用者經驗指導方針](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)中找到 UI 元素的設計指導方針。

## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio 命令資料表架構
如上所述，命令資料表架構支援上述架構原則。 命令資料表架構的抽象概念、資料結構和工具背後的原則如下：

- 有三種基本的專案：功能表、命令和群組。 您可以在 UI 中將功能表公開為功能表、子功能表、工具列或工具視窗。 命令是使用者可以在 IDE 中執行的程式，且可以公開為功能表項目、按鈕、清單方塊或其他控制項。 群組是適用于功能表和命令的容器。

- 每個專案都是由描述專案的定義、其相對於其他專案的優先順序，以及修改其行為的旗標所指定。

- 每個專案都有一個描述專案父系的位置。 一個專案可以有多個父系，因此它可以出現在 UI 中的多個位置。

每個命令都必須有群組作為其父系，即使它是該群組中唯一的子系。 每個標準功能表也都必須有父群組。 工具列和工具視窗作為其本身的父系。 群組可以有主要 Visual Studio 功能表列或任何功能表、工具列或工具視窗的父系。

### <a name="how-items-are-defined"></a>專案的定義方式
*.Vsct* 檔案會以 XML 格式格式化。 它會定義封裝的 UI 元素，並決定這些專案在 IDE 中的顯示位置。 套件中的每個功能表、群組或命令都會先指派一節中的 GUID 和識別碼 `Symbols` 。 在 *.vsct* 檔案的其餘部分中，每個功能表、命令和群組都是以其 GUID 和 ID 組合來識別。 下列範例顯示在 `Symbols` 範本中選取 **功能表命令** 時，Visual Studio 套件範本所產生的一般區段。

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}">
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

區段的最上層元素 `Symbols` 是 [GuidSymbol 元素](../../extensibility/guidsymbol-element.md)。 `GuidSymbol` 專案會將名稱對應至 IDE 用來識別封裝及其元件部分的 Guid。

> [!NOTE]
> Guid 會由 Visual Studio 套件範本自動產生。 您也可以按一下 [**工具**] 功能表上的 [**建立 guid** ]，以建立唯一的 guid。

第一個 `GuidSymbol` 元素 `guid<PackageName>Pkg` 是封裝本身的 GUID。 這是 Visual Studio 用來載入封裝的 GUID。 一般而言，它沒有子項目。

依照慣例，功能表和命令會在第二個元素下分組， `GuidSymbol` `guid<PackageName>CmdSet` 而點陣圖則是在第三個 `GuidSymbol` 元素下 `guidImages` 。 您不需要遵循此慣例，但每個功能表、群組、命令和點陣圖都必須是元素的子系 `GuidSymbol` 。

第二個 `GuidSymbol` 元素（代表封裝命令集）是數個 `IDSymbol` 元素。 每個 [IDSymbol 元素](../../extensibility/idsymbol-element.md) 都會將名稱對應至數值，且可能代表屬於命令集一部分的功能表、群組或命令。 `IDSymbol`第三個元素中的元素 `GuidSymbol` 代表可作為命令圖示的點陣圖。 因為 GUID/識別碼組在應用程式中必須是唯一的，所以相同元素的兩個子系都不能 `GuidSymbol` 有相同的值。

### <a name="menus-groups-and-commands"></a>功能表、群組和命令
當功能表、群組或命令具有 GUID 和識別碼時，可以將它新增至 IDE。 每個 UI 元素都必須有下列專案：

- 符合在其 `guid` `GuidSymbol` 下定義 UI 元素之元素名稱的屬性。

- `id`符合相關聯元素名稱的屬性 `IDSymbol` 。

`guid`和屬性會一起 `id` 撰寫 UI 元素的簽章。

- `priority`屬性，決定 UI 元素在其父功能表或群組中的位置。

- 具有[](../../extensibility/parent-element.md) `guid` `id` 指定父功能表或群組簽章之和屬性的父元素。

#### <a name="menus"></a>功能表
每個功能表都會定義為區段中的 [功能表](../../extensibility/menu-element.md) 項 `Menus` 。 功能表必須有 `guid` 、 `id` 和 `priority` 屬性，以及專案 `Parent` ，以及下列其他屬性和子系：

- `type`屬性，指定功能表是否應在 IDE 中顯示為一種功能表或工具列。

- 包含 [ButtonText](../../extensibility/buttontext-element.md)專案的 [字串](../../extensibility/strings-element.md)專案，這個專案會指定 IDE 中的功能表標題，以及 [CommandName 元素](../../extensibility/commandname-element.md)，以指定 **命令** 視窗中用來存取功能表的名稱。

- 選擇性旗標。 [CommandFlag 元素](../../extensibility/command-flag-element.md)可能會出現在功能表定義中，以變更其在 IDE 中的外觀或行為。

每個 `Menu` 元素都必須有一個群組作為其父系，除非它是可停駐的元素，例如工具列。 可停駐的功能表是本身的父系。 如需有關屬性之功能表和值的詳細資訊 `type` ，請參閱 [功能表](../../extensibility/menu-element.md) 項檔。

下列範例顯示出現在 [ **工具** ] 功能表旁邊 Visual Studio 功能表列上的功能表。

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu" id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>群組
群組是定義于 .vsct 檔案區段中的專案 `Groups`  。 群組只是容器。 它們不會出現在 IDE 中，除了功能表上的分隔線之外。 因此， [Group 元素](../../extensibility/group-element.md) 只會依據其簽章、優先順序和父系來定義。

群組可以有功能表、另一個群組或本身做為父系。 不過，父系通常是功能表或工具列。 先前範例中的功能表是群組的子系 `IDG_VS_MM_TOOLSADDINS` ，而該群組是 Visual Studio 功能表列的子系。 下列範例中的群組是先前範例中功能表的子系。

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

因為它是功能表的一部分，所以此群組通常會包含命令。 不過，它也可以包含其他功能表。 這是子功能表的定義方式，如下列範例所示。

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu" priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>命令
提供至 IDE 的命令會定義為 [按鈕元素](../../extensibility/button-element.md) 或 [組合元素](../../extensibility/combo-element.md)。 若要在功能表或工具列上顯示，命令必須以群組作為其父系。

##### <a name="buttons"></a>按鈕
按鈕會在區段中定義 `Buttons` 。 使用者按一下以執行單一命令的任何功能表項目、按鈕或其他元素都會被視為按鈕。 某些按鈕類型也可以包含清單功能。 按鈕具有相同的必要和選擇性屬性，該功能表具有相同的必要和選擇性屬性，也可以有 [圖示元素](../../extensibility/icon-element.md) ，以指定表示 IDE 中之按鈕的點陣圖 GUID 和識別碼。 如需按鈕和其屬性的詳細資訊，請參閱 [按鈕元素](../../extensibility/buttons-element.md) 檔集。

下列範例中的按鈕是先前範例中群組的子系，並在 IDE 中顯示為該群組之父功能表上的功能表項目。

```xml
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
Combos 是在 `Combos` 一節中定義。 每個 `Combo` 元素都代表 IDE 中的下拉式清單方塊。 視下拉式方塊的屬性值而定，清單方塊可能會或可能無法由使用者寫入 `type` 。 Combos 具有按鈕具有的相同元素和行為，而且也可以具有下列額外屬性：

- `defaultWidth`指定圖元寬度的屬性。

- `idCommandList`屬性，指定包含清單方塊中顯示之專案的清單。 命令清單必須在包含組合的相同節點中宣告 `GuidSymbol` 。

下列範例會定義組合元素。

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
將與圖示一起顯示的命令，必須包含 `Icon` 使用其 GUID 和 ID 參考點陣圖的元素。 每個點陣圖都會定義為區段中的 [點陣圖元素](../../extensibility/bitmap-element.md) `Bitmaps` 。 定義的唯一必要屬性 `Bitmap` 是 `guid` 和 `href` ，指向原始程式檔。 如果來源檔案是資源區，則也需要 **usedList** 屬性，以列出帶狀中的可用映射。 如需詳細資訊，請參閱 [點陣圖元素](../../extensibility/bitmap-element.md) 檔集。

### <a name="parenting"></a>育兒
下列規則會管理專案如何呼叫另一個專案做為其父代。

|元素|在命令資料表的這個區段中定義|可能包含 (做為父系，或在區段中放置 `CommandPlacements` ，或兩者) |可能包含 (稱為父) |
|-------------| - | - | - |
|Group|[Groups 元素](../../extensibility/groups-element.md)、IDE、其他 vspackage|功能表、群組、專案本身|功能表、群組和命令|
|功能表|Menu[元素](../../extensibility/menus-element.md)、IDE、其他 vspackage|1到 *n* 個群組|0到 *n* 個群組|
|工具列|Menu[元素](../../extensibility/menus-element.md)、IDE、其他 vspackage|專案本身|0到 *n* 個群組|
|功能表項目|[按鈕元素](../../extensibility/buttons-element.md)、IDE、其他 vspackage|1到 *n* 個群組，專案本身|-0 到 *n* 個群組|
|按鈕|[按鈕元素](../../extensibility/buttons-element.md)、IDE、其他 vspackage|1到 *n* 個群組，專案本身||
|組合圖|[Combos 元素](../../extensibility/combos-element.md)、IDE、其他 vspackage|1到 *n* 個群組，專案本身||

### <a name="menu-command-and-group-placement"></a>功能表、命令和群組放置
功能表、群組或命令可以出現在 IDE 中的一個以上的位置。 若要讓專案出現在多個位置，則必須將它加入至區段中， `CommandPlacements` 做為 [CommandPlacement 元素](../../extensibility/commandplacement-element.md)。 任何功能表、群組或命令都可以新增為命令位置。 不過，工具列無法以這種方式定位，因為它們不能出現在多個內容相關的位置。

命令放置具有 `guid` 、 `id` 和 `priority` 屬性。 GUID 和識別碼必須符合放置的專案。 `priority`屬性會控制與其他專案有關的專案位置。 當 IDE 合併兩個或多個具有相同優先順序的專案時，它們的位置會是未定義的，因為 IDE 不保證每次建立封裝時都會以相同的順序讀取封裝資源。

如果功能表或群組出現在多個位置，則該功能表或群組的所有子系都會出現在每個實例中。

## <a name="command-visibility-and-context"></a>命令可見度和內容
安裝多個 Vspackage 時，功能表、功能表項目和工具列的這麼大量可能會造成 IDE 混亂。 若要避免這個問題，您可以使用 *可見度條件約束* 和命令旗標來控制個別 UI 元素的可見度。

### <a name="visibility-constraints"></a>可見度條件約束
可見度條件約束會設定為區段中的 [VisibilityItem 元素](../../extensibility/visibilityitem-element.md) `VisibilityConstraints` 。 可見度條件約束會定義可顯示目標專案的特定 UI 內容。 只有在其中一個已定義的內容為作用中時，才會顯示此區段中包含的功能表或命令。 如果未在此區段中參考功能表或命令，預設一律會顯示該功能表或命令。 本節不適用群組。

`VisibilityItem` 元素必須有三個屬性，如下所示 `guid` ： `id` 目標 UI 元素的和和 `context` 。 `context`屬性會指定何時會顯示目標專案，並接受任何有效的 UI 內容做為其值。 Visual Studio 的 UI 內容常數是類別的成員 <xref:Microsoft.VisualStudio.VSConstants> 。 每個 `VisibilityItem` 元素只能採用一個內容值。 若要套用第二個內容，請建立指向相同專案的第二個 `VisibilityItem` 元素，如下列範例所示。

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

### <a name="command-flags"></a>命令旗標
下列命令旗標可能會影響所套用的功能表和命令的可見度。

`AlwaysCreate` 即使沒有群組或按鈕，也會建立功能表。

有效期限： `Menu`

`CommandWellOnly` 如果命令未出現在最上層功能表，而您想要讓它可供其他 shell 自訂使用（例如，將它系結至索引鍵），請套用此旗標。 安裝 VSPackage 之後，使用者可以開啟 [ **選項** ] 對話方塊，然後在 [ **鍵盤環境** ] 類別下編輯命令位置，以自訂這些命令。 不會影響快捷方式功能表、工具列、功能表控制器或子功能表上的放置。

適用于： `Button` 、 `Combo`

`DefaultDisabled` 根據預設，如果未載入執行命令的 VSPackage，或尚未呼叫 QueryStatus 方法，則會停用此命令。

適用于： `Button` 、 `Combo`

`DefaultInvisible` 根據預設，如果未載入執行命令的 VSPackage 或尚未呼叫 QueryStatus 方法，則不會出現此命令。

應與旗標合併 `DynamicVisibility` 。

適用于： `Button` 、 `Combo` 、 `Menu`

`DynamicVisibility` 您可以使用 `QueryStatus` 方法或包含在區段中的內容 GUID 來變更命令的可見度 `VisibilityConstraints` 。

適用于出現在功能表上的命令，而不是工具列上的命令。 `OLECMDF_INVISIBLE`從方法傳回旗標時，可以停用或隱藏最上層工具列專案 `QueryStatus` 。

在功能表上，此旗標也會指出其成員隱藏時應自動隱藏。 此旗標通常會指派給子功能表，因為最上層功能表已經有此行為。

應與旗標合併 `DefaultInvisible` 。

適用于： `Button` 、 `Combo` 、 `Menu`

`NoShowOnMenuController` 如果有此旗標的命令位於功能表控制器上，則命令不會出現在下拉式清單中。

有效期限： `Button`

如需命令旗標的詳細資訊，請參閱 [CommandFlag 元素](../../extensibility/command-flag-element.md) 檔集。

#### <a name="general-requirements"></a>一般需求
您的命令必須先通過下列一系列的測試，才能顯示並啟用：

- 命令的位置正確。

- `DefaultInvisible`未設定旗標。

- 可以看見父功能表或工具列。

- 因為 [VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md) 區段中的內容專案，所以不會隱藏此命令。

- 執行介面的 VSPackage 程式碼會 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 顯示並啟用您的命令。 沒有介面程式碼攔截它，並對其採取動作。

- 當使用者按一下您的命令時，它會受限於 [路由演算法](../../extensibility/internals/command-routing-algorithm.md)中所述的程式。

## <a name="call-pre-defined-commands"></a>呼叫預先定義的命令
[UsedCommands 元素](../../extensibility/usedcommands-element.md)可讓 vspackage 存取其他 VSPACKAGE 或 IDE 所提供的命令。 若要這樣做，請建立 [UsedCommand 元素](../../extensibility/usedcommand-element.md) ，其中包含要使用之命令的 GUID 和識別碼。 這可確保 Visual Studio 會載入命令，即使它不是目前 Visual Studio 設定的一部分也一樣。 如需詳細資訊，請參閱 [UsedCommand 元素](../../extensibility/usedcommand-element.md)。

## <a name="interface-element-appearance"></a>介面元素外觀
選取和定位命令元素的考慮如下：

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供許多以不同方式顯示的 UI 元素，視位置而定。

- 使用旗標定義的 UI 專案 `DefaultInvisible` 將不會顯示在 IDE 中，除非它是透過方法的 VSPackage 執行所顯示 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> ，或與區段中的特定 UI 內容相關聯 `VisibilityConstraints` 。

- 即使是已成功放置的命令也可能不會顯示。 這是因為根據 VSPackage (或尚未) 執行的介面，IDE 會自動隱藏或顯示某些命令。 例如，某些組建介面的 VSPackage 執行會自動顯示組建相關的功能表項目。

- `CommandWellOnly`在 UI 專案的定義中套用旗標表示命令只能由自訂新增。

- 只有當 IDE 在設計檢視中顯示對話方塊時，才可以在特定的 UI 內容中使用命令。

- 若要使某些 UI 元素顯示在 IDE 中，您必須執行一或多個介面或撰寫一些程式碼。

## <a name="see-also"></a>另請參閱
- [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)

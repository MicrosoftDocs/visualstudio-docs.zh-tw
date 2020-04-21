---
title: VS包如何添加使用者介面元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d9cc3184009dd98e743064db1b8eb2abe6059d1
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649602"
---
# <a name="how-vspackages-add-user-interface-elements"></a>VS 套件如何新增使用者介面元素
VSPackage 可以通過 *.vsct*檔案將使用者介面 (UI) 元素(例如選單、工具列和工具視窗)添加到 Visual Studio。

您可以在[Visual Studio 用戶體驗指南](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)中找到 UI 元素的設計指南。

## <a name="the-visual-studio-command-table-architecture"></a>視覺化工作室命令表體系結構
如上所述,命令表體系結構支援上述體系結構原則。 命令表體系結構的抽象、數據結構和工具背後的原理如下:

- 有三種基本類型的項:功能表、命令和組。 功能表可以在 UI 中作為功能表、子功能表、工具列或工具視窗公開。 命令是用戶可以在 IDE 中執行的過程,它們可以作為功能表項、按鈕、清單框或其他控件公開。 組是功能表和命令的容器。

- 每個項都由描述項、相對於其他項的優先順序以及修改其行為的標誌的定義指定。

- 每個項都有一個描述項父項的位置。 專案可以有多個父項,以便它可以顯示在 UI 中的多個位置。

每個命令都必須有一個組作為其父級,即使它是該組中的唯一子級。 每個標準功能表還必須有一個父組。 工具列和工具視窗充當自己的父視窗。 組可以作為其父級主 Visual Studio 功能表欄,或任何功能表、工具列或工具視窗。

### <a name="how-items-are-defined"></a>如何定義項目
*.vsct*檔案以 XML 格式格式化。 它定義包的 UI 元素,並確定這些元素在 IDE 中的顯示位置。 包中的每個功能表、組或命令首先在`Symbols`節中分配 GUID 和 ID。 在 *.vsct*文件的其餘部分中,每個功能表、命令和組都通過其GUID和ID組合進行標識。 下面的範例顯示了 Visual `Symbols` Studio 包範本在範本中選擇**功能表命令**時生成的典型部分。

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

`Symbols`這個部份的頂層元素是[GuidSymbol 元素](../../extensibility/guidsymbol-element.md)。 `GuidSymbol`元素將名稱映射到IDE用於識別包及其元件部件的GUID。

> [!NOTE]
> GUID 由 Visual Studio 包範本自動生成。 您還可以透過按下「工具」功能表上**的「創建 GUID」** 來建立唯一**GUID。**

第一`GuidSymbol`個元素`guid<PackageName>Pkg`, 是套件本身的 GUID。 這是 Visual Studio 用於載入套件的 GUID。 通常,它沒有子元素。

按照慣例,功能表和命令被分組到第`GuidSymbol`二個元素下`guid<PackageName>CmdSet`, 並且位圖位於`GuidSymbol`第三`guidImages`個元素下。 您不必遵循此約定,但每個菜單、組、命令和位圖必須是`GuidSymbol`元素的子級。

在第二`GuidSymbol`個元素(表示包命令集)中,是`IDSymbol`多個 元素。 每個[IDSymbol 元素](../../extensibility/idsymbol-element.md)將名稱映射到數值,並可以表示作為命令集一部分的菜單、組或命令。 第`IDSymbol`三`GuidSymbol`個元素中的元素表示位圖,這些位圖可用作命令的圖示。 由於 GUID/ID 對在應用程式中必須是唯一的,`GuidSymbol`因此同一元素的兩個子級可能具有相同的值。

### <a name="menus-groups-and-commands"></a>選單、群組和指令
當功能表、組或命令具有 GUID 和 ID 時,可以將其添加到 IDE 中。 每個 UI 元素都必須具有以下內容:

- 與`guid`UI 元素下`GuidSymbol`定義的 元素的名稱匹配的屬性。

- 與`id`關聯`IDSymbol`元素的名稱匹配的屬性。

`guid`屬性`id`一起組成 UI 元素*的簽章*。

- 確定`priority`UI 元素在其父功能表或組中的位置的屬性。

- 具有`guid`指定父功能表或`id`組簽名的[父元素](../../extensibility/parent-element.md)和屬性。

#### <a name="menus"></a>功能表
每個選單都定義為`Menus`節中的[選單元素](../../extensibility/menu-element.md)。 選單必須具有`guid`與`id``priority`屬性`Parent`以及元素,以及以下附加屬性和子項:

- 指定`type`選單是否應作為功能表或工具列顯示在 IDE 中的屬性。

- 包含[ButtonText 元素](../../extensibility/buttontext-element.md)的[字串元素](../../extensibility/strings-element.md),該元素指定 IDE 中選單的標題,以及[命令名稱元素](../../extensibility/commandname-element.md),它指定**命令**視窗中用於造取選單的名稱。

- 可選標誌。 [CommandFlag 元素](../../extensibility/command-flag-element.md)可能會出現在功能表定義中,以更改其在IDE中的外觀或行為。

每個`Menu`元素都必須有一個組作為其父元素,除非它是可停靠的元素(如工具列)。 可停靠功能表是其自己的父功能表。 有關`type`屬性的功能表和值的詳細資訊,請參閱[菜單元素](../../extensibility/menu-element.md)文件。

下面的範例顯示顯示在「**工具**」功能表旁邊的 Visual Studio 選單欄上的選單。

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
組是在`Groups`*.vsct*檔部分中定義的項。 組只是容器。 它們不顯示在 IDE 中,除非是功能表上的分界線。 因此,[組元素](../../extensibility/group-element.md)僅由其簽名、優先順序和父元素定義。

組可以具有功能表、另一個組或本身作為父組。 但是,父級通常是功能表或工具列。 前面的示例中的功能表是`IDG_VS_MM_TOOLSADDINS`組的子功能表,該組是 Visual Studio 功能表欄的子級。 以下範例中的組是前面範例中功能表的子級。

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

因為它是功能表的一部分,因此此組通常包含命令。 但是,它還可以包含其他功能表。 這是子功能表的定義方式,如以下範例所示。

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
提供 IDE 的指令定義為[Button 元素](../../extensibility/button-element.md)或[組合元素](../../extensibility/combo-element.md)。 要顯示在功能表或工具列上,該命令必須具有組作為其父級。

##### <a name="buttons"></a>按鈕
按鈕在`Buttons`節中定義。 用戶按一下以執行單個命令的任何功能表項、按鈕或其他元素都被視爲按鈕。 某些按鈕類型還可以包括清單功能。 按鈕具有與功能表相同的必需和可選屬性,還可以具有[一個圖示元素](../../extensibility/icon-element.md),該元素指定表示 IDE 中按鈕的位圖的 GUID 和 ID。 有關按鈕及其屬性的詳細資訊,請參閱[Buttons 元素](../../extensibility/buttons-element.md)文檔。

以下範例中的按鈕是前面範例中的組的子級,並將作為該組父功能表上的菜單項顯示在IDE中。

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
組合在節中`Combos`定義。 每個`Combo`元素表示 IDE 中的下拉列表框。 清單框可能由使用者寫寫,也可能不由使用者寫寫,具體取決於組合`type`屬性的值。 組合具有與按鈕相同的元素和行為,也可以具有以下附加屬性:

- 指定`defaultWidth`圖元寬度的屬性。

- 指定`idCommandList`包含清單框中顯示的項目的清單的屬性。 命令清單必須在包含組合的同`GuidSymbol`一節點中聲明。

下面的範例定義組合元素。

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
與圖示一起顯示的命令必須包含一個`Icon`通過使用其 GUID 和 ID 引用位圖的元素。 每個點陣圖都定義`Bitmaps`為 節中的[位元圖元素](../../extensibility/bitmap-element.md)。 定義的唯一`Bitmap`必需屬性`guid`是`href`和 ,它指向源檔。 如果源檔是資源條,則還需要**使用 List**屬性來列出條帶中的可用圖像。 有關詳細資訊,請參閱[位圖元素](../../extensibility/bitmap-element.md)文檔。

### <a name="parenting"></a>育兒
以下規則控制項如何將另一個項調用為其父項。

|元素|在指令表的此部份定義|可以包含(作為父級,或通過放置在`CommandPlacements`節中,或兩者兼而有之)|可能包含(稱為父級)|
|-------------| - | - | - |
|群組|[群組元素](../../extensibility/groups-element.md),IDE,其他 VS 套件|選單、組、專案本身|選單、群組和指令|
|功能表|[選單元素](../../extensibility/menus-element.md),IDE,其他 VS 套件|1 到*n*群組|0 到*n*群組|
|工具列|[選單元素](../../extensibility/menus-element.md),IDE,其他 VS 套件|專案本身|0 到*n*群組|
|功能表項目|[按鈕元素](../../extensibility/buttons-element.md),IDE,其他 VS 套件|1 到*n*個組,專案本身|-0 到*n*群組|
|按鈕|[按鈕元素](../../extensibility/buttons-element.md),IDE,其他 VS 套件|1 到*n*個組,專案本身||
|組合圖|[組合元素](../../extensibility/combos-element.md),IDE,其他 VS 套件|1 到*n*個組,專案本身||

### <a name="menu-command-and-group-placement"></a>選單、指令和群組放置
選單、組或命令可以顯示在 IDE 中的多個位置。 要將項目顯示在多個位置,必須將`CommandPlacements`[指令放置元素](../../extensibility/commandplacement-element.md)。 任何功能表、組或命令都可以添加為命令放置。 但是,工具列不能以這種方式定位,因為它們不能出現在多個上下文相關位置。

命令位置具有`guid`和`id``priority`屬性。 GUID 和 ID 必須與定位項的 ID 匹配。 屬性`priority`控制項與其他項的放置。 當 IDE 合併具有相同優先順序的兩個或多個項時,它們的位置未定義,因為 IDE 不保證每次生成包時都按相同的順序讀取包資源。

如果功能表或組出現在多個位置,則該功能表或組的所有子級將顯示在每個實例中。

## <a name="command-visibility-and-context"></a>命令可見性和上下文
安裝多個 VS 包時,大量功能表、功能表項和工具列可能會使 IDE 變得雜亂無章。 為了避免此問題,可以使用*可見性約束*和命令標誌來控制各個 UI 元素的可見性。

### <a name="visibility-constraints"></a>可見性限制
可見性限制設定為`VisibilityConstraints`節中的[可見性項目元素](../../extensibility/visibilityitem-element.md)。 可見性約束定義目標項可見的特定 UI 上下文。 僅當其中一個定義的上下文處於活動狀態時,本節中包含的菜單或命令才可見。 如果此部分中未引用功能表或命令,則默認情況下始終可見。 本節不適用於組。

`VisibilityItem`元素必須具有三個屬性,如下所示:`guid``id`目標 UI`context`元素和和 。 該`context`屬性指定目標項何時可見,並將任何有效的 UI 上下文作為其值。 Visual Studio 的 UI 上下<xref:Microsoft.VisualStudio.VSConstants>文常量是 類的成員。 每個`VisibilityItem`元素只能獲取一個上下文值。 要應用第二個上下文,請創建`VisibilityItem`指向同一項的第二個元素,如以下範例所示。

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
以下命令標誌可能會影響它們應用於的功能表和命令的可見性。

`AlwaysCreate`即使功能表沒有組或按鈕,也會創建功能表。

合法:`Menu`

`CommandWellOnly`如果命令未顯示在頂級選單上,並且您希望使其可用於其他 shell 自訂(例如,將其綁定到鍵),請應用此標誌。 安裝 VSPackage 後,使用者可以透過開啟 **「選項」** 對話框,然後在 **「鍵盤環境**」類別下編輯命令放置來自定義這些命令。 不影響在快捷功能表、工具列、功能表控制器或子菜單上放置。

適用於: `Button`, ,`Combo`

`DefaultDisabled`默認情況下,如果未載入實現該命令的 VSPackage 或未調用 QueryStatus 方法,則禁用該命令。

適用於: `Button`, ,`Combo`

`DefaultInvisible`默認情況下,如果未載入實現該命令的 VSPackage 或未調用 QueryStatus 方法,則該命令不可見。

應與`DynamicVisibility`標誌組合。

適用於: `Button` `Combo`、 、 、 、 、 、 、 、 、 、 、 、 、`Menu`

`DynamicVisibility`可以使用`QueryStatus``VisibilityConstraints`本節中包含的方法或上下文 GUID 更改命令的可見性。

應用於顯示在功能表上的命令,不適用於工具列上。 當從`OLECMDF_INVISIBLE``QueryStatus`方法返回標誌時,可以禁用頂級工具列項,但不能隱藏。

在功能表上,此標誌還指示在其成員隱藏時應自動隱藏該標誌。 此標誌通常分配給子功能表,因為頂級功能表已具有此行為。

應與`DefaultInvisible`標誌組合。

適用於: `Button` `Combo`、 、 、 、 、 、 、 、 、 、 、 、 、`Menu`

`NoShowOnMenuController`如果具有此標誌的命令位於功能表控制器上,則該命令不會顯示在下拉清單中。

合法:`Button`

有關命令標誌的詳細資訊,請參閱[CommandFlag 元素](../../extensibility/command-flag-element.md)文件。

#### <a name="general-requirements"></a>一般需求
在顯示與啟用指令之前,命令必須透過以下一系列測試:

- 該命令的位置正確。

- 未`DefaultInvisible`設置標誌。

- 父功能表或工具列可見。

- 由於[「可見性約束」元素](../../extensibility/visibilityconstraints-element.md)部分中的上下文條目,該命令不不可見。

- 實現介面並啟用命令的<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>VSPackage 代碼。 沒有介面代碼截獲它並對其進行操作。

- 當用戶單擊命令時,它將受到[路由演演演算法](../../extensibility/internals/command-routing-algorithm.md)中概述的過程的約束。

## <a name="call-pre-defined-commands"></a>呼叫預定義的指令
[使用命令元素](../../extensibility/usedcommands-element.md)使 VS 套件能夠存取其他 VS 套件或 IDE 提供的命令。 為此,請創建一個[UseCommand 元素](../../extensibility/usedcommand-element.md),該元素具有要使用的命令的 GUID 和 ID。 這可確保可視化工作室將載入該命令,即使該命令不是當前 Visual Studio 配置的一部分。 有關詳細資訊,請參閱[使用指令元素](../../extensibility/usedcommand-element.md)。

## <a name="interface-element-appearance"></a>介面元素外觀
選擇與定位指令元素的注意事項如下:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供了許多 UI 元素,這些元素的顯示方式因位置而異。

- 使用`DefaultInvisible`標誌定義的 UI 元素將不會顯示在 IDE<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>中,除非它由方法的 VSPackage 實現顯示,或與`VisibilityConstraints`節中的特定 UI 上下文相關聯。

- 即使無法顯示成功定位的命令也可能不會顯示。 這是因為 IDE 會自動隱藏或顯示某些命令,具體取決於 VSPackage 已實現(或尚未)實現的介面。 例如,VSPackage 對某些生成介面的實現會導致自動顯示與生成相關的功能表項。

- 在`CommandWellOnly`UI 元素的定義中應用標誌意味著只能透過自訂來添加該命令。

- 命令可能僅在某些 UI 上下文中可用,例如,僅當 IDE 位於設計檢視中時顯示對話方塊時才可用。

- 要導致某些 UI 元素顯示在 IDE 中,必須實現一個或多個介面或編寫一些代碼。

## <a name="see-also"></a>另請參閱
- [延伸選單與指令](../../extensibility/extending-menus-and-commands.md)

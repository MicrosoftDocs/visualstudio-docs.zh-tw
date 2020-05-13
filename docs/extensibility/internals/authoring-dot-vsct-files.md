---
title: 創作。Vsct 檔案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709989"
---
# <a name="author-vsct-files"></a>作者 .vsct 檔案
本文件展示如何創作 *.vsct*檔,將功能表項、工具列和其他使用者介面 (UI) 元素添加到 Visual Studio 整合式開發環境 (IDE)。 將 UI 元素添加到尚未具有 *.vsct*檔案的 Visual Studio 套件 (VSPackage) 時,請使用以下步驟。

 對於新項目,我們建議您使用 Visual Studio 包樣本,因為它會生成一個 *.vsct*檔案,該檔根據您的選擇,該檔已經具有功能表命令、工具視窗或自定義編輯器所需的元素。 您可以修改此 *.vsct*檔案以滿足 VSPackage 的要求。 有關如何修改 *.vsct*檔的詳細資訊,請參閱[擴展功能表和命令](../../extensibility/extending-menus-and-commands.md)中的範例。

## <a name="author-the-file"></a>創作檔案
 在這些階段中編寫一個 *.vsct*檔:為檔和資源創建結構,聲明 UI 元素,將 UI 元素放入 IDE 中,並添加任何專用行為。

### <a name="file-structure"></a>檔案結構
 *.vsct*檔案的基本結構是命令[表](../../extensibility/commandtable-element.md)根元素,其中包含[命令](../../extensibility/commands-element.md)元素和[Symbols](../../extensibility/symbols-element.md)元素。

#### <a name="to-create-the-file-structure"></a>建立檔案結構

1. 按照[操作中的步驟:創建 .vsct 檔](../../extensibility/internals/how-to-create-a-dot-vsct-file.md),將 *.vsct*檔添加到專案中。

2. 新增`CommandTable`元素的命名空間,例如以下範例的範例 :

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. 在`CommandTable`元素中,`Commands`添加一個元素來承載所有自定義功能表、工具列、命令組和命令。 因此,自定義 UI 元素可以載`Commands`入, 該元素`Package`的屬性必須設置為包的名稱。

     元素`Commands`之後,添加一個`Symbols`元素來定義包的 GUID,以及 UI 元素的名稱和命令 ID。

### <a name="include-visual-studio-resources"></a>包括視覺化工作室資源
 使用[Extern](../../extensibility/extern-element.md)元素存取定義 Visual Studio 命令的檔案以及將 UI 元素放入 IDE 所需的選單。 如果要使用包外定義的命令,請使用[「已使用命令」](../../extensibility/usedcommands-element.md)元素通知 Visual Studio。

#### <a name="to-include-visual-studio-resources"></a>包括視覺工作室資源

1. 在`CommandTable`元素的頂部,為每個要引用的外部`Extern`檔 添加一個元素`href`,並將 屬性設置為檔的名稱。 您可以參考以下標頭檔案來造訪 Visual Studio 資源:

   - *Stdidcmd.h*: 為 Visual Studio 公開的所有命令定義 ID。

   - *Vsshlids.h*: 包含可視化工作室功能表的命令 ID。

2. 如果包調用由 Visual Studio 或其他包定義的任何命令`UsedCommands``Commands`,請在 元素之後添加元素。 對於不屬於包的每個命令,使用[UsedCommand](../../extensibility/usedcommand-element.md)元素填充此元素。 將`UsedCommand`元素`guid`的`id`和屬性設置為要呼叫的命令的 GUID 和 ID 值。

   有關如何查找 Visual Studio 命令的 GUID 和 IT 的詳細資訊,請參閱[Visual Studio 命令的 GUID 和 IT。](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md) 要從其他包呼叫命令,請使用這些包 *.vsct*檔案中定義的 GUID 和命令 ID。

### <a name="declare-ui-elements"></a>宣告 UI 元素
 聲明 *.vsct*檔`Symbols`部分中的所有新 UI 元素。

#### <a name="to-declare-ui-elements"></a>宣告 UI 元素

1. 在元素`Symbols`中,添加三個[GuidSymbol](../../extensibility/guidsymbol-element.md)元素。 每個`GuidSymbol`元素都有`name`一個屬性`value`和一個屬性。 設置屬性`name`,以便它反映元素的用途。 該`value`屬性採用 GUID。 ( 要產生 GUID,請在 **'工具'** 選單上,選擇 **'建立 GUID" ,** 然後選擇**註冊表格式**。

     第一`GuidSymbol`個元素表示包,通常沒有子元素。 第二`GuidSymbol`個元素表示命令集,並將包含定義功能表、組和命令的所有符號。 第三`GuidSymbol`個元素表示圖像存儲,並包含命令的所有圖示的符號。 如果沒有使用圖示的命令,則可以省略第三`GuidSymbol`個元素。

2. 在`GuidSymbol`表示命令集的元素中,添加一個或多個[IDSymbol](../../extensibility/idsymbol-element.md)元素。 其中每個表示要添加到 UI 的功能表、工具列、組或命令。

     對於每個`IDSymbol`元素,將`name`屬性設置為用於引用相應功能表、組或命令的名稱,然後`value`將 元素設置為表示其命令 ID 的十六進位數位。 沒有兩`IDSymbol`個具有相同父元素的元素可以具有相同的值。

3. 如果任何 UI 元素需要圖示,請`IDSymbol`為每個圖示添加一個`GuidSymbol`元素到 表示圖像存儲的元素。

### <a name="put-ui-elements-in-the-ide"></a>將 UI 元素放入 IDE
 [選單](../../extensibility/menus-element.md)、[組](../../extensibility/groups-element.md)和[按鈕](../../extensibility/buttons-element.md)元素包含包中定義的所有功能表、組和命令的定義。 通過使用作為 UI 元素定義的一部分[的父](../../extensibility/parent-element.md)元素,或者使用在其他地方定義的[Command安置](../../extensibility/commandplacement-element.md)元素,將這些功能表、組和命令放在 IDE 中。

 每個`Menu``Group`,`Button`和`guid`元素都有一`id`個 屬性和一個屬性。 `guid`始終將屬性設置為匹配表示命令集`GuidSymbol`的元素的名稱,`id`並將該屬性設置為`IDSymbol``Symbols`表示 節中功能表、組或命令的元素的名稱。

#### <a name="to-define-ui-elements"></a>定義 UI 元素

1. 如果要定義任何新功能表、子功能表、快捷功能表或工具列,則向`Menus``Commands`元素添加元素。 然後,要創建每個功能表,向`Menus`元素添加一個[功能表](../../extensibility/menu-element.md)元素。

    設置`Menu``guid`元素`id`的和 屬性,`type`然後將 屬性設置為所需的功能表類型。 還可以設置屬性`priority`以在父組中建立功能表的相對位置。

   > [!NOTE]
   > 該`priority`屬性不適用於工具列和上下文菜單。

2. 可視化工作室 IDE 中的所有命令必須由命令組託管,命令組是功能表和工具列的直接子級。 如果要向 IDE 添加新功能表或工具列,這些功能表或工具列必須包含新的命令組。 您還可以將命令組添加到現有功能表和工具列中,以便可以直觀地對命令進行分組。

    新增新命令組時,必須首先創建一個`Groups`元素,然後為每個命令組添加一個[組](../../extensibility/group-element.md)元素。

    設置每個`guid``id``Group`元素的 和 屬性`priority`,然後設置 屬性以在父功能表上建立組的相對位置。 關於詳細資訊,請參閱[建立可重用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。

3. 如果要向 IDE 添加新命令,則`Buttons``Commands`向元素 添加元素。 然後,對於每個命令,向`Buttons`元素添加一個[Button](../../extensibility/button-element.md)元素。

   1. 設置每個`guid``id``Button`元素的和 屬性,`type`然後將 屬性設置為所需的按鈕類型。 還可以設置屬性`priority`以在父組中建立命令的相對位置。

       > [!NOTE]
       > 用於`type="button"`工具列上的標準功能表命令和按鈕。

   2. 在元素`Button`中,添加包含[ButtonText](../../extensibility/buttontext-element.md)元素和[指令名稱](../../extensibility/commandname-element.md)元素的[字串](../../extensibility/strings-element.md)元素。 該`ButtonText`元素提供功能表項的文本標籤或工具列按鈕的工具提示。 該`CommandName`元素提供要在命令井中使用的命令的名稱。

   3. 如果命令將具有圖示,請在`Button`元素中創建一個[Icon](../../extensibility/icon-element.md)`guid`元素`id`,並將其和`Bitmap`屬性設置為 該圖示的元素。

       > [!NOTE]
       > 工具列按鈕必須具有圖示。

   有關詳細資訊,請參閱[選單指令與 OleMenu 命令](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)。

4. 如果任何命令需要圖示,請向`Commands`元素添加[位元圖](../../extensibility/bitmaps-element.md)元素。 然後,對於每個圖示,向`Bitmaps`元素添加[位圖](../../extensibility/bitmap-element.md)元素。 這是指定點陣圖資源的位置的位置。 有關詳細資訊,請參閱[向選單指令加入圖示](../../extensibility/adding-icons-to-menu-commands.md)。

   您可以依賴父級結構正確放置大多數功能表、組和命令。 對於非常大的命令集,或者當菜單、組或命令必須出現在多個位置時,我們建議您指定命令放置。

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>依靠父子關係在 IDE 中放置 UI 元素

1. 對於典型的父級,請在每個`Parent``Menu``Group`中創建一個`Command`元素,並在包中定義的元素。

    `Parent`元素的目標是包含功能表、組或命令的功能表或組。

   1. 將`guid`屬性設置為定義命令`GuidSymbol`集的元素的名稱。 如果目標元素不是包的一部分,請使用該命令集的 guid,如相應的 *.vsct*檔中定義的那樣。

   2. 將`id`屬性設置為匹配目標功能`id`表 或組的屬性。 有關 Visual Studio 公開的功能表和組的清單,請參閱 Visual Studio 功能表的[GUID 和 IT](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)或[Visual Studio 工具列的 GUID 和 IT。](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

   如果 ID 中要放置大量 UI 元素,或者元素應出現在多個位置,請將其放置在[「命令放置」](../../extensibility/commandplacements-element.md)元素中,如以下步驟所示。

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>使用命令放置在 IDE 中放置 UI 元素

1. 在 `Commands` 元素後方加入 `CommandPlacements` 元素。

2. 在`CommandPlacements`元素中,為`CommandPlacement`每個功能表、組或要放置的命令添加一個元素。

    每個`CommandPlacement`元素`Parent`或 元素在一個 IDE 位置放置一個功能表、組或命令。 UI 元素只能有一個父元素,但它可以有多個命令放置。 要將 UI 元素放置在多個位置,`CommandPlacement`為每個 位置添加一個元素。

3. 將每個`guid``id``CommandPlacement`元素的 和 屬性設置為宿主功能表或組,就像`Parent`對元素一樣。 還可以設置屬性`priority`以建立 UI 元素的相對位置。

   您可以通過父項和命令放置混合放置。 但是,對於非常大的命令集,我們建議您僅使用命令放置。

### <a name="add-specialized-behaviors"></a>新增專門行為
 可以使用[CommandFlag](../../extensibility/command-flag-element.md)元素修改功能表和命令的行為,例如,更改其外觀和可見性。 您還可以使用[可見性約束](../../extensibility/visibilityconstraints-element.md)元素影響命令何時可見,或者通過使用[KeyBindings](../../extensibility/keybindings-element.md)元素添加鍵盤快速鍵。 某些類型的功能表和命令已經內置了專門行為。

#### <a name="to-add-specialized-behaviors"></a>新增專門行為

1. 要使 UI 元素僅在某些 UI 上下文中可見(例如,載入解決方案時)請使用可見性約束。

   1. 在 `Commands` 元素後方加入 `VisibilityConstraints` 元素。

   2. 對於要約束的每個 UI 項,添加[可見性專案](../../extensibility/visibilityitem-element.md)元素。

   3. 對於每個`VisibilityItem`元素,`guid`將`id`和屬性設置為菜單、組或命令,然後`context`將 屬性設置為所需的 UI<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>上下文(如類中定義)。

2. 要在代碼中設定 UI 的可見性或可用性,請使用以下命令標誌中的一個或多個:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   有關詳細資訊,請參閱[CommandFlag](../../extensibility/command-flag-element.md)元素。

3. 要更改元素的顯示方式或動態更改其外觀,請使用以下一個或多個命令標誌:

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

   有關詳細資訊,請參閱[CommandFlag](../../extensibility/command-flag-element.md)元素。

4. 要更改元素在接收命令時的反應方式,請使用以下一個或多個命令標誌:

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

   有關詳細資訊,請參閱[CommandFlag](../../extensibility/command-flag-element.md)元素。

5. 要將依賴於功能表的鍵盤快捷鍵附加到功能表或功能表上的專案,請在菜單或功能表項`ButtonText`的元素中添加一個 ampand 字元 (&)。 當父選單打開時,放大器後面的字元是活動鍵盤快速鍵。

6. 要將獨立於功能表的鍵盤快捷鍵附加到命令,請使用[KeyBindings](../../extensibility/keybindings-element.md)元素。 有關詳細資訊,請參閱[鍵綁定](../../extensibility/keybinding-element.md)元素。

7. 要本地化選單文字,請使用元素`LocCanonicalName`。 有關詳細資訊,請參閱[字串](../../extensibility/strings-element.md)元素。

   某些功能表和按鈕類型包括專門行為。 下面的清單描述了一些專用功能表和按鈕類型。 有關其他類型,請參閱`types`[菜單](../../extensibility/menu-element.md)、[按鈕](../../extensibility/button-element.md)和[組合](../../extensibility/combo-element.md)元素中的屬性說明。

   - 組合框:組合框是可在工具列上使用的下拉清單。 要將組合框添加到 UI,請`Commands`在元素中創建[Combos](../../extensibility/combos-element.md)元素。 然後向`Combos`元素添加要`Combo`添加 的每個組合框的元素。 `Combo`元素具有與`Button`元素相同的屬性和子級,並且`DefaultWidth``idCommandList`具有和 屬性。 屬性`DefaultWidth`以像素為單位設定寬度`idCommandList`, 該屬性指向用於填充組合框的命令 ID。

   - 功能表控制器:功能表控制器是一個按鈕,旁邊有一個箭頭。 按下箭頭將打開一個清單。 要向 UI 新增選單控制器,`Menu`請建立一個`type`元素, 並`MenuController`根據`MenuControllerLatched`所需的行為, 將設定為或 。 要填充功能表控制器,將其設置為`Group`元素的父級。 選單控制器將在其下拉清單中顯示該組的所有子級。

## <a name="see-also"></a>另請參閱
- [延伸選單與指令](../../extensibility/extending-menus-and-commands.md)
- [視覺化工作室指令表 (.vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)

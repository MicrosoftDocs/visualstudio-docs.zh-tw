---
title: 動態加入功能表項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7901cf19b112b1a9d87dcae5bce594f5cc431d78
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633346"
---
# <a name="dynamically-add-menu-items"></a>動態加入功能表項目
您可以藉由在 Visual Studio 命令資料表（ *. .vsct*）檔案中的預留位置按鈕定義上指定 [`DynamicItemStart` 命令] 旗標，然後定義（在程式碼中）顯示和處理命令的功能表項目數目，在執行時間加入功能表項目。 載入 VSPackage 時，會以動態功能表項目取代預留位置。

 Visual Studio 使用 [**最近使用**的（MRU）] 清單中的動態清單（顯示最近開啟的檔案名稱）和 [ **Windows**清單]，以顯示目前開啟的視窗名稱。   命令定義上的 `DynamicItemStart` 旗標會指定命令為預留位置，直到 VSPackage 開啟為止。 開啟 VSPackage 時，會將預留位置取代為在執行時間建立並加入至動態清單的0個或多個命令。 在開啟 VSPackage 之前，您可能無法看到動態清單出現在功能表上的位置。  若要填入動態清單，Visual Studio 會要求 VSPackage 尋找識別碼的命令，其第一個字元與預留位置的識別碼相同。 當 Visual Studio 找到相符的命令時，它會將命令的名稱新增至動態清單。 然後，它會遞增識別碼，並尋找另一個符合的命令來新增至動態清單，直到沒有其他動態命令為止。

 本逐步解說示範如何使用**方案總管**工具列上的命令，在 Visual Studio 方案中設定啟始專案。 它會使用功能表控制器，其具有作用中方案中專案的動態下拉式清單。 若要在未開啟任何解決方案或開啟的方案只有一個專案時，讓此命令不出現，則只有在方案有多個專案時，才會載入 VSPackage。

 如需有關 *.vsct*檔的詳細資訊，請參閱[Visual Studio 命令資料表（. .vsct）](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔案。

## <a name="create-an-extension-with-a-menu-command"></a>使用功能表命令建立擴充功能

1. 建立名為 `DynamicMenuItems` 的 VSIX 專案。

2. 當專案開啟時，請新增自訂命令專案範本，並將其命名為**DynamicMenu**。 如需詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能。

## <a name="setting-up-the-elements-in-the-vsct-file"></a>設定 *.vsct*檔案中的元素
 若要在工具列上建立具有動態功能表項目的功能表控制器，請指定下列元素：

- 兩個命令群組，一個包含功能表控制器，另一個包含下拉式清單中的功能表項目

- @No__t_0 類型的一個 menu 元素

- 兩個按鈕，一個做為功能表項目的預留位置，另一個則會提供工具列上的圖示和工具提示。

1. 在*DynamicMenuPackage. .vsct*中，定義命令識別碼。 移至 [符號] 區段，並取代**guidDynamicMenuPackageCmdSet** GuidSymbol 區塊中的 IDSymbol 元素。 您必須為兩個群組、功能表控制器、預留位置命令和錨點命令定義 IDSymbol 元素。

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. 在 [群組] 區段中，刪除現有的群組，並新增您剛定義的兩個群組：

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     新增 MenuController。 設定 DynamicVisibility 命令旗標，因為它不一定是可見的。 ButtonText 不會顯示。

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. 加入兩個按鈕，一個做為動態功能表項目的預留位置，另一個做為 MenuController 的錨點。

     預留位置按鈕的父系是**MyMenuControllerGroup**。 將 [DynamicItemStart]、[DynamicVisibility] 和 [TextChanges] 命令旗標新增至 [預留位置] 按鈕。 ButtonText 不會顯示。

     錨點按鈕會保存圖示和工具提示文字。 錨點按鈕的父系也是**MyMenuControllerGroup**。 您可以新增 NoShowOnMenuController 命令旗標，以確定按鈕實際上不會出現在 [功能表控制器] 下拉式清單中，而 [FixMenuController 命令] 旗標則會將它設為永久錨點。

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. 將圖示新增至專案（在*Resources*資料夾中），然後在 *.vsct*檔案中新增其參考。 在此逐步解說中，我們會使用專案範本中包含的箭號圖示。

5. 在 [符號] 區段前面的 [命令] 區段外新增 VisibilityConstraints 區段。 （如果您將它加入符號之後，可能會收到警告）。此區段可確保只有在載入具有多個專案的方案時，才會顯示功能表控制器。

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>執行動態功能表命令
 您會建立繼承自 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 的動態功能表命令類別。 在此實作為中，此函式會指定要用於比對命令的述詞。 您必須覆寫 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> 方法，才能使用此述詞來設定 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> 屬性，以識別要叫用的命令。

1. 建立名為C# *DynamicItemMenuCommand.cs*的新類別檔案，並新增一個名為**DynamicItemMenuCommand**的類別，它會繼承自 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>：

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. 新增下列 using 指示詞：

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. 新增私用欄位來儲存 match 述詞：

    ```csharp
    private Predicate<int> matches;

    ```

4. 加入繼承自 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 的函式的函式，並指定命令處理常式和 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 處理常式。 加入述詞以符合命令：

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. 覆寫 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> 方法，使其呼叫符合述詞，並設定 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> 屬性：

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>新增命令
 DynamicMenu 的函式是用來設定功能表命令的位置，包括動態功能表和功能表項目。

1. 在*DynamicMenuPackage.cs*中，新增命令集的 GUID 和命令識別碼：

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. 在*DynamicMenu.cs*檔案中，新增下列 using 指示詞：

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. 在 `DynamicMenu` 類別中，新增私用欄位**dte2**。

    ```csharp
    private DTE2 dte2;
    ```

4. 新增私用 rootItemId 欄位：

    ```csharp
    private int rootItemId = 0;
    ```

5. 在 DynamicMenu 的函式中，新增功能表命令。 在下一節中，我們將定義命令處理常式、`BeforeQueryStatus` 事件處理常式，以及 match 述詞。

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>執行處理常式
 若要在功能表控制器上執行動態功能表項目，您必須在按一下動態專案時處理此命令。 您也必須執行邏輯來設定功能表項目的狀態。 將處理常式新增至 `DynamicMenu` 類別。

1. 若要執行 [**設定啟始專案**] 命令，請新增**OnInvokedDynamicItem**事件處理常式。 它會尋找名稱與已叫用的命令文字相同的專案，並藉由在 <xref:EnvDTE.SolutionBuild.StartupProjects%2A> 屬性中設定其絕對路徑，將它設定為啟始專案。

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. 新增 `OnBeforeQueryStatusDynamicItem` 事件處理常式。 這是在 `QueryStatus` 事件之前呼叫的處理常式。 它會判斷功能表項目是否為「實際」專案（也就是不是預留位置專案），以及專案是否已經核取（表示專案已經設定為啟始專案）。

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>執行命令 ID match 述詞

現在，請執行 match 述詞。 我們需要判斷兩件事：首先，命令識別碼是有效的（它是否大於或等於宣告的命令識別碼），第二個是指定可能的專案（它小於方案中的專案數）。

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>將 VSPackage 設定為只有在方案有多個專案時才會載入
 因為使用中的方案有多個專案，所以 [**設定啟始專案**] 命令沒有意義，因此您可以將 VSPackage 設定為只在該情況下自動載入。 您可以使用 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 搭配 UI 內容 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>。 在*DynamicMenuPackage.cs*檔案中，將下列屬性新增至 DynamicMenuPackage 類別：

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>測試設定啟始專案命令
 現在您可以測試您的程式碼。

1. 建置此專案並開始偵錯。 應該會出現實驗實例。

2. 在實驗實例中，開啟有一個以上專案的方案。

     您應該會在 [**方案總管**] 工具列上看到箭號圖示。 當您展開它時，應該會出現代表方案中不同專案的功能表項目。

3. 當您檢查其中一個專案時，它會變成啟始專案。

4. 當您關閉解決方案，或開啟只有一個專案的方案時，工具列圖示應該會消失。

## <a name="see-also"></a>請參閱
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
- [Vspackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)

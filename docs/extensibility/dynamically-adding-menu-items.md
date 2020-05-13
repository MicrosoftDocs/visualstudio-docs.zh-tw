---
title: 動態新增選單項目 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4387c1930e09e49c0ec5c36ccedc1bb83dc273f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712059"
---
# <a name="dynamically-add-menu-items"></a>動態新增選單項目
通過在 Visual Studio`DynamicItemStart`命令表 *(.vsct)* 檔中的占位符按鈕定義上指定命令標誌,然後定義(以代碼形式)顯示和處理命令的功能表項數,可以在執行時添加功能表項。 載入 VSPackage 時,占位符將替換為動態功能表項。

 Visual Studio 使用 **「最近使用**(MRU)」清單中的動態清單(顯示最近打開的文件的名稱)和顯示目前打開的視窗名稱的**Windows**清單。   命令`DynamicItemStart`定義上的標誌指定命令是佔位符,直到打開 VSPackage。 打開 VSPackage 時,占位符將被在執行時創建並添加到動態清單中的 0 個或多個命令替換。 在開啟 VSPackage 之前,您可能無法看到顯示動態清單的選單上的位置。  要填充動態清單,Visual Studio 要求 VSPackage 尋找具有 ID 的命令,該命令的第一個字元與占位符的 ID 相同。 當 Visual Studio 找到匹配命令時,它將該命令的名稱添加到動態清單中。 然後,它增加 ID 並查找另一個匹配的命令添加到動態清單中,直到沒有更多的動態命令。

 本演練展示如何使用**解決方案資源管理員**工具列上的命令在 Visual Studio 解決方案中設置啟動專案。 它使用功能表控制器,該功能表控制器具有活動解決方案中專案的動態下拉清單。 為了防止在未打開解決方案或打開的解決方案只有一個專案時出現此命令,僅當解決方案有多個專案時才載入 VSPackage。

 有關 *.vsct*檔案的詳細資訊,請參閱[可視化工作室命令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

## <a name="create-an-extension-with-a-menu-command"></a>使用選單指令建立延伸

1. 創建名為的`DynamicMenuItems`VSIX 專案。

2. 開啟項目時,新增自訂指令樣本並將其命名為**DynamicMenu**。 關於詳細資訊,請參閱[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

## <a name="setting-up-the-elements-in-the-vsct-file"></a>設定 *.vsct*檔案中的元素
 要建立工具列上具有動態選單的選單控制器,請指定以下元素:

- 兩個指令組,包含選單控制器,另一個包含下拉選單項目

- 類型的選單元素`MenuController`

- 兩個按鈕,一個充當菜單項的占位符,另一個提供工具列上的圖示和工具提示。

1. 在*動態功能表包.vsct 中*,定義命令指示。 跳到「符號」部分並取代**guidDynamicMenu 包裝 CmdSet** GuidSymbol 塊中的 IDSymbol 元素。 您需要為兩個組(選單控制器、占位符命令和錨點命令)定義 IDSymbol 元素。

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

2. 在「群組」部分中,刪除現有組並添加剛剛定義的兩個組:

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

     添加功能表控制器。 設置動態可見性命令標誌,因為它並不總是可見的。 不顯示按鈕文本。

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

3. 添加兩個按鈕,一個作為動態功能表項的占位符,一個作為功能表控制器的錨點。

     占位符按鈕的父級是**MyMenuControllerGroup。** 將動態項目啟動、動態可見性和文本更改命令標誌添加到占位符按鈕。 不顯示按鈕文本。

     錨點按鈕包含圖示和工具提示文本。 錨點按鈕的父級也是**MyMenu 控制器群組**。 添加 NoShowOnMenu 控制器命令標誌,以確保按鈕實際上不會出現在功能表控制器下拉清單中,以及固定功能表控制器命令標誌使其成為永久錨點。

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

4. 新增圖示(在 *"資源'* 資料夾中),然後在 *.vsct*檔中添加對專案的引用。 在本演練中,我們使用專案範本中包含的箭頭圖示。

5. 在「符號」部分之前「命令」部分之外添加可見性約束部分。 (如果在符號之後添加,您可能會收到警告。此部分確保功能表控制器僅在載入具有多個專案的解決方案時才出現。

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>實現動態選單指令
 創建從<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>繼承的動態功能表命令類。 在此實現中,構造函數指定用於匹配命令的謂詞。 必須重寫<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>方法以使用此謂詞來<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>設置 屬性,該屬性標識要調用的命令。

1. 建立名為*DynamicItemMenuCommand.cs*的新 C# 類別檔案,並加入一個名為**DynamicItemMenu 命令**的<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>類別,該檔從繼承於 :

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. 加入以下 using 指示詞：

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. 新增專用欄位以儲存符合謂詞:

    ```csharp
    private Predicate<int> matches;

    ```

4. 添加從建構函數繼承的<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>建構函數,並指定命令處理程式和<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>處理程式。 新增用於符合命令的謂詞:

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

5. 重寫<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>方法,以便呼叫匹配謂詞並<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>設定 屬性:

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
 動態功能表建構函數是設置功能表命令的位置,包括動態功能表和功能表項。

1. 在*DynamicMenuPackage.cs*中,加入命令集的 GUID 與指令 ID:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. 在*DynamicMenu.cs*檔案中,新增以下使用指令:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. 在`DynamicMenu`類別中,新增專用欄位**dte2**。

    ```csharp
    private DTE2 dte2;
    ```

4. 新增專用根項目 Id 欄位:

    ```csharp
    private int rootItemId = 0;
    ```

5. 在動態功能表建構函數中,添加功能表命令。 在下一節中,我們將定義命令處理程式、`BeforeQueryStatus`事件處理程式和匹配謂詞。

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

## <a name="implement-the-handlers"></a>執行處理程式
 要在功能表控制器上實現動態功能表項,必須在單擊動態項時處理該命令。 還必須實現設置功能表項狀態的邏輯。 將處理程式新增到類別`DynamicMenu`。

1. 要實現 **「設定啟動專案」** 指令,添加**OnIn 被呼叫的 DynamicItem**事件處理程式。 它查找名稱與已調用的命令的文本相同的專案,並通過在<xref:EnvDTE.SolutionBuild.StartupProjects%2A>屬性中設置其絕對路徑將其設置為啟動專案。

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

2. 添加事件`OnBeforeQueryStatusDynamicItem`處理程式。 這是在事件之前調用的`QueryStatus`處理程式。 它確定功能表項是否為「實際」項,即不是占位符項,以及該專案是否已選中(這意味著專案已設置為啟動專案)。

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

## <a name="implement-the-command-id-match-predicate"></a>實作指令 ID 符合謂詞

現在實現匹配謂詞。 我們需要確定兩件事:第一,命令 ID 是否有效(它大於或等於聲明的命令 ID),第二,它是否指定了可能的專案(它小於解決方案中的項目數)。

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>將 VS 套件設定為僅在解決方案具有多個項目時載入
 由於 **「設定啟動專案」** 命令沒有意義,除非活動解決方案有多個專案,因此可以將 VSPackage 設置為僅在該情況下自動載入。 與<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>UI<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>上下文 一起使用。 在*DynamicMenuPackage.cs*檔案中向 DynamicMenu 套件類別新增以下屬性:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>測試集啟動項目指令
 現在,您可以測試代碼。

1. 建置此專案並開始偵錯。 應出現實驗實例。

2. 在實驗實例中,打開一個有多個項目的解決方案。

     您應該在**解決方案資源管理器**工具列上看到箭頭圖示。 展開它時,應顯示表示解決方案中不同專案的功能表項。

3. 當您檢查其中一個專案時,它將成為啟動專案。

4. 當您關閉解決方案或打開只有一個專案的解決方案時,工具列圖示應消失。

## <a name="see-also"></a>另請參閱
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
- [VS 套件如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)

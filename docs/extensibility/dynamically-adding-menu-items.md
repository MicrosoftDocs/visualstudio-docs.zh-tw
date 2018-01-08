---
title: "以動態方式加入功能表項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1eaa8cc41e7b27d509e68d6785c34a9ae214ffd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="dynamically-adding-menu-items"></a>以動態方式加入功能表項目
您可以在執行階段將功能表項目，藉由指定`DynamicItemStart`命令預留位置按鈕定義中，在 Visual Studio 命令表 (.vsct) 檔案中，旗標，然後定義 （在程式碼） 的數目功能表項目以顯示和處理命令。 當載入 VSPackage 時，動態功能表項目取代預留位置。  
  
 Visual Studio 會使用中的動態清單**最近使用**(MRU) 清單，顯示最近開啟的文件的名稱，而**Windows**清單中顯示的 windows 名稱屬於目前開啟的。   `DynamicItemStart`命令定義的旗標會指定命令是預留位置，直到開啟 VSPackage。 VSPackage 開啟時，將會取代預留位置 0 或多個命令會在執行階段建立並加入至動態清單。 您可能無法看見 VSPackage 在開啟之前動態清單隨即出現的功能表上的位置。  若要填入的動態清單，Visual Studio 會詢問 VSPackage 也可以尋找第一個字元的預留位置的識別碼相同 id 的命令。 當 Visual Studio 找到相符的命令時，它會將命令的名稱加入至動態清單中。 然後它會遞增的識別碼，並尋找相符的另一個命令，以加入動態清單，直到沒有其他動態命令。  
  
 本逐步解說示範如何以設定啟始專案，Visual Studio 方案中使用命令**方案總管 中**工具列。 它會使用已在使用中方案中專案的動態下拉式清單的功能表控制站。 若要防止此命令時沒有解決方案出現已開啟或方案中有多個專案時，才開啟的方案中有一個專案，當載入 VSPackage。  
  
 如需.vsct 檔案的詳細資訊，請參閱[Visual Studio 命令表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>建立擴充的功能表命令  
  
1.  建立 VSIX 專案，名為`DynamicMenuItems`。  
  
2.  當專案開啟時，加入自訂命令項目範本並將其命名**DynamicMenu**。 如需詳細資訊，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>.Vsct 檔中設定項目  
 若要建立功能表控制器與工具列上的動態功能表項目，您可以指定下列項目：  
  
-   兩個命令群組、 一個包含功能表控制站，另一個包含下拉式清單中的功能表項目  
  
-   類型的一個功能表項目`MenuController`  
  
-   兩個按鈕，將做為用於功能表項目，而另一個預留位置，顯示圖示，然後在工具列上的工具提示所提供的其中一個。  
  
1.  在 DynamicMenuPackage.vsct，定義命令識別碼。 請移至 [符號] 區段，並取代在 IDSymbol 元件**guidDynamicMenuPackageCmdSet** GuidSymbol 區塊。 您必須定義兩個群組、 功能表控制器、 預留位置命令，與錨定命令 IDSymbol 項目。  
  
    ```csharp  
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
  
2.  在 [群組] 區段中，刪除現有的群組並加入您剛才定義的兩個群組：  
  
    ```  
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
  
     加入 MenuController。 設定 DynamicVisibility 命令旗標，因為它不是一律可見。 ButtonText 不會顯示。  
  
    ```  
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
  
3.  MenuController 加入兩個按鈕做為動態功能表項目的預留位置，一個為錨點。  
  
     [預留位置] 按鈕的父代是**MyMenuControllerGroup**。 加入預留位置按鈕 DynamicItemStart、 DynamicVisibility 和 TextChanges 命令旗標。 ButtonText 不會顯示。  
  
     錨點按鈕保存了圖示和工具提示文字。 也是錨點按鈕的父代**MyMenuControllerGroup**。 請新增 NoShowOnMenuController 命令旗標，以確定按鈕不會實際顯示在功能表控制器下拉式清單中和 FixMenuController 命令旗標，使其永久錨點。  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
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
  
4.  將圖示新增至專案 （在 [資源] 資料夾），並在.vsct 檔案中將它的參考。 在此逐步解說中，我們會使用專案範本中所包含的箭號圖示。  
  
5.  新增外部符號區段之前 Commands 區段 VisibilityConstraints 區段。 （您可能會收到警告如果您將它加入符號之後）。本節可確保，會出現功能表控制器只能載入具有多個專案的方案是。  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>實作動態功能表命令  
 建立動態功能表命令類別繼承自<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>。 在此實作中，建構函式會指定一個述詞，用於比對命令。 您必須覆寫<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>方法用來設定這個述詞<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>屬性，其可識別要叫用命令。  
  
1.  建立新 C# 類別檔案命名為 DynamicItemMenuCommand.cs，並加入類別，名為**DynamicItemMenuCommand**繼承自<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  加入下列 using 陳述式：  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  加入私用欄位來儲存符合述詞：  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  加入繼承的建構函式<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>建構函式，並指定命令處理常式和<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>處理常式。 加入的述詞比對命令：  
  
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
  
5.  覆寫<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>方法，使述詞和集合，它會呼叫相符項目<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>屬性：  
  
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
  
## <a name="adding-the-command"></a>將命令加入  
 DynamicMenu 建構函式是設定功能表命令，包括動態功能表和功能表項目。  
  
1.  在 DynamicMenuPackageGuids.cs，加入的命令集的 GUID 和命令 ID:  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  在 DynamicMenu.cs 檔案中，加入下列 using 陳述式：  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  在 DynamicMenu 類別中，加入私用欄位**dte2**。  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  加入私用 rootItemId 欄位：  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  在 DynamicMenu 建構函式中，加入功能表命令。 我們將在下一節中定義的命令處理常式，`BeforeQueryStatus`事件處理常式，而且符合述詞。  
  
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
  
## <a name="implementing-the-handlers"></a>實作處理常式  
 若要實作動態功能表項目的功能表控制站上，您必須處理命令時按一下動態項目。 您也必須實作設定功能表項目狀態的邏輯。 加入 DynamicMenu 類別處理常式。  
  
1.  若要實作**設定啟始專案**命令，新增**OnInvokedDynamicItem**事件處理常式。 它會尋找其名稱是已叫用，並將它設定為啟始專案中設定它的絕對路徑的命令文字相同的專案<xref:EnvDTE.SolutionBuild.StartupProjects%2A>屬性。  
  
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
  
2.  新增`OnBeforeQueryStatusDynamicItem`事件處理常式。 這是之前呼叫此處理常式`QueryStatus`事件。 它會決定功能表項目是否為 「 實際 」 的項目，也就是不預留位置項目，且是否項目已經簽 （亦即，將專案已設定為啟始專案）。  
  
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
  
## <a name="implementing-the-command-id-match-predicate"></a>實作命令 ID 符合述詞  
  
1.  現在，實作符合述詞。 我們需要決定兩件事： 首先，是否命令識別碼是否有效 （它是大於或等於宣告的命令 id），和第二個，它是否指定可能的專案 （它是小於方案中的專案數目）。  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>設定只在方案中有多個專案時才能載入 VSPackage  
 因為**設定啟始專案**命令沒有任何意義，除非使用中方案中有一個以上的專案，您可以設定只有在此情況下自動載入至 VSPackage。 您使用<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>UI 內容以及<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>。 DynamicMenuPackage.cs 檔案中加入 DynamicMenuPackage 類別中的下列屬性：  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>測試設定啟始專案命令  
 現在您可以測試您的程式碼。  
  
1.  建置此專案並開始偵錯。 實驗執行個體應該會出現。  
  
2.  在實驗執行個體中，開啟具有多個專案的方案。  
  
     您應該會看到箭號圖示**方案總管 中**工具列。 當您展開它時，代表不同的專案方案中的功能表項目應該會出現。  
  
3.  當您核取其中一個專案時，它會變成啟始專案。  
  
4.  當您關閉方案，或開啟含有只能執行一個專案的方案時，工具列圖示應該就會消失。  
  
## <a name="see-also"></a>請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
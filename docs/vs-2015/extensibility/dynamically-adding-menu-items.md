---
title: 以動態方式加入功能表項目 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: edd3a97eea69843bcd09a9483a7cea196d3a4c5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487889"
---
# <a name="dynamically-adding-menu-items"></a>以動態方式新增功能表項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[以動態方式加入功能表項目](https://docs.microsoft.com/visualstudio/extensibility/dynamically-adding-menu-items)。  
  
您可以在執行階段加入功能表項目，藉由指定`DynamicItemStart`命令預留位置按鈕定義中，在 Visual Studio 命令表 (.vsct) 檔案中，旗標，然後定義 （在程式碼） 功能表的數項目來顯示及處理命令。 當載入 VSPackage 時，動態功能表項目會取代預留位置。  
  
 Visual Studio 會使用中的動態清單**最近使用**(MRU) 清單，會顯示最近開啟的文件的名稱，而**Windows**清單中顯示的 windows 名稱目前已開啟。   `DynamicItemStart`命令定義的旗標會指定當命令開啟 VSPackage 時才會是一個預留位置。 當開啟 VSPackage 時，將會取代預留位置 0 或更多命令，都會在執行階段建立並新增至動態清單。 您可能無法開啟 VSPackage 時才動態清單隨即出現的功能表上看到的位置。  若要填入動態清單，Visual Studio 會詢問要尋找其第一個字元是預留位置的 ID 相同識別碼的命令的 VSPackage。 當 Visual Studio 找到相符的命令時，它會將命令的名稱加入至動態清單中。 然後它會遞增的識別碼，並尋找另一個相符的命令，以加入動態的清單，直到沒有其他動態命令。  
  
 本逐步解說示範如何設定中使用命令的 Visual Studio 方案的啟始專案**方案總管 中**工具列。 它會使用已在使用中的方案中的專案的動態下拉式清單的功能表控制站。 若要將此命令不會出現時沒有方案已開啟，或方案中有多個專案時，才開啟的方案中有只有一個專案，當載入 VSPackage。  
  
 如需.vsct 檔的詳細資訊，請參閱[Visual Studio Command Table (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>建立具有功能表命令的延伸模組  
  
1.  建立 VSIX 專案，名為`DynamicMenuItems`。  
  
2.  當專案開啟時，加入自訂命令項目範本並將它命名**DynamicMenu**。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的擴充](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>.Vsct 檔案中的項目設定  
 若要建立的工具列上的動態功能表項目的功能表控制器，您可以指定下列項目：  
  
-   兩個命令群組，一個包含功能表控制站，另一個包含下拉式清單中的功能表項目  
  
-   型別的一個功能表項目 `MenuController`  
  
-   兩個按鈕，將做為預留位置的功能表項目，另一個圖示，然後在工具列上的工具提示所提供的其中一個。  
  
1.  在 DynamicMenuPackage.vsct，定義命令識別碼。 移至的 Symbols 區段，並取代在 IDSymbol 元素**guidDynamicMenuPackageCmdSet** GuidSymbol 區塊。 您要定義兩個群組中，功能表控制器、 預留位置命令和錨點命令的 IDSymbol 元素。  
  
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
  
2.  在 [群組] 區段中，刪除現有的群組並新增您剛才定義的兩個群組：  
  
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
  
     新增 MenuController。 設定 DynamicVisibility 命令旗標，因為它不一定可見。 ButtonText 不會顯示。  
  
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
  
3.  MenuController 新增兩個按鈕，一個作為預留位置，以針對動態功能表項目，一個為錨點。  
  
     [預留位置] 按鈕的父系**MyMenuControllerGroup**。 加入預留位置按鈕 DynamicItemStart、 DynamicVisibility 和 TextChanges 命令旗標。 ButtonText 不會顯示。  
  
     錨點按鈕會保留圖示和工具提示文字。 也是錨點按鈕的父代**MyMenuControllerGroup**。 請新增 NoShowOnMenuController 命令旗標，以確定按鈕不會實際顯示在功能表控制器下拉式清單中和 FixMenuController 命令旗標，讓它永久的錨點。  
  
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
  
4.  將圖示新增至專案期間 （在 [資源] 資料夾），並新增其參考.vsct 檔案中。 在此逐步解說中，我們會使用專案範本中所包含的箭號圖示。  
  
5.  新增 VisibilityConstraints 區段外之前的 Symbols 區段的 [命令] 區段。 （您可能會收到一則警告將它加在符號之後）。此區段可確保，功能表控制器會出現只包含多個專案的方案載入的時機。  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>實作動態功能表命令  
 您建立動態功能表命令類別繼承自<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>。 在此實作中，建構函式會指定要用於比對命令的述詞。 您必須覆寫<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>方法用來設定這個述詞<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>屬性，可識別要叫用命令。  
  
1.  建立的新 C# 類別檔案命名為 DynamicItemMenuCommand.cs，並新增一個名為類別**DynamicItemMenuCommand**繼承自<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  新增下列 using 陳述式：  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  加入私用欄位來儲存符合述詞：  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  加入繼承的建構函式<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>建構函式，並指定命令處理常式和<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>處理常式。 加入的述詞相符的命令：  
  
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
  
5.  覆寫<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>方法，讓它呼叫的相符項目，述詞，並設定<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>屬性：  
  
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
  
## <a name="adding-the-command"></a>加入命令  
 DynamicMenu 建構函式會設定功能表命令，包括動態功能表和功能表項目。  
  
1.  在 DynamicMenuPackageGuids.cs，新增的命令集的 GUID 和命令 ID:  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  在 DynamicMenu.cs 檔案中，新增下列 using 陳述式：  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  在 DynamicMenu 類別中加入一個私用欄位**dte2**。  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  加入私用 rootItemId 欄位：  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  在 DynamicMenu 建構函式中，加入功能表命令。 下一節中，我們會定義的命令處理常式，`BeforeQueryStatus`事件處理常式，並符合述詞。  
  
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
 若要實作動態功能表項目的功能表控制站上，您必須處理命令時按一下動態項目。 您也必須實作邏輯，以設定功能表項目的狀態。 加入 DynamicMenu 類別處理常式。  
  
1.  若要實作**設定啟始專案**命令，新增**OnInvokedDynamicItem**事件處理常式。 它會尋找其名稱是已叫用，並將它設定為啟始專案中設定它的絕對路徑的命令文字相同專案<xref:EnvDTE.SolutionBuild.StartupProjects%2A>屬性。  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
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
  
2.  新增`OnBeforeQueryStatusDynamicItem`事件處理常式。 這是之前呼叫的處理常式`QueryStatus`事件。 它會判斷功能表項目是否為 「 真實 」 的項目，也就不是預留位置項目，且是否項目已經簽 （亦即，將專案已設定為啟始專案）。  
  
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
  
1.  現在實作符合述詞。 我們需要決定兩件事情： 首先，命令識別碼是否有效 （它是大於或等於宣告的命令 ID，） 和第二個，它是否會指定可能的專案 （它是在方案中的專案數目小於）。  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>設定方案中有多個專案時，只載入 VSPackage  
 因為**設定啟始專案**命令沒有任何意義，除非使用中的方案有多個專案，您可以設定以僅在此情況下自動載入 VSPackage。 您使用<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>UI 內容以及<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>。 DynamicMenuPackage.cs 檔案中加入 DynamicMenuPackage 類別中的下列屬性：  
  
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
  
     您應該看到的箭號圖示**方案總管 中**工具列。 當您展開它時，應該會出現代表不同的專案在方案中的功能表項目。  
  
3.  當您選取其中一個專案時，它會成為啟始專案。  
  
4.  當您關閉方案，或開啟含有只能有一個專案的方案時，工具列圖示應該會消失。  
  
## <a name="see-also"></a>另請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)


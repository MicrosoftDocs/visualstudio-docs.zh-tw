---
title: "以動態方式加入功能表項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DYNAMICITEMSTART"
  - "功能表項目，以動態方式加入"
  - "功能表新增動態項目"
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 37
---
# 以動態方式加入功能表項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在執行階段加入功能表項目，藉由指定 `DynamicItemStart` 命令在 Visual Studio 命令對應表 \(.vsct\) 檔案中的預留位置按鈕定義的旗標，然後定義 （在程式碼）\] 功能表上的數項目來顯示及處理命令。 當載入 VSPackage 時，動態功能表項目取代預留位置。  
  
 Visual Studio 會使用中的動態清單 **最近使用的** \(MRU\) 清單，顯示最近開啟的文件的名稱，而 **Windows** 清單，會顯示目前開啟的視窗名稱。`DynamicItemStart` 命令定義的旗標會指定命令是預留位置，直到開啟 VSPackage。 開啟 VSPackage 時，將會取代預留位置 0 或多個命令會在執行階段建立並加入至動態清單。 您可能無法開啟 VSPackage 時才動態清單會出現的功能表上看到的位置。 若要填入的動態清單，Visual Studio 會要求要尋找的第一個字元的版面配置區的識別碼相同識別碼的指令 VSPackage。 當 Visual Studio 找到相符的命令時，它會將命令的名稱加入至動態清單中。 然後它會遞增的識別碼，並尋找相符的另一個命令，以加入動態的清單，直到沒有其他動態命令。  
  
 本逐步解說示範如何設定中使用命令的 Visual Studio 方案的啟始專案 **方案總管\] 中** 工具列。 它會使用作用中的方案具有動態下拉式清單的專案\] 功能表上控制站。 若要防止此命令時沒有解決方案出現已開啟或方案中有多個專案時，才開啟的方案中有一個專案，當載入 VSPackage。  
  
 如需.vsct 檔的詳細資訊，請參閱 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## 建立擴充功能的功能表命令  
  
1.  建立 VSIX 專案，名為 `DynamicMenuItems`。  
  
2.  當專案開啟時，加入自訂命令的項目範本並將其命名 **DynamicMenu**。 如需詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## 設定.vsct 檔中的項目  
 若要建立的工具列上的動態功能表項目的功能表控制器，您可以指定下列項目︰  
  
-   兩個命令群組，一個包含功能表控制站，另一個包含下拉式清單中的功能表項目  
  
-   型別的一個功能表項目 `MenuController`  
  
-   兩個按鈕，將其中一個，做為功能表項目，另一個替代符號，提供了圖示和工具列上的工具提示。  
  
1.  在 DynamicMenuPackage.vsct，定義命令 Id。 請移至 \[符號\] 區段，並取代 IDSymbol 元件在 **guidDynamicMenuPackageCmdSet** GuidSymbol 區塊。 您必須定義兩個群組、 功能表控制器、 預留位置命令和錨定命令 IDSymbol 項目。  
  
    ```c#  
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
  
2.  在 \[群組\] 區段中，刪除現有的群組並新增您剛才定義的兩個群組︰  
  
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
  
     新增 MenuController。 設定 DynamicVisibility 命令旗標，因為它不是一律可見。 不會顯示於。  
  
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
  
3.  MenuController 新增兩個按鈕，一個做為預留位置，動態功能表項目，一個為錨點。  
  
     \[預留位置\] 按鈕的父系是 **MyMenuControllerGroup**。 將 DynamicItemStart、 DynamicVisibility，以及文字變更命令旗標加入至 \[預留位置\] 按鈕。 不會顯示於。  
  
     錨點按鈕會保存圖示和工具提示文字。 錨點按鈕的父項目也是 **MyMenuControllerGroup**。 請新增 NoShowOnMenuController 命令旗標，以確定按鈕不會實際顯示在功能表控制器下拉式清單中和 FixMenuController 命令旗標，讓它永久錨點。  
  
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
  
4.  將圖示新增至專案 （在 \[資源\] 資料夾），並接著.vsct 檔案中新增的參考。 在此逐步解說中，我們會使用專案範本中所包含的箭號圖示。  
  
5.  新增 VisibilityConstraints 區段之外前面 Symbols 區段命令 \> 一節。 （您可能會收到警告如果您加入符號之後）。 本節可確保功能表控制器出現只包含多個專案的方案載入的時機。  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## 實作動態功能表命令  
 您建立動態功能表命令類別繼承自 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>。 在此實作中，建構函式會指定用於比對命令在述詞。 您必須覆寫 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> 方法用來設定這個述詞 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> 屬性，識別要叫用命令。  
  
1.  建立的新 C\# 類別檔案命名為 DynamicItemMenuCommand.cs，並新增名為 **DynamicItemMenuCommand** 繼承自 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```c#  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  新增下列 using 陳述式︰  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  加入私用欄位來儲存符合述詞︰  
  
    ```c#  
    private Predicate<int> matches;  
  
    ```  
  
4.  加入繼承的建構函式 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 建構函式，並指定命令處理常式和 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 處理常式。 加入述詞進行比對此命令︰  
  
    ```c#  
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
  
5.  覆寫 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> 方法，使它呼叫相符項目，述詞，並且設定 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> 屬性︰  
  
    ```c#  
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
  
## 加入命令  
 DynamicMenu 建構函式會設定功能表命令，包括動態功能表和功能表項目。  
  
1.  在 DynamicMenuPackageGuids.cs，新增的命令集的 GUID 和命令 ID:  
  
    ```c#  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  在 DynamicMenu.cs 檔案中，新增下列 using 陳述式︰  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  在 DynamicMenu 類別中加入一個私用欄位 **dte2**。  
  
    ```c#  
    private DTE2 dte2;  
    ```  
  
4.  加入私用 rootItemId 欄位︰  
  
    ```c#  
    private int rootItemId = 0;  
    ```  
  
5.  DynamicMenu 建構函式中加入功能表命令。 下一節中，我們將定義的命令處理常式， `BeforeQueryStatus` 事件處理常式，而且符合述詞。  
  
    ```c#  
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
  
## 實作處理常式  
 若要實作動態功能表項目的功能表控制站上，您必須處理命令時會動態項目。 您也必須實作會設定功能表項目狀態的邏輯。 將處理常式加入至 DynamicMenu 類別。  
  
1.  若要實作 **設定啟始專案** 命令，新增 **OnInvokedDynamicItem** 事件處理常式。 它會尋找名稱為命令中已叫用，並將它設定為啟始專案中設定它的絕對路徑的文字相同專案 <xref:EnvDTE.SolutionBuild.StartupProjects%2A> 屬性。  
  
    ```c#  
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
  
2.  新增 `OnBeforeQueryStatusDynamicItem` 事件處理常式。 這個處理常式前呼叫 `QueryStatus` 事件。 判斷功能表項目是否為 「 真實 」 的項目，也就不是預留位置項目，以及是否項目已選取 （亦即，專案已設定為啟始專案）。  
  
    ```c#  
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
  
## 實作的命令識別碼符合述詞  
  
1.  實作了符合述詞。 我們需要決定兩件事情︰ 首先，命令識別碼是否有效 （它是大於或等於宣告的命令 id），和第二個，它是否會指定可能的專案 （它是小於方案中的專案數目）。  
  
    ```c#  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## 設定方案中有多個專案時，只載入 VSPackage  
 因為 **設定啟始專案** 命令沒有任何意義，除非使用中的方案中有多個專案，您可以設定要僅在此情況下自動載入 VSPackage。 您使用 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> UI 內容以及 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>。 DynamicMenuPackage.cs 檔案中加入 DynamicMenuPackage 類別中的下列屬性︰  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## 測試設定啟始專案命令  
 現在您可以測試您的程式碼。  
  
1.  建置此專案並開始偵錯。 實驗執行個體應該會出現。  
  
2.  在實驗執行個體中，開啟具有多個專案的方案。  
  
     您應該會看到箭號圖示上 **方案總管\] 中** 工具列。 當您展開它時，應該會出現代表不同的專案方案中的功能表項目。  
  
3.  當您檢查其中一個專案時，它會變成啟始專案。  
  
4.  當您關閉方案，或開啟的方案中有一個專案時，工具列圖示應該會消失。  
  
## 請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
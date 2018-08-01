---
title: 加入功能表中的子功能表 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 087957155aeadb906319a6f261fe665060eeacca
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155499"
---
# <a name="add-a-submenu-to-a-menu"></a>將子功能表加入至功能表
本逐步解說是根據在示範[Visual Studio 功能表列中加入功能表](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)示範如何以新增至子功能表**TestMenu**功能表。  
  
 子功能表時出現在另一個功能表中的次要功能表。 可以由其名稱後面的箭號識別子功能表。 按一下名稱，會導致子功能表和它要顯示的命令。  
  
 本逐步解說在 Visual Studio 功能表列上的功能表中建立子功能表，並將新的命令放在子功能表上。 本逐步解說也會實作新的命令。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="add-a-submenu-to-a-menu"></a>將子功能表加入至功能表  
  
1.  請依照下列中的步驟[Visual Studio 功能表列中加入功能表](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)建立專案和功能表項目。 在本逐步解說的步驟假設 VSIX 專案的名稱是`TopLevelMenu`。  
  
2.  開啟*TestCommandPackage.vsct*。 在 `<Symbols>`區段中，新增`<IDSymbol>`子功能表，其中一個子功能表群組中，，另一個命令，在所有的項目`<GuidSymbol>`節點名為"guidTopLevelMenuCmdSet。 」 這是相同的節點，其中包含`<IDSymbol>`最上層的功能表項目。  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  新增至新建立的子功能表`<Menus>`一節。  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     父代的 GUID/識別碼組指定之功能表群組中所產生的[Visual Studio 功能表列中加入功能表](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)，並是最上層功能表的子系。  
  
4.  加入在步驟 2 中定義的功能表群組`<Groups>`區段，並使它成為子系的子功能表。  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  加入新`<Button>`項目`<Buttons>`區段來定義命令的步驟 2 中建立為子功能表上的項目。  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  建置方案並開始偵錯。 您應該會看到的實驗執行個體。  
  
7.  按一下  **TestMenu**若要查看新的子功能表，名為**子功能表**。 按一下 **子功能表**以開啟子功能表，並查看新的命令**測試子命令**。 請注意，按一下**測試子命令**不執行任何動作。  
  
## <a name="add-a-command"></a>新增命令  
  
1.  開啟*TestCommand.cs*和現有的命令識別碼之後加入下列的命令 ID  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  新增子命令。 尋找命令建構函式。 呼叫後方新增下列行`AddCommand`方法。  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback`稍後定義命令處理常式。 建構函式現在看起來應該像這樣：  
  
    ```csharp  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  新增`SubItemCallback()`。 這是新的命令，在子功能表中按一下時呼叫的方法。  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  建置此專案並開始偵錯。 實驗執行個體應該會出現。  
  
5.  在上**TestMenu**功能表上，按一下**子功能表**，然後按一下 **測試子命令**。 訊息方塊應該會出現，並顯示文字，也就是 「 第命令頁，在 TestCommand.SubItemCallback() 測試 」。  
  
## <a name="see-also"></a>另請參閱  
 [將功能表加入 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)

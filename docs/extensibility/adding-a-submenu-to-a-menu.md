---
title: "將子功能表新增至功能表 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "內容功能表"
  - "子功能表，階層式"
  - "階層式子功能表"
  - "建立階層式子功能表的功能表"
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 43
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 43
---
# 將子功能表新增至功能表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說示範的是根據 [將功能表加入至 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 藉由顯示如何新增到子功能表 **TestMenu** 功能表。  
  
 子功能表時出現在另一個功能表的第二個功能表。 子功能表可以識別由其名稱後面的箭號。 按一下名稱，會讓子功能表和它所要顯示的命令。  
  
 本逐步解說建立 Visual Studio 功能表列上的功能表中子功能表，並將新的命令放在子功能表。 本逐步解說也會實作新的命令。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 將子功能表新增至功能表  
  
1.  請依照 [將功能表加入至 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 建立專案和功能表項目。 在本逐步解說步驟假設 VSIX 專案的名稱為 `TopLevelMenu`。  
  
2.  開啟 TestCommandPackage.vsct。 在 `<Symbols>` 區段中，加入 `<IDSymbol>` 的子功能表，一個用於子群組，其中一個命令中的所有項目 `<GuidSymbol>` 節點名為 「 guidTopLevelMenuCmdSet 」。 這是相同的節點，其中包含 `<IDSymbol>` 最上層功能表項目。  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  新增至新建立的子功能表 `<Menus>` 一節。  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     父系的 ID GUID 組指定的功能表群組中所產生 [將功能表加入至 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), ，和子系的最上層的功能表。  
  
4.  加入至步驟 2 中定義的功能表群組 `<Groups>` 區段，並讓子功能表的子系。  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  加入新 `<Button>` 項目來 `<Buttons>` 一節，以定義 \[步驟 2 中建立為子功能表上的項目\] 命令。  
  
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
  
7.  按一下 \[ **TestMenu** 以查看新的子功能表，名為 **\] 子功能表**。 按一下 \[ **\] 子功能表** 開啟子功能表，並查看新的命令， **測試子命令**。 請注意，按一下 **測試子命令** 不做任何動作。  
  
## 加入命令  
  
1.  開啟 TestCommand.cs 和現有的命令 id。 後面加入下列的命令 ID  
  
    ```c#  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  新增子命令。 尋找命令建構函式。 呼叫後面加入下列程式碼行 `AddCommand` 方法。  
  
    ```c#  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback` 稍後定義命令處理常式。 建構函式現在看起來應該像這樣︰  
  
    ```c#  
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
  
3.  新增 SubItemCallback\(\)。 這是按一下子功能表中的 \[新增\] 命令時呼叫的方法。  
  
    ```c#  
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
  
5.  在 **TestMenu** \] 功能表上，按一下 \[ **\] 子功能表** 然後按一下 \[ **測試子命令**。 訊息方塊應該會出現並顯示文字，也就是 「 第命令頁，在 TestCommand.SubItemCallback\(\) 測試 」。  
  
## 請參閱  
 [將功能表加入至 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
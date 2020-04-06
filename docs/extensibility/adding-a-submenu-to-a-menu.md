---
title: 加入選單加入子選單 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740277"
---
# <a name="add-a-submenu-to-a-menu"></a>加入選單加入子選單
本演練基於在[「向可視化工作室功能表欄添加功能表](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)」中的演示為基礎,演示如何向**TestMenu 功能表**添加子功能表。

 子功能表是另一個功能表中顯示的輔助功能表。 子功能表可以通過其名稱後面的箭頭進行標識。 單擊名稱會導致子功能表及其命令顯示。

 本演練在 Visual Studio 功能表欄的功能表中創建一個子功能表,並在子選單上放置一個新命令。 演練還實現了新命令。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="add-a-submenu-to-a-menu"></a>加入選單加入子選單

1. 按照向[可視化工作室功能表欄添加功能表](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)中的步驟創建專案和功能表項。 這個演練中的步驟假定 VSIX 項目的`TopLevelMenu`名稱為 。

2. 開啟*測試指令套件.vsct*. 在本節`<Symbols>`中,為`<IDSymbol>`子 功能表添加一個元素,為子菜單組添加一個元素,為命令添加一個`<GuidSymbol>`元素, 所有這些元素都在名為"guidTopLevelMenuCmdSet"的節點中。 這是包含頂級功能表`<IDSymbol>`元素的同一節點。

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. 新增建立的子選單加入到節中`<Menus>`。

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     父組的 GUID/ID 對指定在[「向可視化工作室功能表欄添加功能表](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)」中生成的功能表組,並且是頂級功能表的子級。

4. 將步驟 2 中定義的功能表組`<Groups>`添加到 分區,使其成為子菜單的子功能表的子功能表。

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. 向`<Buttons>`節添加`<Button>`新 元素,將步驟 2 中創建的命令定義為子功能表上的項。

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

6. 建置方案並開始偵錯。 您應該會看到實驗實例。

7. 點選 **「測試選單**」 以檢視名為 **「子選單」 的新子選單**。 按下 **「子功能表**」打開子功能表並查看新命令 **「測試子命令**」。 請注意,按一下 **「測試子命令**」不執行任何操作。

## <a name="add-a-command"></a>新增命令

1. 開啟*TestCommand.cs,* 並在現有命令 ID 之後新增以下命令 ID。

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. 添加子命令。 查找命令構造函數。 在調用`AddCommand`方法后添加以下行。

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    稍後將`SubItemCallback`定義命令處理程式。 建構函數現在應如下所示:

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
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. 加入 `SubItemCallback()`。 這是單擊子功能表中的新命令時調用的方法。

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
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

4. 建置此專案並開始偵錯。 應出現實驗實例。

5. 在**測試選單「 功能表」,** 按下 **「子選單**」,然後單擊 **「測試子命令**」。 應顯示一個消息框並顯示文本「測試命令內部測試命令.子項目回調()」。

## <a name="see-also"></a>另請參閱

- [向視覺工作室選單欄新增選單](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)

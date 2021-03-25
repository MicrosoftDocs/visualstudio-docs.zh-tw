---
title: 將子功能表新增至功能表 |Microsoft Docs
description: 瞭解如何建立子功能表，將它新增至 Visual Studio 的功能表列，並將新的命令加入至子功能表。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc6d521e699beb2345ba76e2e617ff749886eee9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094896"
---
# <a name="add-a-submenu-to-a-menu"></a>將子功能表新增至功能表
本逐步解說會示範如何將子功能表新增至 [ **TestMenu** ] 功能表，以 [將功能表新增至 Visual Studio 的功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)。

 子功能表是出現在另一個功能表中的次要功能表。 子功能表可透過其名稱後面的箭號來識別。 按一下名稱會顯示子功能表和其命令。

 本逐步解說會在 [Visual Studio] 功能表列上的功能表中建立子功能表，並將新的命令放在子功能表上。 本逐步解說也會實施新的命令。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="add-a-submenu-to-a-menu"></a>將子功能表新增至功能表

1. 遵循 [ [將功能表新增至 Visual Studio] 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 中的步驟，以建立專案和功能表項目。 本逐步解說中的步驟假設 VSIX 專案的名稱是 `TopLevelMenu` 。

2. 開啟 *TestCommandPackage. .vsct*。 在區段中， `<Symbols>` 加入 `<IDSymbol>` 子功能表的專案，一個用於子功能表群組，另一個用於命令，並在 `<GuidSymbol>` 名為 "guidTopLevelMenuCmdSet" 的節點中。 這是包含 `<IDSymbol>` 最上層功能表元素的相同節點。

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. 將新建立的子功能表新增至 `<Menus>` 區段。

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     父系的 GUID/識別碼組會指定在 [Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)的 [加入] 功能表中所產生的功能表群組，以及最上層功能表的子系。

4. 將步驟2中定義的功能表群組新增至 `<Groups>` 區段，並將它設為子功能表的子系。

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. 將新專案加入 `<Button>` 至 `<Buttons>` 區段，以將步驟2中建立的命令定義為子功能表上的專案。

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

7. 按一下 [ **TestMenu** ] 以查看名為 [ **子功能表**] 的新子功能表。 按一下 **子功能表** 以開啟子功能表，並查看新的命令 [ **Test Sub] 命令**。 請注意，按一下 [ **Test Sub] 命令** 不會執行任何動作。

## <a name="add-a-command"></a>新增命令

1. 開啟 *TestCommand* ，並在現有的命令識別碼之後新增下列命令識別碼。

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. 新增子命令。 尋找命令的函式。 在呼叫方法之後，加入下列幾行 `AddCommand` 。

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    `SubItemCallback`稍後會定義命令處理常式。 此函式現在看起來應該像這樣：

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

3. 加入 `SubItemCallback()`。 這是按一下子功能表中的新命令時，所呼叫的方法。

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        IVsUIShell uiShell = this.package.GetService<SVsUIShell, IVsUIShell>();
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

4. 建置此專案並開始偵錯。 實驗實例應會出現。

5. 在 [ **TestMenu** ] 功能表上，按一下 [ **子功能表** ]，然後按一下 [ **測試子命令**]。 應該會出現訊息方塊，並顯示「在 TestCommand. SubItemCallback 中測試命令 () 」文字。

## <a name="see-also"></a>另請參閱

- [將功能表新增至 Visual Studio 的功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)

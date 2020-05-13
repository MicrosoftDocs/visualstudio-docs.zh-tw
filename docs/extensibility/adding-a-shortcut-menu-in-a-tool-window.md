---
title: 在工具視窗中加入快捷方式選單 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740290"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>在工具視窗中加入快捷選單
本演練將快捷方式功能表放在工具視窗中。 快捷選單是當使用者右鍵按下按鈕、文字框或視窗背景時顯示的功能表。 快捷功能表上的命令與其他功能表或工具列上的命令相同。 要支援快捷選單,請在 *.vsct*檔中指定它,並顯示它以響應滑鼠的右鍵按一下。

工具視窗由從<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>繼承的自定義工具視窗類中的 WPF 使用者控制元件組成。

本演練演示如何創建快捷方式功能表作為 Visual Studio 選單,通過在 *.vsct*檔中聲明功能表項,然後使用託管包框架在定義工具視窗的類中實現它們。 此方法便於造訪 Visual Studio 命令、UI 元素和自動化物件模型。

或者,如果快捷功能表無法存訪 Visual Studio 功能,則可以使用<xref:System.Windows.FrameworkElement.ContextMenu%2A>使用者控制項中的 XAML 元素的屬性。 有關詳細資訊,請參閱[上下文選單](/dotnet/framework/wpf/controls/contextmenu)。

## <a name="prerequisites"></a>Prerequisites
從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-the-tool-window-shortcut-menu-package"></a>建立工具視窗快捷方式選單包

1. 創建名為`TWShortcutMenu`VSIX 專案的 VSIX,並將名為 **「捷徑功能表」** 的工具視窗樣本添加到其中。 有關創建工具視窗的詳細資訊,請參閱[使用工具窗口創建副檔](../extensibility/creating-an-extension-with-a-tool-window.md)名。

## <a name="specifying-the-shortcut-menu"></a>指定快捷選單
快捷方式功能表(如本演練中顯示的功能表)允許使用者從用於填充工具視窗背景的顏色清單中選擇。

1. 在 *「快捷選單包.vsct」* 中,在名為 GuidMenuMenuPackageCmdSet 的 GuidSymbol 元素中尋找,並聲明快捷選單、快捷選單組和功能表選項。 GuidSymbol 元素現在應如下所示:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. 在 Buttons 元素之前,創建一個功能表元素,然後在其中定義快捷功能表。

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    快捷功能表沒有父功能表,因為它不是功能表或工具列的一部分。

3. 使用包含快捷選單項的 Group 元素創建組元素,並將組與快捷功能表相關聯。

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. 在「按鈕」元素中,定義將顯示在快捷功能表上的各個命令。 按鈕元素應如下所示:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. 在*ShortcutMenuCommand.cs*中,添加命令集 GUID、快捷功能表和功能表項的定義。

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    這些是*在快捷方式功能表包.vsct*檔「符號」部分中定義的相同的命令指示。 此處不包括上下文組,因為它僅在 *.vsct*檔中是必需的。

## <a name="implementing-the-shortcut-menu"></a>實現快捷選單
 本節實現快捷功能表及其命令。

1. 在*ShortcutMenu.cs*中,工具視窗可以獲取菜單命令服務,但它包含的控制項不能。 以下步驟演示如何使功能表命令服務可供使用者控制件使用。

2. 在*ShortcutMenu.cs*中,加入以下使用指令:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. 重寫工具視窗的初始化() 方法以取得選單指令服務並新增控制項,將選單指令服務傳遞給建構函數:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. 在「快捷方式功能表」工具視窗建構函數中,刪除添加控制項的行。 建構函數現在應如下所示:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. 在*ShortcutMenuControl.xaml.cs*中,為功能表命令服務添加專用欄位,並更改控制項構造函數以獲取選單命令服務。 然後使用功能表指令服務添加上下文選單命令。 快捷功能表控制構造函數現在應類似於以下代碼。 稍後將定義命令處理程式。

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. 在*快捷方式MenuControl.xaml*中<xref:System.Windows.UIElement.MouseRightButtonDown>,<xref:System.Windows.Controls.UserControl>向頂級 元素添加事件。 XAML 檔案現在應如下所示:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. 在*ShortcutMenuControl.xaml.cs*中,為事件處理程式添加存根。

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. 將以下使用指令加入同一檔案:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. 按照`MyToolWindowMouseRightButtonDown`如下方式實施事件。

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    這將為快捷<xref:System.ComponentModel.Design.CommandID>菜單創建一個物件,標識滑鼠單擊的位置,並使用 方法打開該<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>位置的 快捷功能表。

10. 實現命令處理程式。

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    在這種情況下,只有一種方法通過標識<xref:System.ComponentModel.Design.CommandID>和相應地設置背景顏色來處理所有功能表項的事件。 如果功能表項包含不相關的命令,則為每個命令創建單獨的事件處理程式。

## <a name="test-the-tool-window-features"></a>測試工具視窗功能

1. 建置此專案並開始偵錯。 出現實驗實例。

2. 在實驗實例中,按下 **「查看/其他視窗**」,然後單擊 **「快捷功能表**」。。 執行此操作應顯示工具視窗。

3. 右鍵單擊工具視窗的正文。 應顯示包含顏色清單的快捷功能表。

4. 單擊快捷功能表上的顏色。 工具視窗背景顏色應更改為選取的顏色。

## <a name="see-also"></a>另請參閱
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
- [使用與提供服務](../extensibility/using-and-providing-services.md)

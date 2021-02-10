---
title: 在工具視窗中新增快捷方式功能表 |Microsoft Docs
description: 瞭解如何將快捷方式功能表新增至 Visual Studio 中的工具視窗，此視窗會在按鈕、文字方塊或視窗背景以滑鼠右鍵按一下時出現。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a35652c0eacf22a46eed3f3fc64c3bcc0d6d10ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951533"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>在工具視窗中新增快捷方式功能表
本逐步解說會在工具視窗中放置快捷方式功能表。 快速鍵功能表是使用者在按鈕、文字方塊或視窗背景上按一下滑鼠右鍵時所顯示的功能表。 快速鍵功能表上的命令列為與其他功能表或工具列上的命令相同。 若要支援快捷方式功能表，請在 *.vsct* 檔案中指定，並將其顯示以回應滑鼠右鍵。

工具視窗是由繼承自的自訂工具視窗類別中的 WPF 使用者控制項所組成 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 。

本逐步解說示範如何在 *.vsct* 檔中宣告功能表項目，然後使用 Managed Package Framework 在定義工具視窗的類別中執行，以建立快捷方式功能表做為 Visual Studio 的功能表。 這種方法可協助存取 Visual Studio 的命令、UI 元素，以及 Automation 物件模型。

或者，如果您的快捷方式功能表無法存取 Visual Studio 的功能，您可以 <xref:System.Windows.FrameworkElement.ContextMenu%2A> 在使用者控制項中使用 XAML 專案的屬性。 如需詳細資訊，請參閱 [CoNtextMenu](/dotnet/framework/wpf/controls/contextmenu)。

## <a name="prerequisites"></a>必要條件
從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-the-tool-window-shortcut-menu-package"></a>建立工具視窗快捷方式功能表套件

1. 建立名為的 VSIX 專案 `TWShortcutMenu` ，並將名為 **快捷** 方式的工具視窗範本新增至其中。 如需建立工具視窗的詳細資訊，請參閱 [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)模組。

## <a name="specifying-the-shortcut-menu"></a>指定快捷方式功能表
本逐步解說中所顯示的快捷方式功能表可讓使用者從用來填滿工具視窗背景的色彩清單中選取。

1. 在 *ShortcutMenuPackage* 中，在名為 GuidShortcutMenuPackageCmdSet 的 GuidSymbol 元素中尋找，然後宣告快捷方式功能表、快捷方式功能表群組和功能表選項。 GuidSymbol 元素現在看起來應該像這樣：

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

2. 在 [按鈕] 元素之前，建立功能表元素，然後定義其中的快捷方式功能表。

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

    快捷方式功能表沒有父代，因為它不是功能表或工具列的一部分。

3. 使用包含快捷方式功能表項目的 Group 元素建立 Groups 元素，並將該群組與快捷方式功能表產生關聯。

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. 在 [按鈕] 元素中，定義將出現在快捷方式功能表上的個別命令。 按鈕元素看起來應該像這樣：

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

5. 在 *ShortcutMenuCommand.cs* 中，新增命令集 GUID、快捷方式功能表和功能表項目的定義。

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    這些是在 *ShortcutMenuPackage. .vsct* 檔案的 [符號] 區段中定義的相同命令識別碼。 此處不包含內容群組，因為它只有在 *.vsct* 檔案中才需要。

## <a name="implementing-the-shortcut-menu"></a>執行快捷方式功能表
 本節會執行快捷方式功能表和其命令。

1. 在 *ShortcutMenu.cs* 中，工具視窗可以取得功能表命令服務，但是它所包含的控制項則不能。 下列步驟顯示如何讓功能表命令服務可供使用者控制項使用。

2. 在 *ShortcutMenu.cs* 中，新增下列 using 指示詞：

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. 覆寫工具視窗的 Initialize ( # A1 方法，以取得功能表命令服務並加入控制項，並將功能表命令服務傳遞給函式：

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. 在快顯功能表工具視窗的函式中，移除加入控制項的行。 此函式現在看起來應該像這樣：

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. 在 *ShortcutMenuControl.xaml.cs* 中，新增功能表命令服務的私用欄位，並變更控制項的函式以取得功能表命令服務。 然後使用功能表命令服務來新增內容功能表命令。 ShortcutMenuControl 的函式現在看起來應該像下列程式碼。 稍後會定義命令處理常式。

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

6. 在 *ShortcutMenuControl* 中，將事件新增 <xref:System.Windows.UIElement.MouseRightButtonDown> 至最上層 <xref:System.Windows.Controls.UserControl> 元素。 XAML 檔案現在看起來應該像這樣：

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

7. 在 *ShortcutMenuControl.xaml.cs* 中，新增事件處理常式的存根。

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. 將下列 using 指示詞加入至相同的檔案：

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. 依照 `MyToolWindowMouseRightButtonDown` 下列方式執行事件。

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

    這樣會建立 <xref:System.ComponentModel.Design.CommandID> 快捷方式功能表的物件、識別滑鼠點擊的位置，然後使用方法開啟該位置的快捷方式功能表 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> 。

10. 執行命令處理常式。

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

    在此情況下，只有一個方法會藉由識別 <xref:System.ComponentModel.Design.CommandID> 和設定背景色彩，來處理所有功能表項目的事件。 如果功能表項目包含不相關的命令，您就會為每個命令建立個別的事件處理常式。

## <a name="test-the-tool-window-features"></a>測試控管視窗功能

1. 建置此專案並開始偵錯。 實驗實例隨即出現。

2. 在實驗實例中，按一下 [ **視圖]/[其他視窗**]，然後按一下 [ **快顯功能表**]。 這樣做應該會顯示您的工具視窗。

3. 在工具視窗的主體中按一下滑鼠右鍵。 應該會顯示具有色彩清單的快捷方式功能表。

4. 按一下快捷方式功能表上的色彩。 工具視窗的背景色彩應該變更為選取的色彩。

## <a name="see-also"></a>另請參閱
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
- [使用和提供服務](../extensibility/using-and-providing-services.md)

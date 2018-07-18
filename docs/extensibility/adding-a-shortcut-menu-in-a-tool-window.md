---
title: 將快顯功能表加入工具視窗中 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4b36800ea291c6f1bc0948a46b67c4e3549f349
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31568665"
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>工具視窗中加入快顯功能表
本逐步解說置於工具視窗的捷徑功能表。 快顯功能表是在使用者以滑鼠右鍵按一下按鈕、 文字方塊或視窗背景時出現。 捷徑功能表上的命令的行為與其他功能表或工具列上的命令相同。 若要支援快顯功能表，在.vsct 檔案中指定它並顯示以回應按一下滑鼠右鍵。  
  
 工具視窗包含 WPF 使用者控制項中的自訂工具視窗類別繼承自<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>。  
  
 本逐步解說示範如何建立快顯功能表為 Visual Studio 功能表中，宣告在.vsct 檔案中，功能表項目，然後使用 Managed Package Framework 定義的工具視窗的類別中實作它們。 這種方式有助於存取 Visual Studio 命令、 UI 項目，以及自動化物件模型。  
  
 或者，如果您的快顯功能表將不會存取 Visual Studio 功能，您可以使用<xref:System.Windows.FrameworkElement.ContextMenu%2A>XAML 使用者控制項中項目的屬性。 如需詳細資訊，請參閱[ContextMenu](/dotnet/framework/wpf/controls/contextmenu)。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>建立工具視窗的捷徑功能表封裝  
  
1.  建立 VSIX 專案，名為`TWShortcutMenu`並新增名為的工具視窗範本**快顯功能表**給它。 如需有關建立工具視窗的詳細資訊，請參閱[建立工具視窗擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="specifying-the-shortcut-menu"></a>指定的捷徑功能表  
 從用來填滿工具視窗的背景色彩的清單中選取捷徑功能表，例如本逐步解說中所示可讓使用者。  
  
1.  在 ShortcutMenuPackage.vsct，尋找名為 guidShortcutMenuPackageCmdSet，GuidSymbol 項目中，宣告快顯功能表、 捷徑功能表群組和功能表選項。 GuidSymbol 項目現在看起來應該像這樣：  
  
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
  
2.  之前的按鈕項目，建立功能表項目，然後定義的捷徑功能表中。  
  
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
  
     快顯功能表沒有父代，因為它不是功能表或工具列的一部分。  
  
3.  建立群組項目與群組項目，其中包含快顯功能表項目，以及關聯的捷徑功能表中的群組。  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  中的按鈕項目，定義個別命令將會出現快顯功能表。 按鈕項目看起來應該像這樣：  
  
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
  
5.  在 ShortcutMenuCommand.cs，加入命令定義 GUID、 捷徑功能表，以及設定功能表項目。  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     這些是 ShortcutMenuPackage.vsct 檔案的符號一節中所定義的相同命令 Id。 內容群組就不會包含此處因為.vsct 檔中只需要它。  
  
## <a name="implementing-the-shortcut-menu"></a>實作快顯功能表  
 本節會實作快顯功能表和它的命令。  
  
1.  ShortcutMenu.cs，在 [工具] 視窗可取得功能表命令服務，但無法與其包含之控制項。 下列步驟示範如何讓使用者控制功能表命令服務。  
  
2.  在 ShortcutMenu.cs，加入下列 using 陳述式：  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  取得功能表命令服務，並加入控制項，將功能表命令服務傳遞至建構函式的工具視窗的 initialize （） 方法來覆寫：  
  
    ```csharp  
    protected override void Initialize()  
    {  
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  在快顯功能表工具視窗建構函式，移除，將控制項。 建構函式現在看起來應該像這樣：  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  ShortcutMenuControl.xaml.cs，加入功能表命令服務一個私用欄位，變更才會功能表命令服務控制建構函式。 若要加入的內容功能表命令，然後使用功能表命令服務。 ShortcutMenuControl 建構函式現在看起來應該類似下列程式碼。 稍後將會定義命令處理常式。  
  
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
  
6.  在 ShortcutMenuControl.xaml，加入<xref:System.Windows.UIElement.MouseRightButtonDown>最上層事件<xref:System.Windows.Controls.UserControl>項目。 XAML 檔案現在看起來應該像這樣：  
  
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
  
7.  在 ShortcutMenuControl.xaml.cs，加入事件處理常式的 stub。  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  加入下列 using 陳述式相同的檔案：  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. 實作`MyToolWindowMouseRightButtonDown`事件，如下所示。  
  
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
  
     這會建立<xref:System.ComponentModel.Design.CommandID>快速鍵功能表中的物件識別滑鼠點選位置，並使用在該位置開啟快顯功能表<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>方法。  
  
10. 實作的命令處理常式。  
  
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
  
     在此情況下，只有一個方法會處理事件的所有功能表項目藉由識別<xref:System.ComponentModel.Design.CommandID>並據此設定的背景色彩。 如果功能表項目所包含的不相關的命令，您會建立每個命令的另一個事件處理常式。  
  
## <a name="testing-the-tool-window-features"></a>測試工具視窗的功能  
  
1.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
2.  在實驗執行個體中，按一下**檢視 / 其他視窗**，然後按一下 **快顯功能表**。 這樣應該會顯示工具視窗。  
  
3.  以滑鼠右鍵按一下 [工具] 視窗的主體中。 應該會顯示快顯功能表具有色彩的清單。  
  
4.  按一下捷徑功能表上的色彩。 工具視窗背景色彩應該變更為選取的色彩。  
  
## <a name="see-also"></a>另請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)   
 [使用和提供服務](../extensibility/using-and-providing-services.md)
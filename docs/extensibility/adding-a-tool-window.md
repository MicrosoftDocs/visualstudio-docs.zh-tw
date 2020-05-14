---
title: 新增工具視窗 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740261"
---
# <a name="add-a-tool-window"></a>新增工具視窗

在這個演練中,您將瞭解如何建立工具視窗,並透過以下方式將其整合到 Visual Studio 中:

- 向工具視窗添加控制項。

- 向工具視窗添加工具列。

- 向工具列添加命令。

- 實現命令。

- 設定工具視窗的預設位置。

## <a name="prerequisites"></a>Prerequisites

可視化工作室 SDK 作為可選功能包含在可視化工作室設置中。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-tool-window"></a>建立工具視窗

1. 使用 VSIX 範本建立名為**FirstToolWin**的專案,並添加名為**FirstToolWindow**的自訂工具視窗項範本。

    > [!NOTE]
    > 有關使用工具視窗建立擴充的詳細資訊,請參考[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。

## <a name="add-a-control-to-the-tool-window"></a>加入工具視窗加入控制項

1. 刪除預設控制項。 開啟*第一工具視窗控制.xaml*並移除 **「按下我」 !** 按鈕。

2. 在**工具箱**中,**展開「所有 WPF 控制件」** 部分,並將**媒體元素**控制項拖動到 **「第一工具視窗控制」** 窗體。 選擇控制項,並在 **「屬性」** 視窗中命名此元素**mediaElement1**。

## <a name="add-a-toolbar-to-the-tool-window"></a>加入工具視窗加入工具列
通過按以下方式添加工具列,可以保證其漸變和顏色與IDE的其餘部分一致。

1. 在**解決方案資源管理員中**,開啟*第一工具視窗套件.vsct*。 *.vsct*檔案使用 XML 定義工具視窗中的圖形使用者介面 (GUI) 元素。

2. 在"`<Symbols>`部分"中`<GuidSymbol>`, 查`name`找其`guidFirstToolWindowPackageCmdSet`屬性為 的節點。 將以下兩`<IDSymbol>`個元素添加到此節點中`<IDSymbol>`的元素清單中,以定義工具列和工具列組。

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. 在`<Buttons>`節的正上方,`<Menus>`建立 類似於的節:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    有幾個不同類型的功能表。 此功能表是工具視窗中的工具列,由其`type`屬性定義。 和`guid``id`設置構成工具列完全限定的 ID。 通常,`<Parent>`選單的包含組。 但是,工具列定義為其自己的父工具列。 因此,相同的標識碼用於`<Menu>`和`<Parent>`元素。 屬性`priority`只是"0"。

4. 工具列在許多方面類似於菜單。 例如,正如菜單可能具有命令組一樣,工具列也可能具有組。 (在功能表上,命令組由水平線分隔。 在工具列上,組不由可視分隔符分隔。

    添加包含`<Groups>`元素的`<Group>`節。 這將定義您在節中聲明其 ID`<Symbols>`的組。 在`<Groups>``<Menus>`節後添加節。

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    通過將父 GUID 和 ID 設置為工具列的 GUID 和 ID,將組添加到工具列。

## <a name="add-a-command-to-the-toolbar"></a>加入工具列加入指令

向工具列添加命令,該工具列顯示為按鈕。

1. 在本`<Symbols>`節中,在工具列和工具列組聲明之後聲明以下 IDSymbol 元素。

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. 在`<Buttons>`節內添加按鈕元素。 此元素將顯示在工具視窗中的工具列上,並帶有 **「搜索**(放大鏡)」圖示。

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. 打開*FirstToolWindowCommand.cs,* 並在現有欄位之後在類中添加以下行。

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    這樣做會使命令在代碼中可用。

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>新增 MediaPlayer 屬性加入第一工具視窗控制
從工具列控制項的事件處理程式中,程式碼必須能夠存取媒體播放器控制項,該控制項是 FirstToolWindowControl 類的子級。

在**解決方案資源管理員**中,右鍵單擊*FirstToolWindowControl.xaml,* 按下 **「查看代碼**」,並將以下代碼添加到 FirstToolWindowControl 類。

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>實體化工具視窗與工具列
添加工具列和功能表命令,用於呼叫 **「打開檔案」** 對話方塊並播放選取的媒體檔。

1. 開啟*FirstToolWindow.cs*並`using`新增以下 指令:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. 在 FirstToolWindow 類中,添加對 FirstToolWindow 控制的公共引用。

    ```csharp
    public FirstToolWindowControl control;
    ```

3. 在建構函數的末尾,將此控制件變數設置為新創建的控制項。

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. 實例化構造函數內的工具列。

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. 此時,FirstToolWindow 構造函數應如下所示:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. 將功能表命令添加到工具列。 在FirstToolWindowCommand.cs類中,添加以下使用指令:

    ```csharp
    using System.Windows.Forms;
    ```

7. 在 FirstToolWindowCommand 類別中,在 ShowToolWindow() 方法的末尾添加以下代碼。 按鈕處理程式命令將在下一節中實現。

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>在工具視窗中實現選單命令

1. 在第一ToolWindowCommand類中,添加一個按鈕Handler方法,該方法調用**打開的文件**對話方塊。 選擇檔案後,它將播放媒體檔。

2. 在 FirstToolWindowCommand 類中,添加對在 FindToolWindow() 方法中創建的 FirstToolWindow 視窗的私有引用。

    ```csharp
    private FirstToolWindow window;
    ```

3. 更改 ShowToolWindow() 方法以設定上面定義的視窗(以便 ButtonHandler 命令處理程式可以存取視窗控制項。 下面是完整的 ShowToolWindow() 方法。

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. 添加 ButtonHandler 方法。 它創建一個 OpenFileDialog 供使用者指定要播放的媒體檔,然後播放所選檔案。

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>設定工具視窗的預設位置

接下來,在工具視窗的 IDE 中指定預設位置。 工具視窗的設定資訊位於*FirstToolWindowPackage.cs*檔中。

1. 在*FirstToolWindowPackage.cs*<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>,在`FirstToolWindowPackage`類上 查找屬性,該屬性將 FirstToolWindow 類型傳遞給構造函數。 要指定預設位置,必須向下面的建構函數添加更多參數。

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    第一個命名參數`Style`是,其`Tabbed`值 為 ,這意味著視窗將是現有視窗中的選項卡。 停靠位置由`Window`參數(n 本例)**指定,即解決方案資源管理員**的 GUID。

    > [!NOTE]
    > 有關 IDE 中視窗類型的詳細資訊,請<xref:EnvDTE.vsWindowType>參閱 。

## <a name="test-the-tool-window"></a>測試工具視窗

1. 按**F5**打開可視化工作室實驗構建的新實例。

2. 在 **「查看」** 選單上,指向**其他視窗**,然後按**一個工具視窗**"。

    媒體播放器工具視窗應打開與**解決方案資源管理器**相同的位置。 如果它仍然顯示與以前相同的位置,請重置視窗佈局(**視窗/重置視窗佈局**)。

3. 按一下工具視窗中的按鈕(具有 **"搜尋**"圖示)。 選擇受支援的聲音或視訊檔,例如 *,C:\windows\media_chimes.wav,* 然後按 **"打開**"。

    你應該聽到提示音。

## <a name="see-also"></a>另請參閱
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)

---
title: 新增工具視窗 |Microsoft Docs
description: 瞭解如何藉由將包含命令的控制項和工具列加入至工具視窗，來建立工具視窗並將它整合至 Visual Studio。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3c84eafcfe19efdf6427db10f65dcf24504b598
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951429"
---
# <a name="add-a-tool-window"></a>新增工具視窗

在這個逐步解說中，您將瞭解如何建立工具視窗，並透過下列方式將它整合到 Visual Studio：

- 將控制項新增至工具視窗。

- 將工具列新增至工具視窗。

- 將命令新增至工具列。

- 執行命令。

- 設定工具視窗的預設位置。

## <a name="prerequisites"></a>必要條件

Visual Studio SDK 在 Visual Studio 安裝程式中包含為選用功能。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-tool-window"></a>建立工具視窗

1. 使用 VSIX 範本來建立名為 **FirstToolWin** 的專案，並新增名為 **FirstToolWindow** 的自訂工具視窗專案範本。

    > [!NOTE]
    > 如需使用工具視窗建立延伸模組的詳細資訊，請參閱 [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)模組。

## <a name="add-a-control-to-the-tool-window"></a>將控制項新增至工具視窗

1. 移除預設控制項。 開啟 *FirstToolWindowControl* ，然後刪除 **Click Me！** 按鈕。

2. 在 [ **工具箱**] 中，展開 [ **所有 WPF 控制項** ] 區段，並將 **Media 元素** 控制項拖曳至 **FirstToolWindowControl** 表單。 選取控制項，然後在 [ **屬性** ] 視窗中，將這個元素命名為 **>mediaelement1.pause**。

## <a name="add-a-toolbar-to-the-tool-window"></a>將工具列新增至工具視窗
以下列方式加入工具列，可確保其漸層和色彩與 IDE 的其餘部分一致。

1. 在 **方案總管** 中，開啟 *FirstToolWindowPackage .vsct*。 *.Vsct* 檔案會使用 XML，在您的工具視窗中定義圖形化使用者介面 (GUI) 元素。

2. 在 `<Symbols>` 區段中，尋找 `<GuidSymbol>` `name` 屬性為的節點 `guidFirstToolWindowPackageCmdSet` 。 將下列兩個專案加入 `<IDSymbol>` 至此節點的專案清單 `<IDSymbol>` 中，以定義工具列和工具列群組。

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. 在 `<Buttons>` 這一節的正上方，建立類似如下的 `<Menus>` 區段：

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

    有幾種不同的功能表。 此功能表是工具視窗中的工具列，由其屬性定義 `type` 。 `guid`和 `id` 設定會組成工具列的完整識別碼。 一般而言， `<Parent>` 功能表的是包含群組。 不過，工具列會定義為其本身的父系。 因此，和元素會使用相同的識別碼 `<Menu>` `<Parent>` 。 `priority`屬性只是 ' 0 '。

4. 工具列類似功能表的許多方式。 例如，就像功能表可能有命令群組一樣，工具列也可以有群組。 功能表上的 (，命令群組會以水平線分隔。 在工具列上，不會以視覺分隔區分隔群組。 ) 

    加入 `<Groups>` 包含元素的區段 `<Group>` 。 這會定義您在區段中宣告之識別碼的群組 `<Symbols>` 。 在 `<Groups>` 區段之後加入區段 `<Menus>` 。

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    藉由將父 GUID 和 ID 設定為工具列的 GUID 和識別碼，您就可以將群組加入至工具列。

## <a name="add-a-command-to-the-toolbar"></a>將命令新增至工具列

在工具列中新增命令，該命令會顯示為按鈕。

1. 在 `<Symbols>` 區段中，于工具列和工具列群組宣告之後，宣告下列 IDSymbol 專案。

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. 在區段內加入 Button 元素 `<Buttons>` 。 此元素將會出現在工具視窗的工具列上， **搜尋** (放大鏡) 圖示。

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

3. 開啟 *FirstToolWindowCommand.cs* ，並在現有欄位之後的類別中新增下列幾行。

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    這樣做可讓您的命令可在程式碼中使用。

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>將 MediaPlayer 屬性新增至 FirstToolWindowControl
從工具列控制項的事件處理常式中，您的程式碼必須能夠存取 Media Player 控制項，也就是 FirstToolWindowControl 類別的子系。

在 **方案總管** 中，以滑鼠右鍵按一下 [ *FirstToolWindowControl*]，按一下 [ **視圖程式碼**]，然後將下列程式碼加入至 FirstToolWindowControl 類別。

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>將工具視窗和工具列具現化
加入工具列和功能表命令，以叫用 [ **開啟** 檔案] 對話方塊並播放選取的媒體檔案。

1. 開啟 *FirstToolWindow.cs* ，並新增下列指示詞 `using` ：

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. 在 FirstToolWindow 類別中，將公用參考加入 FirstToolWindowControl 控制項。

    ```csharp
    public FirstToolWindowControl control;
    ```

3. 在函式的結尾，將此控制項變數設定為新建立的控制項。

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. 在函式內具現化工具列。

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. 此時，FirstToolWindow 的函式看起來應該像這樣：

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

6. 將功能表命令加入至工具列。 在 FirstToolWindowCommand.cs 類別中，新增下列 using 指示詞：

    ```csharp
    using System.Windows.Forms;
    ```

7. 在 FirstToolWindowCommand 類別中，將下列程式碼新增至 ShowToolWindow ( # A1 方法的結尾。 ButtonHandler 命令將會在下一節中執行。

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>在工具視窗中執行功能表命令

1. 在 FirstToolWindowCommand 類別中，新增叫用 [ **開啟** 檔案] 對話方塊的 ButtonHandler 方法。 選取檔案之後，它就會播放媒體檔案。

2. 在 FirstToolWindowCommand 類別中，將私用參考新增至在 FindToolWindow ( # A1 方法中建立的 FirstToolWindow 視窗。

    ```csharp
    private FirstToolWindow window;
    ```

3. 變更 ShowToolWindow ( # A1 方法來設定您在上面定義的視窗 (，讓 ButtonHandler 命令處理常式可以存取視窗控制項。 以下是完整的 ShowToolWindow ( # A1 方法。

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

4. 加入 ButtonHandler 方法。 它會建立 OpenFileDialog，讓使用者指定要播放的媒體檔案，然後播放選取的檔案。

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

接下來，在工具視窗的 IDE 中指定預設位置。 工具視窗的設定資訊位於 *FirstToolWindowPackage.cs* 檔案中。

1. 在 *FirstToolWindowPackage.cs* 中，尋找 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 類別上的屬性，此屬性會將 `FirstToolWindowPackage` FirstToolWindow 類型傳遞給函式。 若要指定預設位置，您必須在下列範例中新增更多參數到此函式。

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    第一個具名引數是 `Style` ，其值為 `Tabbed` ，表示視窗將是現有視窗中的索引標籤。 停駐位置是由 `Window` 參數（在此案例中為 **方案總管** 的 GUID）指定。

    > [!NOTE]
    > 如需 IDE 中視窗類型的詳細資訊，請參閱 <xref:EnvDTE.vsWindowType> 。

## <a name="test-the-tool-window"></a>測試控管視窗

1. 按 **F5** 以開啟 Visual Studio 實驗組建的新實例。

2. 在 [ **View** ] 功能表上，指向 [ **其他視窗** ]，然後按一下 [ **第一個工具視窗]**。

    Media player 工具視窗應該會在 **方案總管** 的相同位置開啟。 如果它仍出現在與之前相同的位置，請重設視窗版面配置 (**視窗/重設視窗** 配置) 。

3. 按一下該按鈕， (工具視窗中) 的 **搜尋** 圖示。 選取支援的音效或影片檔案，例如 *C:\windows\media\chimes.wav*，然後按 [ **開啟**]。

    您應該會聽到鐘聲音效。

## <a name="see-also"></a>另請參閱
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)

---
title: 加入工具視窗 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: 53
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd8c6efd96d8b70f2f23f526041f2f83867bbd2f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245423"
---
# <a name="adding-a-tool-window"></a>新增工具視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本逐步解說，您會學習如何建立工具視窗，並將它整合到 Visual Studio 中，以下列方式：  
  
-   將控制項新增至 [工具] 視窗。  
  
-   將工具列加入工具視窗。  
  
-   您可以將命令加入工具列。  
  
-   實作命令。  
  
-   設定 [工具] 視窗的預設位置。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-tool-window"></a>建立工具視窗  
  
1.  建立專案，名為**FirstToolWin**使用 [VSIX] 範本，然後新增名為的自訂工具視窗項目範本**FirstToolWindow**。  
  
    > [!NOTE]
    >  如需使用工具視窗建立擴充功能的詳細資訊，請參閱[工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="add-a-control-to-the-tool-window"></a>將控制項加入工具視窗  
  
1.  移除預設的控制項。 開啟 FirstToolWindowControl.xaml 並刪除**Click Me ！** 按鈕。  
  
2.  在**工具箱**，展開**所有 WPF 控制項**區段，然後拖曳**媒體元素**控制**FirstToolWindowControl**表單。 選取控制項，然後在**屬性** 視窗中，命名這個項目**mediaElement1**。  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>將工具列新增至 [工具] 視窗  
 藉由新增工具列，以下列方式，確保其漸層和色彩會與 IDE 的其餘部分一致。  
  
1.  在 [**方案總管] 中**，開啟 FirstToolWindowPackage.vsct。 .Vsct 檔會定義使用 XML 工具視窗中的圖形化使用者介面 (GUI) 項目。  
  
2.  在 `<Symbols>`區段中，尋找`<GuidSymbol>`節點的`name`屬性是`guidFirstToolWindowPackageCmdSet`。 新增下列兩個`<IDSymbol>`的清單項目`<IDSymbol>`定義工具列和工具列群組的此節點中的項目。  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  正上方`<Buttons>`區段中，建立`<Menus>`看起來像這樣的區段：  
  
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
  
     有好幾種不同的功能表。 此功能表會在工具視窗中，工具列所定義其`type`屬性。 `guid`和`id`設定組成工具列的完整識別碼。 一般而言，`<Parent>`是功能表的 包含的群組。 不過，工具列會定義為其本身的父系。 因此，相同的識別碼就會用於`<Menu>`和`<Parent>`項目。 `priority`屬性是只是 ' 0'。  
  
4.  工具列會像在許多方面的功能表。 比方說，就像功能表可能會有群組的命令，工具列可能也會有群組。 （在功能表上的命令群組以分隔水平線。 在工具列上的群組不分隔 visual 的分隔線。）  
  
     新增`<Groups>`區段，其中包含`<Group>`項目。 這會定義群組中您宣告其識別碼`<Symbols>`一節。 新增`<Groups>`正後方區段`<Menus>`一節。  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     藉由設定父 GUID 和 ID 的 GUID 和 ID 的工具列，您將群組加入工具列。  
  
## <a name="add-a-command-to-the-toolbar"></a>將命令加入至工具列  
 將命令新增到顯示為按鈕的工具列。  
  
1.  在 `<Symbols>`區段中，宣告下列 IDSymbol 元素後方的工具列和工具列群組宣告。  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  新增按鈕項目內`<Buttons>`一節。 這個項目會出現在 工具 視窗的 搜尋 （放大鏡） 圖示的工具列上。  
  
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
  
3.  開啟 FirstToolWindowCommand.cs 並類別中加入下列幾行，只在現有的欄位之後。  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     如此一來您的命令可讓在程式碼。  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>新增 FirstToolWindowControl MediaPlayer 屬性  
 從工具列控制項的事件處理常式，您的程式碼必須能夠存取 Media Player 控制項，也就是 FirstToolWindowControl 類別的子系。  
  
 中**方案總管**，以滑鼠右鍵按一下 FirstToolWindowControl.xaml，按一下**檢視程式碼**，並將下列程式碼新增至 FirstToolWindowControl 類別。  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>具現化的工具視窗和工具列  
 新增工具列和功能表命令叫用**開啟檔案**對話方塊，並播放選取的媒體檔案。  
  
1.  開啟 FirstToolWindow.cs 並新增下列`using`陳述式。  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  在內部 FirstToolWindow 類別中，加入 FirstToolWindowControl 控制項的公用參考。  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  在建構函式結束時，此控制項將變數設定至新建立的控制項。  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  具現化建構函式內的工具列。  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  此時 FirstToolWindow 建構函式看起來應該像這樣：  
  
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
  
6.  將功能表命令加入工具列。 在 FirstToolWindowCommand.cs 類別中，新增下列 using 陳述式  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
7.  在 FirstToolWindowCommand 類別中加入下列程式碼 ShowToolWindow() 方法的結尾。 在下一節中，將會實作 ButtonHandler 命令。  
  
    ```csharp  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### <a name="to-implement-a-menu-command-in-the-tool-window"></a>在 [工具] 視窗中實作功能表命令  
  
1.  在 FirstToolWindowCommand 類別中，新增 ButtonHandler 方法叫用**開啟檔案**對話方塊。 選取的檔案，它就會播放媒體檔案。  
  
2.  在 FirstToolWindowCommand 類別中加入 FirstToolWindow 視窗 FindToolWindow() 方法中建立私用的參考。  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  變更設定 視窗 （以便 ButtonHandler 命令處理常式可以存取視窗控制項上述定義 ShowToolWindow() 方法。 以下是完整的 ShowToolWindow() 方法。  
  
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
  
4.  新增 ButtonHandler 方法。 它會建立讓使用者指定的媒體檔案，若要播放，OpenFileDialog 然後播放選取的檔案。  
  
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
  
## <a name="set-the-default-position-for-the-tool-window"></a>設定 [工具] 視窗的預設位置  
 接下來，在 IDE 中工具視窗中指定的預設位置。 工具視窗的設定資訊位於 FirstToolWindowPackage.cs 檔案中。  
  
1.  在 FirstToolWindowPackage.cs，尋找<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>屬性上`FirstToolWindowPackage`類別，可將 FirstToolWindow 類型傳遞至建構函式。 若要指定預設位置，您必須新增更多參數建構函式的下列範例。  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     第一個具名的參數是`Style`且其值為`Tabbed`，這表示會將此視窗中現有的視窗的索引標籤。 停駐的位置由指定`Window`參數，此案例中，n 的 GUID**方案總管 中**。  
  
    > [!NOTE]
    >  如需在 IDE 中 windows 類型的詳細資訊，請參閱<xref:EnvDTE.vsWindowType>。  
  
## <a name="testing-the-tool-window"></a>測試工具視窗  
  
1.  按 f5 鍵開啟實驗性 Visual Studio 的新執行個體建置。  
  
2.  在 **檢視**功能表上，指向**其他 Windows** ，然後按一下 **第一個工具視窗**。  
  
     Media player 的工具視窗應該開啟相同的位置**方案總管 中**。 如果它仍會出現在相同的位置之前，重設視窗配置 (**視窗 / 重設視窗配置**)。  
  
3.  在 [工具] 視窗中按一下 （具有 [搜尋] 圖示） 按鈕。 選取支援音訊或視訊檔案，比方說，C:\windows\media\chimes.wav，然後按**開啟**。  
  
     您應該會聽到鐘聲音效。  
  
## <a name="see-also"></a>另請參閱  
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)


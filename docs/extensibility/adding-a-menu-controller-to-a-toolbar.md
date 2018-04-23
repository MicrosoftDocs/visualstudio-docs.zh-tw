---
title: 功能表控制器加入工具列 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63db98df400333216f5e753f8b6f82a61e785cd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>功能表控制器加入工具列
本逐步解決建置於[工具列加入工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)逐步解說，並示範如何將功能表控制器加入至 [工具] 視窗工具列。 如下所示的步驟也可以套用至所建立的工具列[新增工具列](../extensibility/adding-a-toolbar.md)逐步解說。  
  
 功能表控制器是分割控制項。 功能表控制器的左半部顯示上次使用的命令，並按一下它才能執行。 右邊的功能表控制器是箭號，按一下時，會開啟其他命令的清單。 當您按一下在清單中，執行命令的命令，而它會取代左邊功能表控制器上的命令。 如此一來，功能表控制器運作方式與永遠會顯示上次使用的命令，從清單的命令按鈕。  
  
 功能表控制器可以出現在功能表上，但是通常會使用在工具列上。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-menu-controller"></a>建立功能表控制器  
  
#### <a name="to-create-a-menu-controller"></a>若要建立功能表控制器  
  
1.  請依照下列所述的程序[工具列加入工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)建立具有工具列的工具視窗。  
  
2.  在 TWTestCommandPackage.vsct，移至 [符號] 區段。 在名為 GuidSymbol 元素**guidTWTestCommandPackageCmdSet**，功能表控制器、 功能表控制站群組，以及三個功能表項目宣告。  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  在 [功能表] 區段中，最後一個功能表項目之後定義功能表控制器為功能表。  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     `TextChanges`和`TextIsAnchorCommand`旗標必須是包含啟用功能表控制器，以反映選取的最後一個命令。  
  
4.  在 [群組] 區段中，最後一個群組項目之後加入功能表控制站群組。  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     藉由設定功能表控制器做為父系，放置在此群組中任何命令會出現在功能表控制器。 `priority`省略屬性，則可設定為預設值為 0，因為它會在功能表控制站上的唯一群組。  
  
5.  在 [按鈕] 區段中，最後一個按鈕項目之後加入按鈕項目針對每個功能表項目。  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  此時，您可以查看功能表控制器。 建置此專案並開始偵錯。 您應該會看到實驗執行個體。  
  
    1.  在**檢視 / 其他視窗**功能表中，開啟**測試工具視窗**。  
  
    2.  功能表控制器會出現在 [工具] 視窗的工具列上。  
  
    3.  按一下功能表控制器，以查看可能的三個命令右側的箭號。  
  
     請注意，當您按一下命令，功能表控制器的標題變更為顯示該命令。 在下一步 區段中，我們會加入程式碼來啟用這些命令。  
  
## <a name="implementing-the-menu-controller-commands"></a>實作功能表控制器命令  
  
1.  在 TWTestCommandPackageGuids.cs，加入三個功能表項目的命令 Id 之後的現有命令識別碼。  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  在 TWTestCommand.cs，加入下列程式碼頂端的 TWTestCommand 類別。  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  於 TWTestCommand 建構函式的最後一個呼叫之後`AddCommand`方法，將程式碼加入路由每個命令，透過相同的處理常式的事件。  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  將事件處理常式加入 TWTestCommand 類別標示為已檢查選取的命令。  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  加入事件處理常式，會顯示訊息方塊，當使用者選取功能表控制器上的命令：  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>測試功能表控制器  
  
1.  建置此專案並開始偵錯。 您應該會看到實驗執行個體。  
  
2.  開啟**測試工具視窗**上**檢視 / 其他視窗**功能表。  
  
     功能表控制器會出現在工具視窗的工具列中，並顯示**MC 項目 1**。  
  
3.  按一下功能表控制器按鈕左邊的箭號。  
  
     您應該會看到三個項目，其中第一個已選取，並有醒目提示方塊周圍的圖示。 按一下**MC 項目 3**。  
  
     訊息會出現一個對話方塊**選取功能表控制器項目 3**。 請注意，訊息就會對應到功能表控制器按鈕上的文字。 功能表控制器按鈕現在會顯示**MC 項目 3**。  
  
## <a name="see-also"></a>另請參閱  
 [新增工具列加入工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [加入工具列](../extensibility/adding-a-toolbar.md)
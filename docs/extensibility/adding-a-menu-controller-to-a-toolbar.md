---
title: "加入至工具列功能表控制器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具列 [Visual Studio]，新增功能表控制器"
  - "將功能表控制器加入至工具列功能表"
  - "功能表控制站，將加入至工具列"
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# 加入至工具列功能表控制器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此逐步解說建立於 [將工具列新增至工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md) 逐步解說，並示範如何將功能表控制站新增至工具\] 視窗工具列。 如下所示的步驟也可以套用至中建立的工具列 [新增工具列](../extensibility/adding-a-toolbar.md) 逐步解說。  
  
 功能表控制器是分割控制項。 功能表控制站的左側顯示上次使用的命令，並按一下就可以執行。 右側功能表控制器是箭號，按一下就會開啟其他命令的清單。 當您按一下清單中，執行命令的命令，且會取代左側功能表控制站上的命令。 如此一來，功能表控制器的運作方式相似一定會顯示上次使用的命令，從清單中的命令按鈕。  
  
 功能表控制器可以出現在功能表上，但他們最常使用工具列上。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立功能表控制站  
  
#### 建立功能表控制站  
  
1.  請依照下列所述的程序 [將工具列新增至工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md) 來建立具有工具列的工具視窗。  
  
2.  在 TWTestCommandPackage.vsct，移至 \[符號\] 區段。 在名為 GuidSymbol 元素 **guidTWTestCommandPackageCmdSet**, ，宣告您\] 功能表上的控制器、 功能表控制站群組，以及三個功能表項目。  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  在 \[功能表\] 區段中，在最後一個功能表項目之後定義功能表控制器為功能表。  
  
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
  
     `TextChanges` 和 `TextIsAnchorCommand` 旗標必須是包含啟用功能表控制器，以反映所選取的最後一個命令。  
  
4.  群組中一節，在最後一個群組項目之後加入功能表控制站群組。  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     藉由設定功能表控制站做為父系，放在這個群組中任何命令會出現在功能表上的控制器。`priority` 省略屬性，則可設定為預設值為 0，因為它將會在功能表上的控制站上唯一的群組。  
  
5.  在按鈕\] 區段中，在最後一個按鈕項目之後加入按鈕項目每個功能表項目。  
  
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
  
6.  此時，您可以查看功能表控制站。 建置此專案並開始偵錯。 您應該會看到的實驗執行個體。  
  
    1.  在 **檢視 \/ 其他視窗** \] 功能表上，開啟 **測試工具視窗**。  
  
    2.  功能表控制站會出現在 \[工具\] 視窗工具列上。  
  
    3.  按一下功能表控制站，以查看可能的三個命令的右邊的箭號。  
  
     請注意當您按一下命令，以顯示該命令變更功能表控制器的標題。 下一節中，我們將新增程式碼啟動這些命令。  
  
## 實作功能表控制器命令  
  
1.  在 TWTestCommandPackageGuids.cs，加入三個功能表項目的命令 Id 後現有的命令 Id。  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  在 TWTestCommand.cs，加入下列程式碼頂端的 TWTestCommand 類別。  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  在 TWTestCommand 建構函式的最後一個通話之後 `AddCommand` 方法中，加入程式碼來路由傳送每個命令相同的處理常式的事件。  
  
    ```c#  
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
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  加入事件處理常式，會顯示訊息方塊，當使用者選取功能表控制站上的命令 ︰  
  
    ```c#  
    private void OnMCItemClicked(object sender, EventArgs e)  
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
  
## 測試功能表控制器  
  
1.  建置此專案並開始偵錯。 您應該會看到的實驗執行個體。  
  
2.  開啟 **測試工具視窗** 上 **檢視 \/ 其他視窗** 功能表。  
  
     會出現在 \[工具\] 視窗中的工具列\] 功能表上的控制器，並顯示 **MC 項目 1**。  
  
3.  按一下功能表控制器按鈕向左箭號。  
  
     您應該會看到三個項目，其中第一個選取和已反白顯示周圍的方塊圖示。 按一下 \[ **MC 項目 3**。  
  
     訊息會出現一個對話方塊 **選取功能表控制器項目 3**。 請注意，訊息就會對應到功能表控制器按鈕上的文字。 現在會顯示功能表控制器按鈕 **MC 項目 3**。  
  
## 請參閱  
 [將工具列新增至工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [新增工具列](../extensibility/adding-a-toolbar.md)
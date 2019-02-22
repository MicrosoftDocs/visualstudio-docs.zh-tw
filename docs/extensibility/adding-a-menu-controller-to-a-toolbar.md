---
title: 將功能表控制器加入至工具列 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c355ba523bd16cce9d352d483af8c142f0ee439c
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318234"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>將功能表控制器加入工具列
本逐步解說是根據[將工具列加入工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)逐步解說，並示範如何將功能表控制器加入至 [工具] 視窗工具列。 如下所示的步驟也可以套用到在中建立的工具列[新增工具列](../extensibility/adding-a-toolbar.md)逐步解說。

功能表控制器是分割控制項。 功能表控制器的左下的方顯示上次使用的命令，以及您可以按一下它來執行。 右側功能表控制器是箭號，按一下時，會開啟額外的命令清單。 當您按一下在清單中，執行命令的命令，而它會取代左側的功能表控制站上的命令。 如此一來，功能表控制器運作像命令按鈕，一律會顯示上次使用的命令，從清單中。

功能表控制器可以出現在功能表上，但他們最常使用工具列上。

## <a name="prerequisites"></a>必要條件
從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-menu-controller"></a>建立功能表控制器

1. 請依照下列所述的程序[將工具列加入工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)建立工具視窗具有工具列。

2. 在  *TWTestCommandPackage.vsct*，請移至的 Symbols 區段。 在名為 GuidSymbol 元素**guidTWTestCommandPackageCmdSet**，宣告您的功能表控制站、 功能表控制站群組中和三個功能表項目。

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. 在 [功能表] 區段中之後上次的功能表項目，, 定義功能表控制器為功能表。

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

    `TextChanges`和`TextIsAnchorCommand`旗標必須是包含啟用功能表控制站，以反映選取的最後一個命令。

4. 群組中一節，在最後一個群組項目之後加入功能表控制站群組。

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    藉由設定功能表控制站做為父系，放置在此群組中的任何命令會出現在功能表控制站。 `priority`省略屬性，則可將它設定為預設值為 0，因為它是唯一的群組功能表控制站上。

5. 在 [按鈕] 區段中，最後的按鈕項目之後, 加入按鈕項目為每個功能表項目。

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

6. 此時，您可以查看功能表控制站。 建置此專案並開始偵錯。 您應該會看到的實驗執行個體。

   1. 在 **檢視 / 其他 Windows**功能表中，開啟**測試 ToolWindow**。

   2. 功能表控制器會出現在 [工具] 視窗的工具列上。

   3. 按一下右側看到三個可能的命令將功能表控制站上的箭號。

      請注意當您按一下命令時，功能表控制器的標題會變更以顯示該命令。 在下一步 區段中，我們將啟用這些命令的程式碼。

## <a name="implement-the-menu-controller-commands"></a>實作功能表控制器命令

1. 在  *TWTestCommandPackageGuids.cs*，現有的命令識別碼之後加入這三個功能表項目的命令 Id。

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. 在  *TWTestCommand.cs*，在頂端新增下列程式碼`TWTestCommand`類別。

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. 在 TWTestCommand 建構函式的最後一個呼叫之後`AddCommand`方法，加入程式碼以將每個命令，透過相同的處理常式的事件路由。

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

4. 新增事件處理常式**TWTestCommand**類別來標示為已檢查選取的命令。

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. 加入事件處理常式，會顯示 MessageBox，當使用者選取功能表控制站上的命令：

    ```csharp
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

## <a name="testing-the-menu-controller"></a>測試功能表控制器

1. 建置此專案並開始偵錯。 您應該會看到的實驗執行個體。

2. 開啟**測試 ToolWindow**上**檢視 / 其他 Windows**功能表。

    功能表控制器顯示工具視窗的工具列中，並顯示**MC 項目 1**。

3. 按一下功能表控制器按鈕左邊的箭號。

    您應該會看到三個項目，其中第一個已選取，且具有反白顯示方塊周圍的圖示。 按一下  **MC 項目 3**。

    訊息會出現一個對話方塊**選取功能表控制器項目 3**。 請注意，訊息就會對應到功能表控制器按鈕上的文字。 功能表控制器按鈕現在會顯示**MC 項目 3**。

## <a name="see-also"></a>另請參閱
[新增工具列加入工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)  
[新增工具列](../extensibility/adding-a-toolbar.md)

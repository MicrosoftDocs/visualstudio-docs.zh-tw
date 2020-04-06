---
title: 將選單控制器加入工具列 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4dcb9e51f6633476a8f0eadea30da513e5ef760
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740326"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>將選單控制器加入工具列
本演練基於"[將工具列添加到工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)演練"為基礎,演示如何向工具視窗工具列添加功能表控制器。 此處顯示的步驟也可以應用於在[「添加工具列](../extensibility/adding-a-toolbar.md)演練」中創建的工具列。

功能表控制器是拆分控制件。 選單控制器的左側顯示最後使用的命令,您可以通過單擊該命令來運行它。 功能表控制器的右側是一個箭頭,按一下時,將打開其他命令的清單。 按一下清單中的命令時,該命令將運行,並替換功能表控制器左側的命令。 這樣,功能表控制器的操作就像一個命令按鈕,該按鈕始終顯示清單中最後使用的命令。

功能表控制器可以出現在菜單上,但它們最常用於工具列。

## <a name="prerequisites"></a>Prerequisites
從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-menu-controller"></a>建立選單控制器

1. 按照將[工具列添加到工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)中描述的過程來創建具有工具列的工具視窗。

2. 在*TWTest 命令包.vsct 中*,轉到符號部分。 在名為**guidTWTestCommandPackageCmdSet**的 GuidSymbol 元素中,聲明功能表控制器、功能表控制器組和三個功能表項。

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. 在「菜單」部分中,在最後一個功能表條目之後,將功能表控制器定義為功能表。

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

    必須`TextChanges``TextIsAnchorCommand`包含和標誌才能使功能表控制器反映最後一個選定的命令。

4. 在最後一個組條目之後的「組」部分中,添加功能表控制器組。

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    通過將功能表控制器設置為父級,在此組中放置的任何命令都會顯示在菜單控制器中。 省略`priority`該屬性,該屬性將其設置為預設值 0,因為它是菜單控制器上的唯一組。

5. 在最後一個按鈕條目之後,在"按鈕"部分中,為每個功能表項添加一個按鈕元素。

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

6. 此時,您可以查看功能表控制器。 建置此專案並開始偵錯。 您應該會看到實驗實例。

   1. 在 **「查看/其他視窗」** 選單上,打開 **「測試工具視窗**」 。。

   2. 選單控制器將顯示在工具視窗中的工具列上。

   3. 按一下功能表控制器右側的箭頭以查看三個可能的命令。

      請注意,當您按下命令時,功能表控制器的標題將更改以顯示該命令。 在下一節中,我們將添加代碼來啟動這些命令。

## <a name="implement-the-menu-controller-commands"></a>實現選單控制器指令

1. 在*TWTestCommandPackageGuids.cs*中,在現有命令指示後為三個功能表項添加命令。"選項"

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. 在*TWTestCommand.cs*中,在`TWTestCommand`類的頂部添加以下代碼。

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. 在 TWTestCommand 建構函數中,在上次`AddCommand`調用 方法後,添加代碼以透過相同的處理程式路由每個命令的事件。

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

4. 將事件處理程式添加到**TWTestCommand**類,將所選命令標記為已選中。

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

5. 新增在使用者選擇選單控制器上的指令時顯示 MessageBox 的事件處理程式:

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

## <a name="testing-the-menu-controller"></a>測試選單控制器

1. 建置此專案並開始偵錯。 您應該會看到實驗實例。

2. 在 **'查看/ 其他視窗'** 選單上開啟**測試工具視窗**。

    選單控制器顯示在工具視窗中的工具列中,並顯示 MC**專案 1**。

3. 按下箭頭左側的功能表控制器按鈕。

    您應該會看到三個專案,其中第一個項目被選中,並在其圖示周圍有一個突出顯示框。 點選**MC 專案 3**。

    將顯示一個對話框,其中包含 **「您選擇功能表控制器專案 3」。。** 請注意,該消息對應於菜單控制器按鈕上的文本。 選單控制器按鈕現在顯示**MC 專案 3**。

## <a name="see-also"></a>另請參閱
- [加入工具視窗加入工具列](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [新增工具列](../extensibility/adding-a-toolbar.md)

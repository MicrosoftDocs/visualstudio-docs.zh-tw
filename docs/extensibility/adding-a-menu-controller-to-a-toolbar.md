---
title: 將功能表控制器加入至工具列 |Microsoft Docs
description: 瞭解如何建立功能表控制器，並將它新增至 Visual Studio 中的工具視窗工具列，然後執行功能表控制器命令並加以測試。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82da331d93a2208b76bb953f3a6a489913c907ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951520"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>將功能表控制器新增至工具列
本逐步解說是以將 [工具列加入至工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md) 的逐步解說為基礎，並示範如何將功能表控制器加入至工具視窗工具列。 此處所示的步驟也可以套用至在 [ [加入工具列](../extensibility/adding-a-toolbar.md) ] 逐步解說中建立的工具列。

功能表控制器是一個分割控制項。 功能表控制器的左側會顯示上次使用的命令，您可以按一下它來執行它。 功能表控制器的右側是箭號，按一下時會開啟其他命令的清單。 當您按一下清單中的命令時，命令會執行，並取代功能表控制器左邊的命令。 如此一來，功能表控制器的運作方式就像命令按鈕一樣，一律會從清單中顯示最後使用的命令。

功能表控制器可以出現在功能表上，但是最常用於工具列。

## <a name="prerequisites"></a>必要條件
從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-menu-controller"></a>建立功能表控制器

1. 依照 [將工具列加入至工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md) 中所述的程式，建立具有工具列的工具視窗。

2. 在 *TWTestCommandPackage. .vsct* 中，移至 [符號] 區段。 在名為 **guidTWTestCommandPackageCmdSet** 的 GuidSymbol 元素中，宣告功能表控制器、功能表控制器群組和三個功能表項目。

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. 在 [功能表] 區段中，在最後一個功能表項目之後，將功能表控制器定義為功能表。

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

    `TextChanges` `TextIsAnchorCommand` 必須包含和旗標，才能讓功能表控制器反映最後選取的命令。

4. 在 [群組] 區段中，于最後一個群組專案之後，新增功能表控制器群組。

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    藉由將功能表控制器設定為父代，放置在此群組中的任何命令都會出現在功能表控制器中。 `priority`會省略屬性，將其設定為預設值0，因為它是功能表控制器上的唯一群組。

5. 在 [按鈕] 區段中，于最後一個按鈕專案之後，為每個功能表項目加入 Button 元素。

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

6. 此時，您可以查看功能表控制器。 建置此專案並開始偵錯。 您應該會看到實驗實例。

   1. 在 [ **視圖]/[其他視窗** ] 功能表上，開啟 [ **測試控管視窗**]。

   2. 功能表控制器會出現在工具視窗的工具列上。

   3. 按一下功能表控制器右手邊的箭號，以查看三個可能的命令。

      請注意，當您按一下命令時，功能表控制器的標題會變更以顯示該命令。 在下一節中，我們將新增程式碼來啟動這些命令。

## <a name="implement-the-menu-controller-commands"></a>執行功能表控制器命令

1. 在 *TWTestCommandPackageGuids.cs* 中，為您的三個功能表項目加入現有命令識別碼之後的命令識別碼。

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. 在 *TWTestCommand.cs* 中，將下列程式碼加入至類別的頂端 `TWTestCommand` 。

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. 在 TWTestCommand 的函式中，在最後一次呼叫 `AddCommand` 方法之後，新增程式碼，以透過相同的處理常式來路由傳送每個命令的事件。

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

4. 將事件處理常式新增至 **TWTestCommand** 類別，以將選取的命令標示為已核取。

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

5. 新增事件處理常式，以在使用者選取功能表控制器上的命令時顯示 MessageBox：

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

1. 建置此專案並開始偵錯。 您應該會看到實驗實例。

2. 開啟 [視圖]/[**其他視窗**] 功能表上的 [**測試] 工具視窗**。

    功能表控制器會出現在工具視窗的工具列中，並顯示 **MC 專案 1**。

3. 按一下箭號左邊的功能表控制器按鈕。

    您應該會看到三個專案，其中第一個是選取的專案，並在其圖示周圍顯示反白顯示方塊。 按一下 [ **MC 專案 3**]。

    對話方塊隨即出現，並顯示 **您選取的 [功能表控制器專案 3**] 的訊息。 請注意，訊息會對應至功能表控制器按鈕上的文字。 功能表控制器按鈕現在會顯示 **MC 專案 3**。

## <a name="see-also"></a>另請參閱
- [將工具列新增至工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [加入工具列](../extensibility/adding-a-toolbar.md)

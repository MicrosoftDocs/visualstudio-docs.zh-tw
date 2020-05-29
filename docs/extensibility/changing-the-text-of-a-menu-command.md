---
title: 變更功能表命令的文字 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a20d9f29ae86f7946389cafd26d67c244caea7
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183687"
---
# <a name="change-the-text-of-a-menu-command"></a>變更功能表命令的文字
下列步驟示範如何使用服務來變更功能表命令的文字標籤 <xref:System.ComponentModel.Design.IMenuCommandService> 。

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>使用 IMenuCommandService 變更功能表命令標籤

1. `MenuText`使用名為**ChangeMenuText**的功能表命令，建立名為的 VSIX 專案。 如需詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能。

2. 在 *.vsct*檔案中，將旗標新增 `TextChanges` 至您的功能表命令，如下列範例所示。

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. 在*ChangeMenuText.cs*檔案中，建立將在顯示功能表命令之前呼叫的事件處理常式。

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    您也可以變更 <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> 物件上的、和屬性，以更新這個方法中的功能表命令狀態 <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 。

4. 在 ChangeMenuText 的函式中，將原始的命令初始化和位置程式碼取代為建立 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> （而不是 `MenuCommand` ）代表功能表命令的程式碼，加入 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 事件處理常式，並提供功能表命令給功能表命令服務。

    如下所示：

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. 建置此專案並開始偵錯。 Visual Studio 的實驗實例隨即出現。

6. 在 [**工具**] 功能表上，您應該會看到名為 [叫用**ChangeMenuText**] 的命令。

7. 按一下命令。 您應該會看到指出已呼叫**MenuItemCallback**的訊息方塊。 當您關閉訊息方塊時，您應該會看到 [工具] 功能表上的命令名稱現在是**新的文字**。

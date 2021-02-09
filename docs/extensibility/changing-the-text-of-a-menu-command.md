---
title: 變更功能表命令的文字 |Microsoft Docs
description: 藉由查看此程式碼範例，瞭解如何使用 IMenuCommandService 服務來變更功能表命令的文字標籤。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e2d812dbee833358f682b5227785c78322efe44a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911241"
---
# <a name="change-the-text-of-a-menu-command"></a>變更功能表命令的文字
下列步驟顯示如何使用服務來變更功能表命令的文字標籤 <xref:System.ComponentModel.Design.IMenuCommandService> 。

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>使用 IMenuCommandService 變更功能表命令標籤

1. `MenuText`使用名為 **ChangeMenuText** 的功能表命令來建立名為的 VSIX 專案。 如需詳細資訊，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。

2. 在 *.vsct* 檔案中，將旗標新增 `TextChanges` 至您的功能表命令，如下列範例所示。

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

3. 在 *ChangeMenuText.cs* 檔案中，建立將在功能表命令顯示之前呼叫的事件處理常式。

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

    您也可以在 <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> 物件上變更、和屬性，以更新此方法中的功能表命令狀態 <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 。

4. 在 ChangeMenuText 的函式中，以建立 (的程式碼取代原始命令初始化和放置程式碼 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ，而不是 `MenuCommand` 代表功能表命令的) ，加入 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 事件處理常式，並將功能表命令提供給功能表命令服務。

    看起來應該像這樣：

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

6. 在 [ **工具** ] 功能表上，您應該會看到名為 [ **Invoke ChangeMenuText**] 的命令。

7. 按一下命令。 您應該會看到指出已呼叫 **MenuItemCallback** 的訊息方塊。 當您關閉訊息方塊時，您應該會在 [工具] 功能表上看到命令的名稱現在是 **新的文字**。

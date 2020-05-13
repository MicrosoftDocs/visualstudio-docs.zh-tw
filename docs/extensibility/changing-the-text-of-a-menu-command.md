---
title: 變更選單指令的文字 :微軟文件
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
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739841"
---
# <a name="change-the-text-of-a-menu-command"></a>變更選單指令的文字
以下步驟演示如何使用<xref:System.ComponentModel.Design.IMenuCommandService>服務更改功能表命令的文本標籤。

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>使用 IMenu 指令服務變更選單指令標籤

1. 建立`MenuText`VSIX 專案,該專案名為 **「更改選單文字**」的功能表命令。 關於詳細資訊,請參閱[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 在 *.vsct*檔中`TextChanges`,將標誌添加到功能表命令,如以下範例所示。

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

3. 在*ChangeMenuText.cs*檔案中,創建一個事件處理程式,該處理程式將在顯示選單命令之前調用。

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

    還可以<xref:System.ComponentModel.Design.MenuCommand.Visible%2A>透過<xref:System.ComponentModel.Design.MenuCommand.Checked%2A><xref:System.ComponentModel.Design.MenuCommand.Enabled%2A><xref:Microsoft.VisualStudio.Shell.OleMenuCommand>更改物件上的、屬性來更新此方法中的功能表命令的狀態。

4. 在 ChangeMenuText 建構函數中,將原始命令初始化和放置代碼取代為代碼,<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>該代碼 建立`MenuCommand`一個( 而不是 )表示<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>選單命令、添加事件處理程式並將功能表命令授予功能表命令到選單命令服務的代碼。

    下面是它應該是什麼樣子:

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. 建置此專案並開始偵錯。 視覺工作室的實驗實例出現。

6. 在 **'工具'** 選單上,您應該看到名為 **「呼叫變更選單文字**」的命令。

7. 單擊該命令。 您應該會看到訊息框,宣佈已呼叫**MenuItem 回覆**。 當您關閉訊息框時,您應該看到「工具」功能表上的命令的名稱現在是 **「新文字**」。

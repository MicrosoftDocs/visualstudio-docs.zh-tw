---
title: 變更命令的外觀 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739858"
---
# <a name="change-the-appearance-of-a-command"></a>變更指令的外觀
您可以通過更改命令的外觀向使用者提供回饋。 例如,您可能希望命令在不可用時看起來不同。 可以使命令可用或不可用,隱藏或顯示它們,或檢查或取消選中它們。

要變更命令的外觀,可以執行以下操作之一:

- 在命令表檔中的指令定義中指定適當的標誌。

- 使用<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>該服務。

- 實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面並修改原始命令物件。

  以下步驟演示如何使用託管包框架 (MPF) 查找和更新命令的外觀。

### <a name="to-change-the-appearance-of-a-menu-command"></a>變更選單指令的外觀

1. 按照[更改選單命令的文本](../extensibility/changing-the-text-of-a-menu-command.md)中的說明建立`New Text`名為 的 選單項。

2. 在*ChangeMenuText.cs*檔案中, 加入以下使用敘述:

    ```csharp
    using System.Security.Permissions;
    ```

3. 在*ChangeMenuTextPackageGuids.cs*檔中,添加以下行:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. 在*ChangeMenuText.cs*檔案中,將 ShowMessageBox 方法中的代碼取代為以下內容:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. 取得要從物件更新的命令,<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>然後在命令物件上設定相應的屬性。 例如,以下方法使 VSPackage 命令集中的指定命令可用或不可用。 以下代碼使名為"功能表項"`New Text`的功能表項在單擊後不可用。

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))
            as OleMenuCommandService;
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);
        MenuCommand mc = mcs.FindCommand(newCmdID);
        if (mc != null)
        {
            mc.Enabled = enableCmd;
            cmdUpdated = true;
        }
        return cmdUpdated;
    }
    ```

6. 建置此專案並開始偵錯。 應出現視覺工作室的實驗實例。

7. 在 **「工具」** 選單上,按下 **「調用更改選單文字」** 命令。 此時,命令名稱是 **「呼叫變更選單文字**」,因此命令處理程式不呼叫**ChangeMyCommand()**。

8. 在 **'工具'** 選單上,您現在應該看到 **"新文字**"。 按下 **「新文字**」。 該命令現在應該灰顯。

## <a name="see-also"></a>另請參閱
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
- [VS 套件如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [延伸選單與指令](../extensibility/extending-menus-and-commands.md)
- [視覺化工作室命令表 (.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

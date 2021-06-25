---
title: 變更命令的外觀 |Microsoft Docs
description: 瞭解如何提供變更命令外觀的意見反應，例如讓命令可供使用/無法使用、隱藏/顯示或核取/取消核取。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ddeed08d7bc33b9a9ae5405876f3b28459d4eaf2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905029"
---
# <a name="change-the-appearance-of-a-command"></a>變更命令的外觀
您可以藉由變更命令的外觀，將意見反應提供給您的使用者。 例如，您可能會想讓命令在無法使用時看起來不同。 您可以讓命令可供使用或無法使用、隱藏或顯示命令，或是在功能表上核取或取消選取。

若要變更命令的外觀，請執行下列其中一項動作：

- 在命令表格檔案的命令定義中指定適當的旗標。

- 使用 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 服務。

- 執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面並修改原始的命令物件。

  下列步驟示範如何使用 Managed Package Framework (MPF) 來尋找和更新命令的外觀。

### <a name="to-change-the-appearance-of-a-menu-command"></a>變更功能表命令的外觀

1. 依照中的指示， [變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md) ，以建立名為的功能表項目 `New Text` 。

2. 在 *ChangeMenuText .cs* 檔案中，新增下列 using 語句：

    ```csharp
    using System.Security.Permissions;
    ```

3. 在 *ChangeMenuTextPackageGuids .cs* 檔案中，加入下列程式程式碼：

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. 在 *ChangeMenuText .cs* 檔案中，將 ShowMessageBox 方法中的程式碼取代為下列程式碼：

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. 從物件取得您想要更新的命令 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> ，然後在命令物件上設定適當的屬性。 例如，下列方法會讓 VSPackage 命令集的指定命令可供使用或無法使用。 下列程式碼會在按一下功能表項目之後，將它命名為 `New Text` 無法使用。

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.package.GetService<IMenuCommandService, OleMenuCommandService>();
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

6. 建置此專案並開始偵錯。 應該會出現 Visual Studio 的實驗實例。

7. 在 [ **工具** ] 功能表上，按一下 [叫用 **ChangeMenuText** ] 命令。 此時，命令名稱是 **Invoke ChangeMenuText**，因此命令處理常式不會呼叫 **ChangeMyCommand ()**。

8. 在 [ **工具** ] 功能表上，您現在應該會看到 **新的文字**。 按一下 [ **新文字**]。 命令現在應該會呈現灰色。

## <a name="see-also"></a>另請參閱
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
- [Vspackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
- [Visual Studio 命令表格 (。.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

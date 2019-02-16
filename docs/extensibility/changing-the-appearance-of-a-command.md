---
title: 變更命令的外觀 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6446df8f1f3334cac9ebb6e0501a42b3da408455
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317077"
---
# <a name="change-the-appearance-of-a-command"></a>變更命令的外觀
您可以變更命令的外觀，至您的使用者提供意見反應。 比方說，您可能會想看起來不同，無法使用時的命令。 您可以讓命令，可以或無法使用，隱藏或顯示，或核取或取消核取功能表上。

若要變更命令的外觀，執行下列其中一個動作：

- 命令表檔案中的命令定義中指定適當的旗標。

- 使用<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>服務。

- 實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，並修改原始的命令物件。

  下列步驟顯示如何尋找和使用 Managed Package Framework (MPF) 來更新命令的外觀。

### <a name="to-change-the-appearance-of-a-menu-command"></a>若要變更功能表命令的外觀

1. 請依照下列中的指示[變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md)建立功能表項目命名為`New Text`。

2. 在  *ChangeMenuText.cs*檔案中，新增下列 using 陳述式：

    ```csharp
    using System.Security.Permissions;
    ```

3. 在  *ChangeMenuTextPackageGuids.cs*檔案中，新增下面這一行：

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. 在  *ChangeMenuText.cs*檔案中，ShowMessageBox 方法中的程式碼取代為下列：

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. 取得您想要從更新命令<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>物件，然後在命令物件上設定適當的屬性。 例如，下列方法可指定的命令從 VSPackage 的命令集可以或無法使用。 下列程式碼所做的功能表項目命名為`New Text`已按下後無法使用。

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

6. 建置此專案並開始偵錯。 Visual Studio 的實驗執行個體應該會出現。

7. 在 **工具**功能表上，按一下**叫用 ChangeMenuText**命令。 命令名稱是在此時**叫用 ChangeMenuText**，因此不會呼叫命令處理常式**ChangeMyCommand()**。

8. 在 **工具**您現在應該會看到的功能表**新文字**。 按一下 **新的文字**。 此命令應該現在會變成灰色。

## <a name="see-also"></a>另請參閱
[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)  
[Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
[擴充功能表和命令](../extensibility/extending-menus-and-commands.md)  
[Visual Studio 命令表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

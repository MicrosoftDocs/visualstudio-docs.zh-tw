---
title: 變更的命令外觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a19793f16991bc61636a929822757823728a926
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="changing-the-appearance-of-a-command"></a>變更命令的外觀
您可以變更的命令外觀，對使用者提供意見反應。 例如，您可以命令無法使用時的外觀不同。 您可以使用或無法使用，讓命令、 隱藏或顯示它們，或檢查或取消核取功能表上。  
  
 若要變更命令的外觀，執行下列其中一個動作：  
  
-   命令檔中的定義命令資料表中指定適當的旗標。  
  
-   使用<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>服務。  
  
-   實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，並修改原始的命令物件。  
  
 下列步驟顯示如何尋找及使用 Managed Package Framework (MPF) 來更新命令的外觀。  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>若要變更功能表命令的外觀  
  
1.  請依照下列中的指示[變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md)建立功能表項目，名為`New Text`。  
  
2.  在 ChangeMenuText.cs 檔案中，加入下列 using 陳述式：  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  在 ChangeMenuTextPackageGuids.cs 檔案中，加入下列行：  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  在 ChangeMenuText.cs 檔案中，以下列內容取代 ShowMessageBox 方法中的程式碼：  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  取得您想要從更新命令<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>物件，然後在命令物件上設定適當的屬性。 例如，下列方法可讓您指定的命令從 VSPackage 命令設定可用或無法使用。 下列程式碼會在名為功能表`New Text`已按下之後無法使用。  
  
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
        return cmdUpdated;    }  
    }  
    ```  
  
6.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體應該會出現。  
  
7.  在**工具**功能表上，按一下 **叫用 ChangeMenuText**命令。 在此階段的命令名稱已**叫用 ChangeMenuText**，因此命令處理常式不會呼叫 ChangeMyCommand()。  
  
8.  在**工具**您現在應該會看到的功能表**新文字**。 按一下**新文字**。 此命令應該現在會變成灰色。  
  
## <a name="see-also"></a>另請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
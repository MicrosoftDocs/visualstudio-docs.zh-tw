---
title: "變更外觀的命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "變更外觀的命令"
  - "功能表命令，變更外觀"
  - "變更命令外觀的功能表"
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 變更外觀的命令
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以變更外觀的命令，以您的使用者提供意見反應。 例如，您可以看起來不同，無法使用時的命令。 您可以使用或無法使用，讓命令、 隱藏或顯示它們，或檢查或功能表中的那些項目。  
  
 若要變更命令的外觀，執行下列其中一個動作︰  
  
-   指定命令檔中定義命令資料表中的適當旗標。  
  
-   使用 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 服務。  
  
-   實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面，並修改原始的命令物件。  
  
 下列步驟顯示如何尋找及使用管理套件架構 \(MPF\) 來更新命令的外觀。  
  
### 若要變更功能表命令的外觀  
  
1.  依照 [變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md) 建立功能表項目，名為 `New Text`。  
  
2.  在 ChangeMenuText.cs 檔案中，新增下列 using 陳述式︰  
  
    ```c#  
    using System.Security.Permissions;  
    ```  
  
3.  在 ChangeMenuTextPackageGuids.cs 檔案中，加入下列這一行︰  
  
    ```c#  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  在 ChangeMenuText.cs 檔案中，請以下列取代 ShowMessageBox 方法中的程式碼︰  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  取得您想要從更新的命令 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 物件，然後在命令物件上設定適當的屬性。 例如，下列方法會讓您指定的命令從 VSPackage 命令設定可用或無法使用。 下列程式碼所做的功能表項目名為 `New Text` 已按下之後無法使用。  
  
    ```c#  
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
  
7.  在 **工具** \] 功能表上，按一下 \[ **叫用 ChangeMenuText** 命令。 命令名稱現在是 **叫用 ChangeMenuText**, ，因此命令處理常式並不會呼叫 ChangeMyCommand\(\)。  
  
8.  在 **工具** \] 功能表上，您現在應該會看到 **新文字**。 按一下 \[ **新文字**。 此命令應該現在會變成灰色。  
  
## 請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
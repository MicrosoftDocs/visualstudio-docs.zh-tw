---
title: "變更功能表命令的文字 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "變更文字的功能表"
  - "功能表的文字"
  - "變更文字的命令"
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 變更功能表命令的文字
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下列步驟示範如何使用變更功能表命令的文字標籤 <xref:System.ComponentModel.Design.IMenuCommandService> 服務。  
  
## 變更 IMenuCommandService 與功能表命令標籤  
  
1.  建立 VSIX 專案，名為 `MenuText` 與功能表命令名稱為 **ChangeMenuText**。 如需詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  在.vstc 檔案中，加入 `TextChanges` 旗標設為您的功能表命令，如下列範例所示。  
  
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
  
3.  在 ChangeMenuText.cs 檔案中，建立事件處理常式的功能表命令顯示之前呼叫。  
  
    ```c#  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
                    }  
    }  
    ```  
  
     您也可以藉由變更來更新此方法中的功能表命令狀態 <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, ，<xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, ，和 <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> 屬性 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 物件。  
  
4.  ChangeMenuText 建構函式中的原始命令初始化和放置程式碼取代程式碼會建立 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> \(而非 `MenuCommand`\)，表示功能表命令，新增 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 事件處理常式，並可讓功能表命令的功能表命令的服務。  
  
     以下是什麼看起來應該像︰  
  
    ```c#  
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
  
5.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體隨即出現。  
  
6.  在 **工具** 功能表您應該會看到名為命令 **叫用 ChangeMenuText**。  
  
7.  按一下命令。 您應該會看到訊息方塊，表示已呼叫 MenuItemCallback。 當您關閉訊息方塊時，您應該會看到，在 \[工具\] 功能表上的命令名稱現在是 **新文字**。
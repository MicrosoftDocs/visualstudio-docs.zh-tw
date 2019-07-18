---
title: 將功能表命令的文字變更 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8fd3fc01a5dd3e10e633b876b719695d6b26c18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184485"
---
# <a name="changing-the-text-of-a-menu-command"></a>變更功能表命令的文字
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下列步驟示範如何使用變更功能表命令的文字標籤<xref:System.ComponentModel.Design.IMenuCommandService>服務。  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>變更功能表命令標籤與 IMenuCommandService  
  
1. 建立 VSIX 專案，名為`MenuText`功能表命令與名為**ChangeMenuText**。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的擴充](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2. 在.vstc 檔案中，新增`TextChanges`旗標設為您的功能表命令，如下列範例所示。  
  
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
  
3. 在 ChangeMenuText.cs 檔案中，建立功能表命令會顯示之前呼叫的事件處理常式。  
  
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
  
     您也可以藉由變更來更新這個方法中的功能表命令的狀態<xref:System.ComponentModel.Design.MenuCommand.Visible%2A>， <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>，並<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A>上的屬性<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>物件。  
  
4. ChangeMenuText 建構函式中的原始命令初始化和放置程式碼取代程式碼會建立<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>(而非`MenuCommand`)，表示功能表命令，新增<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>事件處理常式，並提供功能表功能表命令服務命令。  
  
     它應該看起來如下：  
  
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
  
5. 建置此專案並開始偵錯。 Visual Studio 的實驗執行個體隨即出現。  
  
6. 在 [**工具**] 功能表您應該會看到名為的命令**叫用 ChangeMenuText**。  
  
7. 按一下 [命令]。 您應該會看到訊息方塊中，宣佈 MenuItemCallback 已呼叫。 當您關閉訊息方塊時，您應該會看到 [工具] 功能表命令的名稱，現在是**新的文字**。

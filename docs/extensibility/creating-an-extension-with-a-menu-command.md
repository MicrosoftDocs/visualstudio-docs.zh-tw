---
title: 建立擴充的功能表命令 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00c80692929ac19b55f68b8aa20306f39ddceae6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-a-menu-command"></a>建立擴充的功能表命令
本逐步解說示範如何建立擴充功能會啟動 [記事本] 的功能表命令。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-menu-command"></a>建立功能表命令  
  
1.  建立 VSIX 專案，名為**FirstMenuCommand**。 您可以找到 VSIX 專案範本，在**新專案**對話方塊底下**Visual C# / 擴充性**。  
  
2.  當專案開啟時，加入名為的自訂命令項目範本**FirstCommand**。 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在**加入新項目**對話方塊中，移至**Visual C# / 擴充性**選取**自訂命令**。 在**名稱**視窗的底部欄位中，將命令檔名稱變更為**FirstCommand.cs**。  
  
3.  建置此專案並開始偵錯。  
  
     Visual Studio 的實驗執行個體隨即出現。 如需實驗執行個體的詳細資訊，請參閱[實驗執行個體的](../extensibility/the-experimental-instance.md)。  
  
4.  在實驗執行個體中，開啟**工具 / 擴充功能和更新**視窗。 您應該會看到**FirstMenuCommand**這裡擴充功能。 (如果您開啟**擴充功能和更新**在 Visual Studio 工作執行個體，您將不會看到**FirstMenuCommand**)。  
  
     現在請移至**工具**實驗執行個體中的功能表。 您應該會看到**叫用 FirstCommand**命令。 此時只會出現訊息方塊，指出 「 FirstCommandPackage 內 FirstMenuCommand.FirstCommand.MenuItemCallback()"。 我們會了解如何實際啟動 「 記事本 」，此命令，在下一節。  
  
## <a name="changing-the-menu-command-handler"></a>變更功能表命令處理常式  
 現在讓我們更新命令處理常式，以啟動 [記事本]。  
  
1.  停止偵錯，並返回至您的 Visual Studio 的工作執行個體。 開啟 FirstCommand.cs 檔案並加入下列 using 陳述式：  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  找到的私用 FirstCommand 建構函式。 這是此命令會連接到命令服務和命令處理常式會指定位置。 變更命令處理常式的名稱來 StartNotepad，如下所示：  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  移除 MenuItemCallback 方法，並加入 StartNotepad 方法，而這個方法會將只會啟動 [記事本]:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  現在試試看。當您開始偵錯的專案，並按一下**工具] / [叫用 FirstCommand**，您應該會看到 「 記事本 」 的執行個體出現。  
  
     您可以使用的執行個體<xref:System.Diagnostics.Process>類別來執行任何的可執行檔中，而不只是 [記事本]。 請嘗試使用 calc.exe，例如。  
  
## <a name="cleaning-up-the-experimental-environment"></a>清除已完成實驗環境  
 如果您正在開發的多個副檔名，或只瀏覽具有不同版本的延伸模組程式碼的結果，在實驗環境可能會停止運作無誤的方式。 在此情況下，您應該執行重設指令碼。 它會呼叫**重設 Visual Studio 2015 實驗執行個體**，而且它隨附的 Visual Studio SDK。 此指令碼移除實驗環境中，從您的擴充功能的所有參考，因此您可以從頭開始。  
  
 您可以取得此指令碼中有兩種：  
  
1.  從桌面，尋找**重設 Visual Studio 2015 實驗執行個體**。  
  
2.  從命令列中，執行下列命令：  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>部署您的擴充功能  
 現在，您已經執行您想要的方式工具擴充功能，就可以考慮共用與朋友或同事開始。 這很容易，只要有安裝 Visual Studio 2015。 您只需要為您建立.vsix 檔案傳送給他們。 （請務必建立在發行模式中）。  
  
 您可以找到這項擴充功能的.vsix 檔 FirstMenuCommand bin 目錄中。 具體來說，假設您已建立此發行組態，它將會是：  
  
 **\<程式碼目錄 > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 若要安裝擴充功能，您的朋友必須關閉所有開啟的 Visual Studio 中，執行個體，然後按兩下.vsix 檔案時，這會顯示**VSIX 安裝程式**。 檔案會複製到**%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions**目錄。  
  
 當您的朋友一次啟動 Visual Studio 時，他會發現 FirstMenuCommand 擴充功能中的**工具 / 擴充功能和更新**。 他可以移至**擴充功能和更新**解除安裝或停用擴充功能，太。  
  
## <a name="next-steps"></a>後續步驟  
 這個逐步解說示範了一小部分的功用與 Visual Studio 擴充功能。 其他 （相當簡單的） 項目，您可以使用 Visual Studio 擴充功能的簡短清單如下：  
  
1.  您可以使用簡單的功能表命令的更多項目：  
  
    1.  新增您自己的圖示：[將圖示加入功能表命令](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  變更功能表命令的文字：[變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  功能表快速鍵加入命令：[繫結功能表項目的鍵盤快速鍵](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  將不同類型的命令、 功能表和工具列加入：[擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)  
  
3.  加入工具視窗，並擴充內建的 Visual Studio 工具視窗：[延伸和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  加入 IntelliSense、 程式碼的建議，和其他功能，對現有程式碼編輯器：[擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  加入您的擴充功能的選項和屬性頁和使用者設定：[擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)和[擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)  
  
 其他類型的擴充功能需要更多工作，例如建立新類型的專案 ([擴充專案](../extensibility/extending-projects.md))，建立新類型的編輯器 ([建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md))，或實作您的擴充功能隔離 shell 中： [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)
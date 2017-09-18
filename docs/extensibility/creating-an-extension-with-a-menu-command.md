---
title: "建立擴充功能的功能表命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "撰寫 vspackage"
  - "vspackage"
  - "教學課程"
  - "visual studio 套件"
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 56
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 56
---
# 建立擴充功能的功能表命令
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說示範如何建立擴充功能會啟動 \[記事本\] 的功能表命令。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立功能表命令  
  
1.  建立 VSIX 專案，名為 **FirstMenuCommand**。 您可以找到 VSIX 專案範本，在 **新的專案** 下的對話方塊 **Visual C\# \/ 擴充性**。  
  
2.  專案開啟時，加入名為的自訂命令項目範本 **FirstCommand**。 在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 在 **加入新項目** \] 對話方塊中，移至 **Visual C\# \/ 擴充性** ，然後選取 **自訂命令**。 在 **名稱** 視窗的底部欄位中，將命令檔名稱變更為 **FirstCommand.cs**。  
  
3.  建置此專案並開始偵錯。  
  
     Visual Studio 的實驗執行個體隨即出現。 如需詳細的實驗執行個體的詳細資訊，請參閱 [實驗執行個體](../extensibility/the-experimental-instance.md)。  
  
4.  在實驗執行個體中，開啟  **工具 \/ 擴充功能和更新** 視窗。 您應該會看到 **FirstMenuCommand** 這裡延伸模組。 \(如果您開啟 **擴充功能和更新** 在 Visual Studio 的工作執行個體，不會看到 **FirstMenuCommand**\)。  
  
     現在請移至 **工具** 實驗執行個體中的功能表。 您應該會看到 **叫用 FirstCommand** 命令。 此時只會出現訊息方塊，指出 「 FirstCommandPackage 內 FirstMenuCommand.FirstCommand.MenuItemCallback\(\) 」。 我們將了解實際啟動 \[記事本\] 下一節中從這個命令。  
  
## 變更功能表命令處理常式  
 現在讓我們更新命令處理常式，以啟動 \[記事本\]。  
  
1.  停止偵錯，並返回您的 Visual Studio 的工作執行個體。 開啟 FirstCommand.cs 檔案並新增下列 using 陳述式:  
  
    ```c#  
    using System.Diagnostics;  
    ```  
  
2.  尋找 private FirstCommand 建構函式。 這是命令連結至命令的服務和命令處理常式會指定位置。 變更命令處理常式的名稱來 StartNotepad，如下所示:  
  
    ```c#  
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
  
3.  移除 MenuItemCallback 方法並新增 StartNotepad 方法只會啟動 \[記事本\]:  
  
    ```c#  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  現在試試看。 當您開始偵錯的專案，然後按一下 **工具\] \/ \[叫用 FirstCommand**, ，您應該會看到 \[記事本\] 的執行個體出現。  
  
     您可以使用的執行個體 <xref:System.Diagnostics.Process> 類別來執行任何的可執行檔中，而不只是 「 記事本 」。 試試看 calc.exe，例如。  
  
## 清除在實驗環境  
 如果您正在開發多個副檔名，或只瀏覽具有不同版本的延伸模組程式碼的結果，您的實驗環境可能會停止運作無誤的方式。 在此情況下，您應該執行重設指令碼。 它會呼叫 **重設 Visual Studio 2015 實驗執行個體**, ，和其隨附於 Visual Studio SDK。 此指令碼移除在實驗環境中，您的擴充功能的所有參考，因此您可以從頭開始。  
  
 您可以取得此指令碼中有兩種:  
  
1.  從桌面上，尋找 **重設 Visual Studio 2015 實驗執行個體**。  
  
2.  從命令列中，執行下列命令:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## 部署您的擴充功能  
 既然您已經執行您想要的方式工具擴充功能，它是時間來思考與朋友和同事共用。 這很簡單，只要它們已安裝 Visual Studio 2015。 您只需要為您所建立的.vsix 檔傳送給他們。 \(請務必建置在發行模式中\)。  
  
 您可以找到此延伸模組的.vsix 檔案 FirstMenuCommand bin 目錄中。 具體而言，假設您已建立的發行組態，則會發生在:  
  
 **\< 程式碼目錄 \> \\FirstMenuCommand\\FirstMenuCommand\\bin\\Release\\ FirstMenuCommand.vsix**  
  
 若要安裝擴充功能，您的朋友必須關閉所有開啟的 Visual Studio 中，執行個體，然後按兩下此.vsix 檔案，這會開啟 **VSIX 安裝程式**。 將檔案複製到 **%LocalAppData%\\Microsoft\\VisualStudio\\14.0\\Extensions** 目錄。  
  
 當您的朋友一次啟動 Visual Studio 時，他會發現 FirstMenuCommand 擴充功能中的 **工具 \/ 擴充功能和更新**。 他可以移至 **擴充功能和更新** 來解除安裝或停用擴充功能，太。  
  
## 後續步驟  
 此逐步解說示範了一小部分您可以執行的功能與 Visual Studio 擴充功能。 以下是使用 Visual Studio 擴充功能可以執行其他 \(很簡單\) 作業的簡短清單:  
  
1.  您可以使用簡單的功能表命令的更多項目:  
  
    1.  新增您自己的圖示: [將圖示加入至功能表命令](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  變更功能表命令的文字: [變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  將功能表捷徑新增至命令: [功能表項目繫結的鍵盤快速鍵](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  加入不同類型的命令、 功能表和工具列: [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)  
  
3.  加入工具視窗，並擴充內建的 Visual Studio 工具視窗: [擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  加入現有的程式碼編輯器的 IntelliSense 和程式碼的建議，以及其他功能: [擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  加入您的擴充功能的選項和屬性頁和使用者設定: [擴充屬性和 \[屬性\] 視窗](../Topic/Extending%20Properties%20and%20the%20Property%20Window.md) 和 [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)  
  
 其他類型的延伸模組需要多一點的工作，例如建立新的專案類型 \([擴充專案](../extensibility/extending-projects.md)\)，建立新的編輯器類型 \([建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)\)，或在獨立的 shell 中實作您的擴充功能: [Visual Studio 隔離 Shell](../extensibility/visual-studio-isolated-shell.md)
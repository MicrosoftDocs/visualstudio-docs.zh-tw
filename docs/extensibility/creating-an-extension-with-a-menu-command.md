---
title: Creating an Extension with 功能表命令 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e8e98a20fafc825af0cf9486c8a9939c02e3b5f
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194518"
---
# <a name="create-an-extension-with-a-menu-command"></a>建立具有功能表命令的擴充功能

本逐步解說示範如何建立擴充功能會啟動 [記事本] 的功能表命令。

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-menu-command"></a>建立功能表命令

1. 建立 VSIX 專案，名為**FirstMenuCommand**。 您可以找到在 VSIX 專案範本**新的專案**藉由搜尋 「 vsix 」 的對話方塊。

2. 當專案開啟時，新增名為的自訂命令項目範本**FirstCommand**。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增** > **新項目**。 在 **加入新項目**對話方塊中，移至**Visual C#** > **擴充性**，然後選取**自訂命令**。 在 **名稱**視窗的底部欄位中，將命令的檔案名稱變更為*FirstCommand.cs*。

3. 建置此專案並開始偵錯。

    Visual Studio 的實驗執行個體隨即出現。 如需詳細的實驗執行個體的詳細資訊，請參閱[實驗的執行個體](../extensibility/the-experimental-instance.md)。

::: moniker range="vs-2017"

4. 在實驗執行個體中，開啟**工具** > **擴充功能和更新**視窗。 您應該會看到**FirstMenuCommand**延伸模組。 (如果您開啟**擴充功能和更新**在您的 Visual Studio 的工作執行個體，您將不會看到**FirstMenuCommand**)。

::: moniker-end

::: moniker range=">=vs-2019"

4. 在實驗執行個體中，開啟**延伸模組** > **管理延伸模組**視窗。 您應該會看到**FirstMenuCommand**延伸模組。 (如果您開啟**管理延伸模組**在您的 Visual Studio 的工作執行個體，您將不會看到**FirstMenuCommand**)。

::: moniker-end

現在請移至**工具**實驗執行個體中的功能表。 您應該會看到**叫用 FirstCommand**命令。 到目前為止，將此命令會顯示訊息方塊，指出**FirstCommandPackage 內 FirstMenuCommand.FirstCommand.MenuItemCallback()**。 我們會看到如何實際從下一節中的此命令啟動 「 記事本 」。

## <a name="change-the-menu-command-handler"></a>變更功能表命令處理常式

現在讓我們更新命令處理常式，以啟動 [記事本]。

1. 停止偵錯，並返回您的 Visual Studio 的工作執行個體。 開啟*FirstCommand.cs*檔案，並新增下列 using 陳述式：

    ```csharp
    using System.Diagnostics;
    ```

2. 找到的私用 FirstCommand 建構函式。 這是命令連結至命令服務和命令處理常式會指定位置。 變更命令處理常式的名稱來 StartNotepad，如下所示：

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. 移除`MenuItemCallback`方法，並新增`StartNotepad`方法，就會啟動 [記事本]:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. 現在試試看。當您開始偵錯的專案，然後按一下**工具** > **叫用 FirstCommand**，您應該會看到出現 [記事本] 的執行個體。

    您可以使用的執行個體<xref:System.Diagnostics.Process>類別來執行任何的可執行檔中，而不只是 「 記事本 」。 與`calc.exe`，例如。

## <a name="clean-up-the-experimental-environment"></a>清除 實驗性的環境

如果您正在開發多個延伸模組，或只瀏覽具有不同版本的延伸模組程式碼的結果，您的實驗環境可能會停止運作的方式，它應該。 在此情況下，您應該執行重設指令碼。 它會呼叫**重設 Visual Studio 的實驗執行個體**，而且它隨附的 Visual Studio SDK。 此指令碼會移除在實驗環境中，您的擴充功能的所有參考，因此您可以從頭開始。

您可以取得此指令碼中有兩種：

1. 從桌面上，尋找**重設 Visual Studio 的實驗執行個體**。

2. 從命令列執行下列命令：

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>將延伸模組部署

已執行您想要的方式工具擴充功能之後，就可以考慮與朋友和同事共用。 也很容易，只要它們已安裝的 Visual Studio 2015。 您只需要會傳送給他們 *.vsix*您建置的檔案。 （請務必在發行模式中建置）。

您可以找到 *.vsix*檔案中此擴充功能*FirstMenuCommand* bin 目錄。 具體來說，假設您已建立的發行組態，它會是：

*\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*

若要安裝擴充功能，您的朋友必須關閉所有開啟的 Visual Studio 中，執行個體，然後按兩下 *.vsix*檔案，其中會顯示**VSIX 安裝程式**。 檔案會複製到 *%LocalAppData%\Microsoft\VisualStudio\<版本 > \Extensions*目錄。

當您的朋友一次啟動 Visual Studio 時，即可在該處找到中的 FirstMenuCommand 延伸模組**工具** > **擴充功能和更新**。 他們可以移至**擴充功能和更新**解除安裝，或太停用延伸模組。

## <a name="next-steps"></a>後續步驟

此逐步解說示範了一小部分的用途與 Visual Studio 擴充功能。 以下是一份您可以使用 Visual Studio 擴充功能執行其他 （很簡單） 項目：

1. 您可以使用簡單的功能表命令的更多項目：

   1. 新增您自己的圖示：[將圖示加入至功能表命令](../extensibility/adding-icons-to-menu-commands.md)

   2. 變更功能表命令文字：[變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md)

   3. 將功能表捷徑新增至命令：[將鍵盤快速鍵繫結至功能表項目](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. 新增不同類型的命令、 功能表和工具列：[擴充功能表和命令](../extensibility/extending-menus-and-commands.md)

3. 加入工具視窗，並擴充內建的 Visual Studio 工具視窗：[擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)

4. 加入現有的程式碼編輯器的 IntelliSense、 程式碼的建議，以及其他功能：[編輯器和語言服務延伸](../extensibility/extending-the-editor-and-language-services.md)

5. 加入您的延伸模組的選項和 [屬性] 頁面和使用者設定：[擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)和[擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)

   其他類型的延伸模組需要多一點的工作，例如建立新的專案類型 ([擴充專案](../extensibility/extending-projects.md))，建立新類型的編輯器 ([建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md))，或實作您在獨立的 shell 中的延伸模組：[Visual Studio 獨立模式 shell](/visualstudio/extensibility/shell/visual-studio-isolated-shell)

---
title: 使用功能表命令建立延伸模組 |Microsoft Docs
description: 瞭解如何使用可啟動 [記事本] 的功能表命令來建立擴充功能。 建立功能表命令，然後變更功能表命令處理常式。
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4ada5870bc06465b97bdf767eb64910f62e15f0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944904"
---
# <a name="create-an-extension-with-a-menu-command"></a>使用功能表命令建立擴充功能

本逐步解說將示範如何使用可啟動 [記事本] 的功能表命令來建立延伸模組。

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-menu-command"></a>建立功能表命令

1. 建立名為 **FirstMenuCommand** 的 VSIX 專案。 您可以藉由搜尋 "vsix"，在 [ **新增專案** ] 對話方塊中找到 VSIX 專案範本。

::: moniker range="vs-2017"

2. 當專案開啟時，加入名為 **FirstCommand** 的自訂命令專案範本。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案**] 對話方塊中，移至 **Visual c #** 擴充性，  >  然後選取 [**自訂命令**]。 在視窗底部的 [ **名稱** ] 欄位中，將命令檔名稱變更為 *FirstCommand.cs*。

::: moniker-end

::: moniker range=">=vs-2019"

2. 當專案開啟時，加入名為 **FirstCommand** 的自訂命令專案範本。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案**] 對話方塊中，移至 [ **Visual c #** 擴充性]，  >  然後選取 [**命令**]。 在視窗底部的 [ **名稱** ] 欄位中，將命令檔名稱變更為 *FirstCommand.cs*。

::: moniker-end

3. 建置此專案並開始偵錯。

    Visual Studio 的實驗實例隨即出現。 如需實驗實例的詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。

::: moniker range="vs-2017"

4. 在實驗實例中，開啟 [**工具**  >  **擴充功能和更新**] 視窗。 您應該會在這裡看到 **FirstMenuCommand** 延伸模組。  (如果您在 Visual Studio 的工作實例中開啟 [ **擴充功能和更新** ]，就不會看到 **FirstMenuCommand**) 。

::: moniker-end

::: moniker range=">=vs-2019"

4. 在實驗實例中，開啟 [**擴充** 功能  >  **管理延伸** 模組] 視窗。 您應該會在這裡看到 **FirstMenuCommand** 延伸模組。  (如果您在 Visual Studio 的工作實例中開啟 [ **管理擴充** 功能]，就不會看到 **FirstMenuCommand**) 。

::: moniker-end

現在，移至實驗實例中的 [ **工具** ] 功能表。 您應該會看到 **Invoke FirstCommand** 命令。 此時，此命令會顯示一個訊息方塊，指出 **FirstCommand 內部 FirstMenuCommand. FirstCommand. MenuItemCallback ( # B1**。 在下一節中，我們將瞭解如何從此命令實際啟動「記事本」。

## <a name="change-the-menu-command-handler"></a>變更功能表命令處理常式

現在讓我們更新命令處理常式以啟動 [記事本]。

1. 停止偵錯工具，並返回 Visual Studio 的工作實例。 開啟 *FirstCommand.cs* 檔案，並新增下列 using 語句：

    ```csharp
    using System.Diagnostics;
    ```

2. 尋找私用 FirstCommand 的函式。 這是將命令連結至命令服務並指定命令處理常式的位置。 將命令處理常式的名稱變更為 StartNotepad，如下所示：

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

3. 移除 `Execute` 方法並新增 `StartNotepad` 方法，這樣就會啟動 [記事本]：

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();

        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. 現在就試試看。當您開始對專案進行偵錯工具並按一下 [**工具** 叫用  >  **FirstCommand**] 時，您應該會看到 [記事本] 的實例。

    您可以使用類別的實例 <xref:System.Diagnostics.Process> 來執行任何可執行檔，而不只是 [記事本]。 `calc.exe`例如，使用來試試看。

## <a name="clean-up-the-experimental-environment"></a>清除實驗環境

如果您正在開發多個擴充功能，或只是使用不同版本的延伸模組程式碼探索結果，您的實驗環境可能會以它的方式停止運作。 在此情況下，您應該執行重設腳本。 這稱為「 **重設」 Visual Studio 實驗實例**，並隨附于 Visual Studio SDK 的一部分。 此腳本會從實驗環境中移除擴充功能的所有參考，讓您可以從頭開始。

您可以透過下列兩種方式之一來取得此腳本：

1. 在桌面上，尋找 **[重設 Visual Studio 實驗實例**]。

2. 從命令列執行下列命令：

    ```cmd
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>部署您的延伸模組

既然您的工具擴充功能以您想要的方式執行，現在就可以考慮將它與您的朋友和同事分享。 只要安裝了 Visual Studio 2015，就很簡單。 您只需要將您所建立的 *.vsix* 檔案傳送給他們。  (請務必在發行模式中進行建立。 ) 

您可以在 *FirstMenuCommand* bin 目錄中找到此延伸模組的 *.vsix 檔案。* 具體來說，假設您已建立發行設定，它將位於：

*\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\FirstMenuCommand.vsix*

若要安裝此擴充功能，您的 friend 必須關閉 Visual Studio 的所有開啟的實例，然後按兩下 *.vsix* 檔，這會顯示 **vsix 安裝程式**。 這些檔案會複製到 *%LocalAppData%\Microsoft\VisualStudio \<version> \Extensions* 目錄。

當您的朋友再次帶出 Visual Studio 時，他們會在 [**工具**  >  **擴充功能和更新**] 中找到 FirstMenuCommand 延伸模組。 它們也可以移至 [ **擴充功能和更新** ]，以卸載或停用延伸模組。

## <a name="next-steps"></a>下一步

本逐步解說只示範了您可以使用 Visual Studio 擴充功能的一小部分。 以下是您可以使用 Visual Studio 擴充功能來執行的其他 (簡單的) 專案清單：

1. 您可以使用簡單的功能表命令來完成更多工：

   1. 新增您自己的圖示： [將圖示新增至功能表命令](../extensibility/adding-icons-to-menu-commands.md)

   2. 變更功能表命令的文字： [變更功能表命令的文字](../extensibility/changing-the-text-of-a-menu-command.md)

   3. 將功能表快捷方式加入至命令：將 [鍵盤快速鍵系結至功能表項目](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. 新增不同類型的命令、功能表和工具列： [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)

3. 新增工具視窗並擴充內建的 Visual Studio 工具視窗： [擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)

4. 將 IntelliSense、程式碼建議和其他功能新增至現有的程式碼編輯器： [延伸編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)

5. 將選項和屬性頁面和使用者設定新增至您的延伸模組： [ [擴充屬性] 和 [屬性] 視窗](../extensibility/extending-properties-and-the-property-window.md) ，並 [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)

   其他類型的延伸模組需要更多的工作，例如建立新的專案類型 (將 [專案擴充](../extensibility/extending-projects.md)) 、建立新的編輯器類型 ([建立自訂編輯器和設計](../extensibility/creating-custom-editors-and-designers.md) 工具) ，或是在隔離的 shell 中執行您的延伸模組： [Visual Studio 獨立模式 shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

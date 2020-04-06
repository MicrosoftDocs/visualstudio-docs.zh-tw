---
title: 使用選單指令建立延伸 |微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739555"
---
# <a name="create-an-extension-with-a-menu-command"></a>使用選單指令建立延伸

本演練演示如何使用啟動記事本的功能表命令創建擴展。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-menu-command"></a>建立選單指令

1. 創建名為**FirstMenu 指令 的**VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。

2. 打開專案時,添加名為**FirstCommand 的**自定義命令項範本。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 在「**新增新項目」** 對話框中,轉到**可視化 C#** > **擴充性**並選擇 **「自訂命令**」。 在視窗底部的**名稱「 欄**位中」,將命令檔名變更為*FirstCommand.cs*。

3. 建置此專案並開始偵錯。

    視覺工作室的實驗實例出現。 有關實驗實例的詳細資訊,請參閱[實驗實例](../extensibility/the-experimental-instance.md)。

::: moniker range="vs-2017"

4. 在實驗例中,打開 **「工具** > **擴展」和「更新」** 視窗。 您應該在此處看到**FirstMenu 命令**擴展。 (如果在 Visual Studio 的工作實例中打開**擴展和更新**,則看不到**FirstMenu 命令**)。

::: moniker-end

::: moniker range=">=vs-2019"

4. 在實驗例中,打開**擴展** > **管理擴展**視窗。 您應該在此處看到**FirstMenu 命令**擴展。 ( 如果在視覺化工作室的工作實體中開啟 **'管理擴展"** 則看不到**FirstMenu 指令**。

::: moniker-end

現在轉到實驗實例中的 **「工具」** 選單。 您應該會看到**呼叫第一指令命令**。 此時,該命令會顯示一個訊息框,其中顯示**FirstMenu 命令中的 FirstCommand 包.FirstCommand.Menuitemcall()**。 我們將在下一節中瞭解如何從該命令實際啟動記事本。

## <a name="change-the-menu-command-handler"></a>變更選單指令處理程式

現在,讓我們更新命令處理程式以啟動記事本。

1. 停止調試並返回可視化工作室的工作實例。 開啟*FirstCommand.cs*檔案並新增以下使用敘述:

    ```csharp
    using System.Diagnostics;
    ```

2. 查找私有 FirstCommand 建構函數。 這是命令連接到命令服務並指定命令處理程式的位置。 將命令處理程式的名稱更改為 StartNotepad,如下所示:

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

3. 刪除`MenuItemCallback`方法並添加`StartNotepad`一個方法,該方法將啟動記事本:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. 現在試試看。當您開始除錯專案並按下 **「工具** > **呼叫第一命令**」時,您應該會看到一個記事本實例出現。

    您可以使用類的<xref:System.Diagnostics.Process>實例來運行任何可執行檔,而不僅僅是記事本。 例如,使用`calc.exe`嘗試。

## <a name="clean-up-the-experimental-environment"></a>清理實驗環境

如果您正在開發多個擴展,或者只是使用擴展代碼的不同版本探索結果,則實驗環境可能會停止以應有的方式工作。 在這種情況下,您應該運行重置腳本。 它被稱為**重置視覺工作室實驗實例**,並作為可視化工作室 SDK 的一部分提供。 此文本從實驗環境中刪除對擴展的所有引用,因此您可以從頭開始。

您可以通過兩種方式之一存取此文稿:

1. 從桌面上,找到**重置可視化工作室實驗實體 。**

2. 從命令列執行下列命令：

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>部署延伸

現在,您的工具擴展程式可以按照您所需的方式運行,是時候考慮與朋友和同事共用它了。 這很容易,只要他們安裝了 Visual Studio 2015。 所有你需要做的是向他們發送你構建的 *.vsix*檔。 (請確保在發佈模式下生成它。

您可以在*FirstMenu 指令*箱目錄中找到此副檔名的 *.vsix*檔案。 具體來說,假設您已經構建了發佈配置,它將在以下版本中:

*\<代碼目錄>_FirstMenu命令\第一選單命令\bin\釋放]第一功能表命令.vsix*

要安裝副檔名,您的好友需要關閉 Visual Studio 的所有開啟實例,然後按兩下 *.vsix*檔案,該檔將啟動**VSIX 安裝程式**。 這些檔案複製到 *%LocalAppData%%\Microsoft_VisualStudio\<版本>\延伸目錄*。

當你的朋友再次提出 Visual Studio 時,他們會在**工具** > **擴展和更新**中找到 FirstMenu 命令擴展。 它們也可以轉到**擴展和更新**以卸載或禁用擴展。

## <a name="next-steps"></a>後續步驟

本演練只顯示使用 Visual Studio 擴展程式可以執行的部分操作。 以下是使用 Visual Studio 擴充可以執行的其他(相當簡單)操作的簡短清單:

1. 您可以使用簡單的選單指令執行更多操作:

   1. 新增您自己的圖示:[向選單指令加入圖示](../extensibility/adding-icons-to-menu-commands.md)

   2. 變更選單指令的文字:[變更選單指令的文字](../extensibility/changing-the-text-of-a-menu-command.md)

   3. 加入指令加入選單快捷方式:[將鍵盤捷徑連結到選單項目](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. 新增不同類型的指令、選單和工具列:[延伸選單和指令](../extensibility/extending-menus-and-commands.md)

3. 新增工具視窗並延伸內建視覺化工作室工具視窗:[擴充與自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)

4. 將 IntelliSense、代碼建議與現有代碼編輯器:[延伸編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)

5. 將選項與屬性頁面與使用者設定新增到副檔名:[擴充屬性與屬性視窗](../extensibility/extending-properties-and-the-property-window.md)並[擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)

   其他類型的延伸需要更多的工作,例如建立一種新型的專案([擴充專案](../extensibility/extending-projects.md),建立新類型的編輯器([建立自訂編輯器和設計器](../extensibility/creating-custom-editors-and-designers.md)),或在隔離 shell 中實現延伸[:Visual Studio 隔離外殼](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

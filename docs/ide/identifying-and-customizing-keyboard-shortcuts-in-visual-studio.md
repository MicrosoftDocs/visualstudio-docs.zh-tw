---
title: "識別及自訂 Visual Studio 中的鍵盤快速鍵 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 280df2197aa7ef9b5e533244831585cb72f7466e
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2017
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>識別及自訂 Visual Studio 中的鍵盤快速鍵

您可以識別 Visual Studio 命令的鍵盤快速鍵、自訂這些捷徑，以及將它們匯出以供其他人使用。 許多捷徑會叫用相同的命令，不過，捷徑的行為可能會因為下列條件而不同：

- 您在第一次執行 Visual Studio (例如，一般開發或 Visual C#) 時選擇了哪些預設的環境設定。

- 您是否曾自訂捷徑的行為。

- 當您選擇捷徑時，是在使用什麼內容。 例如，如果您使用 [設定設計工具]，則 F2 捷徑會叫用 Edit.EditCell 命令，如果使用的是 [Team Explorer]，則會叫用 File.Rename 命令。

不論設定、自訂和內容為何，您一定可以在 [選項] 對話方塊中找到和變更鍵盤快速鍵。 您也可以在[常用命令的預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)中查閱數十個預設鍵盤快速鍵，在[預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-in-visual-studio.md)中尋找所有預設捷徑的完整清單 (以一般開發設定為基礎)。

如果已在全域內容中將捷徑指派給某個命令，而且沒有其他內容，則該捷徑一定會叫用該命令。 不過，捷徑可以在全域內容中指派給某個命令，並在特定的內容中指派給不同命令。 如果您在特定內容中使用這類捷徑，該捷徑會叫用特定內容的命令，而不是全域內容的命令。

> [!NOTE]
> 您的設定和 Visual Studio 版本可能會變更功能表命令的名稱和位置，以及出現在對話方塊中的選項。 本主題是以**一般開發設定**為基礎。

## <a name="identifying-a-keyboard-shortcut"></a>識別鍵盤快速鍵

1. 在功能表列上選擇 [工具] 、[選項] 。

2. 展開 [環境]，然後選擇 [鍵盤]。

   ![顯示 [選項] 對話方塊中的鍵盤快速鍵](../ide/media/optionskeyboard.png "OptionsKeyboard")

3. 在 [顯示包含下列的命令] 方塊中，輸入沒有空格的所有或部分命令的名稱。

   例如，您可以找到 `solutionexplorer` 的命令。

4. 在清單中，選擇正確的命令。

    例如，您可以選擇 [View.SolutionExplorer]。

5. 如果命令已具有鍵盤快速鍵，則會出現在 [所選取命令的快速鍵] 清單中。

   ![檢視所指定命令的捷徑](../ide/media/viewshortcut.png "ViewShortcut")

## <a name="customizing-a-keyboard-shortcut"></a>自訂鍵盤快速鍵

1. 在功能表列上選擇 [工具] 、[選項] 。

2. 展開 [環境] 資料夾，然後選擇 [鍵盤]。

3. 選擇性：在 [顯示包含下列的命令] 方塊中，輸入沒有空格的全部或部分命令名稱，以篩選命令清單。

4. 在清單中，選擇您要指派給鍵盤快速鍵的命令。

在 [新的快速鍵用於] 清單中選擇您要使用捷徑的功能區域。

    For example, you can choose **Global** if you want the shortcut to work in all contexts. You can use any shortcut that isn't mapped (as Global) in another editor. Otherwise, the editor overrides the shortcut.

    > [!NOTE]
    > You can't assign the following keys as part of a keyboard shortcut in **Global**: Print Scrn/Sys Rq, Scroll Lock, Pause/Break, Tab, Caps Lock, Insert, Home, End, Page Up, Page Down, the Windows logo key, the Application key, any of the Arrow keys, or Enter; Num Lock, Delete, or Clear on the numeric keypad; the Ctrl+Alt+Delete key combination.

6. 在 [按快速鍵] 方塊中，輸入您要使用的捷徑。

    > [!NOTE]
    > 您可以建立組合字母與 Alt、Ctrl 或兩者的捷徑。 您也可以建立組合 Shift 鍵與字母，搭配 Alt、Ctrl 或兩者的捷徑。

     如果已將該捷徑指派給其他命令，則該捷徑會出現在 [快速鍵目前已被下列命令所使用] 方塊中。 在這種情況下，請選擇退格鍵以刪除捷徑，再嘗試指派另一個捷徑。

    ![為命令指定不同的捷徑](../ide/media/reassignshortcut.png "ReassignShortcut")

7. 選擇 [指派] 按鈕。

    > [!NOTE]
    > 如果您要為命令指定不同的快速鍵，請選擇 [指派] 按鈕，然後再選擇 [取消] 按鈕，此時對話方塊會關閉，但不會還原變更。

## <a name="sharing-custom-keyboard-shortcuts"></a>共用自訂鍵盤快速鍵

您可以將自訂鍵盤快速鍵匯出至檔案，再將檔案提供給其他人，讓其他人匯入資料，以共用您的自訂鍵盤快速鍵。

### <a name="to-export-only-keyboard-shortcuts"></a>只匯出鍵盤快速鍵

1. 在功能表列上，選擇 [工具]、[匯入和匯出設定]。

2. 選擇 [匯出選取的環境設定]，然後選擇 [下一步] 按鈕。

3. 在 [您要匯出哪一個設定?] 下方，取消選取 [所有設定] 核取方塊，展開 [選項]，然後展開 [環境]。

4. 選取 [鍵盤] 核取方塊，然後選擇 [下一步] 按鈕。

    ![僅匯出自訂的鍵盤快速鍵](../ide/media/exportshortcuts.png "ExportShortcuts")

5. 在 [您要將設定檔命名為什麼?] 和 [在此目錄中儲存我的設定檔] 方塊中，保留預設值或指定不同的值，然後選擇 [完成] 按鈕。

    根據預設，您的捷徑會儲存在 %USERPROFILE%\Documents\Visual Studio 2017\Settings 資料夾的檔案中。 當您匯出設定時，檔案的名稱會反映日期，其副檔名為 .vssettings。

### <a name="to-import-only-keyboard-shortcuts"></a>只匯入鍵盤快速鍵

1. 在功能表列上，選擇 [工具]、[匯入和匯出設定]。

2. 選擇 [匯入選取的環境設定] 選項按鈕，然後選擇 [下一步] 按鈕。

3. 選擇 [否，只需匯入新設定並覆寫目前設定] 選項按鈕，然後選擇 [下一步] 按鈕。

4. 在 [我的設定] 之下，選擇包含您要匯入之捷徑的檔案，或選擇 [瀏覽] 按鈕尋找正確的檔案。

5. 選擇 [下一步] 按鈕。

6.  在 [您要匯入哪一個設定?] 下方，取消選取 [所有設定] 核取方塊，展開 [選項]，然後展開 [環境]。

7. 選取 [鍵盤] 核取方塊，然後選擇 [完成] 按鈕。

    ![僅匯入自訂的鍵盤快速鍵](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>請參閱

[Visual Studio 的協助工具功能](../ide/reference/accessibility-features-of-visual-studio.md)
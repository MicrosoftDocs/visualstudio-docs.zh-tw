---
title: "Visual Studio IDE 導覽 |Microsoft Docs"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 49518c7d38ebbec74908123b83b57bf039dda6f8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>快速入門：Visual Studio IDE 初探

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，我們將簡介部分視窗、功能表和其他 UI 功能。

## <a name="start-page"></a>起始頁

啟動 Visual Studio 之後，首先會看到的畫面應該是「起始頁」。 起始頁有如一個「中樞」，可協助您更快找到所需的命令和專案檔。 [最近使用的] 區段會顯示您最近使用的專案和資料夾。 在 [新增專案] 底下，您可以按一下連結來開啟 [新增專案] 對話方塊，或在 [開啟] 底下，您可以開啟現有的專案或程式碼資料夾。 右側是最新的開發人員新聞摘要。

![VS 起始頁](media/quickstart-IDE-start-page.png)

關閉起始頁之後若要再次顯示，可以從 [檔案] 功能表重新開啟起始頁。

![檔案功能表](media/quickstart-IDE-file-menu-large.png)

為了繼續探索 IDE，讓我們建立一個新專案。

1. 在 [起始頁] 上，於 [新增專案] 下的搜尋方塊中，輸入 `console` 來篩選專案類型清單。 選擇 C# 或 VB [主控台應用程式 (.NET Framework)]。 (或者，如果您是 C++、Javascript 或其他程式設計語言開發人員，則也可以使用其中一種程式設計語言來建立專案。 我們稍後要介紹的 UI 對於所有程式設計語言都很類似)。

1. 在 [新增專案] 對話方塊中，接受預設專案名稱並選擇 [確定]。

   系統隨即建立專案，並在 [編輯器] 視窗中開啟名為 **Program.cs** 或 **Program.vb** 的檔案。 [編輯器] 會顯示檔案的內容，而且您在 Visual Studio 中撰寫程式碼的工作也大部分都在此進行。

## <a name="solution-explorer"></a>底下提供說明，包括方案總管

[方案總管] 會以圖形方式來顯示專案、方案或程式碼資料夾中的檔案和資料夾階層。 您可以在方案總管中瀏覽階層並移至某個檔案。

![底下提供說明，包括方案總管](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menus

IDE 頂端的功能表列可將命令依類別分組。 例如，[專案] 功能表會包含您正在處理的專案相關命令。 在 [工具] 功能表上，您可以選取 [選項] 來自訂 IDE，或選取 [取得工具與功能] 來將功能新增到您的安裝。

![功能表列](media/quickstart-IDE-menu-bar.png)

讓我們選擇 [檢視] 功能表，然後選擇 [錯誤清單]，以開啟 [錯誤清單] 視窗。

## <a name="error-list"></a>錯誤清單

[錯誤清單] 顯示與您程式碼目前狀態相關的錯誤、警告和訊息。 如果您的檔案中或專案中的任何位置有任何錯誤 (如語法錯字)，便會在此處列出。

![錯誤清單](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>輸出視窗

[輸出] 視窗顯示來自「建置」和「原始檔控制」的輸出訊息。

讓我們建置專案以查看一些輸出記錄。 從 [ **建置** ] 功能表中，選擇 [ **建置方案**]。 [輸出] 視窗會自動取得焦點並顯示成功建置訊息。

![輸出視窗](media/quickstart-IDE-output.png)

## <a name="quick-launch"></a>快速啟動

透過 [快速啟動] 方塊可以快速且輕鬆地執行 IDE 中大部分的工作。 您可以輸入想要執行工作的相關文字，它就會顯示與該文字相關的選項清單。 例如，假設我們想要增加建置輸出的詳細資訊，以顯示建置實際執行工作的相關額外記錄資訊：

1. 在 [快速啟動] 方塊中輸入 `verbosity`，然後選擇 [選項] 類別底下的 [專案和方案] -> [建置並執行]。

   ![快速啟動方塊](media/quickstart-IDE-quick-launch.png)

   [選項] 對話方塊會開啟 [建置並執行] 選項頁面。

1. 在 [MSBuild 專案建置輸出詳細等級] 底下，選擇 [一般]，然後按一下 [確定]。

1. 現在我們以滑鼠右鍵按一下 [方案總管] 中的 [ConsoleApp1] 專案，然後選擇快顯功能表中的 [重建]，以再次建置專案。

   [輸出] 視窗這次顯示更多來自建置流程的詳細資訊記錄，包括複製檔案的來源與目的地。

## <a name="send-feedback-menu"></a>[傳送意見反應] 功能表

如果您在使用 Visual Studio 時遇到任何問題，或如果您有改進產品的建議，請使用位於 IDE 頂端 [快速啟動] 方塊旁邊的 [傳送意見反應] 功能表。

![[傳送意見反應] 功能表](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>後續步驟

我們已經介紹了 Visual Studio IDE 的幾個功能，藉以熟悉使用者介面。 若要進一步探索：

- 請瀏覽 VS 文件中的＜一般使用者介面項目＞小節，其中會進一步討論[錯誤清單](../ide/reference/error-list-window.md)、[輸出視窗](../ide/reference/output-window.md)、[屬性視窗](../ide/reference/properties-window.md)和[選項對話方塊](../ide/reference/options-dialog-box-visual-studio.md)等視窗

- 在 [Visual Studio IDE 概觀](../ide/visual-studio-ide.md)中進行更深入的 IDE 導覽，甚至嘗試一些偵錯工作

## <a name="see-also"></a>另請參閱

[快速入門：將 IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)  
[快速入門：在編輯器中編碼](../ide/quickstart-editor.md)  
[快速入門：專案和解決方案](../ide/quickstart-projects-solutions.md)  
---
title: "Visual Studio 中的 Python 互動式 REPL | Microsoft Docs"
description: "如何在 Visual Studio 中使用適用於 Python 程式碼的互動式視窗 (REPL)，以進行快速程式碼開發。"
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 0bd110b671806c37e59f5f0d52c62c1eed42e9cf
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="working-with-the-python-interactive-window"></a>使用 Python 互動式視窗

Visual Studio 為您的每個 Python 環境提供互動式「讀取、求值、輸出」迴圈 (REPL) 視窗，它是以透過命令列上的 `python.exe` 取得的 REPL 為基礎加以改進。 互動式視窗 (以 檢視 > 其他視窗 > &lt;環境&gt; 互動式 功能表命令開啟) 可讓您輸入任意的 Python 程式碼並立即查看結果。 這種編碼方式可協助您了解並實驗應用程式開發介面和程式庫，並以互動方式開發工作程式碼，以包含在您的專案中。

![Python 互動式視窗](media/interactive-window.png)

Visual Studio 有多個 Python REPL 模式可供選擇：

| REPL | 描述 | 編輯 | 偵錯 | 影像 |
| --- | --- | --- | --- | --- |
| 標準 | 預設的 REPL，直接與 Python 交談 | 標準編輯 (多行等)。 | 是，透過 `$attach` | 否 |
| 偵錯 | 預設的 REPL，與已完成偵錯的 Python 程序交談 | 標準編輯 | 僅偵錯 | 否 |
| IPython | REPL 與 IPython 後端交談 | IPython 命令、Pylab 便利性 | 否 | 是，內嵌於 REPL |
| IPython (沒有 Pylab) | REPL 與 IPython 後端交談 | 標準 IPython | 否 | 是，獨立視窗 | 

本文章描述**標準**和**偵錯** REPL 模式。 如需 IPython 模式的詳細資料，請參閱[使用 IPython REPL](interactive-repl-ipython.md)。

如需範例的詳細逐步解說 (包含與編輯器的互動，例如 Ctrl+Enter)，請參閱[教學課程步驟 3：使用互動式 REPL 視窗](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)。 

|   |   |
|---|---|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | [觀看有關互動式視窗的影片 (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567) \(英文\) (2 分 22 秒)。|

## <a name="opening-an-interactive-window"></a>開啟互動式視窗

有多個方式可以開啟環境的互動式視窗。

第一種方式：切換至 [Python 環境] 視窗 ([檢視] > [其他視窗] > [Python 環境] 或 Ctrl-K、Ctrl-`)，並選取所選環境的 [開啟互動式視窗] 命令或按鈕。

![[Python 環境] 視窗中的互動式視窗連結](media/interactive-window-opening.png)

第二種方式：在 [檢視] > [其他視窗] 功能表底部附近，有您預設環境的 **Python 互動式視窗**命令，以及切換至環境視窗的命令：

![[檢視] > [其他視窗] 中的互動式視窗功能表項目](media/interactive-window-menu.png)

第三種方式：您可以選取 [偵錯] > [在 Python Interactive 中執行 [專案 | 檔案]] 功能表命令 (Shift+Alt+F5)，在專案中的啟動檔案上開啟互動式視窗，或是針對獨立檔案開啟互動式視窗：

![在 Python Interactive 功能表中執行專案](media/interactive-execute-project.png)

最後一種方式：您可以選取檔案中的程式碼，並使用於下方描述的[將程式碼傳送至互動式命令](#send-code-to-interactive-command)。

## <a name="interactive-window-options"></a>互動式視窗選項

您可以透過 [工具] > [選項] > [Python 工具] > [互動式視窗] 控制互動式視窗的各方面 (請參閱[選項](python-support-options-and-settings-in-visual-studio.md))：

![Python 互動式視窗選項](media/options-interactive-windows.png)

## <a name="using-the-interactive-window"></a>使用互動式視窗

互動式視窗開啟之後，您即可開始在 `>>>` 提示字元逐行輸入程式碼。 隨著您輸入每行程式碼，互動式視窗就會執行它，這包括匯入模組、定義變數等等：

![Python 互動式視窗](media/interactive-window.png)

例外情況是在需要其他程式碼行以構成完整的陳述式時，例如當 `for` 陳述式的結尾是冒號時，如上所示。 在這些情況下，行提示字元會變更為 `...`，表示您需要輸入該區塊的其他行，如上圖中的第四和第五行所示。 當您在空白行按下 Enter 時，互動式視窗會關閉該區塊，並在解譯器中執行它。

> [!Tip]
> 互動式視窗是以一般的 Python 命令列 REPL 體驗為基礎加以改進，並會自動對屬於周圍範圍的陳述式做出縮排。 其記錄 (以向上鍵重新叫用) 也會提供多行項目，而命令列 REPL 僅提供單行。

<a name="meta-commands"></a> 互動式視窗也支援數個中繼命令。 所有中繼命令的開頭都是 `$`，而且您可以輸入 `$help` 來取得中繼命令清單，並輸入 `$help <command>` 來取得特定命令的詳細使用方式。

| 中繼命令 | 描述 |
| --- | --- |
| `$$` | 插入註解，這對於在工作階段期間為程式碼做出註解非常有用。 |
| `$attach` | 將 Visual Studio 偵錯工具附加至 REPL 視窗程序以啟用偵錯。 |
| `$cls`, `$clear` | 清除編輯視窗的內容，但不變更記錄和執行內容。 |
| `$help` | 顯示命令清單，或特定命令的說明。 |
| `$load` | 從檔案載入命令並執行，直到完成為止。 |
| `$mod` | 將目前的範圍切換到指定的模組名稱。 |
| `$reset` | 將執行環境重設為初始狀態，但保留記錄。 |
| `$wait` | 至少等候指定的毫秒數。 |

命令也是可由 Visual Studio 延伸模組擴充，方法是實作及匯出 `IInteractiveWindowCommand` ([範例](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85))。

## <a name="switching-scopes"></a>切換範圍

根據預設，專案互動式視窗的範圍是設定為專案的啟動檔案，就如同您從命令提示字元執行它一般。 針對獨立的檔案，則會將範圍設定為該檔案。 不過，您在 REPL 工作階段期間隨時可以從互動式視窗頂端的下拉式功能表變更範圍：

![互動式視窗範圍](media/interactive-scopes.png)

匯入模組之後 (例如輸入 `import importlib`)，選項會出現在下拉式清單中，可切換為該模組中任何範圍。 互動式視窗中的訊息也會指出新範圍，讓您可以追蹤在工作階段期間抵達某特定狀態的方式。

在範圍中輸入 `dir()` 會顯示該範圍中的有效識別項，包括函數名稱、類別和變數。 例如，使用 `import importlib` 並接著使用 `dir()` 會顯示如下內容：

![在 importlib 範圍中的互動式視窗](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>

## <a name="send-code-to-interactive-command"></a>將程式碼傳送至互動式命令

除了直接在互動式視窗內操作之外，您也可以在編輯器中選取程式碼，然後選擇 [傳送到 Interactive]，或按 Ctrl + Enter。

![[傳送到 Interactive] 功能表命令](media/interactive-send-to.png)

此命令對於反覆式或演化式程式碼開發非常實用 (包含在開發程式碼時對它進行測試)。 例如，當您將程式碼片段傳送到互動式視窗並查看其輸出之後，您可以按向上鍵以再次顯示該程式碼，修改它，然後按 Ctrl+Enter 來快速測試它。 (在輸入末端按 Enter 鍵將會執行它，但在輸入中間按 Enter 鍵則會插入新的一行)。當您撰寫出所需的程式碼之後，您可以輕鬆地將它複製回您的專案檔案中。

> [!Tip]
> 根據預設，Visual Studio 會移除 >>> 和 ...從互動式視窗將程式碼貼入編輯器中時，REPL 會提示。 您可以在 [工具] > [選項] > [文字編輯器] > [Python] > [進階] 索引標籤上，使用 [貼上移除 REPL 提示] 選項變更此行為。 請參閱[選項 - 其他選項](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)。

<!-- After 15.3 is released, you can also press "Undo" after pasting to restore prompts. Press "Undo" a second time to remove the pasted code entirely. -->

使用程式碼檔案作為剪貼簿時，您經常會有想要一次全部傳送的程式碼小區塊。 若要將程式碼分組在一起，請將程式碼標記為「程式碼儲存格」，方法是在儲存格的開頭，新增以 `#%%` 開始的註解，這會結束前一個儲存格。 程式碼儲存格可以摺疊和展開，在程式碼儲存格內使用 Ctrl + Enter 會將整個儲存格傳送到互動式視窗，然後移至下一個。

Visual Studio 也會偵測以例如 `# In[1]:` 的註解開始的程式碼儲存格，這是您匯出 Jupyter 筆記本作為 Python 檔案時得到的格式。 此項偵測可讓您輕鬆從 [Azure Notebooks](https://notebooks.azure.com/) 執行筆記本，方法是下載為 Python 檔案、在 Visual Studio 中開啟，然後使用 Ctrl + Enter 來執行每個儲存格。

![互動式程式碼儲存格](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense 行為

互動式視窗包含以即時物件為基礎的 IntelliSense，而不像程式碼編輯器的 IntelliSense，僅以原始程式碼分析為基礎。 這些建議在互動式視窗中更加正確，尤其是針對動態產生的程式碼。 缺點是，具有附加作用 (例如記錄訊息) 的函數可能會影響您的開發體驗。

如果此行為會造成問題，請在 [工具] > [選項] > [Python 工具] > [互動式視窗] 底下的 [完成模式] 群組中變更設定，如[選項 - 互動式視窗選項](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)中所述。

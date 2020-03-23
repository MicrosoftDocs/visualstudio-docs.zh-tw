---
title: Python 互動式視窗 (REPL)
description: 在 Visual Studio 中使用互動式視窗 (REPL) 快速進行 Python 程式碼開發。
ms.date: 02/11/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7ceecffec577528484cd67fd13d3e04f368fb916
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302760"
---
# <a name="work-with-the-python-interactive-window"></a>使用 Python 互動式視窗

Visual Studio 為您的每個 Python 環境提供互動式「讀取、求值、輸出」迴圈 (REPL) 視窗，它是以透過命令列上的 *python.exe* 取得的 REPL 為基礎加以改進。 **互動式** 視窗 (以 [檢視]**** > [其他視窗]**** > **&lt;環境&gt; 互動式**功能表命令開啟) 可讓您輸入任意 Python 程式碼並立即查看結果。 這種編碼方式可協助您了解並實驗應用程式開發介面和程式庫，並以互動方式開發工作程式碼，以包含在您的專案中。

![Python 互動式視窗](media/interactive-window.png)

Visual Studio 有多個 Python REPL 模式可供選擇：

| REPL | 描述 | 編輯 | 偵錯 | 影像 |
| --- | --- | --- | --- | --- |
| 標準 | 預設的 REPL，直接與 Python 交談 | 標準編輯 (多行等)。 | 是，透過 `$attach` | 否 |
| 偵錯 | 預設的 REPL，與已完成偵錯的 Python 程序交談 | 標準編輯 | 僅偵錯 | 否 |
| IPython | REPL 與 IPython 後端交談 | IPython 命令、Pylab 便利性 | 否 | 是，內嵌於 REPL |
| IPython (沒有 Pylab) | REPL 與 IPython 後端交談 | 標準 IPython | 否 | 是，獨立視窗 |

本文章描述**標準**和**偵錯** REPL 模式。 如需 IPython 模式的詳細資料，請參閱[使用 IPython REPL](interactive-repl-ipython.md)。

有關示例的詳細演練，包括與編輯器（如**Ctrl**+**Enter）** 的交互，請參閱[教程步驟 3：使用互動式 REPL 視窗](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)。

## <a name="open-an-interactive-window"></a>開啟互動式視窗

有幾種方法可以打開環境的**互動式**視窗。

首先，切換到 Python 環境視窗（**查看** > **其他 Windows** > **Python 環境**或**Ctrl**+**K** > **Ctrl），**+**`** 然後為所選環境選擇 **"打開互動式視窗**"命令或按鈕。

![[Python 環境] 視窗中的互動式視窗連結](media/interactive-window-opening.png)

其次，在 **"查看** > **其他 Windows"** 功能表的底部附近，有一個用於預設環境的**Python 互動式視窗**命令，以及切換到 **"環境"** 視窗的命令：

![[檢視] > [其他視窗] 中的互動式視窗功能表項目](media/interactive-window-menu.png)

第三種方式， 您可以選取 [偵錯]**** > **執行 [專案 | 檔案] > 在 Python \<互動式** 功能表命令 (**Shift**+**Alt**+**F5**) 中，在專案的啟動檔案上開啟**互動式**視窗，或是針對獨立檔案開啟互動式視窗：

![在 Python Interactive 功能表中執行專案](media/interactive-execute-project.png)

最後一種方式：您可以選取檔案中的程式碼，並使用於下方描述的[**傳送互動式命令**](#send-to-interactive-command)。

## <a name="interactive-window-options"></a>互動式視窗選項

您可以透過 [工具]**** > [選項]**** > [Python]**** > [互動式視窗]**** 控制**互動式**視窗的各方面 (請參閱[選項](python-support-options-and-settings-in-visual-studio.md))：

![Python 互動式視窗選項](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>使用互動式視窗

**打開互動式**視窗後，您可以在**\>\>** 提示符處逐行輸入代碼。 **互動式**視窗在輸入每一行時執行每行，其中包括導入模組、定義變數等：

![Python 互動式視窗](media/interactive-window.png)

例外情況是在需要其他程式碼行以構成完整的陳述式時，例如當 `for` 陳述式的結尾是冒號時，如上所示。 在這些情況下，行提示字元會變更為 **...**，表示您需要輸入該區塊的其他行，如上圖中的第四和第五行所示。 當您在空白行上按**Enter**時，**互動式**視窗將關閉塊並在解譯器中運行它。

> [!Tip]
> **互動式**視窗通過自動縮進屬於周圍作用域的語句來改進通常的 Python 命令列 REPL 體驗。 其記錄 (以向上鍵重新叫用) 也會提供多行項目，而命令列 REPL 僅提供單行。

<a name="meta-commands"></a>**互動式**視窗還支援多個元命令。 所有中繼命令的開頭都是 `$`，而且您可以輸入 `$help` 來取得中繼命令清單，並輸入 `$help <command>` 來取得特定命令的詳細使用方式。

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

## <a name="switch-scopes"></a>切換範圍

預設情況下，專案的**互動式**視窗範圍限定為專案的開機檔案，就像從命令提示符運行它一樣。 針對獨立的檔案，則會將範圍設定為該檔案。 不過，您在 REPL 工作階段期間隨時可以從**互動式**視窗頂端的下拉式功能表變更範圍：

![互動式視窗範圍](media/interactive-scopes.png)

匯入模組之後 (例如輸入 `import importlib`)，選項會出現在下拉式清單中，可切換為該模組中任何範圍。 **"互動式"** 視窗中的消息還指示新作用域，因此您可以跟蹤會話期間如何達到特定狀態。

在範圍中輸入 `dir()` 會顯示該範圍中的有效識別項，包括函數名稱、類別和變數。 例如，使用 `import importlib` 並接著使用 `dir()` 會顯示如下內容：

![在 importlib 範圍中的互動式視窗](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>傳送至互動式命令

除了在 **"交互"** 視窗中直接工作外，您還可以在編輯器中選擇代碼，按右鍵，然後選擇"**發送到互動式"** 或按**Ctrl**+**Enter**。

![[傳送到 Interactive] 功能表命令](media/interactive-send-to.png)

此命令對於反覆式或演化式程式碼開發非常實用 (包含在開發程式碼時對它進行測試)。 例如，一旦將一段代碼發送到**互動式**視窗並看到其輸出，就可以按向上箭號再次顯示代碼、修改代碼，並通過按**Ctrl**+**Enter**快速測試代碼。 （按輸入末尾的**Enter**執行它，但按輸入中間的**Enter**將插入一條新線。獲得所需的代碼後，可以輕鬆地將其複製回專案檔案中。

> [!Tip]
> 預設情況下，視覺化工作室刪除**>>>** 和 **...** 將代碼從**互動式**視窗粘貼到編輯器中時，REPL 會提示。 您可以使用"**粘貼刪除 REPL 提示"** 選項在 **"工具** > **選項** > **文字編輯器** > **Python** > **高級"** 選項卡上更改此行為。 請參閱[選項 - 其他選項](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)。

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>使用程式碼儲存格

程式碼儲存格可在資料分析中使用，且各種文字編輯器都支援程式碼儲存格。

例如，使用程式碼檔案作為便箋時，您通常會有要一次全部傳送的一小塊程式碼。 若要將程式碼分組在一起，請將程式碼標記為「程式碼儲存格」**，方法是在儲存格的開頭，新增以 `#%%` 開始的註解，這會結束前一個儲存格。 代碼儲存格可以折疊和展開，在代碼儲存格中使用**Ctrl**+**Enter**將整個儲存格發送到**互動式**視窗並移動到下一個視窗。

Visual Studio 也會偵測以例如 `# In[1]:` 的註解開始的程式碼儲存格，這是您匯出 Jupyter 筆記本作為 Python 檔案時得到的格式。 通過下載為 Python 檔、在 Visual Studio 中打開並使用**Ctrl**+**Enter**運行每個儲存格，此檢測可以輕鬆地從[Azure 筆記本](https://notebooks.azure.com/)運行筆記本。

![互動式程式碼儲存格](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense 行為

**互動式**視窗包括基於即時物件的 IntelliSense，這與 IntelliSense 僅基於原始程式碼分析的代碼編輯器不同。 這些建議在**互動式**視窗中更為正確，尤其是在動態生成的代碼中。 缺點是，具有附加作用 (例如記錄訊息) 的函數可能會影響您的開發體驗。

如果此行為存在問題，則更改 **"完成模式"** 組中**的工具** > **選項** > **Python** > **互動式 Windows**下的設置，如[選項 - 互動式視窗選項](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)中所述。

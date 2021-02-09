---
title: R 互動 REPL
description: 如何在 Visual Studio 中使用整合了編輯器視窗的 R 互動式 REPL 環境。
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 0355f1017bb661b4f72325fb74f60653f69cd182
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878171"
---
# <a name="work-with-the-r-interactive-window"></a>使用 R 互動視窗

Visual Studio R 工具 (RTVS) 所提供的 R 互動視窗也稱為 **REPL** (Read-Evaluate-Print-Loop) 視窗，您可以在其中輸入 R 程式碼，並立即查看結果。 所有模組、語法和變數以及 IntelliSense 都可以在互動式視窗中使用。

互動式視窗也會與一般 R 編輯器視窗整合。 您可以選取程式碼並按下 **Ctrl** + **enter**，或是按一下滑鼠右鍵並選取 [**以互動方式執行**]，然後在互動式視窗中逐行執行程式碼，就像您直接輸入一樣。 當游標在編輯器視窗中的單一行上時， **Ctrl** + **Enter** 會將該行傳送到互動式視窗，然後將游標移至下一行。 如此一來，您就可以重複按下 **Ctrl** + **enter** ，以逐步執行程式碼。

若要體驗這些功能，請遵循[開始使用 R](getting-started-with-r.md) 逐步解說以及本文中的各節。 [程式碼片段](code-snippets-for-r.md)也作用於互動式視窗，就像在 R 編輯器視窗中一樣。

## <a name="overview-of-the-interactive-window"></a>互動式視窗概觀

在行尾鍵入有效的 R 程式碼並按 **Enter**，會執行該行上的程式碼︰

```repl
> 3 + 3
[1] 6
```

在單行輸入的任意位置按 **enter** 鍵也會執行該行。

REPL 中的所有先前輸入和輸出都是唯讀的，無法進行變更。 不過，您隨時都可以從視窗中選取和複製文字，以及貼上文字。 會執行貼上的程式碼，就像它是逐行輸入地一樣。

也就是說，如果您開始鍵入陳述式，並按 **Enter**，則 RTVS 會知道何時必須繼續執行陳述式，並進入左側有 + 提示且適當縮排的多行模式。 RTVS 也會完成括弧、括號和大括弧：

![互動式視窗中的多行陳述式項目](media/repl-multiline-entry.png)

在這個多行模式中，只有在定位於區塊結尾時， **Enter** 鍵才會執行程式碼區塊，否則會插入新的一行。 不過，您可以在任何位置按 **Ctrl** + **enter** ，立即執行該程式碼區塊。

### <a name="toolbar-commands"></a>工具列命令

互動式視窗與其工具列如下︰

![含工具列的互動式視窗](media/repl-window.png)

工具列命令如下所示，其中大部分都具有鍵盤對等專案，而且也可以在 [ **r 工具**]  >  **會話** 和 **r 工具** 的 [  >  **工作目錄**] 功能表 (或如) 所述：

| 按鈕 | 命令 | 按鍵組合 | 說明 |
| --- | --- | --- | --- |
| ![重置按鈕](media/repl-toolbar-01-reset.png) | 重設 | **Ctrl** +**Shift** +**F10** | 重設互動式視窗工作階段，並清除所有變數和歷程記錄。 |
| ![[清除] 按鈕](media/repl-toolbar-02-clear.png) | 清除 | **Ctrl** +**L** | 清除互動式視窗中所顯示的輸出；不會影響工作階段變數或歷程記錄。 |
| ![[歷程記錄] 按鈕](media/repl-toolbar-03-history.png) | 前一個歷程記錄命令<br/>下一個歷程記錄命令 | **向上鍵**、**向下鍵**<br/>**Alt** +**向上**、  + **向下** Alt | 捲動歷程記錄，具有多行程式碼區塊的特定行為。 請參閱[歷程記錄](#history)。 |
| ![[載入工作區] 按鈕](media/repl-toolbar-04-load-workspace.png) | 載入工作區 | n/a | 載入先前儲存的工作區 (請參閱[工作區和工作階段](#workspaces-and-sessions))。 |
| ![[另存工作區為] 按鈕](media/repl-toolbar-05-save-workspace-as.png)| 另存工作區為 | n/a | 將工作階段的目前狀態儲存為工作區 (請參閱[工作區和工作階段](#workspaces-and-sessions))。 |
| ![[來源 R 指令碼] 按鈕](media/repl-toolbar-06-source-r-script.png) | 來源 R 指令碼 | **Ctrl** +**Shift** +**S** | 使用 Visual Studio 編輯器中目前作用中的 R 指令碼來呼叫 `source`，而編輯器會執行程式碼。  只有在 Visual Studio 編輯器中開啟 R 檔案時，才會出現此按鈕。 |
| ![[有回應的來源 R 指令碼] 按鈕](media/repl-toolbar-07-source-r-script-with-echo.png) | 有回應的來源 R 指令碼 | **Ctrl** +**Shift** +**輸入** | 與 [來源 R 指令碼] 相同，但在互動式視窗中顯示指令碼內容。 |
| ![[插斷 R] 按鈕](media/repl-toolbar-08-interrupt-r.png)| 插斷 R | **Esc** | 停止互動式視窗中的任何執行中程式碼，例如，螢幕擷取畫面中的 `while` 迴圈會顯示在此區段的開頭。 |
| ![[附加偵錯工具] 按鈕](media/repl-toolbar-09b-attach-debugger.png)| 附加偵錯工具 | n/a | 也可以使用 **Debug**  >  **Attach to R 互動** 命令。 |
| ![[將工作目錄設定為來源檔案位置] 按鈕](media/repl-toolbar-10-set-working-directory-source.png)| 將工作目錄設定為來源檔案位置 | **Ctrl** +**Shift** +**E** | 將工作目錄設定為載入至互動式視窗的最近來源檔案 (使用 `source`)。 請參閱[工作目錄](#working-directory)。 |
| ![[將工作目錄設定為專案位置] 按鈕](media/repl-toolbar-11-set-working-directory-to-project.png) | 將工作目錄設定為專案位置 | **Ctrl** +**Shift** +**P** | 將工作目錄設定為 Visual Studio 中目前已載入專案的根目錄。 請參閱[工作目錄](#working-directory)。 |
| (文字欄位) | 選取工作目錄 | n/a | 工作目錄的直接輸入欄位。 請參閱[工作目錄](#working-directory)。 |

## <a name="workspaces-and-sessions"></a>工作區和工作階段

在互動式視窗中執行程式碼，會在您目前的工作階段中建置內容。 內容是由全域變數、函式定義、程式庫載入等所組成。 這個內容統稱為「工作區」，而您隨時可以儲存和載入工作區。

選取 [另存工作區為] 按鈕或使用 [R 工具] > [工作階段] > [另存工作區為] 命令會提示您輸入位置和檔案名稱 (預設副檔名為 *.RData*)。

若要使用特定檔案名稱 (預設值為 *.RData*) 來儲存工作區，請按一下 REPL 中的 [儲存工作區] 按鈕：

若要重新載入先前儲存的工作區，請選取 [載入工作區] 按鈕，或使用 [R 工具] > [工作階段] > [載入工作區]，並巡覽至工作區檔案。

[重設] 按鈕或 [R 工具] > [工作階段] > [重設] 可清除工作階段內容。 如果您要使用遠端工作階段，則重設也會刪除遠端電腦上的使用者設定檔，以清除所有儲存在該處的檔案 (請參閱[工作區](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers))。

## <a name="working-directory"></a>工作目錄

開發人員通常會想要變更其在互動式工作階段時的工作目錄。 可在工具列、[ **R 工具**  >  **工作目錄**] 功能表和 [專案] 操作功能表上使用的各種命令，可讓您輕鬆地將工作目錄設定為來源檔案的位置、位置或專案，或任何其他任意位置。 這麼做可協助您在參考檔案時，避免鍵入完整路徑名稱或過長的相對路徑名稱。

## <a name="history"></a>記錄

您在互動式視窗中輸入的每一行，包括從編輯器傳送的行，都會保留在 REPL 的歷程記錄中。 您接著可以使用向上鍵和向下鍵來巡覽歷程記錄，因為您可能習慣使用命令列。

其中一項差異在於，如果您開始在目前這一行上鍵入，並按向上鍵，則目前這行就會保留在歷程記錄中，即使您尚未執行該行也是一樣。

互動式視窗中的歷程記錄也會透過智慧方式與跨多行的其他程式碼區塊的陳述式搭配運作。 使用向上鍵和向下鍵循環查看歷程記錄時，會將多行程式碼區塊擷取為一整個單位，並顯示為目前的項目。 目前，方向鍵會逐行巡覽該程式碼區塊，直到到達頂端或底端。 在程式碼區塊頂端，向上箭號會擷取歷程記錄中的前一個項目；在底端列，向下箭號會擷取下一個項目。

此行為符合一般情況下，使用向上箭號和 **輸入** 按鍵組合來重新執行歷程記錄中最後一個專案的情況，同時自然允許編輯多行程式碼區塊，方法是按向上箭號來流覽。

若要避免流覽至多行程式碼區塊，請使用工具列按鈕或 **alt** + **向上** 和 - **向下** alt，並將所有這類區塊視為單一行。

體驗歷程記錄功能的最簡單方式是在互動式視窗中自行嘗試即可。 下列程式碼提供數個適合的單行和多行陳述式。 不過，個別搭配使用複製並貼上與每個陳述式，可建立適當的歷程記錄  (您也可以將程式碼貼入不同的程式碼檔案，然後使用 **Ctrl** Enter 將這些行傳送至互動式視窗 + ****。 ) 

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```
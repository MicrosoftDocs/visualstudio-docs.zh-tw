---
title: Visual Studio 中的 Python 教學課程步驟 4，偵錯
titleSuffix: ''
description: 在 Visual Studio 中 Python 功能核心逐步解說的步驟 4，涵蓋如何在偵錯工具中執行 Python 程式碼。
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f6464986cb94ffa3ab3cc9264ab818112046ea9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002856"
---
# <a name="step-4-run-code-in-the-debugger"></a>步驟 4：在偵錯工具中執行程式碼

**上一步：[使用互動式 REPL 視窗](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

除了管理專案、提供豐富的編輯體驗以及**互動式**視窗以外，Visual Studio 還針對 Python 程式碼提供完整功能的偵錯。 在偵錯工具中，您可以逐步執行程式碼 (包含迴圈的每個反覆項目)。 只要符合特定條件，您也可以暫停程式。 在偵錯工具中暫停程式的任何時間點，您都可以檢查整個程式狀態，以及變更變數的值。 這類動作是追蹤程式 Bug 的必要項目，也提供仔細遵循確切程式流程的極實用輔助。

1. 將 *PythonApplication1.py* 檔案中的程式碼取代為下列程式碼。 程式碼的這項差異會展開 `make_dot_string`，以在偵錯工具中檢查其離散步驟。 它也會將 `for` 迴圈放在 `main` 函式中，並呼叫該函式來明確執行它：

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(radians(x)) + 20)   # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. 按下 **F5**，或選取 [偵錯] > [開始偵錯] 功能表命令，檢查程式碼運作是否正常。 此命令會在偵錯工具中執行程式碼，但因為您在執行程式時尚未執行任何作業來暫停程式，所以它只會輸出反覆幾次的波浪圖樣。 按任意鍵以關閉輸出視窗。

    > [!Tip]
    > 若要在程式完成時自動關閉輸出視窗，請選取 [工具] > [選項] 功能表命令，展開 [Python] 節點，選取 [偵錯]，然後清除 [處理序正常結束時等候輸入] 選項：
    >
    > ![Python 偵錯選項，可在正常的程式結束下關閉輸出視窗](media/vs-getting-started-python-22-debugging5.png)

1. 在 `for` 陳述式上設定中斷點，方法是按一下該行旁的灰色邊界，或者將插入點放在該行，並使用 [偵錯] > [切換中斷點] 命令 (**F9**)。 灰色邊界會出現紅點，以指出中斷點 (如下方箭號所註)：

    ![設定中斷點](media/vs-getting-started-python-18-debugging1.png)

1. 重新啟動偵錯工具 (**F5**)，您會看到執行中程式碼停在含該中斷點的行。 您可以在這裡檢查呼叫堆疊，並檢查變數。 範圍內的變數在定義時會出現在 [自動變數] 視窗中；您也可以切換至該視窗底部的 [區域變數] 檢視，以顯示 Visual Studio 在目前範圍中找到的所有變數 (包含函式)，即使在定義之前也是一樣：

    ![Python 的中斷點 UI 體驗](media/vs-getting-started-python-19-debugging2b.png)

1. 觀察 Visual Studio 視窗頂端的偵錯工具列 (如下所示)。 此工具列可快速存取最常見的偵錯命令 (這也可以在 [偵錯] 功能表上找到)：

    ![基本偵錯工具列按鈕](media/vs-getting-started-python-20-debugging3.png)

    從左到右的按鈕如下：
    - [繼續] (**F5**) 會執行程式，直到下一個中斷點或程式完成。
    - [全部中斷] (**Ctrl**+**Alt**+**Break**) 會暫停長時間執行的程式。
    - [停止偵錯] (**Shift**+**F5**) 會停止程式 (不管程式在哪裡)，並結束偵錯工具。
    - [重新啟動] (**Ctrl**+**Shift**+**F5**) 會停止程式 (不管程式在哪裡)，並在偵錯工具中從頭重新啟動它。
    - [顯示下一個陳述式] (**Alt**+**Num** **&#42;**) 會切換至下一行要執行的程式碼。 如果您在偵錯工作階段期間巡覽程式碼，而且想要快速回到偵錯工具的暫停點，則這極有幫助。
    - [逐步執行] (**F11**) 會執行下個程式碼行，以進入所呼叫的函式。
    - [不進入函式] (**F10**) 會執行下個程式碼行，而不進入所呼叫的函式。
    - [跳離函式] (**Shift**+**F11**) 會執行目前函式的其餘部分，並暫停於發出呼叫的程式碼。

1. 使用 [不進入函式]，不進入 `for` 陳述式。 「逐步執行」表示偵錯工具執行目前程式碼行 (包含任何函式呼叫)，然後再次立即暫停。 請注意，現在於 [區域變數] 和 [自動變數] 視窗中如何定義變數 `i`。

1. 不進入可呼叫 `make_dot_string` 並暫停的下個程式碼行。 [不進入函式] 這裡特別表示偵錯工具會在傳回時執行整個 `make_dot_string` 並暫停。 除非該函式有個別的中斷點，否則偵錯工具不會停止在該函式內部。

1. 繼續逐步執行程式碼數次，並觀察 [區域變數] 或 [自動變數] 視窗中的值如何變更。

1. 在 [區域變數] 或 [自動變數] 視窗中，按兩下 `i` 或 `s` 變數的 [值] 資料行，以編輯值。 按 **Enter** 或按一下該值外部，以套用任何變更。

1. 使用 [逐步執行]，繼續逐步執行程式碼。 [逐步執行] 表示偵錯工具進入具有偵錯資訊的任何函式呼叫 (例如 `make_dot_string`)。 位在 `make_dot_string` 內之後，您可以檢查其區域變數，並特別逐步執行其程式碼。

1. 繼續逐步執行 [逐步執行]，並注意到，當您到達 `make_dot_string` 結尾時，下個步驟會回到 `s` 變數中具有新傳回值的 `for` 迴圈。 當您再次逐步執行到 `print` 陳述式時，會注意到對 `print` 的 [逐步執行] 不會進入該函式。 原因是 `print` 不是以 Python 撰寫，而是 Python 執行階段內的原生程式碼。

1. 繼續使用 [逐步執行]，直到您再次到達 `make_dot_string`。 然後使用 [跳離函式]，並注意到，您回到 `for` 迴圈。 使用 [跳離函式]，偵錯工具會執行函式的其餘部分，然後在發出呼叫的程式碼中自動暫停。 如果您逐步執行您想要偵錯之較長函式的某個部分，但不需要逐步執行其餘部分，也不想要在要呼叫的程式碼中設定明確的中斷點，則這十分有用。

1. 若要繼續執行程式，直到達到下一個中斷點，請使用 [繼續] (**F5**)。 因為您在 `for` 迴圈中有中斷點，所以會在下一個反覆項目中斷。

1. 逐步執行迴圈中的數百個反覆項目可能十分冗長，因此 Visual Studio 可讓您將「條件」新增至中斷點。 偵錯工具接著只會在符合條件時，將程式暫停於中斷點。 例如，您可以在 `for` 陳述式上使用含中斷點的條件，讓它只在 `i` 的值超過 1600 時暫停。 若要設定此條件，請以滑鼠右鍵按一下中斷點紅點，然後選取 [條件] (**Alt**+**F9** > **C**)。 在出現的 [中斷點設定] 快顯視窗中，輸入 `i > 1600` 作為運算式，然後選取 [關閉]。 按 **F5** 繼續執行，並觀察程式在下一個中斷之前反覆執行多次。

    ![設定中斷點條件](media/vs-getting-started-python-21-debugging4.png)

1. 若要執行程式直到完成，請按一下滑鼠右鍵並選取 [停用中斷點] (**Ctrl**+**F9**) 來停用中斷點。 然後選取 [繼續] (或按 **F5**) 以 執行程式。 程式結束時，Visual Studio 會停止其偵錯工作階段，並回復為其編輯模式。 請注意，您也可以按一下中斷點來刪除中斷點，但這也會刪除任何您已設定的條件。

> [!Tip]
> 在某些情況下 (例如，無法啟動 Python 解譯器本身)，輸出視窗只會短暫出現後自動關閉，而不讓您看到任何錯誤訊息。 如果發生這種情況，請以滑鼠右鍵按一下 [方案總管] 中的專案，並選取 [屬性]，再選取 [偵錯] 索引標籤，然後將 `-i` 新增至 [解譯器引數] 欄位。 此引數會導致解譯器在程式完成之後進入互動模式，並在您輸入 **Ctrl**+**Z** > **Enter** 結束之前保持視窗開啟。

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Python 環境中安裝套件](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>深入了解

- [偵錯](debugging-python-in-visual-studio.md)
- [Visual Studio 偵錯](../debugger/debugger-feature-tour.md)提供 Visual Studio 偵錯功能的完整文件。

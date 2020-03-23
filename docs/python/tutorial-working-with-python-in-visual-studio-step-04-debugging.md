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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "63002856"
---
# <a name="step-4-run-code-in-the-debugger"></a>步驟 4：在偵錯工具中執行程式碼

**上一個步驟：[使用互動式 REPL 視窗](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

除了管理專案、提供豐富的編輯體驗和**互動式**視窗外，Visual Studio 還為 Python 代碼提供功能齊全的調試。 在偵錯工具中，您可以逐步執行程式碼 (包含迴圈的每個反覆項目)。 只要符合特定條件，您也可以暫停程式。 在偵錯工具中暫停程式的任何時間點，您都可以檢查整個程式狀態，以及變更變數的值。 這類動作是追蹤程式 Bug 的必要項目，也提供仔細遵循確切程式流程的極實用輔助。

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

1. 按下 **F5**，或選取 [偵錯]**** > [開始偵錯]**** 功能表命令，檢查程式碼運作是否正常。 此命令會在偵錯工具中執行程式碼，但因為您在執行程式時尚未執行任何作業來暫停程式，所以它只會輸出反覆幾次的波浪圖樣。 按任意鍵以關閉輸出視窗。

    > [!Tip]
    > 要在程式完成後自動關閉輸出視窗，請選擇 **"工具** > **選項"** 功能表命令，展開**Python**節點，選擇 **"調試**"，然後在**進程正常退出時清除"等待輸入**"選項：
    >
    > ![Python 偵錯選項，可在正常的程式結束下關閉輸出視窗](media/vs-getting-started-python-22-debugging5.png)

1. 通過按一下該行在灰色`for`邊距中按一下一次，或者將撥圖放在該行中並使用**調試** > **切換中斷點**命令 **（F9），** 在語句上設置中斷點。 灰色邊界會出現紅點，以指出中斷點 (如下方箭號所註)：

    ![設定中斷點](media/vs-getting-started-python-18-debugging1.png)

1. 再次啟動調試器 （**F5**），並看到運行代碼停止與該中斷點行。 您可以在這裡檢查呼叫堆疊，並檢查變數。 範圍內的變數在定義時會出現在 [自動變數]**** 視窗中；您也可以切換至該視窗底部的 [區域變數]**** 檢視，以顯示 Visual Studio 在目前範圍中找到的所有變數 (包含函式)，即使在定義之前也是一樣：

    ![Python 的中斷點 UI 體驗](media/vs-getting-started-python-19-debugging2b.png)

1. 觀察 Visual Studio 視窗頂端的偵錯工具列 (如下所示)。 此工具列可快速存取最常見的偵錯命令 (這也可以在 [偵錯]**** 功能表上找到)：

    ![基本偵錯工具列按鈕](media/vs-getting-started-python-20-debugging3.png)

    從左到右的按鈕如下：
    - **繼續**（**F5**） 運行程式，直到下一個中斷點或直到程式完成。
    - **中斷所有**（**Ctrl**+**Alt**+**中斷**） 暫停一個長期運行的程式.
    - **停止調試**（**Shift**+**F5**） 停止程式，無論它在哪裡，並退出調試器。
    - **重新開機**（**Ctrl**+**Shift**+**F5**） 停止程式，無論它在哪裡，並從調試器的開頭重新開機它。
    - [顯示下一個陳述式]**** (**Alt**+**Num** **&#42;**) 會切換至下一行要執行的程式碼。 如果您在偵錯工作階段期間巡覽程式碼，而且想要快速回到偵錯工具的暫停點，則這極有幫助。
    - **進入**（**F11**） 運行下一行代碼，輸入調用的函數。
    - **單一步驟**（**F10**） 在不進入調用函數的情況下運行下一行代碼。
    - **"退出****"（Shift**+**F11）** 運行當前函數的其餘部分並在調用代碼中暫停。

1. 使用 [不進入函式]****，不進入 `for` 陳述式。 「逐步執行」** 表示偵錯工具執行目前程式碼行 (包含任何函式呼叫)，然後再次立即暫停。 請注意，現在於 [區域變數]**** 和 [自動變數]**** 視窗中如何定義變數 `i`。

1. 不進入可呼叫 `make_dot_string` 並暫停的下個程式碼行。 **此處的"一步一步**"特別意味著調試器運行`make_dot_string`整個 調試器，並在返回時暫停。 除非該函式有個別的中斷點，否則偵錯工具不會停止在該函式內部。

1. 繼續逐步執行程式碼數次，並觀察 [區域變數]**** 或 [自動變數]**** 視窗中的值如何變更。

1. 在 [區域變數]**** 或 [自動變數]**** 視窗中，按兩下 `i` 或 `s` 變數的 [值]**** 資料行，以編輯值。 按 **"輸入"** 或按一下該值外部以應用任何更改。

1. 使用 [逐步執行]****，繼續逐步執行程式碼。 **"進一步"** 表示調試器進入具有調試資訊的任何函式呼叫（如`make_dot_string`） 位在 `make_dot_string` 內之後，您可以檢查其區域變數，並特別逐步執行其程式碼。

1. 繼續步**進**，並注意，當您到達 的`make_dot_string`末尾時，下一步將返回`for`迴圈，並在`s`變數中使用新的傳回值。 當您再次步步到語句`print`時，請注意 **，Step** enter `print` on 不會進入該函數。 原因是 `print` 不是以 Python 撰寫，而是 Python 執行階段內的原生程式碼。

1. 繼續使用 **"進入"，** 直到您再次進入`make_dot_string`。 然後使用 [跳離函式]****，並注意到，您回到 `for` 迴圈。 使用 **"退出"** 時，調試器運行函數的其餘部分，然後在調用代碼中自動暫停。 如果您逐步執行您想要偵錯之較長函式的某個部分，但不需要逐步執行其餘部分，也不想要在要呼叫的程式碼中設定明確的中斷點，則這十分有用。

1. 要繼續運行程式直到達到下一個中斷點，請使用 **"繼續**"**（F5**）。 因為您在 `for` 迴圈中有中斷點，所以會在下一個反覆項目中斷。

1. 逐步執行迴圈中的數百個反覆項目可能十分冗長，因此 Visual Studio 可讓您將「條件」** 新增至中斷點。 偵錯工具接著只會在符合條件時，將程式暫停於中斷點。 例如，您可以在 `for` 陳述式上使用含中斷點的條件，讓它只在 `i` 的值超過 1600 時暫停。 若要設定此條件，請以滑鼠右鍵按一下中斷點紅點，然後選取 [條件]**** (**Alt**+**F9** > **C**)。 在出現的 [中斷點設定]**** 快顯視窗中，輸入 `i > 1600` 作為運算式，然後選取 [關閉]****。 按**F5**繼續觀察程式在下一次中斷之前運行多個反覆運算。

    ![設定中斷點條件](media/vs-getting-started-python-21-debugging4.png)

1. 要運行程式以完成，請通過按右鍵並選擇**禁用中斷點****（Ctrl**+**F9**） 來禁用中斷點。 然後選擇 **"繼續**"（或按**F5**） 以運行該程式。 程式結束時，Visual Studio 會停止其偵錯工作階段，並回復為其編輯模式。 請注意，您也可以按一下中斷點來刪除中斷點，但這也會刪除任何您已設定的條件。

> [!Tip]
> 在某些情況下 (例如，無法啟動 Python 解譯器本身)，輸出視窗只會短暫出現後自動關閉，而不讓您看到任何錯誤訊息。 如果發生這種情況，請按右鍵**解決方案資源管理器**中的專案，選擇 **"屬性**"，選擇 **"調試"** 選項卡，然後`-i`添加到 **"解譯器參數"** 欄位中。 此參數會導致解譯器在程式完成後進入互動式模式，從而使視窗保持打開狀態，直到進入**Ctrl**+**Z** > **Enter**退出。

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Python 環境中安裝套件](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>深入了解

- [偵錯](debugging-python-in-visual-studio.md)
- [Visual Studio 偵錯](../debugger/debugger-feature-tour.md)提供 Visual Studio 偵錯功能的完整文件。

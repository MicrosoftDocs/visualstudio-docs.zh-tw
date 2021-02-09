---
title: Visual Studio 中的 Python 教學課程步驟 2，撰寫並執行程式碼
titleSuffix: ''
description: 在 Visual Studio 中 Python 功能核心逐步解說的步驟 2，包含編輯程式碼和執行專案。
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7ca28446377c2e04766f70c9146e09dc47b8f089
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882774"
---
# <a name="step-2-write-and-run-code"></a>步驟 2：撰寫和執行程式碼

**上一步：[建立新的 Python 專案](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

雖然 **方案總管** 是您管理專案檔的位置，但是 *編輯器* 視窗通常是您處理檔案 *內容* 的地方，例如原始程式碼。 編輯器會依照內容判定所編輯的檔案類型，包括程式設計語言 (根據副檔名)，並提供適用於該語言的功能，例如使用 IntelliSense 的語法著色和自動完成。

1. 建立新的「Python 應用程式」專案之後，Visual Studio 編輯器中會開啟名稱為 *PythonApplication1.py* 的預設空白檔案。

1. 在編輯器中，開始鍵入 `print("Hello, Visual Studio")`，並注意 Visual Studio IntelliSense 在過程中如何顯示自動完成選項。 下拉式清單中的大綱選項是當您按下 **tab** 鍵時，所使用的預設完成。 涉及到較長的陳述式或識別項時，完成最有幫助。

    ![IntelliSense 自動完成快顯視窗](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense 會根據您所使用的陳述式、所呼叫的函式等等，顯示不同的資訊。 使用 `print` 函式時，在 `print` 之後鍵入 `(` 表示函式呼叫會顯示該函式的完整使用方式資訊。 IntelliSense 快顯畫面也會以粗體顯示目前的引數 (**valu** 如下所示)：

    ![函式的 IntelliSense 自動完成快顯視窗](media/vs-getting-started-python-05-IntelliSense2b.png)

1. 完成陳述式，使它符合下列內容︰

    ```python
    print("Hello, Visual Studio")
    ```

1. 請注意區別 `print` 陳述式與 `"Hello Visual Studio"` 引數的語法著色。 同時，暫時刪除字串的最後一個 `"` 並注意 Visual Studio 如何為包含語法錯誤的程式碼顯示紅色底線。 然後取代 `"` 以更正程式碼。

    ![IntelliSense 語法著色和錯誤醒目提示](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > 由於某個人的開發環境是非常私人的事情，因此 Visual Studio 可讓您擁有 Visual Studio 外觀和行為的完整控制權。 選取 [**工具**  >  **選項**] 功能表命令，並流覽 [**環境**] 和 [**文字編輯器**] 索引標籤底下的設定。 根據預設，您會看到有限數目的選項。若要查看每種程式設計語言的每個選項，請選取對話方塊底部的 [顯示所有設定]。

1. 執行您已撰寫的程式碼，方法是按 **Ctrl** + **F5** ，或選取 [不使用偵錯工具來  >  **啟動**] 功能表項目。 如果程式碼仍然發生錯誤，Visual Studio 會向您發出警告。

1. 當您執行程式時，隨即出現顯示結果的主控台視窗，就如同您從命令列搭配 *PythonApplication1.py* 執行 Python 解譯器。 按某個按鍵來關閉視窗，並返回到 Visual Studio 編輯器。

    ![第一次執行程式的輸出](media/vs-getting-started-python-07-output.png)

1. 除了陳述式和函式的自動完成以外，IntelliSense 還提供了 Python `import` 和 `from` 陳述式的自動完成。 這些自動完成可協助您輕鬆地找出哪些模組可用於您的環境，以及那些模組的成員。 在編輯器中，刪除 `print` 行，並開始輸入 `import`。 鍵入空格時，會顯示模組清單：

    ![IntellSense 顯示 import 陳述式可用的模組](media/vs-getting-started-python-08-import1.png)

1. 輸入或選取 `sys` 完成行。

1. 在下一行中，再次輸入 `from` 以查看模組清單：

    ![IntellSense 顯示 from 陳述式可用的模組](media/vs-getting-started-python-09-import2.png)

1. 選取或輸入 `math`，然後繼續輸入空格與 `import`，其中顯示模組成員︰

    ![IntellSense 顯示模組成員](media/vs-getting-started-python-10-import3.png)

1. 透過匯入 `sin`、`cos` 和 `radians` 成員來完成，注意每個成員可用的自動完成選項。 當您完成時，您的程式碼應該會如下所示︰

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > 當您輸入時，自動完成選項會與子字串搭配使用，比對部分字組、字組開頭的字母，甚至是略過的字元。 如需詳細資料，請參閱[編輯程式碼 - 自動完成](editing-python-code-in-visual-studio.md#completions)。

1. 新增更多一些的程式碼來列印 360 度的餘弦值：

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. 使用 **Ctrl** + **F5** 或 **Debug** Start 來重新執行程式，  >  **而不進行調試** 程式。 當您完成時，請關閉輸出視窗。

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [使用互動式複製視窗](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>深入了解

- [編輯程式碼](editing-python-code-in-visual-studio.md)
- [格式化程式碼](formatting-python-code.md)
- [重構程式碼](refactoring-python-code.md)
- [使用 PyLint](linting-python-code.md)

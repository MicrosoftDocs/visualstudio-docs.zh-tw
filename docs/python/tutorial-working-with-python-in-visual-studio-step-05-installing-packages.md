---
title: 使用 Python 教學課程的步驟 5：安裝套件
description: 在 Visual Studio 中 Python 功能核心逐步解說的步驟 5，示範 Visual Studio 在 Python 環境中管理套件的功能。
ms.date: 03/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 205af005071c86b7e86dcc465918fccc7243690c
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="step-5-installing-packages-in-your-python-environment"></a>第 5 步：在 Python 環境中安裝套件

**上一步：[在偵錯工具中執行程式碼](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python 開發人員社群已產生數千個有用的套件，您可以將它們加入自己的專案。 Visual Studio 提供了一個可在 Python 環境中管理套件的 UI。

1. 選取 [View (檢視)] > [Other Windows (其他視窗)] > [Python Environments (Python 環境)] 功能表命令。 [Python 環境] 視窗隨即以方案總管的對等項目形式開啟，並顯示您可以使用的不同環境。 此清單同時包含使用 Visual Studio 安裝程式安裝的環境，以及個別安裝的環境。 以粗體顯示的環境是針對新專案使用的預設環境。

  ![[Python Environments (Python 環境)] 視窗](media/environments-default-view-blue.png)

1. 環境的 [概觀] 索引標籤可快速存取該環境的互動式視窗，以及環境的安裝資料夾和解譯器。 例如，選取 [開啟互動式視窗]，該特定環境的互動式視窗即會出現在 Visual Studio 中。

1. 選取 [套件] 索引標籤，您即會看到目前安裝在環境中的套件清單。

  ![環境中安裝的套件](media/environments-installed-packages-blue.png)

1. 透過在搜尋欄位中輸入其名稱來安裝 `matplotlib`，然後選取 `pip install`

  ![在環境中安裝 matplotlib](media/environments-add-matplotlib1.png)

1. 如果系統提示您提高權限，請同意這樣做。

1. 在安裝套件之後，它會顯示在 [Python 環境] 視窗中。 套件右側的 **X** 可用來進行解除安裝。

  ![在環境中完成安裝 matplotlib](media/environments-add-matplotlib2.png)

  環境下的小型進度列表示 Visual Studio 正在為新安裝的套件建置其 IntelliSense 資料庫。 [IntelliSense] 索引標籤也會顯示更詳細的資訊。 請注意，在該資料庫完成之前，自動完成和語法檢查等 IntelliSense 功能不會在編輯器中針對該套件啟動。

  請注意，**Visual Studio 2017 15.6 版**及更新版本會使用不同且較快的方法來搭配 IntelliSense 運作，並會在 [IntelliSense] 索引標籤上顯示訊息來指出這點。

1. 使用 [檔案] > [新增] > [專案] 建立新的專案，並選取「Python 應用程式」範本。 在出現的程式碼檔案中，貼上下列程式碼，這會像先前的教學課程步驟一樣建立一個餘弦波，只是這次會以圖形方式繪製：

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. 在使用 (F5) 或不使用偵錯工具 (Ctrl + F5) 的情況下，執行程式來查看輸出：

  ![matplotlib 範例的輸出](media/environments-add-matplotlib3.png)

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [使用 Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

### <a name="going-deeper"></a>繼續探討

- [Python 環境](managing-python-environments-in-visual-studio.md)

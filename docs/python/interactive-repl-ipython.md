---
title: IPython REPL (互動式視窗)
description: 在 IPython 模式中使用 Visual Studio 互動式視窗，以便有易於使用的互動式開發環境，並具有「互動式平行計算」功能。
ms.date: 06/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 28fb0bdb181b1f4f2c08112e40d6236db22b7a08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918918"
---
# <a name="use-ipython-in-the-interactive-window"></a>在互動式視窗中使用 IPython

IPython 模式的 Visual Studio [互動式] 視窗，是個進階但容易使用的互動式開發環境，且具有「互動式平行計算」功能。 本文將逐步解說如何在 Visual Studio [互動式] 視窗中使用 IPython；該視窗也提供所有的一般[互動式視窗](python-interactive-repl-in-visual-studio.md)功能。

針對此逐步解說，您需要安裝 [Anaconda](https://www.continuum.io) 環境，其中包含 IPython 和必要的程式庫。

> [!Note]
> IronPython 並不支援 IPython，雖然您可以在 [互動式選項] 表單中選取它。 如需詳細資訊，請參閱[功能要求](https://github.com/Microsoft/PTVS/issues/84)。

1. 開啟 Visual Studio，切換到 [Python 環境] 視窗 ([檢視] > [其他視窗] > [Python 環境])，然後選取 Anaconda 環境。

2. 檢查該環境的 [套件 (Conda)] 索引標籤 (這可能會顯示為 [pip] 或 [套件])，以確定會列出 `ipython` 和 `matplotlib`。 如果沒有，請在這裡安裝它們。 (請參閱 [Python 環境視窗 - 套件索引標籤](python-environments-window-tab-reference.md))。

3. 選取 [概觀] 索引標籤並選取 [使用 IPython 互動模式] (在 Visual Studio 2015 中，選取 [設定互動選項] 開啟 [選項] 對話方塊，然後將 [互動模式] 設定為 [IPython]，並選取 [確定])。

4. 選取 [開啟互動式視窗] 以開啟 IPython 模式的 [互動式] 視窗。 如果您剛變更互動模式，可能需要重設視窗，如果僅出現 >>> 提示，也可能需要按下 **Enter** 鍵，讓您收到如 **In [2]** 的提示。

    ![IPython 模式的互動式視窗](media/ipython-repl-03.png)

5. 輸入下列程式碼：

   ```python
   import matplotlib.pyplot as plt
   import numpy as np
  
   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. 輸入最後一行之後，您應該會看到一個内嵌圖表 (您可以視需要拖曳右下角來調整大小)。

    ![互動式視窗中的內嵌圖表](media/ipython-repl-04.png)

7. 除了在 REPL 中鍵入之外，您可以改為在編輯器中撰寫程式碼，選取它，按一下滑鼠右鍵，然後選取 [傳送至互動] 命令 (或按 **Ctrl**+**Enter**)。 嘗試將以下程式碼貼到編輯器中的新檔案，使用 **Ctrl**+**A** 選取它，然後傳送到 [互動式] 視窗。 (Visual Studio 將程式碼以單一單位傳送，以避免產生過渡或部分的圖表。 同時，如果您尚未開啟 Python 專案並選取不同的環境，Visual Studio 會為選取的任何環境開啟 [互動式] 視窗，作為 [Python 環境] 視窗中的預設值。)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![將程式碼從編輯器傳送至互動式視窗](media/ipython-repl-05.png)

8. 若要在 [互動式] 視窗外查看圖表，請改為使用 [偵錯] > [啟動但不偵錯] 命令來執行程式碼。

IPython 有許多其他實用功能，例如逸出到系統殼層、變數替換、擷取輸出等。如需詳細資訊，請參閱 [IPython 文件](http://ipython.org/documentation.html)。

### <a name="see-also"></a>另請參閱

- 若要輕鬆使用 Jupyter，且不需安裝，請嘗試免費的 [Azure Notebooks 託管服務](https://notebooks.azure.com/)，可讓您保留並與其他人共用您的筆記。

- [Azure 資料科學虛擬機器](/azure/machine-learning/data-science-virtual-machine/overview)也會預先設定為執行 Jupyter Notebook，以及各種其他資料科學工具。

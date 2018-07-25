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
ms.openlocfilehash: adfd037cc7362a4aa088d57c3776379caf6de5e3
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057657"
---
# <a name="using-ipython-in-the-interactive-window"></a>在互動式視窗中使用 IPython

IPython 模式的 Visual Studio 互動式視窗，是個進階但容易使用的互動式開發環境，且具有「互動式平行計算」功能。 本文章會引導使用者在 Visual Studio 互動式視窗中使用 IPython；該視窗也提供所有的一般[互動式視窗](python-interactive-repl-in-visual-studio.md)功能。

針對此逐步解說，您需要安裝 [Anaconda](https://www.continuum.io) 環境，其中包含 IPython 和必要的程式庫。

> [!Note]
> IronPython 並不支援 IPython，雖然您可以在 [互動式選項] 表單中選取它。 如需詳細資訊，請參閱[功能要求](https://github.com/Microsoft/PTVS/issues/84)。

1. 開啟 Visual Studio，切換到 [Python 環境] 視窗 ([檢視] > [其他視窗] > [Python 環境])，然後選取 Anaconda 環境。

1. 檢查該環境的 [套件 (Conda)] 索引標籤 (這可能會顯示為 [pip] 或 [套件])，以確定會列出 `ipython` 和 `matplotlib`。 如果沒有，請在這裡安裝它們。 (請參閱 [Python 環境視窗 - 套件索引標籤](python-environments-window-tab-reference.md)。)

1. 選取 [概觀] 索引標籤並選取 [使用 IPython 互動模式]。 (在 Visual Studio 2015 中，選取 [設定互動選項] 開啟 [選項] 對話方塊，然後將 [互動模式] 設定為 IPython，並選取 [確定]。)

1. 選取 [開啟互動式視窗] 以開啟 IPython 模式的互動式視窗。 如果您剛變更互動模式，可能需要重設視窗，如果僅出現 >>> 提示，也可能需要按下 Enter 鍵，讓您收到如「在 [2] 中」的提示。

    ![IPython 模式的互動式視窗](media/ipython-repl-03.png)

1. 輸入下列程式碼：

  ```python
  import matplotlib.pyplot as plt
  import numpy as np
  
  x = np.linspace(0, 5, 10)
  y = x ** 2
  plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. 輸入最後一行之後，您應該會看到一個内嵌圖表 (您可以視需要拖曳右下角來調整大小)。

    ![互動式視窗中的內嵌圖表](media/ipython-repl-04.png)

1. 除了在 REPL 中鍵入之外，您可以改為在編輯器中撰寫程式碼，選取它，以滑鼠右鍵按一下，然後選取 [傳送到 Interactive] 命令 (或按 Ctrl+Enter)。 嘗試將以下程式碼貼到編輯器中的新檔案，使用 Ctrl-A 選取它，然後傳送到互動式視窗。 (Visual Studio 將程式碼以單一單位傳送，以避免產生過渡或部分的圖表。 同時，如果您尚未開啟 Python 專案並選取不同的環境，Visual Studio 會為選取的任何環境開啟互動式視窗，作為 [Python 環境] 視窗中的預設值。)

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

1. 若要在互動式視窗外查看圖表，請改為使用 [偵錯] > [啟動但不偵錯] 命令來執行程式碼。

IPython 有許多其他實用功能，例如逸出到系統殼層、變數替換、擷取輸出等。如需詳細資訊，請參閱 [IPython 文件](http://ipython.org/documentation.html)。

## <a name="related-articles"></a>相關文章

- 若要輕鬆使用 Jupyter，且不需安裝，請嘗試免費的 [Azure Notebooks 託管服務](https://notebooks.azure.com/)，可讓您保留並與其他人共用您的筆記。

- 您也可以在 Azure 上自己的 Windows 或 Linux 虛擬機器執行 Jupyter (之前稱為 IPython)。 如需詳細資訊，請參閱[在 Azure 上建立 Azure VM、安裝 Jupyter 並執行 Jupyter Notebook](/azure/virtual-machines/virtual-machines-linux-jupyter-notebook)。

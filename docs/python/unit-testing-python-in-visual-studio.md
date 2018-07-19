---
title: Python 的單元測試
description: 在 Visual Studio 中設定 Python 程式碼的單元測試，以充分利用測試總管的功能來探索、執行和偵錯測試。
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 37d545adf33a6350f3d2484e4f820ebca8f7353d
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056419"
---
# <a name="setting-up-unit-testing-for-python-code"></a>設定 Python 程式碼的單元測試

單元測試是測試應用程式中其他程式碼單元 (通常是隔離的函數、類別等) 的程式碼片段。 應用程式通過所有單元測試之後，您至少可以確定其低階功能皆能正確運作。

在設計程式時，Python 會廣泛地使用單元測試來驗證案例。 Visual Studio 中的 Python 支援包含在開發程序的內容內針對單元測試進行探索、執行及偵錯，而且不需要個別執行測試。

本文章提供搭配 Python 的 Visual Studio 中的單元測試功能簡介。 如需單元測試的整體詳細資訊，請參閱[對程式碼進行單元測試](../test/unit-test-your-code.md)。

|   |   |
|---|---|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | [ 觀看有關 Python 中單元測試的影片 (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567) \(英文\) (2 分 31 秒)。 |

## <a name="discovering-and-viewing-tests"></a>探索及檢視測試

依照慣例，Visual Studio 會將測試辨識為名稱以 `test` 開頭的方法。 若要查看此行為，請執行下列步驟：

1. 開啟在 Visual Studio 中載入的 [Python 專案](managing-python-projects-in-visual-studio.md)，以滑鼠右鍵按一下專案，選取[新增] > [新增項目...]，然後選取 [Python 單元測試]，再選取 [新增]。

1. 此動作會建立 `test1.py` 檔案，其中的程式碼會匯入標準 `unittest` 模組、從 `unittest.TestCase` 衍生測試類別，並在直接執行指令碼的情況下叫用 `unittest.main()`：

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. 視需要儲存檔案，然後使用 [測試] > [Windows] > [測試總管] 功能表命令，開啟測試總管。

1. 測試總管會搜尋要進行測試的專案，並將它們顯示如下。 按兩下測試會開啟其原始程式檔。

    ![[測試總管] 顯示預設的 test_A](media/unit-test-A.png)

1. 隨著新增更多測試，您可以使用工具列上的 [群組依據] 功能表，組織 [測試總管] 中的檢視：

    ![[測試總管] 的 [群組依據] 工具列功能表](media/unit-test-group-menu.png)

1. 您也可以在搜尋欄位中輸入文字，以依據名稱來篩選測試。

如需 `unittest` 模組以及撰寫測試的詳細資訊，請參閱 [Python 2.7 文件](https://docs.python.org/2/library/unittest.html) 或 [Python 3.4 文件](https://docs.python.org/3/library/unittest.html) (python.org)。

## <a name="running-tests"></a>執行測試

在 [測試總管] 中有多種方式可以執行測試：

- [全部執行] 會執行所有顯示的測試 (視篩選條件而定)。
- [執行...] 功能表提供您以群組執行失敗、通過或無法執行之測試的命令。
- 您可以選取一或多個測試，以滑鼠右鍵按一下，然後選取 [執行選取的測試]。

測試會在背景執行，且 [測試總管] 會在每個測試完成時更新其狀態：

- 通過的測試會顯示綠色的打勾圖示，以及執行測試所花費的時間：

    ![test_A 通過狀態](media/unit-test-A-pass.png)

- 失敗的測試會顯示紅色十字，以及會顯示測試執行的主控台輸出和 `unittest` 輸出的 [輸出] 連結：

    ![test_A 失敗狀態](media/unit-test-A-fail.png)

    ![test_A 失敗且含原因](media/unit-test-A-fail-reason.png)

## <a name="debugging-tests"></a>偵錯測試

因為單元測試是程式碼片段，所以它們和其他程式碼一樣會有錯誤，並在某些情況下需要以偵錯工具執行。 在偵錯工具中，您可以設定中斷點、檢視變數，以及逐步檢視程式碼。 Visual Studio 也提供診斷工具以進行單元測試。

若要開始偵錯，請在程式碼中設定初始中斷點，然後在 [測試總管] 中以滑鼠右鍵按一下測試 (或一系列測試)，然後選取 [偵錯選取的測試]。 Visual Studio 會以與針對應用程式碼一樣的方式，啟動 Python 偵錯工具。

![對測試進行偵錯](media/unit-test-debugging.png)

視您的 Visual Studio 版本而定 (請參閱[功能比較表](overview-of-python-tools-for-visual-studio.md#features-matrix))，您也可以使用 [分析選取之測試的程式碼涵蓋範圍] 和 [程式碼剖析測試] 命令。

### <a name="known-issues"></a>已知問題

- 當開始偵錯時，Visual Studio 會看似啟動並停止偵錯，然後再次啟動。 這是預期的行為。
- 針對多個測試所進行的偵錯都會獨立執行，這會中斷偵錯工作階段。
- 當進行偵錯時，Visual Studio 會間歇性地無法啟動測試。 一般來說，再次嘗試對測試進行偵錯會成功。
- 進行偵錯時，可以離開測試進入 `unittest` 實作。 一般來說，下一個步驟會執行至程式的結尾，並停止偵錯。

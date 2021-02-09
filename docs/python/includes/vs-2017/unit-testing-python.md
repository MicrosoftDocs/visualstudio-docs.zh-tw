---
title: 單元測試 Python 程式碼
description: 在 Visual Studio 中設定 Python 程式碼的單元測試，以充分利用 [測試總管] 的功能來探索、執行和偵錯測試。
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 612d4bd7d66add8c3fe7c45e8f03ca3531b0b4c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920671"
---
## <a name="discover-and-view-tests"></a>探索及檢視測試

依照慣例，Visual Studio 會將測試辨識為名稱以 `test` 開頭的方法。 若要查看此行為，請執行下列步驟：

1. 開啟在 Visual Studio 中載入的 [Python 專案](../../managing-python-projects-in-visual-studio.md)，以滑鼠右鍵按一下專案，選取 [新增] > [新增項目]，然後選取 [Python 單元測試]，再選取 [新增]。

1. 此動作會建立 *test1.py* 檔案，其中會具有會匯入標準 `unittest` 模組，從 `unittest.TestCase` 衍生測試類別，並在您直接執行指令碼的情況下叫用 `unittest.main()` 的程式碼：

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. 視需要儲存檔案，然後使用 [測試] > [Windows] > [測試總管] 功能表命令，開啟 [測試總管]。

1. **測試瀏覽器** 會在您的專案中搜尋測試，並顯示如下所示的專案。 按兩下測試會開啟其原始程式檔。

    ![[測試總管] 顯示預設的 test_A](../../media/unit-test-A.png)

1. 當您將更多測試加入專案時，可以使用工具列上的 [**分組方式**] 功能表，在 [**測試瀏覽器**] 中組織視圖：

    ![[測試總管] 的 [群組依據] 工具列功能表](../../media/unit-test-group-menu.png)

1. 您也可以在 [ **搜尋** ] 欄位中輸入文字，以依名稱篩選測試。

如需 `unittest` 模組和撰寫測試的詳細資訊，請參閱 [python 2.7 檔](https://docs.python.org/2/library/unittest.html) 或 [python 3.7 檔](https://docs.python.org/3/library/unittest.html) (python.org) 。

## <a name="run-tests"></a>執行測試

在 **測試瀏覽器** 中，您可以透過各種不同的方式來執行測試：

- [全部執行] 會執行所有顯示的測試 (視篩選條件而定)。
- [ **執行** ] 功能表可讓您以群組執行失敗、通過或不執行測試的命令。
- 您可以選取一或多個測試，以滑鼠右鍵按一下，然後選取 [執行選取的測試]。

測試會在背景執行，而且 **Test Explorer** 會在每個測試完成時更新其狀態：

- 通過的測試會顯示綠色的打勾圖示，以及執行測試所花費的時間：

    ![test_A 通過狀態](../../media/unit-test-A-pass.png)

- 失敗的測試會顯示紅色十字，以及會顯示測試執行的主控台輸出和 `unittest` 輸出的 [輸出] 連結：

    ![test_A 失敗狀態](../../media/unit-test-A-fail.png)

    ![test_A 失敗且含原因](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>偵錯測試

因為單元測試是程式碼片段，所以它們和其他程式碼一樣會有錯誤，並在某些情況下需要以偵錯工具執行。 在偵錯工具中，您可以設定中斷點、檢視變數，以及逐步檢視程式碼。 Visual Studio 也提供診斷工具以進行單元測試。

若要啟動偵錯工具，請在您的程式碼中設定初始中斷點，然後以滑鼠右鍵按一下 [ **Test Explorer** ] 中的測試 (或選取) ，然後選取 [ **偵錯工具選取的測試**]。 Visual Studio 會以與針對應用程式碼一樣的方式，啟動 Python 偵錯工具。

![對測試進行偵錯](../../media/unit-test-debugging.png)

您也可以 **針對選取的測試使用 [分析程式碼涵蓋範圍**]。 如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

### <a name="known-issues"></a>已知問題

- 當開始偵錯時，Visual Studio 會看似啟動並停止偵錯，然後再次啟動。 這是預期的行為。
- 針對多個測試所進行的偵錯都會獨立執行，這會中斷偵錯工作階段。
- 當進行偵錯時，Visual Studio 會間歇性地無法啟動測試。 一般來說，再次嘗試對測試進行偵錯會成功。
- 進行偵錯時，可以離開測試進入 `unittest` 實作。 一般而言，下一個步驟會執行至程式的結尾，並停止偵錯。

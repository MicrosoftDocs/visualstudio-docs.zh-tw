---
title: 單元測試 Python 程式碼
description: 在 Visual Studio 中設定 Python 程式碼的單元測試，以充分利用 [測試總管] 的功能來探索、執行和偵錯測試。
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933465"
---
## <a name="select-the-test-framework-for-a-python-project"></a>選取 Python 專案的測試架構

Visual Studio 支援適用于 Python、 [unittest](https://docs.python.org/3/library/unittest.html)和[pytest](https://pytest.org/en/latest/)的兩種測試架構（可從16.3 版開始 Visual Studio 2019）。 根據預設，當您建立 Python 專案時，不會選取任何架構。 若要指定架構，請在方案總管中的專案名稱上按一下滑鼠右鍵，然後選取 [**屬性**] 選項。 這會開啟 [專案設計工具]，可讓您透過 [**測試**] 索引標籤來設定測試。從這個索引標籤中，您可以選取要用於專案的測試架構。 

* 針對**unittest**架構，專案的根目錄會用於測試探索。 您可以在 [**測試**] 索引標籤上，針對使用者指定的值，修改這個位置，以及用於識別測試的文字模式。
* 針對**pytest**架構，測試位置和檔案名模式之類的測試選項是使用標準的 pytest 設定檔來指定。 如需詳細資訊，請參閱[pytest 參考檔](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)。

儲存架構的選取專案和設定之後，就會在測試瀏覽器中起始測試探索。 如果 [測試瀏覽器] 視窗尚未開啟，請流覽至工具列，然後選取 [**測試** >  個**test Explorer**]。

## <a name="configure-testing-for-python-without-a-project"></a>設定不含專案的 Python 測試
Visual Studio 可讓您使用 Python 程式碼[開啟資料夾](../../quickstart-05-python-visual-studio-open-folder.md)，以執行和測試現有的 python 程式碼，而不需要專案。 在這些情況下，您將需要使用**PythonSettings 的 json**檔案來設定測試。 
1. 使用 [**開啟本機資料夾**] 選項來開啟現有的 Python 程式碼。 

   ![Visual Studio 啟動畫面](../../media/quickstart-open-folder/01-open-local-folder.png)

1. 在 [方案總管] 視窗中，按一下 [**顯示所有**檔案] 圖示，以顯示目前資料夾中的所有檔案。

   ![顯示所有檔案按鈕](../../media/unit-test-show-files.png)

1. 流覽至 [**本機設定**] 資料夾內的**PythonSettings。** 如果您在 [**本機設定**] 資料夾中看不到這個檔案，請手動建立。
   
1. 將欄位**mstest.testframework**新增至設定檔，並將它設定為**pytest**或**unittest** ，視您想要使用的測試架構而定。

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > 針對**unittest**架構，如果 PythonSettings 檔案中未指定**UnitTestRootDirectory**和**UnitTestPattern**欄位，則會分別新增和指派預設值 "." 和 "test *. .py"。

1. 如果您的資料夾包含**的 src**目錄與包含測試的資料夾不同，請使用**PythonSettings**檔案中的**SearchPaths**欄位，指定**src**資料夾的路徑。

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. 儲存您對 PythonSettings 的變更，以起始指定架構的測試探索。 
   > [!Note]
   > 如果 [測試瀏覽器] 視窗已開啟**CTRL** + **R，則**也會觸發探索。

## <a name="discover-and-view-tests"></a>探索及檢視測試

根據預設，Visual Studio 會將**unittest**和**pytest**測試識別為名稱開頭為 `test` 的方法。 若要查看測試探索，請執行下列動作：

1. 開啟[Python 專案](../../managing-python-projects-in-visual-studio.md)。

1. 在 Visual Studio 中載入專案之後，請在方案總管中以滑鼠右鍵按一下專案，然後從 [屬性**測試**] 索引標籤中選取**unittest**或**pytest**架構。
   > [!Note]
   > 如果您使用 pytest 架構，則可以使用標準的 pytest 設定檔來指定測試位置和檔案名模式。 預設會使用工作區/專案資料夾，其模式為 `test_*py`，而 `*_test.py`。 如需詳細資訊，請參閱[pytest 參考檔](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)。

1. 選取架構之後，再次以滑鼠右鍵按一下專案，然後選取 [**新增 @no__t-** 1 個**新專案**]，然後選取 [ **Python 單元測試**]，再按 [**新增**]。

1. 此動作會使用匯入標準 @no__t 1 模組的程式碼建立*test_1 .py*檔案，從 `unittest.TestCase` 衍生測試類別，並在您直接執行腳本的情況下，叫用 `unittest.main()`：

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. 視需要儲存檔案，然後使用 [**測試** > **測試瀏覽器**] 功能表命令來開啟 [**測試] explorer** 。

1. [測試總管] 會搜尋要進行測試的專案，並將它們顯示如下。 按兩下測試會開啟其原始程式檔。

    ![[測試總管] 顯示預設的 test_A](../../media/unit-test-a-2.png) 

1. 當您將更多測試加入至專案時，您可以使用工具列上的 [**群組依據**] 功能表，在 [**測試瀏覽器**] 中組織此視圖：

    ![[測試總管] 的 [群組依據] 工具列功能表](../../media/unit-test-group-menu-2.png) 

1. 您也可以在 [搜尋] 欄位中輸入文字，以依據名稱來篩選測試。

如需 @no__t 0 模組和撰寫測試的詳細資訊，請參閱[python 2.7 檔](https://docs.python.org/2/library/unittest.html)或[python 3.7 檔](https://docs.python.org/3/library/unittest.html)（python.org）。

## <a name="run-tests"></a>執行測試

在 [測試總管] 中有多種方式可以執行測試：

- [全部執行] 會執行所有顯示的測試 (視篩選條件而定)。
- [執行] 功能表提供您以群組執行失敗、通過或無法執行之測試的命令。
- 您可以選取一或多個測試，以滑鼠右鍵按一下，然後選取 [執行選取的測試]。

測試會在背景執行，且 [測試總管] 會在每個測試完成時更新其狀態：

- 通過的測試會顯示綠色的打勾圖示，以及執行測試所花費的時間：

    ![test_A 通過狀態](../../media/unit-test-A-pass.png)

- 失敗的測試會顯示紅色十字，以及會顯示測試執行的主控台輸出和 `unittest` 輸出的 [輸出] 連結：

    ![test_A 失敗狀態](../../media/unit-test-A-fail.png)

    ![test_A 失敗且含原因](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>針對測試進行偵錯

因為單元測試是程式碼片段，所以它們和其他程式碼一樣會有錯誤，並在某些情況下需要以偵錯工具執行。 在偵錯工具中，您可以設定中斷點、檢視變數，以及逐步檢視程式碼。 Visual Studio 也提供診斷工具以進行單元測試。

> [!Note]
> 根據預設，測試的偵錯工具會使用 ptvsd 4 偵錯工具。 如果您想改為使用 ptvsd 3，您可以在 **工具**  > **選項** 上選取 **使用舊版偵錯工具** 選項， > **Python** > **調試**程式。 

若要開始偵錯，請在程式碼中設定初始中斷點，然後在 [測試總管] 中以滑鼠右鍵按一下測試 (或一系列測試)，然後選取 [偵錯選取的測試]。 Visual Studio 會以與針對應用程式碼一樣的方式，啟動 Python 偵錯工具。

![對測試進行偵錯](../../media/unit-test-debugging.png)

您也可以**針對選取的測試使用 [分析程式碼涵蓋範圍**]。 如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

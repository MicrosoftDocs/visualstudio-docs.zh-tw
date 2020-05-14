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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933465"
---
## <a name="select-the-test-framework-for-a-python-project"></a>選擇 Python 專案的測試框架

Visual Studio 支援兩個針對 Python、[單元測試](https://docs.python.org/3/library/unittest.html)和[熱測試](https://pytest.org/en/latest/)的測試框架（在 Visual Studio 2019 中提供，從版本 16.3 開始）。 預設情況下，在創建 Python 專案時不會選擇任何框架。 要指定框架，請按右鍵解決方案資源管理器中的專案名稱並選擇"**屬性**"選項。 這將打開專案設計器，它允許您通過 **"測試"** 選項卡配置測試。在此選項卡中，您可以選擇要用於專案的測試框架。 

* 對於**單元測試**框架，專案的根目錄用於測試發現。 可以在 **"測試"** 選項卡上修改此位置以及用於標識測試的文字模式，以達到使用者指定的值。
* 對於**pytest**框架，使用標準 pytest .ini 設定檔指定測試位置和檔案名模式等測試選項。 有關詳細資訊，請參閱[pythe 參考文檔](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)。

保存框架選擇和設置後，測試發現將啟動測試資源管理器。 如果測試資源管理器視窗尚未打開，則導航到工具列並選擇**測試** > **資源管理器**。

## <a name="configure-testing-for-python-without-a-project"></a>配置沒有專案的 Python 測試
Visual Studio 允許您使用 Python 代碼[打開資料夾](../../quickstart-05-python-visual-studio-open-folder.md)，在沒有專案的情況下運行和測試現有的 Python 代碼。 在這些情況下，您需要使用**PythonSettings.json**檔來配置測試。 
1. 使用 **"打開本地資料夾"** 選項打開現有 Python 代碼。 

   ![Visual Studio 啟動畫面](../../media/quickstart-open-folder/01-open-local-folder.png)

1. 在"解決方案資源管理器"視窗中，按一下"**顯示所有檔**"圖示以顯示當前資料夾中的所有檔。

   ![顯示所有檔按鈕](../../media/unit-test-show-files.png)

1. 導航到 **"本地設置"** 資料夾中的**PythonSettings.json**檔。 如果在 **"本地設置"** 資料夾中未看到此檔，請手動創建該檔。
   
1. 將欄位**TestFramework**添加到設置檔中，並將其設置為 **"熱測試**"或 **"單元測試"，** 具體取決於要使用的測試框架。

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > 對於**單元測試**框架，如果 PythonSettings.json 檔中未指定欄位**單元測試RootDirectory**和**UnitTestPattern，** 則分別添加和分配預設值"." 和"test_.py"。

1. 如果資料夾包含與包含測試的資料夾分開的**src**目錄，請使用**PythonSettings.json**檔中的 **"搜索路徑"** 欄位指定**src**資料夾的路徑。

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. 保存對 PythonSettings.json 檔的更改，以啟動指定框架的測試發現。 
   > [!Note]
   > 如果測試資源管理器視窗已打開**CTRL** + **R，A**還會觸發發現。

## <a name="discover-and-view-tests"></a>探索及檢視測試

預設情況下，Visual Studio 將**單元測試**和**pytest**測試標識為名稱以`test`開頭的方法。 要查看測試發現，執行以下操作：

1. 打開[Python 專案](../../managing-python-projects-in-visual-studio.md)。

1. 在 Visual Studio 中載入專案後，在解決方案資源管理器中按右鍵專案，並從"屬性**測試**"選項卡中選擇**單元測試**或**檢測**框架。
   > [!Note]
   > 如果使用 pytest 框架，則可以使用標準 pytest .ini 設定檔指定測試位置和檔案名模式。 預設情況下，使用工作區/專案資料夾，其模式為`test_*py`和`*_test.py`。 有關詳細資訊，請參閱[pythe 參考文檔](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)。

1. 選擇框架後，再次按右鍵專案，然後選擇 **"添加新** > **項**"，然後選擇**Python 單元測試**，然後**添加**。

1. 此操作創建一個*test_1.py*檔，該檔的代碼導入標準`unittest`模組，從`unittest.TestCase`派生測試類，`unittest.main()`並在直接運行腳本時調用：

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. 如有必要，保存該檔，然後使用**測試** > **資源管理器**功能表命令打開**測試資源管理器**。

1. **測試資源管理器**搜索您的專案以搜索測試並如下所示顯示它們。 按兩下測試會開啟其原始程式檔。

    ![[測試總管] 顯示預設的 test_A](../../media/unit-test-a-2.png) 

1. 向專案添加更多測試時，可以使用工具列上的 **"分組"** 功能表在**測試資源管理器**中組織視圖：

    ![[測試總管] 的 [群組依據] 工具列功能表](../../media/unit-test-group-menu-2.png) 

1. 您還可以在 **"搜索"** 欄位中輸入文本以按名稱篩選測試。

有關`unittest`模組和編寫測試的詳細資訊，請參閱[Python 2.7 文檔](https://docs.python.org/2/library/unittest.html)或 Python [3.7 文檔](https://docs.python.org/3/library/unittest.html)（python.org）。

## <a name="run-tests"></a>執行測試

在**測試資源管理器**中，您可以通過多種方式運行測試：

- [全部執行]**** 會執行所有顯示的測試 (視篩選條件而定)。
- "**運行"** 功能表提供命令，用於以組身份運行失敗、通過或不運行測試。
- 您可以選取一或多個測試，以滑鼠右鍵按一下，然後選取 [執行選取的測試]****。

測試在後臺運行，**測試資源管理器**在完成每個測試時更新其狀態：

- 通過的測試會顯示綠色的打勾圖示，以及執行測試所花費的時間：

    ![test_A 通過狀態](../../media/unit-test-A-pass.png)

- 失敗的測試會顯示紅色十字，以及會顯示測試執行的主控台輸出和 `unittest` 輸出的 [輸出]**** 連結：

    ![test_A 失敗狀態](../../media/unit-test-A-fail.png)

    ![test_A 失敗且含原因](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>偵錯測試

因為單元測試是程式碼片段，所以它們和其他程式碼一樣會有錯誤，並在某些情況下需要以偵錯工具執行。 在偵錯工具中，您可以設定中斷點、檢視變數，以及逐步檢視程式碼。 Visual Studio 也提供診斷工具以進行單元測試。

> [!Note]
> 預設情況下，測試調試使用 ptvsd 4 調試器。 如果要改用 ptvsd 3，則可以在**工具** > **選項** > **Python** > 調試上選擇 **"使用舊調試器****"** 選項。 

要開始調試，請在代碼中設置初始中斷點，然後在**測試資源管理器**中按右鍵測試（或選擇），然後選擇 **"調試選定測試**"。 Visual Studio 會以與針對應用程式碼一樣的方式，啟動 Python 偵錯工具。

![對測試進行偵錯](../../media/unit-test-debugging.png)

您還可以使用 **"分析所選測試的代碼覆蓋率**"。 如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

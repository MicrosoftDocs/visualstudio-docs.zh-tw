---
title: 對 Visual C# 程式碼進行單元測試
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590861"
---
# <a name="unit-test-c-code"></a>對 C# 程式碼進行單元測試

本文描述如何在 UWP 應用程式中建立 C# 類別的單元測試。

**Rooter**類別是受測的類別，它會執行函式來計算指定數位之平方根的估計值。

本文示範以*測試為導向的開發*。 在這種方法中，您會先撰寫測試來驗證您要測試之系統中的特定行為，然後撰寫通過測試的程式碼。

## <a name="create-the-solution-and-the-unit-test-project"></a>建立方案和單元測試專案

1. 在 [檔案] 功能表上，依序選擇 [新增] 和 [專案] > 。

2. 搜尋並選取 [空白應用程式 (通用 Windows)] 專案範本。

3. 將專案命名為**Maths**。

4. 在**方案總管**中，以滑鼠右鍵按一下方案，然後選擇 [**加入** > **新增專案**]。

5. 搜尋並選取 [單元測試應用程式 (通用 Windows)] 專案範本。

6. 將測試專案命名為**RooterTests**。

## <a name="verify-that-the-tests-run-in-test-explorer"></a>驗證測試總管中執行的測試

1. 在*UnitTest.cs*檔案的**TestMethod1**中插入一些測試程式碼：

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別提供數個靜態方法，可讓您用來驗證測試方法中的結果。

::: moniker range="vs-2017"

2. 在 [**測試**] 功能表上，選擇 [**執行**] > [**所有測試**]。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在 [**測試**] 功能表上，選擇 [**執行所有測試**]。

::: moniker-end

   測試專案隨即建置並執行。 請耐心等候，因為這可能需要一些時間。 [測試總管] 視窗隨即開啟，而且測試會在 [通過的測試] 底下列出。 視窗底部的 [摘要] 窗格會提供有關所選取測試的其他詳細資料。

## <a name="add-the-rooter-class-to-the-maths-project"></a>將 Rooter 類別新增至 Maths 專案

1. 在**方案總管**中，以滑鼠右鍵按一下**Maths**專案，然後選擇 [**加入** > **類別**]。

2. 將類別檔案命名為 *Rooter.cs*。

3. 將下列程式碼新增至**Rooter**類別*Rooter.cs*檔案：

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   **Rooter**類別會宣告一個函式和**SquareRoot**估計工具方法。 **SquareRoot**方法只是最小的實作為，足以測試測試設定的基本結構。

4. 將 `public` 關鍵字新增至**Rooter**類別宣告，讓測試程式碼可以存取它。

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>新增專案參考

1. 將 RooterTests 專案的參考新增至 Maths 應用程式。

    1. 在**方案總管**中，以滑鼠右鍵按一下**RooterTests**專案，然後選擇 [**加入** > **參考**]。

    2. 在 [新增參考 - RooterTests] 對話方塊中，展開 [方案] 並選擇 [專案]。 選取 [ **Maths** ] 專案。

        ![加入 Maths 專案的參考](../test/media/ute_cs_windows_addreference.png)

2. 將 `using` 語句加入至*UnitTest.cs*檔案：

    1. 開啟*UnitTest.cs*。

    2. 將這個程式碼新增至 `using Microsoft.VisualStudio.TestTools.UnitTesting;` 這一行下方：

       ```csharp
       using Maths;
       ```

3. 加入使用**Rooter**函數的測試。 將下列程式碼新增至*UnitTest.cs*：

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

   新測試會出現在 [測試總管] 的 [未執行的測試] 節點中。

4. 若要避免「裝載包含兩個或多個具有相同目的地路徑的檔案」錯誤，請在**方案總管**中，展開**Maths**專案下的 [**屬性**] 節點，然後*刪除 [default.aspx* ] 檔案。

::: moniker range="vs-2017"

6. 在 [測試總管] 中，選擇 [全部執行]。

   解決方案組建和測試會執行並通過。

   ![在測試瀏覽器中傳遞的 BasicTest](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. 在 [**測試] Explorer**中，選擇 [**執行所有測試**]。

   解決方案組建和測試會執行並通過。

   ![測試瀏覽器中通過的基本測試](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

您已設定測試和應用程式專案，並確認您可以執行可在應用程式專案中呼叫函式的測試。 現在您可以開始撰寫實際的測試和程式碼。

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>反覆擴大測試範圍並讓測試成功

1. 新增名為**RangeTest**的新測試：

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > 建議您不要變更成功的測試。 請改為加入新的測試。

2. 執行**RangeTest**測試並確認它失敗。

   ![RangeTest 失敗](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > 在您撰寫測試之後，請立即執行它來確認它是否失敗。 這有助於避免犯下撰寫永遠不會失敗的測試這種簡單的錯誤。

3. 透過測試強化程式碼，讓新的測試都成功。 將*Rooter.cs*中的**SquareRoot**函數變更為：

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

::: moniker range="vs-2017"

4. 在 [測試總管] 中，選擇 [全部執行]。

::: moniker-end

::: moniker range=">=vs-2019"

4. 在 [**測試] Explorer**中，選擇 [**執行所有測試**]。

::: moniker-end

   現在三項測試都會成功。

> [!TIP]
> 藉由一次加入一項測試的方式開發程式碼。 確定在每次反覆運算後，所有測試都成功。

## <a name="refactor-the-code"></a>重構程式碼

在本節中，您會重構應用程式和測試程式碼，然後重新執行測試以確定它們仍然通過。

### <a name="simplify-the-square-root-estimation"></a>簡化平方根的估計

1. 藉由變更一行程式碼，簡化**SquareRoot**函式中的中央計算，如下所示：

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. 執行所有測試，以確定您尚未導入回歸。 它們都應該通過。

> [!TIP]
> 一組穩定而良好的單元測試，可確認您並未在變更程式碼時引入錯誤。

### <a name="eliminate-duplicated-code"></a>消除重複的程式碼

**RangeTest**方法會將傳遞給 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 方法之*容錯*變數的分母硬編碼。 如果您打算加入其他使用相同容錯計算的測試，則在多個位置使用硬式編碼的值，會使程式碼更難維護。

1. 將私用 helper 方法新增至**unittest1.cpp**類別以計算容錯值，然後從**RangeTest**呼叫該方法。

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // Old code
        // double tolerance = expected/1000;

        // New code
        double tolerance = ToleranceHelper(expected);
    }
    ...
    ```

2. 執行**RangeTest**以確保它仍會通過。

> [!TIP]
> 如果您將 helper 方法加入至測試類別，而不想讓它出現在 [**測試瀏覽器**] 中，請勿將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性加入至方法。

## <a name="see-also"></a>請參閱

- [逐步解說：使用測試瀏覽器進行測試導向的開發](quick-start-test-driven-development-with-test-explorer.md)

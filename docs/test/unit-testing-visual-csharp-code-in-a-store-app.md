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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590861"
---
# <a name="unit-test-c-code"></a>對 C# 程式碼進行單元測試

本文描述如何在 UWP 應用程式中建立 C# 類別的單元測試。

**Rooter**類是被測類，它實現了一個函數，用於計算給定數位的平方根的估計值。

本文演示*了測試驅動開發*。 在此方法中，首先編寫一個測試，以驗證要測試的系統中的特定行為，然後編寫通過測試的代碼。

## <a name="create-the-solution-and-the-unit-test-project"></a>建立方案和單元測試專案

1. 在 [檔案]**** 功能表上，依序選擇 [新增]**** 和 [專案] > ****。

2. 搜尋並選取 [空白應用程式 (通用 Windows)]**** 專案範本。

3. 命名專案**數學**。

4. 在**解決方案資源管理器**中，按右鍵解決方案並選擇"**添加新** > **專案**"。

5. 搜尋並選取 [單元測試應用程式 (通用 Windows)]**** 專案範本。

6. 命名測試專案**RooterTest**。

## <a name="verify-that-the-tests-run-in-test-explorer"></a>驗證測試總管中執行的測試

1. 在*UnitTest.cs*檔中將一些測試代碼插入**TestMethod1：**

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   該<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>類提供了幾種靜態方法，可用於驗證測試方法中的結果。

::: moniker range="vs-2017"

2. 在 [測試]**** 功能表上，選擇 [執行]**[所有測試]** > ****。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在 **"測試"** 功能表上，選擇 **"運行所有測試**"。

::: moniker-end

   測試專案隨即建置並執行。 要有耐心，因為它可能需要一點時間。 將顯示 **"測試資源管理器"** 視窗，測試列在 **"通過測試"** 下。 視窗底部的 **"摘要"** 窗格提供有關所選測試的其他詳細資訊。

## <a name="add-the-rooter-class-to-the-maths-project"></a>將 Rooter 類別新增至 Maths 專案

1. 在**解決方案資源管理器**中，按右鍵**數學**專案，然後選擇 **"添加** > **類**"。

2. 將類別檔案命名為 *Rooter.cs*。

3. 將以下代碼添加到**rooter**類*Rooter.cs*檔中：

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

   **Rooter**類聲明建構函式和**平方根**估計器方法。 **SquareRoot**方法只是一個最小的實現，足以測試測試設定的基本結構。

4. 將`public`關鍵字添加到**Rooter**類聲明，以便測試代碼可以訪問它。

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>新增專案參考

1. 將 Rooter 測試專案的引用添加到數學應用。

    1. 在**解決方案資源管理器**中，按右鍵**Rooter 測試**專案，然後選擇 **"添加** > **參考**"。

    2. 在 [新增參考 - RooterTests]**** 對話方塊中，展開 [方案]**** 並選擇 [專案]****。 選擇**數學**專案。

        ![加入 Maths 專案的參考](../test/media/ute_cs_windows_addreference.png)

2. 向UnitTest.cs`using`檔添加語句*UnitTest.cs*：

    1. 打開*UnitTest.cs*。

    2. 將這個程式碼新增至 `using Microsoft.VisualStudio.TestTools.UnitTesting;` 這一行下方：

       ```csharp
       using Maths;
       ```

3. 添加使用**Rooter**函數的測試。 將以下代碼添加到*UnitTest.cs*：

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

   新測試將顯示在 **"未運行測試**"節點中的**測試資源管理器**中。

4. 為了避免"Payload 包含具有相同目標路徑的兩個或多個檔"錯誤，在**解決方案資源管理器**中，展開**數學**專案下**的屬性**節點，然後刪除*Default.rd.xml*檔。

::: moniker range="vs-2017"

6. 在 [測試總管]**** 中，選擇 [全部執行]****。

   解決方案生成和測試回合並通過。

   ![測試資源管理器中傳遞的基本測試](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. 在**測試資源管理器中**，選擇 **"運行所有測試**"。

   解決方案生成和測試回合並通過。

   ![測試資源管理器中通過的基本測試](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

您已設置測試和應用專案，並驗證是否可以運行調用應用專案中函數的測試。 現在您可以開始撰寫真正的測試和程式碼。

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>反覆擴大測試範圍並使其通過

1. 添加新測試稱為**RangeTest**：

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
   > 建議您不要變更已通過的測試。 而是添加新測試。

2. 運行**RangeTest 測試**並驗證其失敗。

   ![RangeTest 失敗](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > 編寫測試後立即運行它以驗證它是否失敗。 這樣有助於避免撰寫永遠不會失敗的測試這種易犯的錯誤。

3. 透過測試強化程式碼，讓新的測試都成功。 *將 Rooter.cs*中的**SquareRoot**函數更改為：

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

4. 在 [測試總管]**** 中，選擇 [全部執行]****。

::: moniker-end

::: moniker range=">=vs-2019"

4. 在**測試資源管理器中**，選擇 **"運行所有測試**"。

::: moniker-end

   現在三項測試都會成功。

> [!TIP]
> 開發程式碼時，一次加入一個測試。 確定所有測試在每次反覆之後都通過。

## <a name="refactor-the-code"></a>重構程式碼

在本節中，您可以重構應用代碼和測試代碼，然後重新運行測試以確保它們仍然通過。

### <a name="simplify-the-square-root-estimation"></a>簡化平方根估計

1. 通過更改一行代碼來簡化**SquareRoot**函數中的集中計算，如下所示：

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. 運行所有測試以確保尚未引入回歸。 他們應該都通過。

> [!TIP]
> 一組穩定而良好的單元測試，可確認您並未在變更程式碼時引入錯誤。

### <a name="eliminate-duplicated-code"></a>消除重複的代碼

**RangeTest**方法硬編碼傳遞給<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>該方法的*容差*變數的分母。 如果計畫添加使用相同容差計算的其他測試，則在多個位置使用硬編碼值會使代碼更難維護。

1. 向**UnitTest1**類添加專用説明器方法以計算容差值，然後從**RangeTest**調用該方法 。

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

2. 運行**範圍測試**，以確保它仍然通過。

> [!TIP]
> 如果將説明器方法添加到測試類，並且不希望它顯示在**測試資源管理器**中，請不要將<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>屬性添加到 方法。

## <a name="see-also"></a>另請參閱

- [演練：使用測試資源管理器進行測試驅動開發](quick-start-test-driven-development-with-test-explorer.md)

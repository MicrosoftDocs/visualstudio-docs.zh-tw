---
title: 對 Visual C# 程式碼進行單元測試
description: '瞭解如何在 UWP 應用程式中建立 c # 類別的單元測試。 本文將示範以測試為導向的開發。'
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 410d5dfefa5980bceabff99d66067987b390a615
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330078"
---
# <a name="unit-test-c-code"></a>對 C# 程式碼進行單元測試

本文描述如何在 UWP 應用程式中建立 C# 類別的單元測試。

**Rooter** 類別（即受測類別）會執行一個函式，該函式會計算指定數位之平方根的估計值。

本文將示範以 *測試為導向的開發*。 在此方法中，您會先撰寫測試來驗證您要測試之系統中的特定行為，然後撰寫通過測試的程式碼。

## <a name="create-the-solution-and-the-unit-test-project"></a>建立方案和單元測試專案

1. 在 [檔案] 功能表上，依序選擇 [新增] 和 [專案] > 。

2. 搜尋並選取 [空白應用程式 (通用 Windows)] 專案範本。

3. 將專案命名為 **Maths**。

4. 在 **方案總管** 中，以滑鼠右鍵按一下方案，然後選擇 [**加入**  >  **新專案**]。

5. 搜尋並選取 [單元測試應用程式 (通用 Windows)] 專案範本。

6. 將測試專案命名為 **RooterTests**。

## <a name="verify-that-the-tests-run-in-test-explorer"></a>驗證測試總管中執行的測試

1. 在 *UnitTest.cs* 檔案的 **TestMethod1** 中插入一些測試程式碼：

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>類別提供數個靜態方法，可讓您用來驗證測試方法的結果。

::: moniker range="vs-2017"

2. 在 [測試] 功能表上，選擇 [執行]**[所有測試]** > 。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在 [ **測試** ] 功能表上，選擇 [ **執行所有測試**]。

::: moniker-end

   測試專案隨即建置並執行。 請耐心等候，因為可能需要一些時間。 [ **測試瀏覽器** ] 視窗隨即出現，且測試會列在 [ **通過的測試**] 底下。 視窗底部的 [ **摘要** ] 窗格會提供有關所選取測試的其他詳細資料。

## <a name="add-the-rooter-class-to-the-maths-project"></a>將 Rooter 類別新增至 Maths 專案

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **Maths** 專案，然後選擇 [**加入**  >  **類別**]。

2. 將類別檔案命名為 *Rooter.cs*。

3. 將下列程式碼加入至 **Rooter** 類別 *Rooter.cs* 檔：

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

   **Rooter** 類別會宣告一個函式和 **SquareRoot** 估算器方法。 **SquareRoot** 方法只是最基本的實作為，足以測試測試設定的基本結構。

4. 將 `public` 關鍵字加入至 **Rooter** 類別宣告，讓測試程式碼可以存取它。

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>新增專案參考

1. 將 RooterTests 專案的參考新增至 Maths 應用程式。

    1. 在 **方案總管** 中，以滑鼠右鍵按一下 **RooterTests** 專案，然後選擇 [**加入**  >  **參考**]。

    2. 在 [新增參考 - RooterTests] 對話方塊中，展開 [方案] 並選擇 [專案]。 選取 **Maths** 專案。

        ![加入 Maths 專案的參考](../test/media/ute_cs_windows_addreference.png)

2. 將 `using` 語句新增至 *UnitTest.cs* 檔案：

    1. 開啟 *UnitTest.cs*。

    2. 將這個程式碼新增至 `using Microsoft.VisualStudio.TestTools.UnitTesting;` 這一行下方：

       ```csharp
       using Maths;
       ```

3. 加入使用 **Rooter** 函數的測試。 將下列程式碼新增至 *UnitTest.cs*：

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

   新測試會出現在 [ **測試瀏覽器** ] 的 [ **未執行的測試** ] 節點中。

4. 若要避免「承載包含兩個或多個具有相同目的地路徑的檔案」錯誤，請在 **方案總管** 中展開 [ **Maths** ] 專案底下的 [**屬性**] 節點，然後刪除 *Default.rd.xml* 檔。

::: moniker range="vs-2017"

6. 在 [測試總管] 中，選擇 [全部執行]。

   方案組建和測試會執行並傳遞。

   ![在測試瀏覽器中傳遞的 BasicTest](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. 在 [ **測試瀏覽器**] 中，選擇 [ **執行所有測試**]。

   方案組建和測試會執行並傳遞。

   ![測試瀏覽器中傳遞的基本測試](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

您已設定測試和應用程式專案，並確認您可以執行在應用程式專案中呼叫函式的測試。 現在您可以開始撰寫真正的測試和程式碼。

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>反覆擴大測試範圍並使其通過

1. 加入名為 **RangeTest** 的新測試：

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
   > 建議您不要變更已通過的測試。 請改為加入新的測試。

2. 執行 **RangeTest** 測試並確認其失敗。

   ![RangeTest 失敗](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > 當您撰寫測試之後，請執行它來確認它是否失敗。 這樣有助於避免撰寫永遠不會失敗的測試這種易犯的錯誤。

3. 透過測試強化程式碼，讓新的測試都成功。 將 *Rooter.cs* 中的 **SquareRoot** 函數變更為：

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

4. 在 [ **測試瀏覽器**] 中，選擇 [ **執行所有測試**]。

::: moniker-end

   現在三項測試都會成功。

> [!TIP]
> 開發程式碼時，一次加入一個測試。 確定所有測試在每次反覆之後都通過。

## <a name="refactor-the-code"></a>重構程式碼

在本節中，您會重構應用程式和測試程式碼，然後重新執行測試，以確定它們仍然通過。

### <a name="simplify-the-square-root-estimation"></a>簡化平方根的根估計

1. 藉由變更一行程式碼，以簡化 **SquareRoot** 函式中的集中計算，如下所示：

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. 執行所有測試，以確定您未引進回歸。 它們應該全部通過。

> [!TIP]
> 一組穩定而良好的單元測試，可確認您並未在變更程式碼時引入錯誤。

### <a name="eliminate-duplicated-code"></a>消除重複的程式碼

**RangeTest** 方法會將傳遞給方法之 *容錯* 變數的分母硬編碼 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 。 如果您打算加入其他使用相同容錯計算的測試，在多個位置使用硬式編碼值會使程式碼更難維護。

1. 將私用 helper 方法加入至 **UnitTest1** 類別以計算容錯值，然後從 **RangeTest** 呼叫該方法。

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

2. 執行 **RangeTest** 以確定它仍然通過。

> [!TIP]
> 如果您將 helper 方法加入至測試類別，而不想讓它出現在 [ **Test Explorer**] 中，請不要將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性加入至方法。

## <a name="see-also"></a>另請參閱

- [逐步解說：使用 Test Explorer 進行測試導向開發](quick-start-test-driven-development-with-test-explorer.md)

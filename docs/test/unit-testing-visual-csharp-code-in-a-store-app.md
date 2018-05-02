---
title: 對 Visual Studio 中的 Visual C# 程式碼進行單元測試
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: b409e3faa44b19cf0018e770915c8a3868f9ead4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="unit-testing-visual-c-code"></a>對 Visual C# 程式碼進行單元測試

本主題說明如何在 UWP 應用程式中建立 Visual C# 類別的單元測試。 Rooter 類別會藉由實作計算某數值的平方根估計數的函式，示範微積分中極限理論的模糊記憶。 然後 Maths 應用程式就可以使用這個函式向使用者展現許多可運用數學運算執行的有趣作業。

本主題示範如何使用單元測試做為開發工作的第一步。 採用這種方式時，您會先撰寫測試方法，用來驗證要測試之系統中的特定行為，然後撰寫通過測試的程式碼。 依照下列程序的順序進行變更，您就可以反轉策略，先撰寫要測試的程式碼，再撰寫單元測試。

本主題還會建立單一 Visual Studio 方案，以及用於單元測試和要測試之 DLL 的個別專案。 您也可以直接在 DLL 專案中包含單元測試，或是針對單元測試和 DLL 建立個別方案。

## <a name="create-the-solution-and-the-unit-test-project"></a>建立方案和單元測試專案

1. 在 [檔案] 功能表上，選擇 [新增] > [專案]。

2. 在 [新增專案] 對話方塊上，展開 [已安裝] > [Visual C#]，並選擇 [Windows 通用]。 然後從專案範本清單中選擇 [空白應用程式]。

3. 將專案命名為 `Maths`，並確認已選取 [為方案建立目錄]。

4. 在方案總管中選擇方案名稱，並從捷徑功能表選擇 [新增]，然後選擇 [新增專案]。

5. 在 [新增專案] 對話方塊上，展開 [已安裝]，然後展開 [Visual C#]，並選擇 [Windows 通用]。 接著從專案範本清單中選擇 [單元測試應用程式 (通用 Windows)]。

6. 在 Visual Studio 編輯器中開啟 *UnitTest1.cs*。

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using Maths;

   namespace RooterTests
   {
       [TestClass]
       public class UnitTest1

           [TestMethod]
           public void TestMethod1()
           {

           }
   ```

   請注意：

   - 每一項測試都是使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性定義。 測試方法必須傳回 void，而且不可以有任何參數。

   - 測試方法必須在以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性裝飾的類別中。

        在測試執行時，會建立每個測試類別的執行個體。 將會以非指定的順序來呼叫測試方法。

   - 您可以定義在每個模組、類別或方法之前和之後叫用的特殊方法。 如需詳細資訊，請參閱[在單元測試中使用 MSTest 架構](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)。

## <a name="verify-that-the-tests-run-in-test-explorer"></a>驗證測試總管中執行的測試

1. 在 **UnitTest1.cs** 檔案的 TestMethod1 中插入一些測試程式碼：

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   請注意， <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別提供數個靜態方法，可讓您在測試方法中用來驗證結果。

2. 選擇 [測試] 功能表上的 [執行]，然後選擇 [全部執行]。

   測試專案隨即建置並執行。 [測試總管] 視窗隨即開啟，而且測試會在 [通過的測試] 底下列出。 視窗底部的 [摘要] 窗格會提供有關所選取測試的其他詳細資料。

   ![測試總管](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-rooter-class-to-the-maths-project"></a>將 Rooter 類別新增至 Maths 專案

1. 在方案總管中，選擇 **Maths** 專案名稱。 從捷徑功能表中選擇 [新增]，然後選擇 [類別]。

2. 將類別檔案命名為 *Rooter.cs*。

3. 將下列程式碼新增至 Rooter 類別 *Rooter.cs* 檔案：

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

   `Rooter` 類別會宣告建構函式和 `SquareRoot` 評估工具方法。

4. `SquareRoot` 方法只是最簡單的實作，剛好足夠進行測試設定的基本結構測試。

## <a name="couple-the-test-project-to-the-app-project"></a>將測試專案與應用程式專案結合

1. 將 Maths 應用程式的參考新增至 RooterTests 專案。

    1. 在方案總管中選擇 **RooterTests** 專案，然後在捷徑功能表上選擇 [新增參考...]。

    2. 在 [新增參考 - RooterTests] 對話方塊中，展開 [方案] 並選擇 [專案]。 然後選取 **Maths** 項目。

        ![將參考加入 Maths 專案](../test/media/ute_cs_windows_addreference.png)

2. 將 using 陳述式加入至 *UnitTest1.cs* 檔案：

    1. 開啟 *UnitTest1.cs*。

    2. 將這個程式碼新增至 `using Microsoft.VisualStudio.TestTools.UnitTesting;` 這一行下方：

       ```csharp
       using Maths;
       ```

3. 新增使用 Rooter 函式的測試。 將下列程式碼加入至 *UnitTest1.cs*：

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

4. 建置方案。

   新測試會出現在 [測試總管] 的 [未執行的測試] 節點中。

5. 在 [測試總管] 中，選擇 [ **全部執行**]。

   ![基本測試成功](../test/media/ute_cpp_testexplorer_basictest.png)

您已經設定測試和程式碼專案，並確認您可以執行在程式碼專案中執行函式的測試。 現在您可以開始撰寫真正的測試和程式碼。

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>反覆擴大測試範圍並使其通過

1. 加入新的測試：

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = ToleranceHelper(expected);
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > 建議您不要變更已通過的測試。 相反地，請加入新的測試，更新程式碼，使測試通過，然後再加入另一個測試，依此類推。
   >
   > 當您的使用者變更他們的需求時，請停用已不再正確的測試。 以相同的累加方式，撰寫新的測試，一次使一個測試生效。

2. 在 [測試總管] 中，選擇 [ **全部執行**]。

3. 測試失敗。

   ![RangeTest 失敗](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > 在您撰寫每一項測試之後立即確認其失敗。 這樣有助於避免撰寫永遠不會失敗的測試這種易犯的錯誤。

4. 透過測試強化程式碼，讓新的測試都成功。 將 *Rooter.cs* 中的 `SquareRoot` 函式變更如下：

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

5. 建置方案，然後在 [測試總管] 中選擇 [全部執行]。

   現在三項測試都會成功。

> [!TIP]
> 開發程式碼時，一次加入一個測試。 確定所有測試在每次反覆之後都通過。

## <a name="debug-a-failing-test"></a>偵錯失敗的測試

1. 將另一個測試新增至 *UnitTest1.cs*：

    ```csharp
    // Verify that negative inputs throw an exception.
    [TestMethod]
    public void NegativeRangeTest()
    {
        string message;
        Rooter rooter = new Rooter();
        for (double v = -0.1; v > -3.0; v = v - 0.5)
        {
            try
            {
                // Should raise an exception:
                double actual = rooter.SquareRoot(v);

                message = String.Format("No exception for input {0}", v);
                Assert.Fail(message);
            }
            catch (ArgumentOutOfRangeException ex)
            {
                continue; // Correct exception.
            }
            catch (Exception e)
            {
                message = String.Format("Incorrect exception for {0}", v);
                Assert.Fail(message);
            }
        }
    }
    ```

2. 在 [測試總管] 中，選擇 [全部執行]。

   測試失敗。 在 [測試總管] 中選擇測試名稱。 失敗的判斷提示會反白顯示。 [測試總管] 的詳細資料窗格中會顯示失敗的訊息。

   ![NegativeRangeTests 失敗](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. 若要查看測試失敗的原因，請逐步執行函式：

    1. 在 `SquareRoot` 函式的開頭設定中斷點。

    2. 在失敗測試的捷徑功能表上，選擇 [偵錯選取的測試] 。

        當在中斷點停止執行時，逐步執行程式碼。

    3. 將程式碼新增至 Rooter 方法以擷取例外狀況：

        ```csharp
        public double SquareRoot(double x)
        {
            if (x < 0.0)
            {
                throw new ArgumentOutOfRangeException();
        }
        ```

4. 在 [測試總管] 中，選擇 [全部執行] 測試修正過的方法，並確定並未導入迴歸。

現在所有測試都通過了。

![所有測試都成功](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code"></a>重構程式碼

**簡化 SquareRoot 函式中的主要計算。**

1. 變更結果實作

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. 選擇 [全部執行] 測試重構的方法，並確定並未導入迴歸。

> [!TIP]
> 一組穩定而良好的單元測試，可確認您並未在變更程式碼時引入錯誤。

**重構測試程式碼以消除重複的程式碼。**

請注意，`tolerance` 方法會對傳遞至 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 方法之 `RangeTest` 變數的分母採用硬式編碼。 如果您打算新增其他使用相同容錯計算的測試，則在多個位置使用硬式編碼值可能導致錯誤。

1. 將私用方法加入至 Unit1Test 類別以計算容錯值，然後改為呼叫該方法。

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
        // old code
        // double tolerance = expected/1000;
        // new code
        double tolerance = ToleranceHelper(expected);
        Assert.AreEqual(expected, actual, tolerance);
    }
    ...
    ```

2. 選擇 [全部執行] 以測試重構的方法，並確定並未導入錯誤。

> [!NOTE]
> 如果您將 helper 方法加入測試類別，而不希望該測試類別出現在 [測試總管] 中，請勿將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性加入方法。
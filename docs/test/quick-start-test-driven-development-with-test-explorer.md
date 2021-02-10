---
title: 測試驅動開發逐步解說
description: '瞭解如何在 c # 中使用 Microsoft Test Framework 開發經過測試的方法，您可以輕鬆地針對其他語言或測試架構（例如 NUnit）進行調整。'
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 56bfe2b00efc4af71ca562672ad01423778edecd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943727"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>逐步解說：使用 Test Explorer 進行測試導向開發

建立單元測試，以協助讓您的程式碼在經歷漸進的程式碼變更之後仍然能夠正確運作。 有數種架構都可以用來撰寫單元測試，包含由協力廠商所開發的架構。 某些測試架構是專門讓您使用不同的語言或平台來進行測試。 [測試總管] 提供單一介面，讓您使用任一種架構來進行單元測試。 如需 [測試總管] 的詳細資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)和[測試總管常見問題集](test-explorer-faq.md)。

本逐步解說示範如何使用 Microsoft 測試架構 (MSTest) 以 C# 來開發受測方法。 您可以輕鬆地將它改寫成其他語言或其他測試架構 (例如 NUnit)。 如需詳細資訊，請參閱 [安裝協力廠商單元測試](install-third-party-unit-test-frameworks.md)架構。

## <a name="create-a-test-and-generate-code"></a>建立測試並產生程式碼

1. 建立一個 C# **類別庫 (.NET Standard)** 專案。 這個專案將包含我們想要測試的程式碼。 將專案命名為 **MyMath**。

2. 在同一個方案中，新增一個 **MSTest 測試專案 (.NET Core)** 專案。 將測試專案命名為 **MathTests**。

   ![新程式碼和測試專案](../test/media/test-driven-development-ide.png)

3. 撰寫簡單的測試方法以驗證特定輸入所產生的結果。 將下列程式碼新增至 `UnitTest1` 類別：

   ```csharp
   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. 從測試程式碼產生類型。

   1. 將游標放在上 `Rooter` ，然後從燈泡功能表中選擇 [**產生類型 ' Rooter '**  >  **產生新的類型**]。

      ![產生新的類型快速動作](media/test-driven-development-generate-new-type.png)

   2. 在 [產生類型] 對話方塊中，將 [專案] 設為類別庫專案 **MyMath**，然後選擇 [確定]。

      ![Visual Studio 2019 中的 [產生類別] 對話方塊](media/test-driven-development-generate-type-dialog.png)

5. 從測試程式碼產生方法。 將游標置於 `SquareRoot` 上，然後從燈泡功能表選擇 [產生方法 'Rooter.SquareRoot']。

6. 執行單元測試。

   1. 在 [測試] 功能表上，開啟 [測試總管]，選擇 [Windows] > [測試總管]。

   2. 在 [測試總管] 中，選擇 [全部執行] 按鈕以執行測試。

   接著就會建置方案並執行測試，然後失敗。

7. 選取測試的名稱。

   測試的詳細資料會顯示在 [測試詳細摘要] 窗格中。

   ![測試總管中的測試詳細資料摘要](media/test-driven-development-test-detail-summary.png)

8. 選取 [堆疊追蹤] 底下的第一個連結，以跳至測試失敗的位置。

此時，您已建立可以修改的測試和 stub，好讓測試能夠成功。

## <a name="verify-a-code-change"></a>驗證程式碼變更

1. 在 *Class1.cs* 檔案中，改進 `SquareRoot` 的程式碼：

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. 在 [測試總管] 中，選擇 [全部執行]。

   接著就會建置方案並執行測試，然後通過測試。

   ![顯示通過測試的測試總管](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>擴充輸入的範圍

若要提高您對於程式碼在任何情況下都能運作的信心，可以加入嘗試各種輸入值的測試。

> [!TIP]
> 避免改變已經成功的現有測試， 而改為加入新的測試。 只有在使用者的需求改變時，才變更現有的測試。 這個原則可協助您確保在擴充程式碼時不會失去現有的功能。

1. 在測試類別中加入以下測試，該測試會嘗試某個範圍的輸入值：

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. 在 [測試總管] 中，選擇 [全部執行]。

   新的測試失敗了，不過，第一個測試仍然成功。 若要找出失敗點，請選取失敗的測試，然後在 [測試詳細資料摘要] 窗格中查看詳細資料。

3. 檢查受測方法看看可能是哪裡出錯了。 依照下列方式修改 `SquareRoot` 程式碼：

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4. 在 [測試總管] 中，選擇 [全部執行]。

   現在兩個測試都成功了。

## <a name="add-tests-for-exceptional-cases"></a>加入例外狀況的測試

1. 加入新的測試以找出不正確的輸入：

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. 在 [測試總管] 中，選擇 [全部執行]。

   受測方法會產生迴圈現象，必須手動取消。

3. 選擇 [測試總管] 工具列上的 [取消]。

   測試會停止執行。

4. 透過在方法的開始位置新增以下的 `if` 陳述式，以修正 `SquareRoot` 程式碼：

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. 在 [測試總管] 中，選擇 [全部執行]。

   所有測試都成功。

## <a name="refactor-the-code-under-test"></a>重構受測程式碼

重構程式碼，但不變更測試。

> [!TIP]
> 「重構」(Refactoring) 是要讓程式碼的效能變得更好或讓程式碼更容易了解而做的變更。 它不是要變更程式碼的行為，因此並不會變更測試。
>
> 我們建議您分開執行重構步驟與擴充功能的步驟。 讓測試保持不變，您就會有信心沒有在重構時不小心引入了 Bug。

1. 如下所示，變更 `SquareRoot` 方法中計算 `result` 的程式碼：

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }

        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
            previousResult = result;
            result = (result + input / result) / 2;
            //was: result = result - (result * result - input) / (2*result);
        }
        return result;
    }
    ```

2. 選擇 [全部執行]，然後確認仍然通過所有測試。

   ![顯示 3 個通過測試的測試總管](../test/media/test-driven-development-three-passed-tests.png)

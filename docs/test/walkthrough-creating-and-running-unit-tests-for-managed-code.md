---
title: C# 單元測試教學課程
description: 瞭解如何使用適用于 managed 程式碼的 Microsoft 單元測試架構和 Visual Studio Test Explorer，建立、執行和自訂一系列的單元測試。
ms.custom: SEO-VS-2020
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: a6ab205b7f651f8bb5954bee4998602c79fd78e7
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683917"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>逐步解說：針對受控碼建立和執行單元測試

本文會引導您使用適用於受控碼的 Microsoft 單元測試架構和 Visual Studio [測試總管]，來建立、執行和自訂一系列的單元測試。 您可以從開發中的 C# 專案開始，建立執行其程式碼的測試、執行測試，並檢查結果。 然後，變更專案程式碼並重新執行測試。



## <a name="create-a-project-to-test"></a>建立要測試的專案

::: moniker range="vs-2017"

1. 開啟 Visual Studio。

2. **在 [檔案**] 功能表上選取 [**新增** > **專案**]。

   [新增專案]  對話方塊隨即出現。

3. 在 [Visual C#]**[.NET Core]** >  類別下方，選擇 [主控台應用程式 (.NET Core)] 專案範本。

4. 將專案命名為 **Bank**，然後按一下 [確定]。

   即會建立 Bank 專案並顯示在 [方案總管] 中，並於程式碼編輯器中開啟 *Program.cs* 檔案。

   > [!NOTE]
   > 如果 *Program.cs* 檔案並未在編輯器中開啟，請在 [方案總管] 中按兩下 *Program.cs* 檔案來開啟。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。

2. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

3. 搜尋並選取適用于 .NET Core 的 c # **主控台應用程式** 專案範本，然後按 **[下一步]**。

   > [!NOTE]
   > 如果您沒有看到 [ **主控台應用程式** ] 範本，您可以從 [ **建立新專案** ] 視窗進行安裝。 在 [找不到您要找的資料嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。 接下來，在 Visual Studio 安裝程式中選擇 **.NET Core 跨平台開發** 工作負載。

4. 將專案命名為 **Bank**，然後按 **[下一步]**。

   選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。

   即會建立 Bank 專案並顯示在 [方案總管] 中，並於程式碼編輯器中開啟 *Program.cs* 檔案。

   > [!NOTE]
   > 如果 *Program.cs* 檔案並未在編輯器中開啟，請在 [方案總管] 中按兩下 *Program.cs* 檔案來開啟。

::: moniker-end

5. 使用下列會定義 *BankAccount* 類別的 C# 程式碼取代 *Program.cs* 內容：

   ```csharp
   using System;

   namespace BankAccountNS
   {
       /// <summary>
       /// Bank account demo class.
       /// </summary>
       public class BankAccount
       {
           private readonly string m_customerName;
           private double m_balance;

           private BankAccount() { }

           public BankAccount(string customerName, double balance)
           {
               m_customerName = customerName;
               m_balance = balance;
           }

           public string CustomerName
           {
               get { return m_customerName; }
           }

           public double Balance
           {
               get { return m_balance; }
           }

           public void Debit(double amount)
           {
               if (amount > m_balance)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount; // intentionally incorrect code
           }

           public void Credit(double amount)
           {
               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount;
           }

           public static void Main()
           {
               BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

               ba.Credit(5.77);
               ba.Debit(11.22);
               Console.WriteLine("Current balance is ${0}", ba.Balance);
           }
       }
   }
   ```

6. 按一下滑鼠右鍵，選擇 [方案總管] 中的 [重新命名]，將檔案重新命名為 *BankAccount.cs*。

7. 在 [**組建**] 功能表上，按一下 [**建立方案** (]，或按 **Ctrl**  +  **SHIFT**  +  **B**) 。

您現在已擁有具備測試方法的專案。 本文中的測試著重於 `Debit` 方法。 從帳戶中提領貨幣時，會呼叫 `Debit` 方法。

## <a name="create-a-unit-test-project"></a>建立單元測試專案

1. 在 [檔案] 功能表上，選取 [新增] > [新增專案]。

   > [!TIP]
   > 您也可以在 [方案總管] 中以滑鼠右鍵按一下方案，然後選擇 [新增] > [新增專案]。

::: moniker range="vs-2017"

2. 在 [ **新增專案** ] 對話方塊中，展開 [ **已安裝**]，展開 [ **Visual c #**]，然後選擇 [ **測試**]。

3. 從範本清單中選取 [MSTest 測試專案 (.NET Core)]。

4. 在 [名稱] 文字方塊中，輸入 `BankTests`，然後選取 [確定]。

   **BankTests** 專案就會新增至 **Bank** 方案中。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在 [搜尋] 方塊中輸入 **單元測試** ，選取 **c #** 做為語言，然後選取 [.net Core] 範本的 c # **單元測試專案** ，然後按 **[下一步]**。

   > [!NOTE]
   > 從 Visual Studio 2019 版本16.9 開始，MSTest 專案範本名稱從 **Mstest 單元測試專案 ( .Net Core)** 變更為 **單元測試專案**。

3. 將專案命名為 **BankTests** ，然後按 **[下一步]**。

4. 選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。

   **BankTests** 專案就會新增至 **Bank** 方案中。

::: moniker-end

5. 在 **BankTests** 專案中，新增 **Bank** 專案的參考。

   在 [方案總管] 中，選取 **BankTests** 專案下方的 [相依性]，然後從右鍵功能表選擇 [新增參考]。

6. 在 [參考管理員] 對話方塊中，展開 [專案] 並選取 [方案]，然後選取 [Bank] 項目。

7. 選擇 [確定]。

## <a name="create-the-test-class"></a>建立測試類別

建立測試類別，以確認 `BankAccount` 類別。 您可以使用由專案範本所產生的 *UnitTest1.cs* 檔案；不過，請使用更具有描述性的名稱來命名檔案和類別。

### <a name="rename-a-file-and-class"></a>重新命名檔案和類別

1. 若要重新命名檔案，請在 [方案總管] 中選取 BankTests 專案中的 *UnitTest1.cs* 檔案。 從滑鼠右鍵功能表中，選擇 [ **重新命名** (或按 **F2**) ，然後將檔案重新命名為 *BankAccountTests.cs*。

::: moniker range="vs-2017"

2. 若要重新命名類別，請在隨即顯示且詢問您是否也想重新命名程式碼項目之參考的對話方塊中選擇 [是]。

::: moniker-end

::: moniker range=">=vs-2019"

2. 若要重新命名類別，請將游標放在程式 `UnitTest1` 代碼編輯器中，按一下滑鼠右鍵，然後選擇 [ **重新命名** (或按 **F2**) 。 鍵入 **BankAccountTests**，然後按下 **Enter**。

::: moniker-end

*BankAccountTests.cs* 檔案現在包含下列程式碼：

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

### <a name="add-a-using-statement"></a>新增 using 陳述式

在測試類別中加入[ `using` 語句](/dotnet/csharp/language-reference/keywords/using-statement)，以便能夠呼叫受測專案，而不需要使用完整名稱。 在類別檔案的頂端，加入：

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>測試類別需求

測試類別的最低需求如下：

- 對於包含要在 [測試總管] 中執行之單元測試方法的任何類別而言，`[TestClass]` 屬性是必要的。

- 您要讓 [測試總管] 辨識的每個測試方法都必須具有 `[TestMethod]` 屬性。

單元測試專案中可以含有不具有 `[TestClass]` 屬性的其他類別，而測試類別中也可以含有不具有 `[TestMethod]` 屬性的其他方法。 您可以從您的測試方法中呼叫這些其他類別和方法。

## <a name="create-the-first-test-method"></a>建立第一個測試方法

在這個程序中，您會撰寫單元測試方法以驗證 `BankAccount` 類別之 `Debit` 方法的行為。

至少有三項需要檢查的行為：

- 如果付款金額大於餘額，該方法會擲回 <xref:System.ArgumentOutOfRangeException> 。

- 如果付款金額小於零，該方法會擲回 <xref:System.ArgumentOutOfRangeException>。

- 如果付款金額有效，該方法會從帳戶餘額減去此付款金額。

> [!TIP]
> 您可以刪除預設的 `TestMethod1` 方法，因為您不會在本逐步解說中使用它。

### <a name="to-create-a-test-method"></a>建立測試方法

第一個測試會確認有效金額 (即小於帳戶餘額但大於零的金額) 將從帳戶中提領正確的金額。 將下面方法加入至該 `BankAccountTests` 類別：

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

此方法很直接：會設定具有初始餘額的新 `BankAccount` 物件，然後提領有效的金額。 它會使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> 方法，以確認結尾餘額如預期。

### <a name="test-method-requirements"></a>測試方法需求

測試方法必須符合下列需求：

- 它是以 `[TestMethod]` 屬性裝飾。

- 它會傳回 `void`。

- 它不能有參數。

## <a name="build-and-run-the-test"></a>建置並執行測試

1. 在 [**組建**] 功能表上，選擇 [**組建方案** (]，或按 **Ctrl**  +  **SHIFT**  +  **B**) 。

2. 如果 [ **test explorer** ] 未開啟，請  >  從頂端功能表列中選擇 [測試 **Windows**  >  **test explorer** ] 來開啟它 (或按下 **Ctrl**  +  **E**、 **T**) 。

3. 選擇 [**全部執行**] 以執行測試 (或按 **Ctrl**  +  **R**、 **V**) 。

   執行測試時，[測試總管] 視窗頂端的狀態列會顯示動畫效果。 在測試回合結束時，如果所有的測試方法都成功，狀態列會變成綠色，如果有任何測試失敗則變成紅色。

   在本案例中，測試會失敗。

4. 在 [ **測試瀏覽器** ] 中選取方法，以查看視窗底部的詳細資料。

## <a name="fix-your-code-and-rerun-your-tests"></a>修正程式碼並重新執行測試

測試結果會包含說明失敗的訊息。 針對 `AreEqual` 方法，訊息會顯示預期項目和實際收到的項目。 您預期餘額會減少，但它增加了提領的金額。

單元測試發現了一個錯誤：提領的金額應該從帳戶餘額「減去」，但卻被「加入」至帳戶餘額。

### <a name="correct-the-bug"></a>修正 Bug

若要更正錯誤，請在 *BankAccount.cs* 檔案中取代這一行：

```csharp
m_balance += amount;
```

成為：

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>重新執行測試

在 [**測試瀏覽器**] 中，選擇 [**全部執行**] 以重新執行測試 (或按 **Ctrl**  +  **R**、 **V**) 。 紅色/綠色狀態列會變成綠色，表示測試已通過。

![Visual Studio 2019 的 [測試總管] 顯示已通過測試](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>使用單元測試改善您的程式碼

這一節會說明分析、單元測試開發和重構的反覆流程，是如何協助您讓生產環境程式碼更加強固而有效。

### <a name="analyze-the-issues"></a>分析問題

您已建立測試方法，以確認會在 `Debit` 方法中正確扣除有效金額。 現在，請確認如果付款金額處於下列任一狀況，該方法會擲回 <xref:System.ArgumentOutOfRangeException>：

- 大於餘額，或
- 小於零。

### <a name="create-and-run-new-test-methods"></a>建立並執行新的測試方法

建立測試方法，以確認付款金額小於零時的正確行為：

```csharp
[TestMethod]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act and assert
    Assert.ThrowsException<System.ArgumentOutOfRangeException>(() => account.Debit(debitAmount));
}
```

使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> 方法來判斷提示已擲回正確的例外狀況。 除非擲回 <xref:System.ArgumentOutOfRangeException>，否則此方法會造成測試失敗。 如果在付款金額小於零時，暫時修改受測方法以擲回多個泛型 <xref:System.ApplicationException>，則測試運作方式正確 &mdash; 亦即，它會失敗。

若要測試提領金額大於餘額的案例，請執行下列步驟：

1. 建立名為 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`的新測試方法。

2. 將 `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` 中的方法主體複製到新的方法。

3. 將 `debitAmount` 設定為大於餘額的數字。

執行兩個測試，並確認它們是否通過。

### <a name="continue-the-analysis"></a>繼續分析

您可以進一步改善要測試的方法。 透過目前的實作，我們沒有辦法知道哪些條件 (`amount > m_balance` 或 `amount < 0`) 會導致測試期間擲回例外狀況。 我們只知道在方法中的某處擲回 `ArgumentOutOfRangeException`。 如果我們可以分辨 `BankAccount.Debit` 中的哪個條件造成擲回例外狀況 (`amount > m_balance` 或 `amount < 0`)，讓我們可以確信我們的方法正確地對其引數進行了例行性檢查，這樣會比較好。

請再次查看受測方法 (`BankAccount.Debit`)，您會注意到兩個條件陳述式都使用只接受引數名稱作為參數的 `ArgumentOutOfRangeException` 建構函式：

```csharp
throw new ArgumentOutOfRangeException("amount");
```

有一個建構函式可用來報告更豐富的資訊：<xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> 包含引數的名稱、引數值和使用者定義的訊息。 您可以重構受測方法以使用這個建構函式。 更好的是，您可以使用可公開取得的類型成員來指定錯誤。

### <a name="refactor-the-code-under-test"></a>重構受測程式碼

首先，在類別範圍定義錯誤訊息的兩個常數。 將這些常數放入受測類別 `BankAccount` 中：

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

然後，修改 `Debit` 方法中的兩個條件陳述式：

```csharp
if (amount > m_balance)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
}

if (amount < 0)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
}
```

### <a name="refactor-the-test-methods"></a>重構測試方法

透過移除對 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 的呼叫來重構測試方法。 將呼叫包裝到 `Debit()` 的 `try/catch` 區塊中、攔截預期的特定例外狀況，並確認其相關聯的訊息。 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> 方法可讓您比較兩個字串。

現在，`Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` 可能看起來像這樣：

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>重新測試、重新撰寫和重新分析

目前，測試方法不會處理它應該的所有案例。 如果正在進行測試的方法， `Debit` <xref:System.ArgumentOutOfRangeException> 當 `debitAmount` 大於餘額 (或小於零) 時，方法就無法擲回，測試方法會通過。 這樣就不好了，因為您要的是測試方法在未擲回例外狀況時失敗。

這是測試方法中的錯誤。 若要解決這個問題，請在測試方法的結尾新增 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> 判斷提示，以處理未擲回例外狀況的情況。

重新執行測試後顯示，測試現在會因為攔截到正確的例外狀況而「失敗」。 `catch` 區塊會攔截例外狀況，但是該方法會繼續執行，並且會在新的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> 判斷提示處失敗。 爲了解決此問題，請在 `catch` 區塊的 `StringAssert` 之後新增 `return` 陳述式。 重新執行測試即可確認您已修正這個問題。 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` 的最終版本看起來像這樣：

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

### <a name="conclusion"></a>結論

測試程式碼的改善帶來了更穩固、包含更多資訊的測試方法。 但是更重要的是，它們也改善了受測程式碼。

> [!TIP]
> 本逐步解說會使用適用於 Managed 程式碼的 Microsoft 單元測試架構。 [測試總管] 也可以從已安裝 [測試總管] 配接器的協力廠商單元測試架構來執行測試。 如需詳細資訊，請參閱 [安裝協力廠商單元測試](../test/install-third-party-unit-test-frameworks.md)架構。

## <a name="see-also"></a>另請參閱

如需如何從命令列執行測試的資訊，請參閱 [VSTest.Console.exe 命令列選項](vstest-console-options.md)。

---
title: 針對受控碼建立和執行單元測試
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 2618b8a27ceb4ed03c8b4bb2f3e910c60e61b6cc
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978150"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>逐步解說：為受控碼建立和執行單元測試

本文會引導您使用適用於受控碼的 Microsoft 單元測試架構和 Visual Studio [測試總管]，來建立、執行和自訂一系列的單元測試。 您可以從開發中的 C# 專案開始，建立執行其程式碼的測試、執行測試，並檢查結果。 然後，您可以變更專案程式碼並重新執行測試。

> [!NOTE]
> 本逐步解說會使用適用於 Managed 程式碼的 Microsoft 單元測試架構。 [測試總管] 也可以從已安裝 [測試總管] 配接器的協力廠商單元測試架構來執行測試。 如需詳細資訊，請參閱[安裝協力廠商單元測試架構](../test/install-third-party-unit-test-frameworks.md)

如需如何從命令列執行測試的資訊，請參閱 [VSTest.Console.exe 命令列選項](vstest-console-options.md)。

## <a name="prerequisites"></a>必要條件

- Bank 專案。 請參閱[用於建立單元測試的範例專案](../test/sample-project-for-creating-unit-tests.md)。

## <a name="create-a-project-to-test"></a>建立要測試的專案

1. 開啟 Visual Studio。

2. 在 [檔案] 功能表上選取 [新增] > [專案]。

   [ **新增專案** ] 對話方塊隨即出現。

3. 在 [ **已安裝的範本**] 下，按一下 [ **Visual C#**]。

4. 在應用程式類型清單中，按一下 [ **類別庫**]。

5. 在 [名稱] 方塊中，鍵入 **Bank**，然後按一下 [確定]。

   新的 Bank 專案會建立並顯示在 [方案總管] 中，並於程式碼編輯器中開啟 *Class1.cs* 檔案。

   > [!NOTE]
   > 如果 *Class1.cs* 檔案並未在程式碼編輯器中開啟，請在 [方案總管] 中按兩下 *Class1.cs* 檔案加以開啟。

6. 從[用於建立單元測試的範例專案](../test/sample-project-for-creating-unit-tests.md)複製原始程式碼，並以複製的程式碼取代 *Class1.cs* 的原始內容。

7. 另存新檔成 *BankAccount.cs* 檔案。

8. 在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

現在您已經有一個名為 Bank 的專案。 其中包含要測試的原始程式碼和用來測試它的工具。 Bank 的命名空間 BankAccountNS，包含公用類別 BankAccount，您將會在下列程序中測試其方法。

在本文中，測試著重在 Debit 方法。 從帳戶中提領金額時，就會呼叫 Debit 方法。 以下是方法定義：

```csharp
// Method to be tested.
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}
```

## <a name="create-a-unit-test-project"></a>建立單元測試專案

1. 在 [檔案] 功能表上，選取 [新增] > [新增專案]。

2. 在 [新增專案] 對話方塊中，依序展開 [ **已安裝的**]、[ **Visual C#**]，然後選擇 [ **測試**]。

3. 在範本清單中選擇 [ **單元測試專案**]。

4. 在 [名稱] 文字方塊中，輸入 `BankTests`，然後選取 [確定]。

   **BankTests** 專案就會新增至 **Bank** 方案中。

5. 在 **BankTests** 專案中，新增 **Bank** 專案的參考。

   在 [方案總管] 中，選取 **BankTests** 專案中的 [參考]，然後從操作功能表選擇 [新增參考]。

6. 在 [參考管理員] 對話方塊中，展開 [ **方案** ]，然後檢查 [ **Bank** ] 項目。

## <a name="create-the-test-class"></a>建立測試類別

建立測試類別，以確認 `BankAccount` 類別。 您可以使用由專案範本所產生的 *UnitTest1.cs* 檔案；不過，請使用更具有描述性的名稱來命名檔案和類別。 在 [方案總管] 中重新命名檔案，就能以一個步驟達成目的。

### <a name="rename-a-class-file"></a>重新命名類別檔案

在 [方案總管] 中，選取 BankTests 專案中的 *UnitTest1.cs* 檔案。 從操作功能表中，選擇 [重新命名]，然後將檔案重新命名為 *BankAccountTests.cs*。 在詢問您是否要重新命名專案中程式碼項目 `UnitTest1` 的所有參考的對話方塊上，選擇 [是]。

此步驟會將類別名稱變更為 `BankAccountTests`。 *BankAccountTests.cs* 檔案現在會包含下面程式碼：

```csharp
using System;
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

### <a name="add-a-using-statement-to-the-project-under-test"></a>將 using 陳述式加入至受測專案

您也可以將 `using` 陳述式新增至類別，以便能夠呼叫受測專案，而不需使用完整名稱。 在類別檔案的頂端，加入：

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>測試類別需求

測試類別的最低需求如下：

- 在適用於 Managed 程式碼的 Microsoft 單元測試架構中，對於包含要在 [測試總管] 中執行的單元測試方法的任何類別而言， `[TestClass]` 屬性是必要的。

- 您要讓 [測試總管] 執行的每個測試方法都必須具有 `[TestMethod]` 屬性。

單元測試專案中可以含有不具有 `[TestClass]` 屬性的其他類別，而測試類別中也可以含有不具有 `[TestMethod]` 屬性的其他方法。 您可以在測試方法中使用這些其他類別和方法。

## <a name="create-the-first-test-method"></a>建立第一個測試方法

在這個程序中，您會撰寫單元測試方法以驗證 `BankAccount` 類別之 `Debit` 方法的行為。 `Debit` 方法先前已在本文中顯示。

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

該方法非常簡單：它會設定一開始就有餘額的新 `BankAccount` 物件，然後提領有效的金額。 它會使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> 方法，以確認結尾餘額如預期。

### <a name="test-method-requirements"></a>測試方法需求

測試方法必須符合下列需求：

- 它是以 `[TestMethod]` 屬性裝飾。

- 它會傳回 `void`。

- 它不能有參數。

## <a name="build-and-run-the-test"></a>建置並執行測試

1. 在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。

   如果沒有發生錯誤，則 [測試總管] 視窗隨即出現，並在 [未執行的測試] 群組中列出 **Debit_WithValidAmount_UpdatesBalance**。

   > [!TIP]
   > 如果順利完成建置後，[測試總管] 沒有出現，請選擇功能表上的 [測試]，然後依序選擇 [視窗]和 [測試總管]

2. 選擇 [ **全部執行** ] 以執行測試。 當測試在執行時，視窗頂端的狀態列會顯示動畫效果。 在測試回合結束時，如果所有的測試方法都成功，狀態列會變成綠色，如果有任何測試失敗則變成紅色。

3. 在本案例中，測試會失敗。 測試方法會移至 [失敗的測試] 群組。 在 [測試總管] 中選取該方法，以在視窗底部檢視詳細資料。

## <a name="fix-your-code-and-rerun-your-tests"></a>修正程式碼並重新執行測試

### <a name="analyze-the-test-results"></a>分析測試結果

測試結果會包含說明失敗的訊息。 如果是 `AreEquals` 方法，訊息會顯示預期的參數 (**Expected\<值>** 參數) 和實際收到的參數 (**Actual\<值>** 參數)。 您預期餘額會減少，但實際上它增加了提領的金額。

單元測試發現了一個錯誤：提領的金額應該從帳戶餘額「減去」，但卻被「加入」至帳戶餘額。

### <a name="correct-the-bug"></a>修正 Bug

若要更正這個錯誤，請將這一行：

```csharp
m_balance += amount;
```

取代為：

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>重新執行測試

在 [測試總管] 中，選擇 [ **全部執行** ] 以重新執行測試。 紅色/綠色狀態列會轉成綠色，表示通過測試，且測試會移至 [成功的測試] 群組。

## <a name="use-unit-tests-to-improve-your-code"></a>使用單元測試改善您的程式碼

這一節會說明分析、單元測試開發和重構的反覆流程，是如何協助您讓生產環境程式碼更加強固而有效。

### <a name="analyze-the-issues"></a>分析問題

您已建立測試方法，以確認會在 `Debit` 方法中正確扣除有效金額。 現在，請確認如果付款金額處於下列任一狀況，該方法會擲回 <xref:System.ArgumentOutOfRangeException>：

- 大於餘額，或
- 小於零。

### <a name="create-the-test-methods"></a>建立測試方法

建立測試方法，以確認付款金額小於零時的正確行為：

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> 屬性來判斷提示已擲回正確的例外狀況。 除非擲回 <xref:System.ArgumentOutOfRangeException> ，否則此屬性會造成測試失敗。 如果在付款金額小於零時，暫時修改受測方法以擲回多個泛型 <xref:System.ApplicationException>，則測試運作方式正確 &mdash; 亦即，它會失敗。

若要測試提領金額大於餘額的案例，請執行下列步驟：

1. 建立名為 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`的新測試方法。

2. 將 `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` 中的方法主體複製到新的方法。

3. 將 `debitAmount` 設定為大於餘額的數字。

### <a name="run-the-tests"></a>執行測試

執行兩個測試方法可示範如何正確運作測試。

### <a name="continue-the-analysis"></a>繼續分析

不過，最後兩個測試方法也令人困擾。 在任一測試時，您無法確定受測方法中的哪個條件會擲回例外狀況。 某種可區分兩個條件 (即負的付款金額或金額大於餘額) 的方式，會增加您對測試的信賴度。

請再次查看受測方法，您會注意到兩個條件陳述式都使用只接受引數名稱作為參數的 `ArgumentOutOfRangeException` 建構函式：

```csharp
throw new ArgumentOutOfRangeException("amount");
```

有一個建構函式可用來報告更豐富的資訊：<xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> 包含引數的名稱、引數值和使用者定義的訊息。 您可以重構受測方法以使用這個建構函式。 更好的是，您可以使用可公開取得的類型成員來指定錯誤。

### <a name="refactor-the-code-under-test"></a>重構受測程式碼

首先，在類別範圍定義錯誤訊息的兩個常數。 將這些常數放入受測類別 BankAccount 中：

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

然後，修改 `Debit` 方法中的兩個條件陳述式：

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>重構測試方法

移除 `ExpectedException` 測試方法屬性，改為攔截擲回的例外狀況，並確認其相關聯的訊息。 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> 方法可讓您比較兩個字串。

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
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>重新測試、重新撰寫和重新分析

假設受測方法中有一個錯誤，因此 `Debit` 方法不僅不會「擲回」<xref:System.ArgumentOutOfRangeException>，更不會輸出包含例外狀況的正確訊息。 目前，測試方法不會處理這種情況。 如果 `debitAmount` 值有效 (也就是說，小於餘額但大於零)，則不會攔截到任何例外狀況，因此永遠不會引發判斷提示。 然而，測試方法會成功。 這樣就不好了，因為您要的是測試方法在未擲回例外狀況時失敗。

這是測試方法中的錯誤。 若要解決這個問題，請在測試方法的結尾新增 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> 判斷提示，以處理未擲回例外狀況的情況。

但是重新執行測試後顯示，測試現在會因為攔截到正確的例外狀況而「失敗」。 `catch` 區塊會攔截例外狀況，但是該方法會繼續執行，並且會在新的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> 判斷提示處失敗。 爲了解決此問題，請在 `catch` 區塊的 `StringAssert` 之後新增 `return` 陳述式。 重新執行測試即可確認您已修正這個問題。 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` 的最終版本看起來像這樣：

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
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

測試程式碼的改善帶來了更穩固、包含更多資訊的測試方法。 但是更重要的是，它們也改善了受測程式碼。

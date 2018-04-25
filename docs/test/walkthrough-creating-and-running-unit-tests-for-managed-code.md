---
title: 逐步解說：在 Visual Studio 中針對 Managed 程式碼建立和執行單元測試 | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: a34fded72a0d04f3920e0d7a76f9550993b520e7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>逐步解說：針對 Managed 程式碼建立和執行單元測試

本逐步解說會引導您使用適用於 Managed 程式碼的 Microsoft 單元測試架構和 Visual Studio 測試總管，來建立、執行和自訂一系列的單元測試。 您可以從開發中的 C# 專案開始，建立執行其程式碼的測試、執行測試，並檢查結果。 然後，您可以修改專案程式碼並重新執行測試。

 此主題包括下列章節：

 [準備逐步解說](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)

 [建立單元測試專案](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)

 [建立測試類別](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)

-   [測試類別需求](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)

 [建立第一個測試方法](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)

-   [測試方法需求](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)

 [建置並執行測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)

 [修正程式碼並重新執行測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)

 [使用單元測試改善您的程式碼](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)

> [!NOTE]
>  本逐步解說會使用適用於 Managed 程式碼的 Microsoft 單元測試架構。 [測試總管] 也可以從已安裝測試總管配接器的協力廠商單元測試架構來執行測試。 如需詳細資訊，請參閱[安裝協力廠商單元測試架構](../test/install-third-party-unit-test-frameworks.md)

> [!NOTE]
>  如需有關如何從命令列執行測試的資訊，請參閱[逐步解說：使用命令列測試公用程式](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)。

## <a name="prerequisites"></a>必要條件

-   Bank 專案。 請參閱[用於建立單元測試的範例專案](../test/sample-project-for-creating-unit-tests.md)。

##  <a name="BKMK_Prepare_the_walkthrough"></a> 準備逐步解說

1.  開啟 Visual Studio。

2.  在 [ **檔案** ] 功能表上，指向 [ **新增** ]，然後按一下 [ **專案**]。

     [ **新增專案** ] 對話方塊隨即出現。

3.  在 [ **已安裝的範本**] 下，按一下 [ **Visual C#**]。

4.  在應用程式類型清單中，按一下 [ **類別庫**]。

5.  在 [ **名稱** ] 方塊中，輸入 `Bank` ]，然後按一下 [ **確定**。

    > [!NOTE]
    > 如果已經有專案使用 "Bank" 這個名稱，就請為專案選擇另一個名稱。

     新的 Bank 專案會建立並顯示在方案總管中，並於程式碼編輯器中開啟 Class1.cs 檔。

    > [!NOTE]
    > 如果 Class1.cs 檔並未在程式碼編輯器中開啟，請在方案總管中按兩下 Class1.cs 檔加以開啟。

6.  從[用於建立單元測試的範例專案](../test/sample-project-for-creating-unit-tests.md)複製原始程式碼。

7.  使用[用於建立單元測試的範例專案案](../test/sample-project-for-creating-unit-tests.md)的程式碼取代 Class1.cs 的原始內容。

8.  另存新檔成 BankAccount.cs 檔案

9. 在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

 現在您已經有一個名為 Bank 的專案。 其中包含要測試的原始程式碼和用來測試它的工具。 Bank 的命名空間 **BankAccountNS**，包含了公用類別 **BankAccount**，您將會在下列程序中測試其方法。

 在這個快速入門中，我們將重點放在 `Debit` 方法上。當有款項自帳戶中提領時，就會呼叫 Debit 方法，其中包含下面程式碼：

```csharp
// method under test
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

##  <a name="BKMK_Create_a_unit_test_project"></a> 建立單元測試專案
 **必要條件**：遵循 [Prepare the walkthrough](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)程序中的步驟。

### <a name="to-create-a-unit-test-project"></a>建立單元測試專案

1.  在 [ **檔案** ] 功能表上，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2.  在 [新增專案] 對話方塊中，依序展開 [ **已安裝的**]、[ **Visual C#**]，然後選擇 [ **測試**]。

3.  在範本清單中選擇 [ **單元測試專案**]。

4.  在 [ **名稱** ] 方塊中，輸入 BankTest，然後選擇 [ **確定**]。

     [ **BankTests** ] 專案就會加入至 [ **Bank** ] 方案中。

5.  在 [ **BankTests** ] 專案中，加入 [ **Bank** ] 方案的參考。

     在 [方案總管] 中，選取 [ **BankTests** ] 專案中的 [ **參考** ]，然後從內容功能表選擇 [ **加入參考** ]。

6.  在 [參考管理員] 對話方塊中，展開 [ **方案** ]，然後檢查 [ **Bank** ] 項目。

##  <a name="BKMK_Create_the_test_class"></a> 建立測試類別
 我們需要一個測試類別以驗證 `BankAccount` 類別。 我們可以使用由專案範本所產生的 UnitTest1.cs，不過，我們應該使用更具有描述性的名稱來命名檔案和類別。 我們可以在方案總管中重新命名檔案，就能一個步驟達成目的。

 **重新命名類別檔案**

 在方案總管中，選取 BankTests 專案中的 UnitTest1.cs 檔案。 從內容功能表中，選擇 [ **重新命名**]，然後將檔案重新命名為 BankAccountTests.cs。 在詢問您是否要重新命名專案中程式碼項目 'UnitTest1' 的所有參考的對話方塊上，選擇 [ **是** ]。 此步驟會將類別名稱變更為 `BankAccountTest`。

 BankAccountTests.cs 檔案現在會包含下面程式碼：

```csharp
// unit test code
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

 **將 using 陳述式加入至受測專案**

 我們也可以將 using 陳述式加入至類別，讓我們呼叫受測專案，而不需使用完整名稱。 在類別檔案的頂端，加入：

```csharp
using BankAccountNS;
```

###  <a name="BKMK_Test_class_requirements"></a> 測試類別需求
 測試類別的最低需求如下：

-   在適用於 Managed 程式碼的 Microsoft 單元測試架構中，對於包含要在 [測試總管] 中執行的單元測試方法的任何類別而言， `[TestClass]` 屬性是必要的。

-   您要讓 [測試總管] 執行的每個測試方法都必須具有 `[TestMethod]`屬性。

 單元測試專案中可以含有不具有 `[TestClass]` 屬性的其他類別，而測試類別中也可以含有不具有 `[TestMethod]` 屬性的其他方法。 您可以在測試方法中使用這些其他類別和方法。

##  <a name="BKMK_Create_the_first_test_method"></a> 建立第一個測試方法
 在這個程序中，我們會撰寫單元測試方法以驗證 `Debit` 類別之 `BankAccount` 方法的行為。 該方法如上所列。

 藉由分析受測方法，我們判斷至少有三種需要檢查的行為：

1.  如果付款金額大於餘額，該方法會擲回 <xref:System.ArgumentOutOfRangeException> 。

2.  如果付款金額小於零，也會擲回 `ArgumentOutOfRangeException` 。

3.  如果在 1.) 和 2.) 中的檢查符合要求，該方法會從帳戶餘額減去此金額。

 在第一個測試中，我們會確認有效金額 (低於帳戶餘額但大於零) 會從帳戶提領正確金額。

### <a name="to-create-a-test-method"></a>建立測試方法

1.  將 using `BankAccountNS;` 陳述式加入至 BankAccountTests.cs 檔案。

2.  將下面方法加入至該 `BankAccountTests` 類別：

    ```csharp
    // unit test code
    [TestMethod]
    public void Debit_WithValidAmount_UpdatesBalance()
    {
        // arrange
        double beginningBalance = 11.99;
        double debitAmount = 4.55;
        double expected = 7.44;
        BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

        // act
        account.Debit(debitAmount);

        // assert
        double actual = account.Balance;
        Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
    }
    ```

 此方法相當簡單。 我們設定一開始就有餘額的新 `BankAccount` 物件，然後提領有效的金額。 我們針對 Managed 程式碼 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> 方法使用 Microsoft 單元測試架構，以確認結尾餘額如預期。

###  <a name="BKMK_Test_method_requirements"></a> 測試方法需求
 測試方法必須符合下列需求：

-   此方法必須以 `[TestMethod]` 屬性裝飾。

-   此方法必須傳回 `void`。

-   此方法不能有參數。

##  <a name="BKMK_Build_and_run_the_test"></a> 建置並執行測試

### <a name="to-build-and-run-the-test"></a>建置並執行測試

1.  在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。

     如果沒有發生錯誤，則 [UnitTestExplorer] 視窗隨即出現，並在 [ **未執行的測試** ] 群組中列出 [ **Debit_WithValidAmount_UpdatesBalance** ]。 如果順利完成組建後，[測試總管] 沒有出現，請選擇功能表上的 [ **測試** ]，選擇 [ **視窗**]，然後選擇 [  **測試總管**]。

2.  選擇 [ **全部執行** ] 以執行測試。 當測試在執行時，視窗頂端的狀態列會顯示動畫效果。 在測試回合結束時，如果所有的測試方法都成功，狀態列會變成綠色，如果有任何測試失敗則變成紅色。

3.  在本案例中，測試就失敗了。 測試方法會移至 [ **失敗的測試**] 群組。 。 在 [測試總管] 中選取該方法，以檢視視窗底部的詳細資料。

##  <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> 修正程式碼並重新執行測試
 **分析測試結果**

 測試結果會包含說明失敗的訊息。 如果是 `AreEquals` 方法，訊息會顯示預期 (**預期的\<*XXX*>** 參數) 和實際收到的參數 (**實際的\<*YYY*>** 參數)。 我們預期餘額會低於一開始的餘額，但相反地，它卻增加了提領金額。

 重新對 Debit 程式碼執行檢查後發現了 Bug，單元測試現在已成功了。 提領的金額應該從帳戶餘額減去，但卻被加入至帳戶餘額。

 **修正 Bug**

 若要更正這個錯誤，請將這一行

```csharp
m_balance += amount;
```

 取代為

```csharp
m_balance -= amount;
```

 **重新執行測試**

 在 [測試總管] 中，選擇 [ **全部執行** ] 以重新執行測試。 紅色/綠色狀態列會轉成綠色，且測試會移至 [ **成功的測試** ] 群組。

##  <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> 使用單元測試改善您的程式碼
 這一節會說明分析、單元測試開發和重構的反覆流程，是如何協助您讓生產環境程式碼更加強固而有效。

 **分析問題**

 在建立測試方法以確認 `Debit` 方法可正確扣除有效金額之後，就可以轉而分析原始分析中的其餘情況：

1.  如果付款金額大於餘額，該方法會擲回 `ArgumentOutOfRangeException` 。

2.  如果付款金額小於零，也會擲回 `ArgumentOutOfRangeException` 。

 **建立測試方法**

 首先，我們嘗試建立測試方法來解決這些問題，這似乎有可能成功：

```csharp
//unit test method
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    account.Debit(debitAmount);

    // assert is handled by ExpectedException
}
```

 我們使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> 屬性來判斷提示已擲回正確的例外狀況。 除非擲回 `ArgumentOutOfRangeException` ，否則此屬性會造成測試失敗。 使用正數和負數的 `debitAmount` 值執行測試，然後暫時修改受測方法以在金額小於零時擲回泛型 <xref:System.ApplicationException> ，表示測試正確運作。 若要測試提領金額大於餘額的案例，我們所要做的就是：

1.  建立名為 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`的新測試方法。

2.  將 `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` 中的方法主體複製到新的方法。

3.  將 `debitAmount` 設定為大於餘額的數字。

 **執行測試**

 使用不同的 `debitAmount` 值來執行兩個方法，表示測試可以充分地處理我們其餘的情況。 執行所有三項測試可確認我們原始分析中的所有情況都已正確涵蓋。

 **繼續分析**

 不過，最後兩個測試方法也有些令人困擾。 我們無法確定在哪一個測試執行時，受測程式碼中哪個條件會擲回。 若有某種方式可區分這兩個條件將會很有用。 更深入考慮問題時，就會明白，知道到底是違反了哪個條件將會增加我們對測試的把握。 對於處理受測方法所擲回例外狀況的生產環境機制，這項資訊也很可能很有用。 在方法擲回時產生更多資訊有助於進行所有的相關處理，但是 `ExpectedException` 屬性無法提供這項資訊。

 再次查看受測方法，將會看到兩個條件陳述式都使用接受引數名稱做為參數的 `ArgumentOutOfRangeException` 建構函式：

```csharp
throw new ArgumentOutOfRangeException("amount");
```

 從搜尋 MSDN Library 中，我們發現有會報告更豐富資訊的建構函式存在。 <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` 會包含引數的名稱、引數值和使用者定義的訊息。 我們可以重構受測方法以使用這個建構函式。 更好的是，我們可以使用可公開取得的類型成員來指定錯誤。

 **重構受測程式碼**

 我們先在類別範圍定義錯誤訊息的兩個常數：

```csharp
// class under test
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";
```

 然後修改 `Debit` 方法中的兩個條件陳述式：

```csharp
// method under test
// ...
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
// ...
```

 **重構測試方法**

 在我們的測試方法中，我們先移除 `ExpectedException` 屬性。 在其原本的位置中，我們會攔截擲回的例外狀況，並確認它是在正確的條件陳述式中擲回。 不過，我們現在必須在兩個選項中選擇其一，以驗證我們其餘的情況。 例如在 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` 方法中，可以採取下列其中一個動作：

-   判斷提示例外狀況 ( `ActualValue` 建構函式的第二個參數) 的 `ArgumentOutOfRangeException` 屬性大於一開始的餘額。 這個選項必須要對測試方法的 `ActualValue` 變數測試例外狀況的 `beginningBalance` 屬性，然後也需要驗證 `ActualValue` 大於零。

-   判斷提示訊息 (建構函式的第三個參數) 包含 `DebitAmountExceedsBalanceMessage` 類別中所定義的 `BankAccount` 。

 Microsoft 單元測試架構的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> 方法可讓我們驗證第二個選項，而不需要進行第一個選項所必要的計算。

 再來，我們嘗試修訂 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` ，看起來可能會像這樣：

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
    }
}
```

 **重新測試、重新撰寫和重新分析**

 當我們使用不同的值來重新測試這些測試方法時，發現了下列幾個事實：

1.  如果使用比餘額大的 `debitAmount` 判斷提示而攔截到正確的錯誤，則會通過 `Contains` 判斷提示、忽略例外狀況，而測試方法因此成功。 這是我們所要的行為。

2.  如果我們使用小於 0 的 `debitAmount` ，判斷提示會因為傳回了不正確的錯誤訊息而失敗。 如果我們在測試程式碼路徑下的方法中的另一個點引進了暫時的 `ArgumentOutOfRange` 例外狀況，判斷提示也會失敗。 這樣也不錯。

3.  如果 `debitAmount` 值有效 (也就是說，小於餘額但大於零)，則不會攔截到任何例外狀況，因此也永遠不會攔截判斷提示。 測試方法就會成功。 這樣就不好了，因為我們要的是測試方法在未擲回例外狀況時失敗。

 第三個事實是我們的測試方法有 Bug。 若要嘗試解決這個問題，我們在測試方法的結尾加入了 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> 判斷提示，以處理未擲回例外狀況的情況。

 但是重新測試後顯示，測試現在會因為攔截到正確的例外狀況而失敗。 Catch 陳述式重設了例外狀況，且方法會繼續執行，而在新的判斷提示處失敗。 爲了解決新的問題，我們在 `return` 之後加入 `StringAssert`陳述式。 重新測試後確認我們已修正問題。 我們的 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` 最終版本看起來像下面這樣：

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
        return;
    }
    Assert.Fail("No exception was thrown.");
}
```

在這最後一節中，我們所做的測試程式碼改善工作，產生了更強固且更具資訊性的測試方法。 但更重要的是，額外的分析也會讓我們的受測專案得到更好的程式碼。

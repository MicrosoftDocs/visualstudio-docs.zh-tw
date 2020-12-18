---
title: 警告與錯誤 | Microsoft IntelliTest 開發人員測試工具
description: 本文包含 IntelliTest 的警告和錯誤，分為不同的分類，並提供每個警告和錯誤的描述。
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d72ee803389c692233478d742dadbcf514a3a036
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668062"
---
# <a name="warnings-and-errors"></a>警告和錯誤

## <a name="warnings-and-errors-by-category"></a>警告與錯誤分類

* **界限**
  * [超過 MaxBranches](#maxbranches-exceeded)
  * [超過 MaxConstraintSolverTime](#maxconstraintsolvertime-exceeded)
  * [超過 MaxConditions](#maxconditions-exceeded)
  * [超過 MaxCalls](#maxcalls-exceeded)
  * [超過 MaxStack](#maxstack-exceeded)
  * [超過 MaxRuns](#maxruns-exceeded)
  * [超過 MaxRunsWithoutNewTests](#maxrunswithoutnewtests-exceeded)

* **限制式求解**
  * [無法將實體化方案](#cannot-concretize-solution)

* **網域或執行時間**
  * [需要協助來建立物件](#help-construct)
  * [需要協助以尋找類型](#help-types)
  * [猜測的可用類型](#usable-type-guessed)

* **執行**
  * [探索期間發生非預期的失敗](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **儀錶**
  * [呼叫的未經檢測方法](#uninstrumented-method-called)
  * [呼叫的外部方法](#external-method-called)
  * [呼叫的了無法檢測方法](#uninstrumentable-method-called)
  * [可測試性問題](#testability-issue)
  * [限制](#limitation)

* **解譯器**
  * [觀察到的呼叫不相符](#observed-call-mismatch)
  * [儲存在靜態欄位中的值](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>超過 MaxBranches

IntelliTest 會限制在[輸入產生](input-generation.md)期間探索之任何執行路徑的長度。 當程式進入無限迴圈時，此功能會防止 IntelliTest 變成無回應。

每個已執行和受監視程式碼的條件式和無條件分支都會計入此限制，包括與[參數化單元測試](test-generation.md#parameterized-unit-testing)輸入不相依的分支。

例如，下列程式碼會取用第 100 順位的分支：

```csharp
for (int i=0; i<100; i++) { }
```

您可以編輯 **PexSettingsAttributeBase** 所衍生屬性的 **MaxBranches** 選項，例如 [PexClass](attribute-glossary.md#pexclass) 或 [PexMethod](attribute-glossary.md#pexmethod)。 下例會有效移除此限制：

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

您也可以設定 **TestExcludePathBoundsExceeded** 選項，通知 IntelliTest 一般如何處理這些問題。

在測試程式碼中，您可以使用 [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) 略過迴圈條件產生的條件約束：

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>超過 MaxConstraintSolverTime

IntelliTest 使用[限制式求解](input-generation.md#constraint-solver)來計算新的測試輸入。 限制式求解是相當耗時的程序，因此 IntelliTest 讓您設定界限，尤其是 **MaxConstraintSolverTime**。

對於許多應用程式而言，大幅增加逾時並不會產生較好的涵蓋範圍。 原因是，大部分的逾時是因為條件約束系統沒有解決方案所造成。 不過，IntelliTest 無法在未嘗試所有可能的解決方案下，判斷它是否不一致，就是這項嘗試導致逾時。

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>超過 MaxConditions

IntelliTest 會限制在[輸入產生](input-generation.md)期間探索之任何執行路徑的長度。 當程式進入無限迴圈時，此功能會防止 IntelliTest 變成無回應。

每個與[參數化單元測試](test-generation.md#parameterized-unit-testing)輸入相依的條件式分支都會計入這項限制。

例如，下列程式碼中的每個路徑都會使用 **n + 1** 個條件：

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++)
    { ... }
}
```

您可以編輯 **PexSettingsAttributeBase** 所衍生屬性的 **MaxConditions** 選項，例如 [PexClass](attribute-glossary.md#pexclass) 或 [PexMethod](attribute-glossary.md#pexmethod)。 例如：

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

您也可以設定 **TestExcludePathBoundsExceeded** 選項，通知 IntelliTest 一般如何處理這些問題。

您可以使用 [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) 略過迴圈條件產生的條件約束：

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>超過 MaxCalls

IntelliTest 會限制在[輸入產生](input-generation.md)期間探索之任何執行路徑的長度。 當程式進入無限迴圈時，此功能會防止 IntelliTest 變成無回應。

已執行和受監視程式碼的每個呼叫 (直接、間接、虛擬或跳躍) 都會計入這項限制。

您可以編輯 **PexSettingsAttributeBase** 所衍生屬性的 **MaxCalls** 選項，例如 [PexClass](attribute-glossary.md#pexclass) 或 [PexMethod](attribute-glossary.md#pexmethod)。 下例會有效移除此限制：

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

您也可以設定 **TestExcludePathBoundsExceeded** 選項，通知 IntelliTest 一般如何處理這些問題。

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>超過 MaxStack

IntelliTest 會限制在[輸入產生](input-generation.md)期間探索之任何執行路徑的呼叫堆疊大小。 這項功能可防止 IntelliTest 在發生堆疊溢位時終止。

您可以編輯 **PexSettingsAttributeBase** 所衍生屬性的 **MaxStack** 選項，例如 [PexClass](attribute-glossary.md#pexclass) 或 [PexMethod](attribute-glossary.md#pexmethod)。 下例會有效移除此繫結 (不建議)：

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

您也可以設定 **TestExcludePathBoundsExceeded** 選項，通知 IntelliTest 一般如何處理這些問題。

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>超過 MaxRuns

IntelliTest 會限制在[輸入產生](input-generation.md)期間探索的執行路徑數量。 這項功能可確保 IntelliTest 在程式迴圈或遞迴時終止。

也可能並非如此，而是每次 IntelliTest 以特定輸入資料執行參數化測試時，就發出新的測試案例。 如需詳細資訊，請參閱 [TestEmissionFilter](exploration-bounds.md#testemissionfilter)。

您可以編輯 **PexSettingsAttributeBase** 所衍生屬性的 **MaxRuns** 選項，例如 [PexClass](attribute-glossary.md#pexclass) 或 [PexMethod](attribute-glossary.md#pexmethod)。 下例會有效移除此繫結 (不建議)：

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>超過 MaxRunsWithoutNewTests

IntelliTest 會限制在[輸入產生](input-generation.md)期間探索的執行路徑數量。 這項功能可確保 IntelliTest 在程式迴圈或遞迴時終止。

也可能並非如此，而是每次 IntelliTest 以特定輸入資料執行參數化測試時，就發出新的測試案例。 如需詳細資訊，請參閱 [TestEmissionFilter](exploration-bounds.md#testemissionfilter)。

雖然 IntelliTest 經常在一開始就找到許多有趣的測試輸入，但一段時間之後，它可能不會再發出更多的測試。 此選項掌控 IntelliTest 嘗試尋找其他相關測試輸入的時間長短。

您可以編輯 **PexSettingsAttributeBase** 所衍生屬性的 **MaxRunsWithoutNewTests** 選項，例如 [PexClass](attribute-glossary.md#pexclass) 或 [PexMethod](attribute-glossary.md#pexmethod)。 下例會有效移除此繫結 (不建議)：

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>無法將解決方案實體化

此錯誤通常是以前錯誤的結果。 IntelliTest 使用[限制式求解](input-generation.md#constraint-solver)決定新的測試輸入。 有時候，[限制式求解](input-generation.md#constraint-solver)提議的測試輸入無效。 發生的時機為：

* 未知的特定條件約束
* 如果值是以使用者定義的方式建立，就會導致使用者程式碼發生錯誤
* 某些涉及的類型具有不受 IntelliTest 控制的初始化邏輯 (例如 COM 類別)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>需要協助以建構物件

IntelliTest 會[產生測試輸入](input-generation.md)，而某些輸入可能是有欄位的物件。
在這裡，IntelliTest 嘗試產生有私用欄位的類別執行個體，並假設當此私用欄位具有特定值時，會發生有趣的程式行為。

不過，雖然反映很可能出現這種情況，但 IntelliTest 不會製造有任意欄位值的物件。
反倒是在這些情況下，它會依賴使用者提供的相關提示，使用類別的公用方法來建立物件，並將它帶入其私用欄位有所需值的狀態。

若要了解如何協助 IntelliTest 建構有趣的物件，請參閱[現有類別具現化](input-generation.md#existing-classes)。

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>需要協助以尋找類型

IntelliTest 會為所有 .NET 類型[產生測試輸入](input-generation.md)。 在這裡，IntelliTest 會嘗試建立衍生自抽象類別的執行個體，或實作抽象的介面，IntelliTest 不知道能滿足這些條件約束的任何類型。

您可以指向一或多個符合條件約束的類型，協助 IntelliTest。 通常，下列屬性之一會提供幫助：

* **PexUseTypeAttribute**，指向特定的類型。

  例如，如果 IntelliTest 回報「不知道可指派給 **System.Collections.IDictionary** 的任何類型」，您可以將下列的 **PexUseTypeAttribute** 附加到測試 (或裝置類別) 來幫助它：

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **組件層級屬性**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>猜到可使用的類型

IntelliTest 會為所有 .NET 類型[產生測試輸入](input-generation.md)。 當類型為抽象或介面時，IntelliTest 必須選擇該類型的特定實作。 它需要知道有哪些類型，才能進行這種選擇。

顯示此警告時，表示 IntelliTest 已查看部分參考的元件並找到實作為型別，但是不確定是否應該使用該型別，或其他地方是否有更適當的型別可供使用。 IntelliTest 只要選擇有希望的類型即可。

為避免此警告，您可以接受 IntelliTest 選擇的類型，或新增對應的 [PexUseType](attribute-glossary.md#pexusetype)，協助 IntelliTest 使用其他類型。

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>在探索期間發生未預期的失敗

探索測試時攔截到未預期的例外狀況。

請[回報為 Bug](#report-bug)。

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

使用者程式碼中發生例外狀況。 檢查堆疊追蹤，並移除程式碼中的 Bug。

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>呼叫了未經檢測的方法

IntelliTest 透過監視程式執行[產生測試輸入](input-generation.md)。 請務必正確檢測相關程式碼，以利 IntelliTest 監視其行為。

當已檢測的程式碼呼叫另一個未經檢測組件中的方法時，就會顯示此警告。
如果您希望 IntelliTest 探索兩者的互動，您也必須檢測另一個組件 (或其部分)。

<a name="external-method-called"></a>
## <a name="external-method-called"></a>呼叫了外部方法

IntelliTest 透過監視 .NET 應用程式的執行，[產生測試輸入](input-generation.md)。
IntelliTest 無法為非以 .NET 語言撰寫的程式碼產生有意義的測試輸入。

當已檢測的程式碼呼叫 IntelliTest 無法分析的未受管理原生方法時，就會顯示此警告。 如果您希望 IntelliTest 探索兩者的互動，您必須模擬未受管理的方法。

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>呼叫了無法檢測的方法

IntelliTest 透過監視 .NET 應用程式的執行，[產生測試輸入](input-generation.md)。 不過因為技術原因，IntelliTest 無法監視某些方法 。 例如，IntelliTest 無法監視靜態的建構函式。

當已檢測的程式碼呼叫 IntelliTest 無法監視的方法時，就會顯示此警告。

<a name="testability-issue"></a>
## <a name="testability-issue"></a>可測試性問題

IntelliTest 透過監視程式執行[產生測試輸入](input-generation.md)。 當程式具決定性，且相關的行為受測試輸入控制時，它只會產生相關的測試輸入。

這個警告出現的原因是，在執行測試案例期間，所呼叫的方法行為不具決定性，或與環境產生互動。 範例為 **System.Random** 和 **System.IO.File** 的方法。 如果您想要 IntelliTest 建立有意義的測試輸入，您必須模擬 IntelliTest 標記為可測試性問題的方法。

<a name="limitation"></a>
## <a name="limitation"></a>限制

IntelliTest 使用[限制式求解](input-generation.md#constraint-solver)[產生測試輸入](input-generation.md)。
不過，有些作業超出[限制式求解](input-generation.md#constraint-solver)的範圍。
目前包括：

* 大部分的浮點運算 (浮點數僅支援某些線性算術運算)
* 浮點數和整數之間的轉換
* **System.Decimal** 類型上的所有作業

當執行過的程式碼執行作業，或呼叫 IntelliTest 無法解譯的方法時，就會顯示此警告。

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>觀察到呼叫不相符

IntelliTest 透過監視程式執行[產生測試輸入](input-generation.md)。 不過，IntelliTest 可能無法監視所有的指示。 例如，它無法監視原生程式碼，且無法監視未經檢測的程式碼。

當 IntelliTest 無法監視程式碼時，就無法產生與該程式碼相關的測試輸入。
通常，在對方法的呼叫傳回之前，IntelliTest 並不知道自己無法監視該方法。 不過，這個警告的原因是：

* IntelliTest 因監視了某些程式碼而起始了對未經檢測方法的呼叫
* 未經檢測的方法呼叫了已檢測的方法
* IntelliTest 會監視已呼叫的已檢測方法

IntelliTest 不知道未經檢測的中繼方法做了什麼，因此它可能無法產生與巢狀已檢測呼叫相關的測試輸入。

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>儲存在靜態欄位的值

唯有當單元測試具決定性時，IntelliTest 才能有系統地判斷[相關測試輸入](input-generation.md)；換言之，它對相同的測試輸入一律有相同的行為。 具體而言，就是測試應該讓系統保持在能夠重新執行該測試的狀態。
在理想的情況下，單元測試不應該變更任何全域狀態，但應該要模擬所有全域互動。

這則警告表示靜態欄位已變更，這可能會使測試出現不具決定性的行為。

在某些情況下，變更靜態欄位是可以接受的：

* 當測試輸入造成安裝程式或清除程式碼復原變更時
* 當欄位只起始一次，但值之後不會變更時。

<a name="report-bug"></a>

## <a name="got-feedback"></a>有人給您意見嗎？

在[開發人員社群](https://aka.ms/feedback/suggest?space=8)上張貼您的意見與功能建議。

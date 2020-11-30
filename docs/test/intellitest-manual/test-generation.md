---
title: 測試產生 | Microsoft IntelliTest 開發人員測試工具
description: 瞭解 IntelliTest 如何從您的執行方法產生測試案例，然後產生方法的輸入，並檢查資料的判斷提示。
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 790146e3014765224f22bd247732c7ac3f062269
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329441"
---
# <a name="test-generation"></a>測試產生

在傳統的單元測試中，測試由多個項目組成：

* [方法呼叫的序列](test-generation.md#test-generators)
* 所呼叫方法的引數，這些引數為[測試輸入](input-generation.md)
* 指出一組[判斷提示](#assumptions-and-assertions)，來驗證預期的受測應用程式行為

以下為範例測試結構：

```csharp
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

IntelliTest 通常會自動判斷多項一般[參數化單元測試](#parameterized-unit-testing)的相關引數值，這會提供一系列的方法呼叫和判斷提示。

<a name="test-generators"></a>
## <a name="test-generators"></a>測試產生器

IntelliTest 產生測試案例的方法是，在要執行的測試下選取一系列的實作方法，然後產生方法的輸入，同時檢查衍生資料的判斷提示。

[參數化單元測試](#parameterized-unit-testing)會直接指出其主體中的一系列方法呼叫。

當 IntelliTest 需要建構物件時，對建構函式和 Factory 方法的呼叫會依需要自動新增至序列。

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>參數化單元測試

*參數化單元測試* (PUT) 是採用參數的測試。 不同於傳統的單元測試，它們通常是 Closed 方法，PUT 會採取任何一組參數。 就這麼簡單嗎？ 是 - IntelliTest 會在這裡嘗試[產生 (最小的) 輸入集](input-generation.md)，[完全涵蓋](input-generation.md#dynamic-code-coverage)測試接觸到的程式碼。

PUT 是使用 [PexMethod](attribute-glossary.md#pexmethod) 自訂屬性以類似 MSTest (或 NUnit、xUnit) 的方式定義。 PUT 是標記為 [PexClass](attribute-glossary.md#pexclass)，以邏輯方式分組為類別的執行個體方法。 下列範例顯示的簡單 PUT，儲存在 **MyPexTest** 類別：

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

其中 **ReplaceFirstChar** 方法會取代字串的第一個字元：

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

從這項測試中，IntelliTest 會自動為涵蓋許多受測程式碼執行路徑的 PUT [產生輸入](input-generation.md)。 每個涵蓋不同執行路徑的輸入，都會被「序列化」為單元測試：

```csharp
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>一般參數化單元測試

參數化單元測試可以是泛型方法。 在此情況下，使用者必須使用 [PexGenericArguments](attribute-glossary.md#pexgenericarguments) 來指定具現化方法所用的類型。

```csharp
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>允許例外狀況

IntelliTest 會提供許多驗證屬性，幫助將例外狀況分級為預期的例外狀況和未預期的例外狀況。

預期的例外狀況會產生有 **ExpectedException(typeof(*xxx*))** 等適當註釋的負面測試案例，而未預期的例外狀況則會產生失敗的測試案例。

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

驗證程式如下：

* [PexAllowedException](attribute-glossary.md#pexallowedexception)：允許來自任何地方的特定例外狀況類型
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)：允許來自指定組件的特定例外狀況類型
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)：允許來自指定類型的特定例外狀況類型
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)：允許來自測試下類型的特定例外狀況類型

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>測試內部類型

IntelliTest 只要看得見內部類型，就可以「測試」它們。 為使 Intellitest 看見這些類型，Visual Studio IntelliTest 精靈會將下列屬性新增至您的產品或測試專案：

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>假設和判斷提示

使用者可以使用假設和判斷提示來表示其測試的[先決條件](#precondition) (假設) 和[後置條件](#postcondition) (判斷提示)。 當 IntelliTest 產生一組參數值並「探索」程式碼時，它可能會違反測試的假設。 發生這種情況時，它不會產生對該路徑的測試，但會以無訊息模式忽略它。

判斷提示是一般單元測試架構中眾所周知的概念，因此 IntelliTest 已經「了解」每個受支援測試架構所提供的內建 **Assert** 類別。 不過，大部分的架構不提供 **Assume** 類別。 在此情況下，IntelliTest 提供 [PexAssume](static-helper-classes.md#pexassume) 類別。 如果您不想要使用現成的測試架構，IntelliTest 還有 [PexAssert](static-helper-classes.md#pexassert) 類別。

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

尤其是，非 null 假設可以編碼為自訂屬性：

```csharp
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>先決條件

方法的前置條件會以方法能夠成功的條件表示。

通常，強制執行前置條件的方法是檢查參數以及物件狀態，並在違規時擲回 **ArgumentException** 或 **InvalidOperationException**。

在 IntelliTest 中，[參數化單元測試](#parameterized-unit-testing)的前置條件會使用 [PexAssume](static-helper-classes.md#pexassume) 表示。

<a name="postcondition"></a>
## <a name="postcondition"></a>後置條件

方法的後置條件會以方法執行期間和之後應該保留的條件表示，假設其前置條件一開始有效。

通常，強制執行後置條件的方法是呼叫 **Assert** 方法。

使用 IntelliTest，[參數化單元測試](#parameterized-unit-testing)的後置條件會使用 [PexAssert](static-helper-classes.md#pexassert) 表示。

<a name="test-failures"></a>
## <a name="test-failures"></a>測試失敗
產生的測試案例會在何時失敗？

1. 如果它不是在[設定的路徑界限](exploration-bounds.md)內終止，就視為失敗，除非設定 [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) 選項。

1. 如果測試擲回 **PexAssumeFailedException**，即成功。 不過，除非 [TestEmissionFilter](exploration-bounds.md#testemissionfilter) 設為 [全部]，否則通常會被篩選掉。

1. 如果測試違反[判斷提示](#assumptions-and-assertions)，例如，擲回單元測試架構的判斷提示違規例外狀況，即失敗。

如果上述程序均無定論，測試只有在不擲回例外狀況時才算成功。 判斷提示違規視同例外狀況處理。

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>設定和卸除

IntelliTest 是測試架構整合的一部分，支援偵測與執行設定和卸除方法。

**範例**

```csharp
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}
```

<a name="further-reading"></a>
## <a name="further-reading"></a>進一步閱讀

* [程式碼繫結測試](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [一項掌控全場的測試](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>有人給您意見嗎？

在[開發人員社群](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)上張貼您的意見與功能建議。

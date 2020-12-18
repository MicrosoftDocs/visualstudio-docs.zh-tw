---
title: 靜態協助程式類別 | Microsoft IntelliTest 開發人員測試工具
description: 瞭解 IntelliTest 為撰寫參數化單元測試所提供的靜態 helper 類別。
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d4b5ad68186142ae61a266d688a0430b0a623605
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668725"
---
# <a name="static-helper-classes"></a>靜態協助程式類別

IntelliTest 提供一組靜態的協助程式類別，可以在撰寫[參數化單元測試](test-generation.md#parameterized-unit-testing)時使用：

* [PexAssume](#pexassume)：用來在輸入上定義假設，對於篩選不想要的輸入很有幫助。
* [PexAssert](#pexassert)：當您的測試架構不提供時，可使用的簡易判斷提示類別。
* [PexChoose](#pexchoose)：IntelliTest 管理的其他測試輸入資料流
* [PexObserve](#pexobserve)：記錄具體值，並選擇性地在產生的程式碼中驗證它們

某些類別可讓您與 IntelliTest 推理引擎在低層級進行互動：

* [PexSymbolicValue](#pexsymbolicvalue)：檢查或修改變數上符號條件約束的公用程式

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

[參數化單元測試](test-generation.md#parameterized-unit-testing)中表達假設用的靜態類別，例如[先決條件](test-generation.md#precondition)。 此類別的方法可以用來篩選掉不要的測試輸入。

如果某些測試輸入中不含假設條件，就會擲回 **PexAssumeFailedException**。 這會導致以無訊息模式忽略測試。

**範例**

下列參數化測試不會考慮 **j=0**：

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**備註**

上述程式碼幾乎等同於：

```csharp
     if (j==0)
          return;
```

不同之處是失敗的 **PexAssume** 導致沒有測試案例。 如果是 **if** 陳述式，IntelliTest 會另外產生測試案例，以涵蓋 **if** 陳述式的 **then** 分支。

**PexAssume** 也包含如字串、陣列和集合上的假設的特殊化巢狀類別。

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

[參數化單元測試](test-generation.md#parameterized-unit-testing)中表達判斷提示用的靜態類別，例如[後置條件](test-generation.md#postcondition)。

如果某些測試輸入中不含判斷提示條件，就會擲回 **PexAssertFailedException**，造成測試失敗。

**範例**

整數的絕對值是正數的判斷提示如下：

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

為測試提供輔助輸入值的靜態類別，可用以實作[參數化模擬](input-generation.md#parameterized-mocks)。

**PexChoose** 類別無法協助決定特定輸入值的測試是通過還是失敗。 **PexChoose** 只提供輸入值，也稱為「選項」。 使用者仍然需要限制輸入值，以及撰寫判斷提示來定義測試何時通過或失敗。

**作業模式**

**PexChoose** 類別可在兩種模式下操作：

* 當 IntelliTest 在[輸入產生](input-generation.md)期間執行測試和受測程式碼的符號分析時，選擇器會傳回任意值，而 IntelliTest 會追蹤每個值在測試和受測程式碼中的使用方式。 IntelliTest 會產生相關的值，在測試和受測程式碼中觸發不同的執行路徑。

* 針對特定測試案例所產生的程式碼，會以特定方式設定選擇提供者，以便重新執行此類測試案例時會做出特定的選擇，觸發特定的執行路徑。

**使用方式**

* 簡單呼叫 **PexChoose.Value** 以產生新值：

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

記錄具名值的靜態類別。

當 IntelliTest 探索程式碼時，會使用其格式化的字串表示法利用 **PexObserve** 記錄計算的值。 值與唯一的名稱建立關聯。

```csharp
PexObserve.Value<string>("result", result);
```

**範例**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}

// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a);
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

靜態類別，可用來略過參數上的條件約束，以及列印與值建立關聯的符號資訊。

**使用方式**

在執行期間，IntelliTest 一般會嘗試涵蓋程式碼的所有執行路徑。 不過，它不應該探索所有可能的案例，特別是在運算假設和判斷提示條件時。

**範例**

本例會示範 **PexAssume.Arrays.ElementsAreNotNull** 方法的實作。
在此方法中，您會忽略陣列值的長度條件約束，以免 IntelliTest 嘗試產生不同的陣列大小。 只在這裡忽略條件約束。 如果受測程式碼對不同的陣列長度有不同的行為，則 IntelliTest 無法從受測程式碼的條件約束產生不同大小的陣列。

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>有人給您意見嗎？

在[開發人員社群](https://aka.ms/feedback/suggest?space=8)上張貼您的意見與功能建議。

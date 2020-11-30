---
title: 泛型方法的單元測試
description: 瞭解如何使用這項資訊來產生泛型方法的單元測試，以及如何建立泛型方法的單元測試範例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 88ef5d64d2513bb97bdd5589e04669629dfdf6ae
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330039"
---
# <a name="unit-tests-for-generic-methods"></a>泛型方法的單元測試

您可以產生泛型方法的單元測試，就像您為其他方法所進行的測試一樣。 下列章節提供建立泛型方法之單元測試的相關資訊與範例。

## <a name="type-arguments-and-type-constraints"></a>型別引數和類型條件約束

在 Visual Studio 產生泛型類別 (例如 `MyList<T>`) 的單元測試時，會產生兩個方法：一個泛型協助程式方法和一個測試方法。 如果 `MyList<T>` 具有一個或多個類型條件約束，則此類型引數必須滿足所有類型條件約束。 為了確定待測泛型程式碼是否如預期般適用於允許的所有輸入，測試方法會使用您想測試的所有條件約束來呼叫泛型協助程式方法。

## <a name="examples"></a>範例
下列範例說明泛型的單元測試：

- [編輯產生的測試程式碼](#EditingGeneratedTestCode)。 本範例包含「產生的測試程式碼」和「編輯的測試程式碼」兩節。 其示範如何將由泛型方法產生之未經處理的測試程式碼，編輯成有用的測試方法。

- [使用類型條件約束](#TypeConstraintNotSatisfied)。 本範例示範的單元測試適用於使用類型條件約束的泛型方法。 本範例中並未滿足類型條件約束。

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a> 範例 1：編輯產生的測試程式碼
此區段中的測試程式碼測試的是名稱為 `SizeOfLinkedList()` 的待測程式碼方法。 這個方法會傳回指定連結清單中節點數目的整數。

〈產生的測試程式碼〉一節中的第一個程式碼範例顯示 Visual Studio Enterprise 所產生之未編輯的測試程式碼。 〈編輯的測試程式碼〉一節中的第二個程式碼範例，則顯示如何針對 `int` 和 `char` 兩種不同的資料類型來測試 SizeOfLinkedList 方法的運作狀況。

此程式碼說明兩種方法：

- 測試協助程式方法，`SizeOfLinkedListTestHelper<T>()`。 根據預設，測試協助程式方法的名稱中包含 "TestHelper" 字串。

- 測試方法，`SizeOfLinkedListTest()`。 每個測試方法都會以 TestMethod 屬性標示。

#### <a name="generated-test-code"></a>產生的測試程式碼
下列測試程式碼是從 `SizeOfLinkedList()` 方法產生。 因為這項產生的測試尚未經過編輯，所以您必須修改它才能正確測試 SizeOfLinkedList 方法。

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T); // TODO: Initialize to an appropriate value
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value
    int expected = 0; // TODO: Initialize to an appropriate value
    int actual;
    actual = target.SizeOfLinkedList();
    Assert.AreEqual(expected, actual);
    Assert.Inconclusive("Verify the correctness of this test method.");
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
   SizeOfLinkedListTestHelper<GenericParameterHelper>();
}
```

在前面的程式碼中，泛型類型參數是 `GenericParameterHelper`。 雖然您可以編輯此參數來提供特定的資料類型 (如下面的範例所示)，但是您也可以直接執行測試，而不用編輯這個陳述式。

#### <a name="edited-test-code"></a>編輯的測試程式碼
在下列程式碼中，測試方法和測試協助程式方法都已經過編輯，使其能夠成功測試受測試程式碼方法 `SizeOfLinkedList()`。

##### <a name="test-helper-method"></a>測試協助程式方法
測試協助程式方法會執行下列步驟，而這些步驟與程式碼中標記為步驟 1 到步驟 5 的各行相對應。

1. 建立泛型連結清單。

2. 將四個節點附加到此連結清單。 這些節點中有資料類型未知的內容。

3. 將預期的連結清單大小指派給變數 `expected`。 

4. 計算此連結清單的實際大小，並將它指派給變數 `actual`。

5. 比較 Assert 陳述式中的 `actual` 與 `expected`。 如果 actual 不等於 expected，測試便會失敗。

##### <a name="test-method"></a>測試方法
測試方法會編譯到您在執行名為 SizeOfLinkedListTest 之測試時所呼叫的程式碼中。 它會執行下列步驟，而這些步驟與程式碼中標記為步驟 6 和步驟 7 的各行相對應。

1. 在呼叫測試協助程式方法時指定 `<int>`，以驗證此測試是否適用於 `integer` 變數。

2. 在呼叫測試協助程式方法時指定 `<char>`，以驗證此測試是否適用於 `char` 變數。

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T);
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1
    for (int i = 0; i < 4; i++) // step 2
    {
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);
        target.Append(newNode);
    }
    int expected = 5; // step 3
    int actual;
    actual = target.SizeOfLinkedList(); // step 4
    Assert.AreEqual(expected, actual); // step 5
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> 每次 SizeOfLinkedListTest 測試執行時，都會呼叫其 TestHelper 方法兩次。 Assert 陳述式的計算結果每次都必須為 true，測試才會通過。 如果測試失敗，可能無法確定造成失敗的是指定 `<int>` 的呼叫，還是指定 `<char>` 的呼叫。 如果要找出答案，您可以檢查呼叫堆疊，也可以在測試方法中設定中斷點，然後在執行測試時同時進行偵錯。 如需詳細資訊，請參閱[如何：在 ASP.NET 方案中執行測試時偵錯](/previous-versions/ms243172(v=vs.140))。

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a> 範例 2：使用類型條件約束
本範例示範泛型方法的單元測試，而該泛型方法使用了未能滿足的類型條件約束。 第一個區段顯示來自待測程式碼專案的程式碼。 其中的類型條件約束以反白顯示。

第二個區段顯示來自測試專案的程式碼。

#### <a name="code-under-test-project"></a>待測程式碼專案

```csharp
using System;
using System.Linq;
using System.Collections.Generic;
using System.Text;

namespace ClassLibrary2
{
    public class Employee
    {
        public Employee(string s, int i)
        {
        }
    }

    public class GenericList<T> where T : Employee
    {
        private class Node
        {
            private T data;
            public T Data
            {
                get { return data; }
                set { data = value; }
            }
        }
    }
}
```

#### <a name="test-project"></a>測試專案

如同所有新產生的單元測試一樣，您必須將非結果不明的 Assert 陳述式加入此單元測試，使它傳回有用的結果。 您不會將它們加入標記為 TestMethod 屬性的方法，而會加入 "TestHelper" 方法 (在此測試中的名稱為 `DataTestHelper<T>()`)。

在這個範例中，泛型型別參數 `T` 具有條件約束 `where T : Employee`。 測試方法並未滿足此條件約束。 因此，`DataTest()` 方法包含 Assert 陳述式，以提醒您必須提供對 `T` 所設的類型條件約束。 此 Assert 陳述式的訊息如下：`("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

換句話說，當您從測試方法 `DataTest()` 呼叫方法 `DataTestHelper<T>()` 時，您必須傳遞型別為 `Employee` 的參數，或衍生自 `Employee` 的類別。

```csharp
using ClassLibrary2;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestProject1
{
    [TestClass()]
    public class GenericList_NodeTest
    {

        public void DataTestHelper<T>()
            where T : Employee
        {
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value
            T expected = default(T); // TODO: Initialize to an appropriate value
            T actual;
            target.Data = expected;
            actual = target.Data;
            Assert.AreEqual(expected, actual);
            Assert.Inconclusive("Verify the correctness of this test method.");
        }

        [TestMethod()]
        public void DataTest()
        {
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +
            "Please call DataTestHelper<T>() with appropriate type parameters.");
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)
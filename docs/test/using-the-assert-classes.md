---
title: 在 Visual Studio 中使用 Assert 類別進行單元測試
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2d56477822fa2d965902d9442d47e2c3ab24d656
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="use-the-assert-classes"></a>使用 Assert 類別

使用 UnitTestingFramework 命名空間的 Assert 類別來驗證特定功能。 單元測試方法會執行開發程式碼中方法的程式碼，但是只有在加入 Assert 陳述式時，才會報告程式碼行為的正確性。

## <a name="kinds-of-asserts"></a>Assert 的類型

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 命名空間提供數種 Assert 類別：

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

 在測試方法中，您可以呼叫任何數目的 Assert 類別方法，例如 Assert.AreEqual()。 Assert 類別有許多方法可供選擇，且許多這些方法都有數個多載。

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

 使用 CollectionAssert 類別比較物件集合，以及確認一或多個集合的狀態。

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

 使用 StringAssert 類別來比較字串。 這個類別包含各種不同的有用方法，例如 StringAssert.Contains、StringAssert.Matches 和 StringAssert.StartsWith。

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

 每當測試失敗時，便會擲回 AssertFailedException 例外狀況。 測試在逾時、擲回未預期的例外狀況，或包含產生「失敗」結果的 Assert 陳述式時，便會失敗。

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

 每當測試所產生的結果不明，便會擲回 AssertInconclusiveException。 一般而言，您會將 Assert.Inconclusive 陳述式加入至您仍在處理的測試，以表示它尚未做好執行準備。

> [!NOTE]
> 另一種方法就是將尚未準備好要執行的測試以 Ignore 屬性標示。 不過，此方法的缺點在於您無法輕鬆地就您尚未實作的測試數量產生報告。

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 如果您撰寫新的 Assert 例外狀況類別，讓該類別繼承基底類別 UnitTestAssertException，可使它更輕鬆地將例外狀況識別為判斷提示失敗，而不是從您的測試或實際執行程式碼擲回的例外狀況。

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 當您想要測試方法確認您預期由開發程式碼中之方法擲回的例外狀況，確實是由該方法擲回時，請使用 ExpectedExceptionAttribute 屬性裝飾測試方法。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [對程式碼進行單元測試](../test/unit-test-your-code.md)

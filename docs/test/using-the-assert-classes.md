---
title: MSTest Assert 類別和方法
description: 瞭解如何在應用程式程式碼的單元測試期間，使用 Assert 語句測試程式程式碼為的正確性。
ms.custom: SEO-VS-2020
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 1f064ee1ca41aab19e19fa6006d983a76ed006d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946198"
---
# <a name="use-assert-classes-for-unit-testing"></a>使用 Assert 類別進行單元測試

使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 命名空間的 Assert 類別來驗證特定功能。 單元測試方法會執行應用程式程式碼中方法的程式碼，但是只有在包含 Assert 陳述式時，才會報告程式碼行為的正確性。

## <a name="kinds-of-asserts"></a>Assert 的類型

<xref:Microsoft.VisualStudio.TestTools.UnitTesting> 命名空間提供數種 Assert 類別。

在測試方法中，您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> 類別的任何方法，例如 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>。 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別有許多方法可供選擇，且這些方法很多都有數個多載。

### <a name="compare-strings-and-collections"></a>比較字串與集合

使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> 類別來比較物件集合，或確認集合的狀態。

使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> 類別來比較並檢查字串。 這個類別包含各種實用的方法，例如 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType>，以及 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>。

### <a name="exceptions"></a>例外狀況

每當測試失敗時，便會擲回 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> 例外狀況。 測試在逾時、擲回未預期的例外狀況，或包含產生 **失敗** 結果的 Assert 陳述式時，便會失敗。

每當測試所產生的結果 **不明**，便會擲回 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>。 一般而言，您會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> 陳述式新增至您仍在處理的測試，以表示它尚未做好執行準備。

> [!NOTE]
> 另一種方法就是將尚未準備好要執行的測試以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> 屬性標示。 不過，此方法的缺點在於您無法輕鬆地就您未實作的測試數量產生報告。

如果您撰寫新的 Assert 例外狀況類別，繼承基底類別 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>可使它更輕鬆地將例外狀況識別為判斷提示失敗，而不是從您的測試或生產環境程式碼擲回未預期的例外狀況。

若要確認您預期由應用程式程式碼中之方法擲回的例外狀況，確實是由該方法擲回時，請使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 方法。

## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)

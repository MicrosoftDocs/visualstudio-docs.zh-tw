---
title: 使用 Assert 類別 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6a4f7f1631ac4bfc651f5df347db010cf47a656
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657142"
---
# <a name="using-the-assert-classes"></a>使用 Assert 類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>[針對現有的程式碼建立和執行單元測試](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)

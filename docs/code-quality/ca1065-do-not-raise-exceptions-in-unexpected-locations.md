---
title: CA1065：不要在非預期的位置中引發例外狀況
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b338b37d62f3612dd5eb6d575b6ef0d57202c1f8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900659"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065：不要在非預期的位置中引發例外狀況

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因

不可擲回例外狀況 (Exception) 的方法卻擲回例外狀況。

## <a name="rule-description"></a>規則描述

不會擲回例外狀況的方法可分類如下：

- 屬性 Get 方法

- 事件存取子方法

- Equals 方法

- GetHashCode 方法

- ToString 方法

- 靜態建構函式

- 完成項

- Dispose 方法

- 等號比較運算子

- 隱含轉型運算子

下列章節會討論這些方法的型別。

### <a name="property-get-methods"></a>屬性 Get 方法

屬性基本上是智慧型欄位。 因此，它們應該像是盡量欄位的行為。 欄位不會擲回例外狀況，所以屬性。 如果您有會擲回例外狀況的屬性，請考慮將它的方法。

從屬性 get 方法，可能會擲回下列例外狀況：

- <xref:System.InvalidOperationException?displayProperty=fullName> 和所有衍生項目 (包括<xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> 和所有衍生項目

- <xref:System.ArgumentException?displayProperty=fullName> （只能從索引的 get）

- <xref:System.Collections.Generic.KeyNotFoundException> （只能從索引的 get）

### <a name="event-accessor-methods"></a>事件存取子方法

事件存取子都應該是簡單的操作，不擲回例外狀況。 當您嘗試新增或移除事件處理常式時，事件不應該擲回例外狀況。

從事件存取子，可能會擲回下列例外狀況：

- <xref:System.InvalidOperationException?displayProperty=fullName> 和所有衍生項目 (包括<xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> 和所有衍生項目

- <xref:System.ArgumentException> 蠻

### <a name="equals-methods"></a>Equals 方法

下列**等於**方法不可擲回例外狀況：

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

**等於**方法應傳回`true`或`false`而不是擲回例外狀況。 比方說，如果 Equals 傳遞兩個不相符的類型應該只傳回`false`而不是擲回<xref:System.ArgumentException>。

### <a name="gethashcode-methods"></a>GetHashCode 方法

下列**GetHashCode**方法通常不應該擲回例外狀況：

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**GetHashCode**應該一律會傳回的值。 否則，您可能會失去雜湊表中的項目。

舊版**GetHashCode**擲回引數可的採用<xref:System.ArgumentException>。 不過， **Object.GetHashCode**應該絕不會擲回例外狀況。

### <a name="tostring-methods"></a>ToString 方法

偵錯工具會使用<xref:System.Object.ToString%2A?displayProperty=fullName>可顯示物件的相關資訊，以字串格式。 因此， **ToString**不應該變更物件的狀態，以及它不應該擲回例外狀況。

### <a name="static-constructors"></a>靜態建構函式

擲回例外狀況，從靜態建構函式會導致無法在目前的應用程式定義域中的類型。 您應針對擲回例外狀況從靜態建構函式有充分的理由 （例如安全性問題）。

### <a name="finalizers"></a>完成項

從完成項擲回例外狀況會導致 CLR 執行失敗，其處理序終止。 因此，在完成項中擲回例外狀況應該避免。

### <a name="dispose-methods"></a>Dispose 方法

A<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法不可擲回例外狀況。 處置通常稱為一部分中的清除邏輯`finally`子句。 因此，明確處置從擲回例外狀況會強制使用者在新增例外狀況處理內`finally`子句。

**Dispose （false)** 程式碼路徑應該絕不會擲回例外狀況，因為在 Dispose 幾乎一律會呼叫來自完成項。

### <a name="equality-operators--"></a>等號比較運算子 (= =、 ！ =)

像 Equals 方法，等號比較運算子應該傳回`true`或`false`，並不應該擲回例外狀況。

### <a name="implicit-cast-operators"></a>隱含轉型運算子

因為使用者通常不需要知道已呼叫隱含轉型運算子，隱含轉型運算子所擲回例外狀況與預期不符。 因此，任何例外狀況應會擲不回從隱含轉型運算子。

## <a name="how-to-fix-violations"></a>如何修正違規

屬性 getter，請變更邏輯，使其不再具有擲回例外狀況，或將屬性變更的方法。

對於所有其他方法類型先前所列，變更邏輯，使它不再需要擲回例外狀況。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果違規所造成的例外狀況宣告，而不是擲回的例外狀況，則安全地隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則

- [CA2219：不要在 exception 子句中引發例外狀況](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>另請參閱

- [設計警告](../code-quality/design-warnings.md)
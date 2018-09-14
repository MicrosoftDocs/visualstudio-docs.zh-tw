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
ms.openlocfilehash: 4999770367ad7b170398333cf7c7cf2cb9d1c407
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546690"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065：不要在非預期的位置中引發例外狀況

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|類別|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因

不可擲回例外狀況 (Exception) 的方法卻擲回例外狀況。

## <a name="rule-description"></a>規則描述

不會擲回例外狀況的方法可以分類如下：

- 屬性的 Get 方法

- 事件存取子方法

- Equals 方法

- GetHashCode 方法

- ToString 方法

- 靜態建構函式

- 完成項

- Dispose 方法

- 等號比較運算子

- 隱含轉型運算子

下列各節將討論這些方法類型。

### <a name="property-get-methods"></a>屬性的 Get 方法

屬性基本上是智慧型欄位。 因此，它們應該表現得像是最大的欄位。 欄位不會擲回例外狀況，所以屬性。 如果您有此屬性，則會擲回例外狀況，請考慮將它的方法。

從屬性的 get 方法，可能會擲回下列例外狀況：

- <xref:System.InvalidOperationException?displayProperty=fullName> 所有的衍生項目 (包括<xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> 所有的衍生項目

- <xref:System.ArgumentException?displayProperty=fullName> （只能從索引的 get)

- <xref:System.Collections.Generic.KeyNotFoundException> （只能從索引的 get)

### <a name="event-accessor-methods"></a>事件存取子方法

事件存取子都應該是簡單的作業不會擲回例外狀況。 當您嘗試新增或移除事件處理常式時，事件不應該擲回例外狀況。

從事件存取子，可能會擲回下列例外狀況：

- <xref:System.InvalidOperationException?displayProperty=fullName> 所有的衍生項目 (包括<xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> 所有的衍生項目

- <xref:System.ArgumentException> 衍生項目

### <a name="equals-methods"></a>Equals 方法

下列**等於**方法不應該擲回例外狀況：

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

**Equals**方法應傳回`true`或`false`而非擲回例外狀況。 例如，若等於傳遞兩個不相符的類型應只會傳回`false`而非擲回<xref:System.ArgumentException>。

### <a name="gethashcode-methods"></a>GetHashCode 方法

下列**GetHashCode**方法通常不應該擲回例外狀況：

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**GetHashCode**應該一律會傳回值。 否則，您可能會遺失雜湊表中的項目。

新版**GetHashCode**採用引數可能會擲回<xref:System.ArgumentException>。 不過， **Object.GetHashCode**應該永遠不會擲回例外狀況。

### <a name="tostring-methods"></a>ToString 方法

偵錯工具會使用<xref:System.Object.ToString%2A?displayProperty=fullName>可顯示物件的相關資訊，以字串格式。 因此， **ToString**不應變更的物件狀態，它不應該擲回例外狀況。

### <a name="static-constructors"></a>靜態建構函式

擲回例外狀況從靜態建構函式會導致無法在目前的應用程式定義域中的型別。 您應該的擲回的例外狀況的靜態建構函式 （例如安全性問題） 的好理由。

### <a name="finalizers"></a>完成項

從完成項擲回例外狀況會導致 CLR 立即失敗，這讓處理序終止。 因此，在完成項擲回例外狀況應該避免。

### <a name="dispose-methods"></a>Dispose 方法

A<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法不應該擲回例外狀況。 中的清除邏輯一部分經常呼叫 dispose`finally`子句。 因此，明確地從 Dispose 擲回例外狀況會強制使用者加入例外狀況處理內`finally`子句。

**Dispose （false)** 程式碼路徑應該永遠不會擲回例外狀況，因為幾乎一律會來自完成項呼叫 Dispose。

### <a name="equality-operators--"></a>等號比較運算子 (= =、 ！ =)

Equals 方法，例如等號比較運算子應該傳回`true`或`false`，應該不會擲回例外狀況。

### <a name="implicit-cast-operators"></a>隱含轉型運算子

因為使用者通常不知道已呼叫隱含轉型運算子，隱含轉換運算子所擲回例外狀況是未預期的。 因此，任何例外狀況應會擲不回從隱含轉型運算子。

## <a name="how-to-fix-violations"></a>如何修正違規

屬性 getter，請變更邏輯，使它不會再擲回例外狀況，或變更屬性的方法。

對於所有其他方法型別先前所列，請變更邏輯，使它不再一定會擲回例外狀況。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果違規所造成的例外狀況宣告而不是擲回的例外狀況，它可安全地隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則

- [CA2219：不要在 exception 子句中引發例外狀況](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>另請參閱

- [設計警告](../code-quality/design-warnings.md)
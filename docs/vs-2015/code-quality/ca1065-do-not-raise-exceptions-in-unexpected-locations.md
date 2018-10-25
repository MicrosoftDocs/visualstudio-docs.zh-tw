---
title: CA1065： 不要引發例外狀況中的非預期的位置 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 142322360d4ba1ffed6ef893bf02254548ee2705
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887587"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065：不要在非預期的位置中引發例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|分類|Microsoft.Design|
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
 屬性基本上是智慧型欄位。 因此，它們應該表現得像是最大的欄位。 欄位並不會擲回例外狀況，所以屬性。 如果您有此屬性，則會擲回例外狀況，請考慮將它的方法。

 允許從屬性的 get 方法會擲回下列例外狀況：

-   <xref:System.InvalidOperationException?displayProperty=fullName> 所有的衍生項目 (包括<xref:System.ObjectDisposedException?displayProperty=fullName>)

-   <xref:System.NotSupportedException?displayProperty=fullName> 所有的衍生項目

-   <xref:System.ArgumentException?displayProperty=fullName> （只能從索引的 get)

-   <xref:System.Collections.Generic.KeyNotFoundException> （只能從索引的 get)

### <a name="event-accessor-methods"></a>事件存取子方法
 事件存取子都應該是簡單的作業不會擲回例外狀況。 當您嘗試新增或移除事件處理常式時，事件不應該擲回例外狀況。

 允許事件存取從擲回下列例外狀況：

-   <xref:System.InvalidOperationException?displayProperty=fullName> 所有的衍生項目 (包括<xref:System.ObjectDisposedException?displayProperty=fullName>)

-   <xref:System.NotSupportedException?displayProperty=fullName> 所有的衍生項目

-   <xref:System.ArgumentException> 衍生項目

### <a name="equals-methods"></a>Equals 方法
 下列**等於**方法不應該擲回例外狀況：

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)

  **Equals**方法應傳回`true`或`false`而非擲回例外狀況。 例如，若等於傳遞兩個不相符的類型應只會傳回`false`而非擲回<xref:System.ArgumentException>。

### <a name="gethashcode-methods"></a>GetHashCode 方法
 下列**GetHashCode**方法通常不應該擲回例外狀況：

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode(T)](http://go.microsoft.com/fwlink/?LinkId=113477)

  **GetHashCode**應該一律會傳回值。 否則，您可能會遺失雜湊表中的項目。

  新版**GetHashCode**採用引數可能會擲回<xref:System.ArgumentException>。 不過， **Object.GetHashCode**應該永遠不會擲回例外狀況。

### <a name="tostring-methods"></a>ToString 方法
 偵錯工具會使用<xref:System.Object.ToString%2A?displayProperty=fullName>可顯示物件的相關資訊，以字串格式。 因此， **ToString**不應變更物件的狀態，它不應該擲回例外狀況。

### <a name="static-constructors"></a>靜態建構函式
 擲回例外狀況從靜態建構函式會導致無法在目前的應用程式定義域中的型別。 您應針對擲回的例外狀況的靜態建構函式中有很充分的理由 （例如安全性問題）。

### <a name="finalizers"></a>完成項
 從完成項擲回例外狀況會導致 CLR 立即失敗，這讓處理序終止。 因此，在完成項擲回例外狀況應該避免。

### <a name="dispose-methods"></a>Dispose 方法
 A<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法不應該擲回例外狀況。 通常稱為 dispose 的清除邏輯一部分`finally`子句。 因此，明確地從 Dispose 擲回例外狀況會強制使用者加入例外狀況處理內`finally`子句。

 **Dispose （false)** 程式碼路徑應該永遠不會擲回例外狀況，因為這幾乎一律會呼叫來自完成項。

### <a name="equality-operators--"></a>等號比較運算子 (= =、 ！ =)
 Equals 方法，例如等號比較運算子應該傳回`true`或`false`和不應該擲回例外狀況。

### <a name="implicit-cast-operators"></a>隱含轉型運算子
 因為使用者通常不知道已呼叫隱含轉型運算子，隱含轉換運算子所擲回例外狀況是完全無法預期。 因此，任何例外狀況應會擲不回從隱含轉型運算子。

## <a name="how-to-fix-violations"></a>如何修正違規
 屬性 getter，請變更邏輯，使它不會再擲回例外狀況，或變更屬性的方法。

 對於所有其他方法型別先前所列，請變更邏輯，使它不再一定會擲回例外狀況。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果違規所造成的例外狀況宣告，而不是擲回的例外狀況。

## <a name="related-rules"></a>相關的規則
 [CA2219：不要在 exception 子句中引發例外狀況](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>另請參閱
 [設計警告](../code-quality/design-warnings.md)




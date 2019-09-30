---
title: CA2213:可處置的欄位應該受到處置
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1838d7e57b841c932d95006d1ff33972dd7a1a1f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231602"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213:可處置的欄位應該受到處置

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

一個型別， <xref:System.IDisposable?displayProperty=fullName>它會宣告<xref:System.IDisposable>也會實作為類型的欄位。 宣告類型的<xref:System.IDisposable.Dispose%2A>方法不會呼叫欄位的方法。<xref:System.IDisposable.Dispose%2A>

## <a name="rule-description"></a>規則描述

「類型」負責處置其所有非受控資源。 [規則 CA2213] 會檢查可處置的類型<xref:System.IDisposable>（也就是執行的） `T`是否宣告的欄位`F`是可處置類型`FT`的實例。 對於在包含`F`類型`T`的方法或初始化運算式中指派了本機建立物件的每個欄位，此規則會嘗試找出對的`FT.Dispose`呼叫。 此規則會搜尋所呼叫`T.Dispose`的方法，其中一個層級較低（也就是由所`T.Dispose`呼叫的方法所呼叫的方法）。

> [!NOTE]
> 除了[特殊情況](#special-cases)以外，規則 CA2213 只會針對在包含類型的方法和初始化運算式中指派為本機建立之可處置物件的欄位引發。 如果物件是在類型`T`外部建立或指派，則不會引發此規則。 這可減少包含類型不負責處置物件的情況下的雜訊。

### <a name="special-cases"></a>特殊案例

規則 CA2213 也可以針對下列類型的欄位引發，即使指派的物件不是在本機建立也一樣：

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

將其中一種類型的物件傳遞至函式，然後將它指派給欄位，表示*處置擁有權傳送*至新建立的類型。 也就是說，新建立的型別現在負責處置物件。 如果未處置物件，則會發生 CA2213 違規。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請<xref:System.IDisposable.Dispose%2A>在執行<xref:System.IDisposable>之類型的欄位上呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

在下列情況下，您可以放心地隱藏此規則中的警告：

- 標記的類型不負責釋放欄位所持有的資源（也就是類型沒有*處置擁有權*）
- 對的呼叫<xref:System.IDisposable.Dispose%2A>會在比規則檢查更深入的呼叫層級發生

## <a name="example"></a>範例

下列程式碼片段顯示的類型`TypeA` <xref:System.IDisposable>會執行。

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

下列程式碼片段顯示違反規則`TypeB` CA2213 的類型，方法是將欄位`aFieldOfADisposableType`宣告為可處置的`TypeA`類型（）， <xref:System.IDisposable.Dispose%2A>而不是在欄位上呼叫。

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

若要修正違規，請`Dispose()`在 [可處置] 欄位上呼叫：

```csharp
protected virtual void Dispose(bool disposing)
{
   if (!disposed)
   {
      // Dispose of resources held by this instance.
      aFieldOfADisposableType.Dispose();

      disposed = true;

      // Suppress finalization of this disposed instance.
      if (disposing)
      {
          GC.SuppressFinalize(this);
      }
   }
}
```

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)
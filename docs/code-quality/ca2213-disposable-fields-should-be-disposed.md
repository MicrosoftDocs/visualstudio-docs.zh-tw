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
ms.openlocfilehash: b38157fcc23561b47a919151aa78a71f98b3909b
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805004"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213:可處置的欄位應該受到處置

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

型別可實作<xref:System.IDisposable?displayProperty=fullName>宣告的型別，也會實作的欄位<xref:System.IDisposable>。 <xref:System.IDisposable.Dispose%2A>欄位的方法不由呼叫<xref:System.IDisposable.Dispose%2A>宣告型別的方法。

## <a name="rule-description"></a>規則描述

類型會負責所有 unmanaged 資源的處置。 規則 CA2213 會檢查以查看是否可處置的類型 (也就是其中一個可實作<xref:System.IDisposable>)`T`宣告欄位`F`也就是可處置型別的執行個體`FT`。 每個欄位`F`，已指派在本機建立的物件內的方法或初始設定式包含型別的`T`，此規則會嘗試找出呼叫`FT.Dispose`。 此規則會搜尋呼叫的方法`T.Dispose`和 下一層 (也就是由所呼叫的方法呼叫的方法`T.Dispose`)。

> [!NOTE]
> 以外[特殊的情況下](#special-cases)，規則只適用於已指派在本機建立的可處置物件，包含類型的方法和初始設定式內的欄位 CA2213 引發。 如果建立或指派給外部型別物件`T`，不會引發此規則。 這可減少雜訊，其中包含類型未擁有處置物件的責任的情況下。

### <a name="special-cases"></a>特殊案例

即使不在本機建立其指派的物件，則規則 CA2213 也可能引發下列類型的欄位：

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

將其中一種類型的物件傳遞至建構函式，然後將它指派給 欄位指出*處置擁有權移轉*新建構的類型。 也就是新建構的型別負責現在處置的物件。 如果未處置的物件，就會發生 CA2213 的違規情形。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，呼叫<xref:System.IDisposable.Dispose%2A>之實作類型的欄位上<xref:System.IDisposable>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，如果：

- 標有旗標的型別並不負責該欄位所持有的釋放資源 (也就是型別沒有*處置擁有權*)
- 若要呼叫<xref:System.IDisposable.Dispose%2A>發生更深層級呼叫比規則檢查

## <a name="example"></a>範例

下列程式碼片段顯示的型別`TypeA`實作<xref:System.IDisposable>。

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

下列程式碼片段顯示的型別`TypeB`，藉由宣告欄位違反規則 CA2213`aFieldOfADisposableType`做為可處置的類型 (`TypeA`) 並不會呼叫<xref:System.IDisposable.Dispose%2A>的欄位。

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)
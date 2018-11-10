---
title: CA2213：可處置的欄位應該受到處置
ms.date: 11/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be06c9bf38ec360cedc858d92a84b1f89c662856
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220628"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213：可處置的欄位應該受到處置

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

型別可實作<xref:System.IDisposable?displayProperty=fullName>宣告的型別，也會實作的欄位<xref:System.IDisposable>。 <xref:System.IDisposable.Dispose%2A>欄位的方法不由呼叫<xref:System.IDisposable.Dispose%2A>宣告型別的方法。

## <a name="rule-description"></a>規則描述

類型會負責所有 unmanaged 資源的處置。 規則 CA2213 會檢查以查看是否可處置的類型 (也就是其中一個可實作<xref:System.IDisposable>)`T`宣告欄位`F`也就是可處置型別的執行個體`FT`。 每個欄位`F`，已指派在本機建立的物件內的方法或初始設定式包含型別的`T`，此規則會嘗試找出呼叫`FT.Dispose`。 此規則會搜尋呼叫的方法`T.Dispose`和 下一層 (也就是由所呼叫的方法呼叫的方法`FT.Dispose`)。

> [!NOTE]
> 只適用於已指派在本機建立的可處置物件，包含類型的方法和初始設定式內的欄位，就會引發規則 CA2213。 如果建立或指派給外部型別物件`T`，不會引發此規則。 這可減少雜訊，其中包含類型未擁有處置物件的責任的情況下。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，呼叫<xref:System.IDisposable.Dispose%2A>之實作類型的欄位上<xref:System.IDisposable>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

安全地隱藏此規則的警告，如果您不負責針對欄位中，所持有的釋放資源，或如果呼叫<xref:System.IDisposable.Dispose%2A>比規則檢查更深入的呼叫層級，就會發生。

## <a name="example"></a>範例

下列程式碼片段顯示的型別`TypeA`實作<xref:System.IDisposable>。

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

下列程式碼片段顯示的型別`TypeB`，藉由宣告欄位違反規則 CA2213`aFieldOfADisposableType`做為可處置的類型 (`TypeA`) 並不會呼叫<xref:System.IDisposable.Dispose%2A>的欄位。

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)
---
title: CA2115:使用原生資源時必須呼叫 GC.KeepAlive
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: eb6d28e15870907034479e698ba8e7464f4f5159
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232729"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115:使用原生資源時必須呼叫 GC.KeepAlive

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|分類|Microsoft.Security|
|重大變更|不中斷|

## <a name="cause"></a>原因

在具有完成項的類型中宣告的方法會<xref:System.IntPtr?displayProperty=fullName>參考<xref:System.UIntPtr?displayProperty=fullName>或欄位，但不會<xref:System.GC.KeepAlive%2A?displayProperty=fullName>呼叫。

## <a name="rule-description"></a>規則描述

如果在 managed 程式碼中沒有其他參考，則垃圾收集會完成物件。 物件的非受控參考不會防止垃圾收集。 此規則所偵測的錯誤，可能是因為在 Unmanaged 程式碼仍在使用 Unmanaged 資源時，就完成 Unmanaged 資源所致。

此規則假設和<xref:System.IntPtr> <xref:System.UIntPtr>欄位儲存非受控資源的指標。 因為完成項的目的是要釋放非受控資源，此規則會假設完成項將會釋放指標欄位所指向的非受控資源。 此規則也假設方法正在參考指標欄位，以將非受控資源傳遞給非受控碼。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請將對的<xref:System.GC.KeepAlive%2A>呼叫新增至方法，並將目前的`this`實例C# （ C++在和中）當做引數傳遞。 將呼叫放在程式碼的最後一行之後，其中物件必須受到保護，以防止垃圾收集。 在呼叫<xref:System.GC.KeepAlive%2A>之後，物件會再次被視為已準備好進行垃圾收集，假設沒有受控參考。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

此規則會做出一些假設，可能會導致誤報。 您可以在下列情況中，安全地隱藏此規則中的警告：

- 完成項不會釋放方法所參考之<xref:System.IntPtr>或<xref:System.UIntPtr>欄位的內容。

- 方法不會將<xref:System.IntPtr>或<xref:System.UIntPtr>欄位傳遞至未受管理的程式碼。

請仔細檢查其他訊息，再將它們排除。 此規則會偵測不容易重現和 debug 的錯誤。

## <a name="example"></a>範例

在下列範例中， `BadMethod`不包含對的`GC.KeepAlive`呼叫，因此會違反規則。 `GoodMethod`包含已更正的程式碼。

> [!NOTE]
> 這個範例是虛擬程式碼。 雖然程式碼會進行編譯和執行，但不會引發警告，因為不會建立或釋放非受控資源。

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)
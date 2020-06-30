---
title: CA2115：呼叫 GC。使用原生資源時的 KeepAlive |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c668172ca318000068fb4e90f4848e456c32208d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543620"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115:使用原生資源時必須呼叫 GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|類別|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 在具有完成項的類型中宣告的方法 <xref:System.IntPtr?displayProperty=fullName> 會參考或 <xref:System.UIntPtr?displayProperty=fullName> 欄位，但不會呼叫 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 如果在 managed 程式碼中沒有其他參考，則垃圾收集會完成物件。 物件的非受控參考不會防止垃圾收集。 此規則所偵測的錯誤，可能是因為在 Unmanaged 程式碼仍在使用 Unmanaged 資源時，就完成 Unmanaged 資源所致。

 此規則假設 <xref:System.IntPtr> 和 <xref:System.UIntPtr> 欄位儲存非受控資源的指標。 因為完成項的目的是要釋放非受控資源，此規則會假設完成項將會釋放指標欄位所指向的非受控資源。 此規則也假設方法正在參考指標欄位，以將非受控資源傳遞給非受控碼。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將對的呼叫新增 <xref:System.GC.KeepAlive%2A> 至方法，並將目前的實例（ `this` 在 c # 和 c + + 中）當做引數傳遞。 將呼叫放在程式碼的最後一行之後，其中物件必須受到保護，以防止垃圾收集。 在呼叫之後 <xref:System.GC.KeepAlive%2A> ，物件會再次被視為已準備好進行垃圾收集，假設沒有受控參考。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 此規則會做出一些假設，可能會導致誤報。 您可以在下列情況中，安全地隱藏此規則中的警告：

- 完成項不會釋放方法所參考之 <xref:System.IntPtr> 或 <xref:System.UIntPtr> 欄位的內容。

- 方法不會將 <xref:System.IntPtr> 或欄位傳遞 <xref:System.UIntPtr> 至未受管理的程式碼。

  請仔細檢查其他訊息，再將它們排除。 此規則會偵測不容易重現和 debug 的錯誤。

## <a name="example"></a>範例
 在下列範例中，不包含對的 `BadMethod` 呼叫 `GC.KeepAlive` ，因此會違反規則。 `GoodMethod`包含已更正的程式碼。

> [!NOTE]
> 這個範例是虛擬程式碼，雖然程式碼會進行編譯和執行，但不會引發警告，因為不會建立或釋放非受控資源。

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

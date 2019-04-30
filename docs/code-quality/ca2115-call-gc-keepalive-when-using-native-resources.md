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
ms.openlocfilehash: 9a74f6313f90a31d43cf39443b1c44d78f0628f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545185"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115:使用原生資源時必須呼叫 GC.KeepAlive

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

在具有完成項的型別中宣告的方法參考<xref:System.IntPtr?displayProperty=fullName>或是<xref:System.UIntPtr?displayProperty=fullName>欄位中，但不會呼叫<xref:System.GC.KeepAlive%2A?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述

如果 managed 程式碼中有多個參考，記憶體回收會終結物件。 未受管理的物件的參考不會防止記憶體回收。 此規則所偵測的錯誤，可能是因為在 Unmanaged 程式碼仍在使用 Unmanaged 資源時，就完成 Unmanaged 資源所致。

這項規則假設<xref:System.IntPtr>和<xref:System.UIntPtr>欄位儲存 unmanaged 資源的指標。 因為完成項的用途是釋放 unmanaged 的資源，此規則會假設完成項會釋放指標欄位所指向的 unmanaged 的資源。 這項規則也會假設方法參考傳遞至 unmanaged 程式碼的 unmanaged 的資源的指標欄位。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將呼叫加入<xref:System.GC.KeepAlive%2A>方法，並傳遞目前執行個體 (`this`在C#和C++) 做為引數。 位置呼叫程式碼的最後一行之後，物件必須加以保護以免記憶體回收。 若要在呼叫之後立即<xref:System.GC.KeepAlive%2A>，物件一次視為已準備好進行記憶體回收假設沒有受管理的參考它。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

此規則可讓一些可能會導致誤判的假設。 您可以安全地隱藏此規則的警告，如果：

- 完成項不會釋放的內容<xref:System.IntPtr>或<xref:System.UIntPtr>方法所參考的欄位。

- 此方法不會通過<xref:System.IntPtr>或<xref:System.UIntPtr>欄位至 unmanaged 程式碼。

請仔細檢閱其他訊息之前排除它們。 此規則會偵測難以重現及偵錯的錯誤。

## <a name="example"></a>範例

在下列範例中，`BadMethod`不包含呼叫`GC.KeepAlive`且因此違反此規則。 `GoodMethod` 包含已更正的程式碼。

> [!NOTE]
> 這個範例是虛擬程式碼。 雖然程式碼會編譯並執行，因為尚未建立或釋放 unmanaged 的資源，並不會引發警告。

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)
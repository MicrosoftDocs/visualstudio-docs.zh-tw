---
title: CA1060:必須將 P-Invokes 移到 NativeMethods 類別
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a01c8ca81ab469d578d58e6195171c2e3b07704b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788669"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060:必須將 P/Invokes 移到 NativeMethods 類別

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

方法會存取 unmanaged 程式碼會使用平台叫用服務，並不是其中的成員**NativeMethods**類別。

## <a name="rule-description"></a>規則描述

平台叫用方法，例如使用標記<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性或使用所定義的方法`Declare`中的關鍵字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，存取 unmanaged 程式碼。 這些方法應該在下列類別之一：

- **NativeMethods** -此類別不會抑制堆疊查核行程，unmanaged 程式碼權限。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>不會套用至這個類別。)這個類別是可用於任何地方會執行堆疊查核行程，因此的方法。

- **SafeNativeMethods** -這個類別會抑制堆疊查核行程，unmanaged 程式碼權限。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>套用至這個類別。)這個類別是對呼叫的任何人都是安全的方法。 這些方法的呼叫端不需要執行完整的安全性檢閱，以確定使用是安全的因為是無害的任何呼叫端的方法。

- **UnsafeNativeMethods** -這個類別會抑制堆疊查核行程，unmanaged 程式碼權限。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>套用至這個類別。)此類別適用於有潛在危險的方法。 這些方法的任何呼叫端必須不執行完整的安全性檢閱，以確定使用是安全的因為會執行任何的堆疊查核行程。

這些類別會宣告為`internal`(`Friend`，在 Visual Basic 中)，並宣告私用的建構函式，來防止建立新的執行個體。 這些類別中的方法應該`static`並`internal`(`Shared`和`Friend`Visual Basic 中)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將方法移至適當**NativeMethods**類別。 對於大部分的應用程式，將 P/Invokes 移到新的類別，稱為**NativeMethods**就已足夠。

 不過，如果您正在開發其他應用程式中使用的程式庫，您應該考慮定義兩個其他類別，可呼叫**SafeNativeMethods**並**UnsafeNativeMethods**。 這些類別類似於**NativeMethods**類別，不過，藉由呼叫的特殊屬性會標示**SuppressUnmanagedCodeSecurityAttribute**。 套用這個屬性時，執行階段不會執行以確定所有的呼叫端必須擁有完整堆疊查核行程**UnmanagedCode**權限。 執行階段通常會在啟動此權限檢查。 未執行檢查，因為它可大幅改善這些未受管理的方法呼叫的效能，它也可讓具有有限的權限來呼叫這些方法的程式碼。

 不過，您應該在十二萬分地謹慎使用這個屬性。 如果未正確實作，它可以有嚴重的安全性含意...

 如需有關如何實作方法的資訊，請參閱**NativeMethods**範例中， **SafeNativeMethods**範例中，並**UnsafeNativeMethods**範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會宣告方法違反此規則。 若要更正此違規情形， **RemoveDirectory** P/Invoke 應該移至適當的類別是設計用來保存只 P/Invoke。

 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>NativeMethods 範例

### <a name="description"></a>描述
 因為**NativeMethods**類別不應該使用標示**SuppressUnmanagedCodeSecurityAttribute**，將要求放入其中的 P/Invokes **UnmanagedCode**權限。 因為大部分的應用程式從本機電腦上執行，以及完全信任執行，這通常不是問題。 不過，如果您正在開發可重複使用程式庫，您應該考慮定義**SafeNativeMethods**或是**UnsafeNativeMethods**類別。

 下列範例所示**Interaction.Beep**包裝的方法**MessageBeep**函式從 user32.dll。 **MessageBeep**置於 P/Invoke **NativeMethods**類別。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>SafeNativeMethods 範例

### <a name="description"></a>描述
 P/Invoke 方法，可以安全地公開給任何應用程式，並沒有任何副作用都應該放在名為類別**SafeNativeMethods**。 您不必要求權限，您就不必在多注意力在從的呼叫，用多少付多少。

 下列範例所示**environment.tickcount 做**屬性，可包裝**GetTickCount**函式，從 kernel32.dll。

### <a name="code"></a>程式碼
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods 範例

### <a name="description"></a>描述
 無法安全地呼叫和，可能會造成副作用的 P/Invoke 方法都應該放在名為類別**UnsafeNativeMethods**。 這些方法應該嚴格檢查以確定它們都不會公開該使用者不小心。 此規則[CA2118:檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)可以解決這個。 或者，方法應該有其他的權限，而不是要求**UnmanagedCode**時使用它們。

 下列範例所示**Cursor.Hide**包裝的方法**ShowCursor**函式從 user32.dll。

### <a name="code"></a>程式碼
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>另請參閱

- [設計警告](../code-quality/design-warnings.md)
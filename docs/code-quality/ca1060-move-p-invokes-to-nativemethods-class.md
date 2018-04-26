---
title: CA1060： 移動 P-叫用到 NativeMethods 類別
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6035553f8d3a4518fe99e7800a61f1b5921d947
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060：將 P/Invokes 移到 NativeMethods 類別
|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法用來存取 unmanaged 程式碼的平台叫用服務，並不是其中一個成員**NativeMethods**類別。

## <a name="rule-description"></a>規則描述
 平台叫用方法，例如使用標記的<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性或方法定義使用`Declare`關鍵字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，存取 unmanaged 程式碼。 這些方法應為下列類別的其中一個：

-   **NativeMethods** -這個類別不會抑制堆疊查核行程，unmanaged 程式碼權限。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>不會套用至這個類別。)這個類別是因為將會執行堆疊查核行程可以任何地方使用的方法。

-   **SafeNativeMethods** -這個類別會隱藏堆疊查核行程，unmanaged 程式碼權限。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>套用至這個類別。)這個類別是安全的任何人呼叫的方法。 這些方法的呼叫端不需要執行完整的安全性檢閱，並確定使用方式是安全的因為方法都是無害的任何呼叫端。

-   **UnsafeNativeMethods** -這個類別會隱藏堆疊查核行程，unmanaged 程式碼權限。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>套用至這個類別。)這個類別是有潛在危險的方法。 這些方法的任何呼叫端必須不執行完整的安全性檢閱，並確定使用方式是安全的因為將會執行任何堆疊查核行程。

 這些類別會宣告為`internal`(`Friend`，在 Visual Basic 中)，並宣告私用的建構函式，來防止建立的新執行個體。 這些類別中的方法應該`static`和`internal`(`Shared`和`Friend`在 Visual Basic 中)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將方法移至適當**NativeMethods**類別。 對於大部分的應用程式，將 P/Invokes 移到新的類別，名為**NativeMethods**即已足夠。

 不過，如果您正在開發以用於其他應用程式的程式庫，您應該考慮定義兩個其他類別，可呼叫**SafeNativeMethods**和**UnsafeNativeMethods**。 這些類別類似於**NativeMethods**類別; 不過，使用稱為的特殊屬性來標記它們**SuppressUnmanagedCodeSecurityAttribute**。 套用這個屬性時，執行階段不會執行完整堆疊查核行程，以確定所有呼叫端擁有**UnmanagedCode**權限。 執行階段通常會在啟動此權限檢查。 因為未執行檢查，可大幅提升效能的這些 unmanaged 方法的呼叫，它也可讓具有有限的權限可以呼叫這些方法的程式碼。

 不過，您應該小心使用這個屬性。 如果未正確實作可能會造成嚴重的安全性含意...

 如需如何實作方法的資訊，請參閱**NativeMethods**範例中， **SafeNativeMethods**範例中，和**UnsafeNativeMethods**範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會宣告方法違反此規則。 若要更正違規， **RemoveDirectory** P/Invoke 應移到適當的類別是設計用來保存只 P/Invokes。

 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>NativeMethods 範例

### <a name="description"></a>描述
 因為**NativeMethods**類別不應該使用標示**SuppressUnmanagedCodeSecurityAttribute**，將要求放入其中的 P/Invokes **UnmanagedCode**權限。 由於大部分的應用程式從本機電腦上執行，而且與完全信任執行，這通常不是問題。 不過，如果您正在開發可重複使用程式庫，您應該考慮定義**SafeNativeMethods**或**UnsafeNativeMethods**類別。

 下列範例所示**Interaction.Beep**方法包裝**MessageBeep**從 user32.dll 函式。 **MessageBeep** P/Invoke 置於**NativeMethods**類別。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>SafeNativeMethods 範例

### <a name="description"></a>描述
 可以安全地公開之任何應用程式並沒有任何副作用的 P/Invoke 方法都應該放在名為類別**SafeNativeMethods**。 您沒有指定的權限，並沒有太多注意從的呼叫位置。

 下列範例所示**Environment.TickCount**包裝屬性**GetTickCount**函式，從 kernel32.dll。

### <a name="code"></a>程式碼
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods 範例

### <a name="description"></a>描述
 無法安全地呼叫，而且，可能會造成副作用的 P/Invoke 方法都應該放在名為類別**UnsafeNativeMethods**。 這些方法應該嚴格檢查以確定它們都不會公開該使用者不小心。 此規則[ca2118 必須： 檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)這可以協助。 或者，方法應該有另一個權限，而不是要求**UnmanagedCode**它們時使用。

 下列範例所示**Cursor.Hide**方法包裝**ShowCursor**從 user32.dll 函式。

### <a name="code"></a>程式碼
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>另請參閱
 [設計警告](../code-quality/design-warnings.md)
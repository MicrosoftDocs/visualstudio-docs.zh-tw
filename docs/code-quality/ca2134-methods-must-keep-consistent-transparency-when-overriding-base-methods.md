---
title: CA2134:覆寫基底方法時，方法必須保持一致的透明度
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 517588826983613c71a74296914b1dfeb3eaa2b4
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253308"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134:覆寫基底方法時，方法必須保持一致的透明度

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|分類|Microsoft.Security|
|重大變更|中斷|

## <a name="cause"></a>原因
當以標記的<xref:System.Security.SecurityCriticalAttribute>方法覆寫透明或<xref:System.Security.SecuritySafeCriticalAttribute>以標記的方法時，就會引發此規則。 當透明或以標記的<xref:System.Security.SecuritySafeCriticalAttribute>方法覆寫以標記<xref:System.Security.SecurityCriticalAttribute>的方法時，也會引發此規則。

覆寫虛擬方法或實作介面時會套用此規則。

## <a name="rule-description"></a>規則描述
嘗試在繼承鏈上進一步變更方法的安全性存取範圍時，就會引發此規則。 例如，如果基類中的虛擬方法是透明或安全關鍵，則衍生的類別必須以透明或安全關鍵的方法覆寫它。 相反地，如果虛擬的安全性關鍵，衍生的類別就必須使用安全性關鍵方法來覆寫它。 相同的規則適用于執行介面方法。

當程式碼是以 JIT 編譯而不是在執行時間時，會強制執行透明度規則，因此透明度計算沒有動態類型資訊。 因此，透明度計算的結果必須只能從進行 JIT 編譯的靜態類型來判斷，而不論動態類型為何。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請變更覆寫虛擬方法或執行介面的方法透明度，以符合虛擬或介面方法的透明度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。 此規則的違規會導致使用層級 2 <xref:System.TypeLoadException>透明度之元件的執行時間。

## <a name="examples"></a>範例

### <a name="code"></a>程式碼
[!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>另請參閱
[安全性透明的程式碼，層級2](/dotnet/framework/misc/security-transparent-code-level-2)
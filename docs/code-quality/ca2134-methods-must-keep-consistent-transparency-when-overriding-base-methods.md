---
title: CA2134：覆寫基底方法時，方法必須保持一致的透明度
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e74eee5098b23d5e0adf94259aa6ce0b9f2f423e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134：覆寫基底方法時，方法必須保持一致的透明度
|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 此規則會引發的方法以標記時<xref:System.Security.SecurityCriticalAttribute>覆寫透明或使用的方法<xref:System.Security.SecuritySafeCriticalAttribute>。 是透明或使用的方法時，也會引發此規則<xref:System.Security.SecuritySafeCriticalAttribute>覆寫的方法標示為<xref:System.Security.SecurityCriticalAttribute>。

 覆寫虛擬方法或實作介面時會套用此規則。

## <a name="rule-description"></a>規則描述
 此規則會引發變更的方法進一步繼承鏈結上的安全性存取嘗試。 例如，如果透明或安全關鍵基底類別中的虛擬方法，然後在衍生的類別必須覆寫它透明或安全關鍵方法使用。 相反地，如果虛擬是安全性關鍵，衍生的類別必須覆寫它與安全性關鍵方法。 實作介面方法適用於相同的規則。

 程式碼時 JIT 編譯而不是在執行階段，以便透明度計算沒有動態類型資訊時，會強制執行透明度規則。 因此，透明度計算的結果必須能夠只根據進行 JIT 編譯，不論動態類型的靜態類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更會覆寫虛擬方法或實作透明虛擬或介面方法比對介面之方法的透明度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 違反此規則會導致執行階段<xref:System.TypeLoadException>的組件，請使用層級 2 透明度。

## <a name="examples"></a>範例

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>另請參閱
 [安全性透明的程式碼，層級 2](/dotnet/framework/misc/security-transparent-code-level-2)
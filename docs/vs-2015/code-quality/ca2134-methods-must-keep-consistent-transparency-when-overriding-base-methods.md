---
title: CA2134：覆寫基底方法時，方法必須保持一致的透明度 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96910ffc53e6c48f930232c83d87570f1bc71e00
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608928"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134：覆寫基底方法時，方法必須保持一致的透明度
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 當以 <xref:System.Security.SecurityCriticalAttribute> 標記的方法覆寫透明或以 <xref:System.Security.SecuritySafeCriticalAttribute> 標記的方法時，就會引發此規則。 當透明或以 <xref:System.Security.SecuritySafeCriticalAttribute> 標記的方法覆寫以 <xref:System.Security.SecurityCriticalAttribute> 標記的方法時，也會引發此規則。

 覆寫虛擬方法或實作介面時會套用此規則。

## <a name="rule-description"></a>規則描述
 嘗試在繼承鏈上進一步變更方法的安全性存取範圍時，就會引發此規則。 例如，如果基類中的虛擬方法是透明或安全關鍵，則衍生的類別必須以透明或安全關鍵的方法覆寫它。 相反地，如果虛擬的安全性關鍵，衍生的類別就必須使用安全性關鍵方法來覆寫它。 相同的規則適用于執行介面方法。

 當程式碼是以 JIT 編譯而不是在執行時間時，會強制執行透明度規則，而透明度計算則不會有動態類型資訊。 因此，透明度計算的結果必須只能從進行 JIT 編譯的靜態類型來判斷，而不論動態類型為何。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請變更覆寫虛擬方法或執行介面的方法透明度，以符合虛擬或介面方法的透明度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 違反這項規則將會導致使用層級2透明度之元件的執行時間 <xref:System.TypeLoadException>。

## <a name="examples"></a>範例

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>請參閱
 [安全性透明的程式碼，層級2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)

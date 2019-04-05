---
title: CA2134:覆寫基底方法時，方法必須保持一致的透明度 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f5c8e6298ab8ec7da947ae3c71fd2dcf4e1e9e25
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944496"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134:覆寫基底方法時，方法必須保持一致的透明度
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 以標記方法時，就會引發此規則<xref:System.Security.SecurityCriticalAttribute>覆寫的方法為透明或使用<xref:System.Security.SecuritySafeCriticalAttribute>。 當透明或使用的方法時，也會引發此規則<xref:System.Security.SecuritySafeCriticalAttribute>覆寫的方法標記著<xref:System.Security.SecurityCriticalAttribute>。

 覆寫虛擬方法或實作介面時會套用此規則。

## <a name="rule-description"></a>規則描述
 若要變更的方法進一步繼承鏈結上的安全性存取嘗試都會引發此規則。 比方說，如果透明或安全關鍵性的基底類別中的虛擬方法，然後在衍生的類別必須覆寫它使用透明或安全關鍵性的方法。 相反地，如果虛擬是安全性關鍵，衍生的類別必須覆寫它使用安全性關鍵方法。 實作介面方法適用於相同的規則。

 程式碼是 JIT 編譯而不是在執行階段，讓透明度計算沒有動態型別資訊時，會強制執行透明度規則。 因此，透明度計算的結果必須能夠判斷完全從進行 JIT 編譯，不論動態類型的靜態類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更方法覆寫虛擬方法或實作介面，以比對透明度的虛擬或介面方法的透明度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏這項規則的警告。 違反此規則會導致執行階段<xref:System.TypeLoadException>使用層級 2 透明度的組件。

## <a name="examples"></a>範例

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>另請參閱
 [安全性透明程式碼，層級 2](http://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)

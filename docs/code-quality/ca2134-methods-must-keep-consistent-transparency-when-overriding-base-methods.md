---
title: "CA2134： 覆寫基底方法時方法必須保持一致的透明度 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: feb33e630322237522c98ff3f803bc44b3fbcc86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
 [安全性透明的程式碼，層級 2](http://msdn.microsoft.com/Library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
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
ms.openlocfilehash: fe9a84280b0124eed6bb0cfffae9c1ec2942bddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547715"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134:覆寫基底方法時，方法必須保持一致的透明度
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 當以標記的方法 <xref:System.Security.SecurityCriticalAttribute> 覆寫透明或以標記的方法時，就會引發此規則 <xref:System.Security.SecuritySafeCriticalAttribute> 。 當透明或以標記的方法覆寫以標記的方法時，也會引發此規則 <xref:System.Security.SecuritySafeCriticalAttribute> <xref:System.Security.SecurityCriticalAttribute> 。

 覆寫虛擬方法或實作介面時會套用此規則。

## <a name="rule-description"></a>規則描述
 這項規則會在嘗試變更繼承鏈上方法的安全性存取範圍時引發。 例如，如果基類中的虛擬方法為透明或安全關鍵，則衍生類別必須使用透明或安全關鍵的方法來覆寫它。 相反地，如果虛擬為安全性關鍵，則衍生類別必須使用安全性關鍵方法來覆寫它。 相同的規則適用于執行介面方法。

 當程式碼是 JIT 編譯而不是在執行時間時，會強制執行透明度規則，讓透明計算沒有動態類型資訊。 因此，不論動態類型為何，透明計算的結果都必須能夠僅從 JIT 編譯的靜態型別判斷。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請變更覆寫虛擬方法或執行介面以符合虛擬或介面方法透明度的方法透明度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 違規此規則將會產生 <xref:System.TypeLoadException> 使用層級2透明度之元件的執行時間。

## <a name="examples"></a>範例

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>另請參閱
 [安全性透明的程式碼，層級 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)

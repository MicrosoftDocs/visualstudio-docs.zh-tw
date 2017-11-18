---
title: "CA1057： 字串 URI 多載呼叫 System.Uri 多載 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 094680be86955a47486ec108e779a313b7b0c0fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057：字串 URI 多載呼叫 System.Uri 多載
|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 類型會宣告方法多載，只在於以字串參數取代<xref:System.Uri?displayProperty=fullName>參數，並採用字串參數的多載不會呼叫的多載，<xref:System.Uri>參數。  
  
## <a name="rule-description"></a>規則描述  
 因為多載的差別只由字串 /<xref:System.Uri>參數，會假設字串是代表統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri>類別以安全的方式提供這些服務。 若要獲得的好處<xref:System.Uri>類別，字串多載應該呼叫<xref:System.Uri>多載使用字串引數。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 重新實作的方法，使用 URI 的字串表示，因此它會建立的執行個體<xref:System.Uri>類別使用的字串引數，並接著會將傳遞<xref:System.Uri>物件的多載<xref:System.Uri>參數。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果字串參數不代表 URI。  
  
## <a name="example"></a>範例  
 下列範例顯示正確實作的字串多載。  
  
 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA2234：必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
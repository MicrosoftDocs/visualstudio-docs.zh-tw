---
title: CA1057： 字串 URI 多載呼叫 System.Uri 多載 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e948e91a0559034e688e029eb5ba227a8dd343c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920504"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057：字串 URI 多載呼叫 System.Uri 多載
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 型別會宣告只有字串參數取代為不同的方法多載<xref:System.Uri?displayProperty=fullName>參數，以及採用字串參數的多載不會呼叫多載，<xref:System.Uri>參數。

## <a name="rule-description"></a>規則描述
 因為多載的差別只能由字串 /<xref:System.Uri>參數，該字串會假設為代表統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri>類別會提供這些服務安全的方式。 若要獲得的好處<xref:System.Uri>類別，字串多載呼叫<xref:System.Uri>多載使用字串引數。

## <a name="how-to-fix-violations"></a>如何修正違規
 重新實作，以建立的執行個體，請使用 URI 的字串表示的方法<xref:System.Uri>類別使用的字串引數，並接著傳遞<xref:System.Uri>物件的多載<xref:System.Uri>參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它會安全地隱藏此規則的警告，如果字串參數不代表 URI。

## <a name="example"></a>範例
 下列範例會示範正確實作的字串多載。

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA2234：必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)




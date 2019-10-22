---
title: CA1057：字串 URI 多載呼叫 System.object 多載 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba7e7de4f3ef6336ed3d82dc1e1da03ec0bf2575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603070"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057：字串 URI 多載呼叫 System.Uri 多載
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 類型宣告的方法多載，只會以 <xref:System.Uri?displayProperty=fullName> 參數取代 string 參數，而接受字串參數的多載則不會呼叫接受 <xref:System.Uri> 參數的多載。

## <a name="rule-description"></a>規則描述
 因為多載只有 string/<xref:System.Uri> 參數不同，所以會假設字串代表統一資源識別元（URI）。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 @No__t_0 類別以安全且安全的方式提供這些服務。 若要獲得 <xref:System.Uri> 類別的優點，字串多載應該使用字串引數呼叫 <xref:System.Uri> 多載。

## <a name="how-to-fix-violations"></a>如何修正違規
 重新執行使用 URI 之字串表示的方法，讓它使用字串引數建立 <xref:System.Uri> 類別的實例，然後將 <xref:System.Uri> 物件傳遞至具有 <xref:System.Uri> 參數的多載。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果 string 參數不代表 URI，就可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示正確實作為字串多載。

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2234：必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

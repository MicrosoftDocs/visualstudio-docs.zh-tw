---
title: CA1057:字串 URI 多載呼叫 System.Uri 多載
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e6bd77a49690979ea7ab3c4619fdd578a80bb77c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235515"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057:字串 URI 多載呼叫 System.Uri 多載

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|分類|Microsoft.Design|
|重大變更|不中斷|

## <a name="cause"></a>原因

類型宣告的方法多載，只會以<xref:System.Uri?displayProperty=fullName>參數取代字串參數，而接受字串參數的多載則不會呼叫<xref:System.Uri>接受參數的多載。

## <a name="rule-description"></a>規則描述
因為多載只會因字串或<xref:System.Uri>參數而有所不同，所以會假設字串代表統一資源識別元（URI）。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri>類別以安全且安全的方式提供這些服務。 若要獲得<xref:System.Uri>類別的優點，字串多載應該使用字串自<xref:System.Uri>變數呼叫多載。

## <a name="how-to-fix-violations"></a>如何修正違規
重新產生使用 URI 字串表示的方法，讓它使用字串引數來建立<xref:System.Uri>類別的實例，然後將<xref:System.Uri>物件傳遞至具有<xref:System.Uri>參數的多載。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果 string 參數不代表 URI，就可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示正確實作為字串多載。

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>相關規則
[CA2234 必須傳遞 System.object 物件，而不是字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

[CA1056URI 屬性不應為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054URI 參數不應為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055URI 傳回值不應為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
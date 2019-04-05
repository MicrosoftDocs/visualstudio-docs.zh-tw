---
title: CA1041:提供 ObsoleteAttribute 訊息 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fe14ca0c0e917896a2ed5a31a03a8c1a7057d613
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930497"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041:必須提供 ObsoleteAttribute 訊息
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 使用標示的型別或成員<xref:System.ObsoleteAttribute?displayProperty=fullName>屬性，並沒有其<xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>指定的屬性。

## <a name="rule-description"></a>規則描述
 <xref:System.ObsoleteAttribute> 用來標記已被取代的程式庫類型和成員。 程式庫取用者應該避免使用任何類型或已標記為過時的成員。 這是因為它可能不支援，且最後會移除來自較新版本的程式庫。 使用標記的型別或成員的時<xref:System.ObsoleteAttribute>編譯時，<xref:System.ObsoleteAttribute.Message%2A>顯示屬性的屬性。 以便提供使用者有關過時類型或成員的資訊。 這項資訊通常包括多少時間的過時類型或成員會支援程式庫設計人員，並將慣用的取代項目。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入`message`參數來<xref:System.ObsoleteAttribute>建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告，因為<xref:System.ObsoleteAttribute.Message%2A>屬性會提供過時的型別或成員的重要資訊。

## <a name="example"></a>範例
 下列範例顯示過時的成員具有正確宣告<xref:System.ObsoleteAttribute>。

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.ObsoleteAttribute?displayProperty=fullName>

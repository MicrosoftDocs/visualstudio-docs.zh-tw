---
title: CA1041：提供 ObsoleteAttribute 訊息 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d738cf15ebe734cb74e553f38f6eb26af17e8cfd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542307"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041:必須提供 ObsoleteAttribute 訊息
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|類別|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 類型或成員是使用 <xref:System.ObsoleteAttribute?displayProperty=fullName> 未指定其屬性的屬性來標記 <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 <xref:System.ObsoleteAttribute>用來標示已取代的程式庫類型和成員。 程式庫取用者應避免使用標示為已淘汰的任何類型或成員。 這是因為它可能不受支援，而且最終會從程式庫的較新版本中移除。 當編譯使用標記的類型或成員時 <xref:System.ObsoleteAttribute> ， <xref:System.ObsoleteAttribute.Message%2A> 會顯示內容（attribute）的屬性（property）。 以便提供使用者有關過時類型或成員的資訊。 這項資訊通常包含程式庫設計工具支援過時類型或成員的時間長度，以及使用的慣用取代。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將參數新增至此函式 `message` <xref:System.ObsoleteAttribute> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則中的警告，因為 <xref:System.ObsoleteAttribute.Message%2A> 屬性會提供有關過時類型或成員的重要資訊。

## <a name="example"></a>範例
 下列範例顯示已正確宣告的過時成員 <xref:System.ObsoleteAttribute> 。

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.ObsoleteAttribute?displayProperty=fullName>

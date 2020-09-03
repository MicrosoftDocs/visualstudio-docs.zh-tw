---
title: CA1038：枚舉器應該是強型別 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e660b1af58dca8d0d69ce2844076382c4a5a1f12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548261"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038:列舉程式應該是強類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的型別 <xref:System.Collections.IEnumerator?displayProperty=fullName> 會執行，但不會提供屬性的強型別版本 <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> 。 衍生自下列類型的型別不受此規則所規範：

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>規則描述
 這項規則需要的實值 <xref:System.Collections.IEnumerator> 也會提供屬性的強型別版本， <xref:System.Collections.IEnumerator.Current%2A> 讓使用者在使用介面所提供的功能時，不需要將傳回值轉換成強型別。 這項規則假設 implements 的型別 <xref:System.Collections.IEnumerator> 包含的型別實例的集合比更強 <xref:System.Object> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請明確地執行介面屬性 (將它宣告為 `IEnumerator.Current`) 。 加入屬性的公用強型別版本（宣告為 `Current` ），並讓它傳回強型別物件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當您執行以物件為基礎的列舉值搭配以物件為基礎的集合（例如二進位樹狀結構）時，請隱藏此規則的警告。 擴充新集合的類型將會定義強型別列舉值，並公開強型別屬性。

## <a name="example"></a>範例
 下列範例示範執行強型別型別的正確方式 <xref:System.Collections.IEnumerator> 。

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1035:ICollection 的實作有強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039:清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

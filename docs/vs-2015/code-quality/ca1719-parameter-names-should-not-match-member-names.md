---
title: CA1719：參數名稱不應與成員名稱相符 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5024d2ddb7f31593c8eaedfc2fb421b4a0e9b0a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545362"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719:參數名稱不應該和成員名稱相符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|類別|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見成員的名稱會與它的其中一個參數的名稱相符，以不區分大小寫的比較。

## <a name="rule-description"></a>規則描述
 參數名稱應該要能傳達參數的意義，而成員名稱應該要能傳達成員的意義。 兩者相同屬罕見的設計。 如果將參數命名為與成員名稱相同的名稱，則不僅會不容易了解，也會讓程式庫難以使用。

## <a name="how-to-fix-violations"></a>如何修正違規
 請選取不符合成員名稱的參數名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 針對新的開發，在您必須隱藏此規則的警告的情況下，不會發生任何已知的狀況。 針對運送媒體櫃，您可能必須隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707:識別項名稱不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

---
title: CA1052：靜態預留位置類型應該是密封的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 75498be48e5ed4e723a95c5193001720db878458
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668893"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052：靜態預留位置類型應該為密封的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型只包含靜態成員，而且不是使用[sealed](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) （[NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)）修飾詞宣告的。

## <a name="rule-description"></a>規則描述
 此規則假設僅包含靜態成員的類型不是為了繼承而設計，因為該類型不會提供可在衍生類型中覆寫的任何功能。 不想要繼承的類型應該使用 `sealed` 修飾詞加以標記，以禁止其作為基底類型使用。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將類型標記為 `sealed`。 如果您的目標是 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 或更早版本，則較好的方法是將類型標記為 `static`。 如此一來，您就不需要宣告私用函式來防止建立類別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有當類型設計為要繼承時，才隱藏此規則的警告。 缺少 `sealed` 修飾詞，會建議型別相當適合做為基底型別。

## <a name="example-of-a-violation"></a>違規的範例

### <a name="description"></a>描述
 下列範例顯示違反規則的類型。

### <a name="code"></a>程式碼
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>使用靜態修飾詞修正

### <a name="description"></a>描述
 下列範例顯示如何使用 `static` 修飾詞來標記類型，以修正此規則的違規。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1053：靜態預留位置類型不應該包含建構函式](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)

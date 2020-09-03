---
title: CA1052：靜態預留位置類型應該為密封的Microsoft Docs
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
ms.openlocfilehash: 14231cc4dcde5aed5cabc2d8a6172a002c0ba6bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539746"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052:靜態預留位置類型應該為密封的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的型別只包含靜態成員，且不會使用 [sealed](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) 修飾詞來宣告。

## <a name="rule-description"></a>規則描述
 這項規則假設只包含靜態成員的型別不會被繼承，因為該型別不提供任何可在衍生類型中覆寫的功能。 不打算繼承的類型應該 `sealed` 以修飾詞標記，以禁止其作為基底類型使用。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將類型標示為 `sealed` 。 如果您是 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 以2.0 或更早版本為目標，更好的方法是將類型標示為 `static` 。 如此一來，您就不用宣告私用的函式來防止建立類別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有當型別設計為繼承時，才會隱藏此規則的警告。 缺少 `sealed` 修飾詞會建議類型可做為基底類型。

## <a name="example-of-a-violation"></a>違規範例

### <a name="description"></a>說明
 下列範例顯示違反規則的類型。

### <a name="code"></a>程式碼
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>使用 Static 修飾詞修正

### <a name="description"></a>說明
 下列範例顯示如何使用修飾詞來標記類型，以修正此規則的違規 `static` 。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1053:靜態預留位置類型不應該包含建構函式](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)

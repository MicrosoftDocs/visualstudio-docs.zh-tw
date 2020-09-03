---
title: CA2104：不要宣告唯讀的可變動參考型別 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ff42cc2b8543fe8e1cf980a3574ae15922febf9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521039"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104:不要宣告唯讀的可變動參考類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|類別|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見類型包含了可變動參考類型的外部可見唯讀欄位。

## <a name="rule-description"></a>規則描述
 可變動類型是可以修改執行個體資料的類型。 <xref:System.Text.StringBuilder?displayProperty=fullName>類別是可變動參考型別的範例。 它包含可變更類別實例值的成員。 不可變的參考型別範例是 <xref:System.String?displayProperty=fullName> 類別。 在具現化之後，它的值永遠不會變更。

 C # 中的唯讀修飾詞 ([readonly](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) 、 [readonly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) in 和 c + + 中的 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318)) 在 c + + 中的參考型別字段 (指標) 防止該欄位被不同的參考型別實例所取代。 不過，此修飾詞不會防止欄位的實例資料透過參考型別進行修改。

 唯讀陣列欄位不會套用此規則，而是會導致違反 [CA2105：陣列欄位不應該是唯讀](../code-quality/ca2105-array-fields-should-not-be-read-only.md) 規則。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除唯讀修飾詞，或者，如果可接受中斷性變更，請以不可變的型別取代該欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果欄位類型是不可變的，則可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示造成此規則違規的欄位宣告。

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]

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
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521039"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104:不要宣告唯讀的可變動參考類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|類別|Microsoft.Security|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 外部可見類型包含了可變動參考類型的外部可見唯讀欄位。

## <a name="rule-description"></a>規則描述
 可變動類型是可以修改執行個體資料的類型。 <xref:System.Text.StringBuilder?displayProperty=fullName>類別是可變參考型別的範例。 它包含可以變更類別實例值的成員。 類別是不可變參考型別的範例 <xref:System.String?displayProperty=fullName> 。 在具現化之後，其值永遠不會變更。

 參考型別字段（c # 中的 readonly）的唯讀修飾[詞（在](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4)c # 中為 readonly，在 c + + 中為[readonly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) ） [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 會防止欄位被參考型別的不同實例所取代。 [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) 不過，修飾詞不會防止欄位的實例資料透過參考型別進行修改。

 唯讀陣列欄位不受此規則的規範，而是會造成 CA2105 的違規[：陣列欄位不應為唯讀](../code-quality/ca2105-array-fields-should-not-be-read-only.md)規則。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請移除唯讀的修飾詞，如果可以接受中斷性變更，請將欄位取代為不可變的類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果欄位類型是不可變的，您可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示導致此規則違規的欄位宣告。

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]

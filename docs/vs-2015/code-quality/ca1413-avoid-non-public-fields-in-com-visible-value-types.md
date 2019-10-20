---
title: CA1413：避免在 COM 可見實數值型別中的非公用欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7d66c2c52b6ee7f7d1d2fbbd461ca8c1251ce13d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652705"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413：避免在 COM 可見的實值類型中使用非公用欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Category|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 特別標示為「元件物件模型（COM）可見」的實值型別會宣告非公用實例欄位。

## <a name="rule-description"></a>規則描述
 COM 可見實值類型的非公用執行個體欄位對 COM 用戶端而言是可見的。 請參閱欄位內容，以取得不應公開的資訊，或將會有非預期的設計或安全性效果。

 根據預設，COM 可以看到所有公用實數值型別。 不過，若要減少誤報，此規則需要明確陳述類型的 COM 可見度。 包含的元件必須標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 設定為 `false`，而且類型必須標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 設定為 `true`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，並將欄位保留為隱藏狀態，請將實數值型別變更為參考型別，或從類型中移除 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果可以接受欄位的公開曝光，則可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>請參閱
 [與未受管理](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)的程式碼互通，[符合用於互通的 .net 類型](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)

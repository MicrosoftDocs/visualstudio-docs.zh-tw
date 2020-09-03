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
ms.openlocfilehash: 1054330b26cf145ebcbc943a56dc699fe793999f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548456"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413:避免在 COM 可見實值類型中使用非公用欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|類別|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 明確標示為元件物件模型可見的實數值型別 (COM) 宣告非公用實例欄位。

## <a name="rule-description"></a>規則描述
 COM 可見實值類型的非公用執行個體欄位對 COM 用戶端而言是可見的。 請檢查欄位的內容，以取得不應該公開的資訊，或是會有非預期的設計或安全性效果。

 根據預設，COM 可以看到所有公用實數值型別。 不過，若要減少誤報，此規則需要明確陳述型別的 COM 可見度。 包含的元件必須標記 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 為， `false` 而且類型必須標記為，而且必須將 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 設為 `true` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形並讓欄位保持隱藏，請將數值型別變更為參考型別，或 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 從型別中移除該屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果可以接受欄位的公開公開，就可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1407:避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017:組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱
 [與未受管理的程式碼交互操作，](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [以符合互通的 .net 類型](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)

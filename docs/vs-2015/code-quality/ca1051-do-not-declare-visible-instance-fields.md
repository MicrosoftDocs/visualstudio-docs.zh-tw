---
title: CA1051：不要宣告可見的實例欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 41332ab7d729f7b2187ccace6b05fe2d17763a0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672524"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051：不要宣告可見的執行個體欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的類型具有外部可見的實例欄位。

## <a name="rule-description"></a>規則描述
 欄位的主要用法應該是當做實作詳細資料。 欄位應該 `private` 或 `internal`，而且應該使用屬性來公開。 存取欄位的方式很簡單，因為它是用來存取欄位，而屬性存取子中的程式碼可能會隨著類型的擴充功能而變更，而不會引入中斷性變更。 只傳回私用或內部欄位值的屬性，已經過優化，可在存取欄位時進行比對。在屬性上使用外部可見的欄位，幾乎不會有太大的效能提升。

 外部可見指的是 `public`、`protected` 和 `protected internal` （`Protected` 中的 `Public`、`Protected Friend` 和 Visual Basic）存取範圍層級。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將欄位 `private` 或 `internal`，並使用外部可見的屬性加以公開。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 外部可見欄位不會提供屬性無法使用的任何好處。 此外，公用欄位無法受到[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)的保護。 請參閱[CA2112：安全的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型（`BadPublicInstanceFields`）。 `GoodPublicInstanceFields` 會顯示已更正的程式碼。

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2112：受保護類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>請參閱
 [連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)

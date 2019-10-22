---
title: CA1034：不應該看到嵌套的類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 33e7ea6aaefcaf5b6cbf0bf8c52ade0b9e68a549
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661860"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034：巢狀類型不應為可見
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的類型包含外部可見的類型宣告。 此規則會豁免嵌套列舉和受保護的類型。

## <a name="rule-description"></a>規則描述
 巢狀型別是在另一個類型的範圍內宣告的類型。 巢狀型別適用于封裝包含類型的私用實作為詳細資料。 因為有這樣的用途，所以巢狀類型不應為外部可見的。

 請不要針對邏輯群組使用外部可見的巢狀型別，或避免名稱衝突;請改用命名空間。

 巢狀型別包含成員存取範圍的概念，而有些程式設計人員並不清楚瞭解。

 在預先自訂的情況下，可在子類別和巢狀型別中使用受保護的類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果您不想要讓巢狀型別成為外部可見的，請變更類型的存取範圍。 否則，請從其父系移除巢狀型別。 如果嵌套的目的是要將巢狀型別分類，請改用命名空間來建立階層。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]

---
title: CA1034:巢狀類型不應該為可見的
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ead932af202bd1a44464025a1b09baa698acb7b1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236041"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034:巢狀類型不應該為可見的

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|分類|Microsoft.Design|
|重大變更|中斷|

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

[!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
[!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]
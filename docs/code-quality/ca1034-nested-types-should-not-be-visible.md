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
ms.openlocfilehash: fb01065fed41a30f26e15d7295fabc03fb3f1f4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779074"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034:巢狀類型不應該為可見的

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

外部可見的型別包含為外部可見的型別宣告。 巢狀的列舉與受保護的類型是 免套用此規則。

## <a name="rule-description"></a>規則描述
 巢狀型別是另一種類型的範圍內宣告的類型。 巢狀型別可用於封裝為包含類型的私用實作詳細資料。 因為有這樣的用途，所以巢狀類型不應為外部可見的。

 邏輯群組，或避免發生名稱衝突，請不要使用外部可見的巢狀的類型相反地，使用命名空間。

 巢狀型別包含成員存取範圍，某些程式設計人員不清楚地了解的概念。

 受保護的類型可以用於子類別以及進階的自訂案例中的巢狀型別。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果您不想要為外部可見的巢狀型別，變更型別的存取範圍。 否則，從其父代移除巢狀型別。 如果巢狀的目的是要分類的巢狀的類型，請改為建立階層中使用的命名空間。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。

 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]
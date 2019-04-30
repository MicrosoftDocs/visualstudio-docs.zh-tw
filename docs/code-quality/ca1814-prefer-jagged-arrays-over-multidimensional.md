---
title: CA1814:建議使用不規則陣列取代多維陣列
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6d3dc26964a62c952b9c8d18c710e6163bf8ab08
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796913"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814:建議使用不規則陣列取代多維陣列

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|分類|Microsoft.Performance|
|中斷變更|中斷|

## <a name="cause"></a>原因
 成員宣告為多維陣列。

## <a name="rule-description"></a>規則描述
 不規則陣列是一種陣列，其元素也是陣列。 組成元素的陣列大小可以不相同，對於某些資料集而言較不會浪費空間。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將多維陣列的內容變更為不規則陣列。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 此規則的警告如果隱藏多維陣列不會浪費空間。

## <a name="example"></a>範例
 下列範例示範宣告不規則陣列和多維度陣列。

 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]
---
title: CA1814：建議使用不規則陣列取代多維陣列
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cedac542d003ccc89357f3a01e2f167a2471a128
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814：建議使用不規則陣列取代多維陣列
|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|分類|Microsoft.Performance|
|中斷變更|中斷|

## <a name="cause"></a>原因
 成員宣告為多維度陣列。

## <a name="rule-description"></a>規則描述
 不規則陣列是一種陣列，其元素也是陣列。 組成元素的陣列大小可以不相同，對於某些資料集而言較不會浪費空間。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將多維陣列的內容變更為不規則的陣列。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果多維度陣列不會浪費空間，請隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示不規則和多維度陣列的宣告。

 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]
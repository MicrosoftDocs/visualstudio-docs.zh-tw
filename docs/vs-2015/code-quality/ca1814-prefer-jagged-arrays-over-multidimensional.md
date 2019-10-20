---
title: CA1814：偏好多維度的不規則陣列 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f0ac183321bd2a3070b1f1ddc54402b74c8fb823
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668409"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814：建議使用不規則陣列取代多維陣列
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Category|Microsoft。效能|
|中斷變更|中斷|

## <a name="cause"></a>原因
 成員會宣告為多維陣列。

## <a name="rule-description"></a>規則描述
 不規則陣列是一種陣列，其元素也是陣列。 組成元素的陣列大小可以不相同，對於某些資料集而言較不會浪費空間。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將多維陣列變更為不規則陣列。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果多維陣列不會浪費空間，請隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示不規則和多維陣列的宣告。

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]

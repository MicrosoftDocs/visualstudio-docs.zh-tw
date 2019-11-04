---
title: CA1800:不要不必要地轉換 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 466309cef8905faa9b659e2d3652975d815767fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663097"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800:不要執行不必要的轉換
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|分類|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 方法會對其中一個引數或區域變數執行重複的轉換。 如需此規則的完整分析，必須使用偵錯工具建立已測試的元件，而且必須要有相關聯的程式資料庫（.pdb）檔案。

## <a name="rule-description"></a>規則描述
 重複轉型會降低效能，尤其是在精簡型態的反覆運算陳述式中執行轉型時。 對於明確的重複轉換作業，請將轉換的結果儲存在本機變數中，並使用區域變數，而不是重複的轉換作業。

 如果在C#執行實際轉換之前，使用 `is` 運算子來測試轉換是否成功，請考慮改為測試 `as` 運算子的結果。 這會提供相同的功能，而不會有 `is` 運算子所執行的隱含轉換作業。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請修改方法執行，將轉換作業的數目降至最低。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告，或完全忽略此規則（如果效能不是問題）。

## <a name="example"></a>範例
 下列範例顯示使用C# `is` 運算子來違反規則的方法。 第二種方法會藉由將 `is` 運算子取代為對 `as` 運算子之結果的測試來滿足規則，這會減少從二到一次反覆運算的轉換作業數目。

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>範例
 下列範例顯示的方法 `start_Click`，其中包含多個重複的明確轉換（違反規則）和方法（`reset_Click`），其會將轉換儲存在本機變數中以滿足規則。

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>另請參閱
 [依](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e)[情況](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)

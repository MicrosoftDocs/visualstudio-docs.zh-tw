---
title: CA1800：不必要轉換 |Microsoft Docs
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
ms.openlocfilehash: 757d66ef719b3a1f39a9164dfd50ce1fcf8799db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547793"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800:不要執行不必要的轉換
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|類別|Microsoft。效能|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法會在其一個引數或區域變數上執行重複的轉換。 若要透過此規則進行完整分析，您必須使用偵錯工具來建立已測試的元件，以及相關聯的程式資料庫 ( .pdb) 檔必須可用。

## <a name="rule-description"></a>規則描述
 重複轉型會降低效能，尤其是在精簡型態的反覆運算陳述式中執行轉型時。 對於明確的重複轉換作業，請將轉換的結果儲存在區域變數中，然後使用本機變數，而不是重複的轉換作業。

 如果使用 c # `is` 運算子來測試轉換是否會在執行實際轉換之前成功，請考慮改為測試運算子的結果 `as` 。 這會提供相同的功能，而不會有運算子所執行的隱含轉換操作 `is` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請修改方法的執行，以將轉換作業的數目降至最低。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則中的警告，如果效能不是問題，則完全忽略規則。

## <a name="example"></a>範例
 下列範例顯示使用 c # 運算子違反規則的方法 `is` 。 第二個方法會將運算子取代為 `is` 運算子結果的測試，以滿足規則，這會將每個反復專案的 `as` cast 作業數目減少為1。

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>範例
 下列範例會示範一個方法， `start_Click` 這個方法具有多個重複的明確轉換（違反規則）和一個方法， `reset_Click` 此方法會將轉換儲存在本機變數中，以滿足規則。

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>另請參閱
 [同樣](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)

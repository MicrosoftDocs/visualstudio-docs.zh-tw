---
title: CA1800:執行不必要的轉型 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 49ffc66b1b7047c7b88664ac0c5198fbd51c51c6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682080"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800:不要執行不必要的轉換
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因
 方法會執行其中一個引數或區域變數重複轉型。 此規則的完整分析，必須使用 偵錯資訊建置測試的組件以及相關聯的程式資料庫 (.pdb) 檔案必須能夠使用。

## <a name="rule-description"></a>規則描述
 重複轉型會降低效能，尤其是在精簡型態的反覆運算陳述式中執行轉型時。 對於明確重複的轉換作業，轉型將結果儲存在本機變數，並使用本機變數，而不是重複轉型作業。

 如果 C#`is`運算子用來測試是否轉型成功執行實際的轉型之前, 測試的結果，請考慮`as`運算子改。 這會提供相同的功能，而不由執行隱含轉型作業`is`運算子。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，修改的方法實作的型別轉換作業數目降到最低。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 則隱藏這項規則的警告，或完全忽略規則如果效能不成問題。

## <a name="example"></a>範例
 下列範例示範的方法，使用 C# 中違反規則`is`運算子。 第二種方法來取代符合規則`is`運算子的結果對測試加`as`運算子，就會減少每個反覆項目至其中的兩個型別轉換作業的數目。

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>範例
 下列範例示範的方法中， `start_Click`，具有多個重複的明確轉型規則和方法，這會違反`reset_Click`，這會滿足規則，藉由將轉換儲存在本機變數。

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>另請參閱
 [as](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)

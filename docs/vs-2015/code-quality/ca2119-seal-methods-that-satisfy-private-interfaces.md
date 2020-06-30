---
title: CA2119：密封滿足私用介面的方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0afa6950a6ad876cdcfdcc1a56dd143422b9d44f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544348"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119:密封方法以滿足私用介面的要求
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 可繼承的公用類型會提供 `internal` （ `Friend` 在 Visual Basic）介面中可覆寫的方法執行。

## <a name="rule-description"></a>規則描述
 介面方法具有公用存取範圍，無法由實作為類型變更。 內部介面會建立一個不打算在定義介面之元件外部執行的合約。 使用（在 Visual Basic 中）修飾詞來實作為內部介面方法的公用類型，可 `virtual` `Overridable` 讓該方法由元件外部的衍生類型覆寫。 如果定義元件中的第二個類型呼叫方法，並預期僅供內部使用的合約，則在執行外部元件中的覆寫方法時，行為可能會受到危害。 這會產生安全性弱點。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用下列其中一項，防止在元件外部覆寫方法：

- 建立宣告類型 `sealed` （ `NotInheritable` 在 Visual Basic 中）。

- 將宣告類型的存取範圍變更為 `internal` （ `Friend` 在 Visual Basic 中）。

- 從宣告類型移除所有公用的函式。

- 在不使用修飾詞的情況下，執行方法 `virtual` 。

- 明確地執行方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果在仔細審查之後，不會有任何安全性問題存在，如果在元件外部覆寫該方法，就可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示 `BaseImplementation` 違反此規則的類型。

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>範例
 下列範例會利用上一個範例的虛擬方法執行。

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>另請參閱
 [介面](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)[介面](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)

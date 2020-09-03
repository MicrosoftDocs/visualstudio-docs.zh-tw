---
title: CA1011：考慮以參數傳遞基底類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f689dfd6c1d39bbd03d522a33ed8c5639a3da9f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545479"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011:建議將基底類型當作參數傳遞
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法宣告包含的型式參數是衍生型別，而且方法只會呼叫參數基底類型的成員。

## <a name="rule-description"></a>規則描述
 當方法宣告將基底類型指定為參數，則從此基底類型衍生的任何類型都可以當做對應引數傳遞給方法。 在方法主體內使用引數時，所執行的特定方法取決於引數的類型。 如果衍生類型所提供的其他功能不是必要的，使用基底類型可讓您更廣泛地使用方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將參數的類型變更為其基底類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告是安全的

- 如果方法需要衍生類型所提供的特定功能

   \- 或 -

- 若要強制只將衍生型別或更多衍生型別傳遞給方法。

  在這些情況下，因為編譯器和執行時間所提供的強型別檢查，所以程式碼會更健全。

## <a name="example"></a>範例
 下列範例會顯示一個方法， `ManipulateFileStream` 這個方法只能用於 <xref:System.IO.FileStream> 違反此規則的物件。 第二個方法是 `ManipulateAnyStream` 使用來取代參數來滿足規則 <xref:System.IO.FileStream> <xref:System.IO.Stream> 。

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1059:成員不應該公開特定的具象類型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)

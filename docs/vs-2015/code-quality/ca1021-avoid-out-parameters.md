---
title: CA1021：避免 out 參數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f8f1b0c17fe9135bf534b9f30bf4e54c8c286ada
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546688"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021:避免使用 out 參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|類別|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用類型中的公用或受保護方法具有 `out` 參數。

## <a name="rule-description"></a>規則描述
 以傳址方式傳遞類型（使用 `out` 或 `ref` ）需要使用指標的經驗、瞭解實數值型別和參考型別之間的差異，以及處理具有多個傳回值的方法。 此外，和參數之間的差異也 `out` `ref` 無法廣泛瞭解。

 當以傳址方式傳遞參考型別時，方法會使用參數來傳回物件的不同實例。 以傳址方式傳遞參考型別，也稱為使用雙重指標、指標指標或雙重間接取值。 藉由使用預設的呼叫慣例（以傳值方式傳遞），接受參考型別的參數已經收到物件的指標。 指標（而不是其指向的物件）會以傳值方式傳遞。 [以傳值方式傳遞] 表示方法無法變更指標，使其指向參考型別的新實例。 不過，它可以變更它所指向之物件的內容。 對於大部分的應用程式而言，這是足夠的，並且會產生所需的行為。

 如果方法必須傳回不同的實例，請使用方法的傳回值來完成這項操作。 請參閱 <xref:System.String?displayProperty=fullName> 類別，以瞭解在字串上運作並傳回字串之新實例的各種方法。 使用此模型時，呼叫端必須決定是否保留原始物件。

 雖然傳回值是常見且經常使用的，但和參數的正確應用 `out` `ref` 需要中繼設計和編碼技能。 設計一般物件的程式庫架構師不應預期使用者會使用 `out` 或參數來主控 `ref` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則因實值型別而造成的違規，請讓方法傳回物件做為其傳回值。 如果方法必須傳回多個值，請重新設計，以傳回保留值之物件的單一實例。

 若要修正此規則因參考型別而造成的違規，請確定所需的行為是傳回參考的新實例。 如果是，此方法應該使用其傳回值來執行此動作。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告。 不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
 下列程式庫顯示類別的兩個實作為，其會產生對使用者意見反應的回應。 第一個執行（ `BadRefAndOut` ）會強制程式庫使用者管理三個傳回值。 第二個實 `RedesignedRefAndOut` 作為（）藉由傳回將 `ReplyData` 資料當做單一單位來管理的容器類別（）實例，來簡化使用者體驗。

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>範例
 下列應用程式說明使用者的體驗。 重新設計的程式庫（ `UseTheSimplifiedClass` 方法）呼叫較為簡單，而且方法所傳回的資訊很容易管理。 這兩個方法的輸出完全相同。

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>範例
 下列範例程式庫說明如何 `ref` 使用參考型別的參數，並顯示更好的方法來執行此功能。

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>範例
 下列應用程式會呼叫程式庫中的每個方法，以示範此行為。

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 此範例會產生下列輸出。

 **變更以傳值方式傳遞的指標：** 
**12345** 
**12345** 
**變更以傳址方式傳遞的指標：** 
**12345** 
**12345 ABCDE** 
**以傳回值傳遞：** 
**12345 ABCDE**
## <a name="try-pattern-methods"></a>試用模式方法

### <a name="description"></a>描述
 執行** \<Something> Try**模式的方法（例如 <xref:System.Int32.TryParse%2A?displayProperty=fullName> ）不會引發這個違規。 下列範例顯示的結構（實值型別）會執行 <xref:System.Int32.TryParse%2A?displayProperty=fullName> 方法。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1045:不要以傳址方式傳遞類型](../code-quality/ca1045-do-not-pass-types-by-reference.md)

---
title: CA1045：不要以傳址方式傳遞類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 259e0d17ccf71518759ac192ee87a6ef5b921b23
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668285"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045：不要以傳址方式傳遞類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用類型中的公用或受保護方法具有 `ref` 參數，其採用基本類型、參考型別或不是其中一個內建類型的實數值型別。

## <a name="rule-description"></a>規則描述
 以傳址方式傳遞類型（使用 `out` 或 `ref`）需要使用指標的經驗、瞭解實數值型別和參考型別之間的差異，以及處理具有多個傳回值的方法。 此外，`out` 和 `ref` 參數之間的差異並不廣泛瞭解。

 當以傳址方式傳遞參考型別時，方法會使用參數來傳回物件的不同實例。 （以傳址方式傳遞參考型別也稱為使用 double 指標、指標指標或雙重間接取值）。使用預設的呼叫慣例（以傳值方式傳遞），接受參考型別的參數已經接收物件的指標。 指標（而不是其指向的物件）會以傳值方式傳遞。 以傳值方式傳遞表示方法無法變更指標，使其指向參考型別的新實例，但是可以變更它所指向之物件的內容。 對於大部分的應用程式而言，這是足夠的，並且會產生您想要的行為。

 如果方法必須傳回不同的實例，請使用方法的傳回值來完成這項操作。 如需在字串上運作並傳回字串之新實例的各種方法，請參閱 <xref:System.String?displayProperty=fullName> 類別。 藉由使用此模型，它會留給呼叫端決定是否保留原始物件。

 雖然傳回值是常見且經常使用的，但 `out` 和 `ref` 參數的正確應用程式需要中繼設計和編碼技能。 設計一般物件的程式庫架構師不應預期使用者會使用 `out` 或 `ref` 參數來主控。

> [!NOTE]
> 當您使用大型結構的參數時，複製這些結構所需的其他資源可能會在您以傳值方式傳遞時造成效能影響。 在這些情況下，您可以考慮使用 `ref` 或 `out` 參數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則因實值型別而造成的違規，請讓方法傳回物件做為其傳回值。 如果方法必須傳回多個值，請重新設計，以傳回保留值之物件的單一實例。

 若要修正此規則因參考型別而造成的違規，請確定您想要的行為是傳回參考的新實例。 如果是，此方法應該使用其傳回值來執行此動作。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告;不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
 下列程式庫顯示類別的兩個實作為，其會產生對使用者意見反應的回應。 第一個執行（`BadRefAndOut`）會強制程式庫使用者管理三個傳回值。 第二個實作為（`RedesignedRefAndOut`）藉由傳回將資料當做單一單位來管理的容器類別實例（`ReplyData`），來簡化使用者體驗。

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>範例
 下列應用程式說明使用者的體驗。 重新設計的程式庫（`UseTheSimplifiedClass` 方法）的呼叫更簡單，而且方法所傳回的資訊很容易管理。 這兩個方法的輸出完全相同。

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>範例
 下列範例程式庫說明如何使用參考型別的 `ref` 參數，並顯示更好的方法來執行這項功能。

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
**12345 ABCDE** 1**以傳回值傳遞：** 3**12345 ABCDE**
## <a name="related-rules"></a>相關規則
 [CA1021：避免使用 out 參數](../code-quality/ca1021-avoid-out-parameters.md)

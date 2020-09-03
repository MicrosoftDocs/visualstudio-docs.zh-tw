---
title: CA1021：避免輸出參數 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546688"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021:避免使用 out 參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用類型中的公用或受保護方法具有 `out` 參數。

## <a name="rule-description"></a>規則描述
 使用或) 以傳址方式傳遞類型 (`out` `ref` 需要使用指標的經驗、瞭解實值型別和參考型別有何不同，以及處理具有多個傳回值的方法。 此外，和參數之間的差異 `out` 並 `ref` 不大易懂。

 當參考型別以傳址方式傳遞時，方法會使用參數來傳回不同的物件實例。 以傳址方式傳遞參考型別也稱為使用雙指標、指標指標或雙間接取值。 使用以傳值方式傳遞的預設呼叫慣例，將採用參考型別的參數已經接收到物件的指標。 指標（而不是它所指向的物件）是以傳值方式傳遞。 [以傳值方式傳遞] 表示方法無法變更指標，使其指向參考型別的新實例。 不過，它可以變更它所指向之物件的內容。 對於大部分的應用程式而言，這是足夠的，並且會產生所需的行為。

 如果方法必須傳回不同的實例，請使用方法的傳回值來完成此動作。 請參閱 <xref:System.String?displayProperty=fullName> 類別，以取得在字串上操作的各種方法，並傳回字串的新實例。 使用此模型時，呼叫端必須決定是否保留原始物件。

 雖然傳回值很常見且經常使用，但正確的 `out` 和參數應用程式 `ref` 需要中繼設計和程式碼撰寫技能。 設計一般物件的程式庫架構設計人員不應預期使用者使用 `out` 或 `ref` 參數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正由實值型別造成的這個規則違規，請讓方法將物件傳回做為其傳回值。 如果方法必須傳回多個值，請重新設計它，以傳回保存值之物件的單一實例。

 若要修正因參考型別而造成此規則的違規，請確定所需的行為是傳回參考的新實例。 如果是，則方法應該使用它的傳回值來執行這項作業。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告是安全的。 不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
 下列程式庫顯示類別的兩個實作為，可產生對使用者意見反應的回應。 第一個執行 (`BadRefAndOut`) 會強制程式庫使用者管理三個傳回值。 第二個執行 (`RedesignedRefAndOut`) 藉由將容器類別的實例（ (以 `ReplyData` 單一單位來管理資料的) ）傳回，以簡化使用者體驗。

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>範例
 下列應用程式說明使用者的體驗。 呼叫重新設計的程式庫 (`UseTheSimplifiedClass` 方法) 更為簡單，而且方法所傳回的資訊很容易管理。 這兩種方法的輸出完全相同。

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

### <a name="description"></a>說明
 執行** \<Something> Try**模式的方法（例如 <xref:System.Int32.TryParse%2A?displayProperty=fullName> ）不會引發這個違規。 下列範例顯示的結構 (值型別) 來執行 <xref:System.Int32.TryParse%2A?displayProperty=fullName> 方法。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1045:不要以傳址方式傳遞類型](../code-quality/ca1045-do-not-pass-types-by-reference.md)

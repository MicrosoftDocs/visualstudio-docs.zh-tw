---
title: CA1045：不以傳址方式傳遞類型 |Microsoft Docs
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
ms.openlocfilehash: dad2f90a51a4247a4c111ef51e85a28ba1a118ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548469"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045:不要以傳址方式傳遞類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用類型中的公用或受保護的方法具有 `ref` 參數，該參數會採用基本型別、參考型別，或非其中一個內建類型的實值型別。

## <a name="rule-description"></a>規則描述
 使用或) 以傳址方式傳遞類型 (`out` `ref` 需要使用指標的經驗、瞭解實值型別和參考型別有何不同，以及處理具有多個傳回值的方法。 此外，和參數之間的差異 `out` 並 `ref` 不大易懂。

 當參考型別以傳址方式傳遞時，方法會使用參數來傳回不同的物件實例。  (以傳址方式傳遞參考型別也稱為使用雙精度指標、指標指標或雙間接取值。 ) 使用以傳值方式傳遞的預設呼叫慣例，則是採用參考型別的參數已經接收到物件的指標。 指標（而不是它所指向的物件）是以傳值方式傳遞。 以傳值方式傳遞表示方法無法變更指標，使其指向參考型別的新實例，但可以變更它所指向之物件的內容。 對於大部分的應用程式而言，這是足夠的，並且會產生您想要的行為。

 如果方法必須傳回不同的實例，請使用方法的傳回值來完成此動作。 請參閱 <xref:System.String?displayProperty=fullName> 類別，以取得在字串上操作的各種方法，並傳回字串的新實例。 藉由使用此模型，呼叫端會將其保留給呼叫端，以決定是否要保留原始物件。

 雖然傳回值很常見且經常使用，但正確的 `out` 和參數應用程式 `ref` 需要中繼設計和程式碼撰寫技能。 設計一般物件的程式庫架構設計人員不應預期使用者使用 `out` 或 `ref` 參數。

> [!NOTE]
> 當您使用大型結構的參數時，複製這些結構所需的其他資源可能會在您以傳值方式傳遞時產生效能影響。 在這些情況下，您可以考慮使用 `ref` 或 `out` 參數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正由實值型別造成的這個規則違規，請讓方法將物件傳回做為其傳回值。 如果方法必須傳回多個值，請重新設計它，以傳回保存值之物件的單一實例。

 若要修正由參考型別所造成的此規則違規，請確定您想要的行為會傳回新的參考實例。 如果是，則方法應該使用它的傳回值來執行這項作業。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告是安全的;不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
 下列程式庫顯示類別的兩個實作為，可產生對使用者意見反應的回應。 第一個執行 (`BadRefAndOut`) 會強制程式庫使用者管理三個傳回值。 第二個執行 (`RedesignedRefAndOut`) 藉由將容器類別的實例（ (以 `ReplyData` 單一單位來管理資料的) ）傳回，以簡化使用者體驗。

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>範例
 下列應用程式說明使用者的體驗。 呼叫重新設計的程式庫 (`UseTheSimplifiedClass` 方法) 更為簡單，而且可以輕鬆地管理方法所傳回的資訊。 這兩種方法的輸出完全相同。

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>範例
 下列範例程式庫說明如何 `ref` 使用參考型別的參數，並顯示更好的方法來執行這項功能。

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
## <a name="related-rules"></a>相關規則
 [CA1021:避免使用 out 參數](../code-quality/ca1021-avoid-out-parameters.md)

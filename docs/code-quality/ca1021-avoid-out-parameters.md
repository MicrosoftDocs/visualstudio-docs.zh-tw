---
title: "CA1021： 避免使用 out 參數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f8748b9943f3a3aa31a6585de07bdc9eff3cc5ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021：避免使用 out 參數
|||  
|-|-|  
|TypeName|AvoidOutParameters|  
|CheckId|CA1021|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的方法中的公用型別具有`out`參數。  
  
## <a name="rule-description"></a>規則描述  
 以傳址方式傳遞類型 (使用`out`或`ref`) 需要擁有使用指標，了解實值類型和參考型別之間的差異，並處理具有多個傳回值的方法經驗。 此外，之間的差異`out`和`ref`廣泛無法辨識的參數。  
  
 當 「 傳址 」 傳遞參考類型時，方法會使用參數可傳回物件的不同執行個體。 傳址方式傳遞參考型別也稱為使用的兩個指標的指標或兩個間接取值的指標。 使用預設呼叫慣例，將傳遞 「 值 」，已接受參考類型的參數，會接收到的物件的指標。 指標，而非它所指向的物件是傳值方式傳遞。 傳遞給該方法無法變更的指標，讓它指向參考類型的新執行個體的值表示。 不過，它可以變更它所指向的物件的內容。 對於大部分應用程式這就足夠，並產生所要的行為。  
  
 如果方法必須傳回不同的執行個體，使用方法的傳回值來完成這項作業。 請參閱<xref:System.String?displayProperty=fullName>各種不同的方法，在字串上運作，並傳回字串的新執行個體的類別。 使用此模型時，呼叫端必須決定是否要保留原始物件。  
  
 雖然傳回值很常見，並且大量使用正確的應用程式的`out`和`ref`參數需要中繼設計和編碼技術。 程式庫架構設計人員負責設計的目標為一般使用者不應預期使用者熟練地運用`out`或`ref`參數。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正的起因是實值類型，此規則的違規情形，讓方法傳回的物件，當做其傳回值。 如果此方法必須傳回多個值，請將它傳回的物件，包含值的單一執行個體重新設計。  
  
 若要修正的起因是參考類型，此規則的違規情形，請確定所要的行為是要傳回的新執行個體的參考。 如果是，則方法應該使用它的傳回值，若要這樣做。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告。 不過，這項設計導致可用性問題。  
  
## <a name="example"></a>範例  
 下列程式庫顯示兩個產生的使用者意見回應的類別的實作。 首次實作 (`BadRefAndOut`) 會強制程式庫使用者管理三個傳回的值。 第二個實作 (`RedesignedRefAndOut`) 傳回的容器類別的執行個體，藉以簡化使用者經驗 (`ReplyData`) 將資料當做單一單位管理。  
  
 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]  
  
## <a name="example"></a>範例  
 下列應用程式說明使用者的經驗。 重新設計的程式庫的呼叫 (`UseTheSimplifiedClass`方法) 方法很簡單，並輕鬆地管理方法所傳回的資訊。 兩種方法的輸出是完全相同。  
  
 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]  
  
## <a name="example"></a>範例  
 下列範例程式庫將說明如何`ref`參考型別參數使用，並示範實作這項功能的較佳方式。  
  
 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]  
  
## <a name="example"></a>範例  
 下列應用程式會呼叫每個方法，示範行為文件庫中。  
  
 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]  
  
 此範例會產生下列輸出。  
  
 **變更指標的傳值方式傳遞：**  
**12345**  
**12345**  
**變更指標的傳址方式傳遞：**  
**12345**  
**12345 ABCDE**  
**傳遞所傳回的值：**  
**12345 ABCDE**   
## <a name="try-pattern-methods"></a>再試一次模式方法  
  
### <a name="description"></a>描述  
 實作方法**再試一次\<項目 >**模式，例如<xref:System.Int32.TryParse%2A?displayProperty=fullName>，不會引發這個違規。 下列範例示範結構 （實值型別），實作<xref:System.Int32.TryParse%2A?displayProperty=fullName>方法。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1045：不要以傳址方式傳遞類型](../code-quality/ca1045-do-not-pass-types-by-reference.md)
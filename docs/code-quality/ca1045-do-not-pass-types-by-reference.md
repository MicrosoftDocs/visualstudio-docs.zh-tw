---
title: CA1045： 不要依參考傳遞類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6640942827834ff1eafeecc84e1256ce3589443b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045：不要以傳址方式傳遞類型
|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的方法中的公用型別具有`ref`接受基本類型、 參考類型或實值類型的參數不是其中一個內建型別。  
  
## <a name="rule-description"></a>規則描述  
 以傳址方式傳遞類型 (使用`out`或`ref`) 需要擁有使用指標，了解實值類型和參考型別之間的差異，並處理具有多個傳回值之方法的經驗。 此外，之間的差異`out`和`ref`廣泛無法辨識的參數。  
  
 當 「 傳址 」 傳遞參考類型時，方法會使用參數可傳回物件的不同執行個體。 （傳址方式傳遞參考型別也稱為使用的兩個指標的指標或兩個間接取值的指標。）使用預設呼叫慣例，將傳遞 「 值 」，已接受參考類型的參數，會接收物件的指標。 指標，而非它所指向的物件是傳值方式傳遞。 以傳值表示此方法無法變更，讓它指向新的執行個體參考的指標類型，但可以變更它所指向的物件內容傳遞。 對於大部分應用程式這就足夠，並產生您想要的行為。  
  
 如果方法必須傳回不同的執行個體，使用方法的傳回值來完成這項作業。 請參閱<xref:System.String?displayProperty=fullName>各種不同的方法，在字串上運作，並傳回字串的新執行個體的類別。 藉由使用此模型，它就可讓呼叫端決定是否要保留原始物件。  
  
 雖然傳回值很常見，並且大量使用正確的應用程式的`out`和`ref`參數需要中繼設計和編碼技術。 程式庫架構設計人員負責設計的目標為一般使用者不應預期使用者熟練地運用`out`或`ref`參數。  
  
> [!NOTE]
>  當您以大型結構的參數，請複製這些結構所需的其他資源可能會造成效能上的影響時傳值方式傳遞。 在這些情況下，您可以考慮使用`ref`或`out`參數。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正的起因是實值類型，此規則的違規情形，讓方法傳回的物件，當做其傳回值。 如果此方法必須傳回多個值，請將它傳回的物件，包含值的單一執行個體重新設計。  
  
 若要修正問題的起因是參考類型，此規則的違規情形，請確定您想要的行為是要傳回的新執行個體的參考。 如果是，則方法應該使用它的傳回值，若要這樣做。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 安全地隱藏的警告，這項規則。不過，這項設計導致可用性問題。  
  
## <a name="example"></a>範例  
 下列程式庫顯示兩個產生的使用者意見回應的類別的實作。 首次實作 (`BadRefAndOut`) 會強制程式庫使用者管理三個傳回的值。 第二個實作 (`RedesignedRefAndOut`) 傳回的容器類別的執行個體，藉以簡化使用者經驗 (`ReplyData`) 將資料當做單一單位管理。  
  
 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## <a name="example"></a>範例  
 下列應用程式說明使用者的經驗。 重新設計的程式庫的呼叫 (`UseTheSimplifiedClass`方法) 方法很簡單，並輕鬆地管理方法所傳回的資訊。 兩種方法的輸出是完全相同。  
  
 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## <a name="example"></a>範例  
 下列範例程式庫將說明如何`ref`參考型別參數使用，以及顯示更好的方式來實作這項功能。  
  
 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## <a name="example"></a>範例  
 下列應用程式會呼叫每個方法，示範行為文件庫中。  
  
 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 此範例會產生下列輸出。  
  
 **變更指標的傳值方式傳遞：**  
**12345**  
**12345**  
**變更指標的傳址方式傳遞：**  
**12345**  
**12345 ABCDE**  
**傳遞所傳回的值：**  
**12345 ABCDE**   
## <a name="related-rules"></a>相關的規則  
 [CA1021：避免使用 out 參數](../code-quality/ca1021-avoid-out-parameters.md)
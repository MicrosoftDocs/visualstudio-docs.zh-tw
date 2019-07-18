---
title: CA1045:不要以傳址方式傳遞類型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5174d00593b44d51b5628851039b1d0a37753c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387487"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045:不要以傳址方式傳遞類型

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的方法中的公用型別具有`ref`採用基本型別、 參考型別或實值型別參數不是其中一個內建類型。

## <a name="rule-description"></a>規則描述
 傳址方式傳遞類型 (使用`out`或`ref`) 需要擁有了實值型別和參考型別之間的差異，並處理具有多個傳回值的方法的指標使用經驗。 此外，之間的差異`out`和`ref`參數不廣泛了解。

 傳遞參考型別時，「 傳址 」，方法會使用參數來傳回物件的不同執行個體。 （傳址方式傳遞參考型別也稱為使用 double 指標的指標或 double 的間接取值的指標。）使用的預設呼叫慣例，「 依值 「 通過，已接受參考類型的參數會接收物件的指標。 指標，而不將它指向，物件是傳值方式傳遞。 以傳值，表示該方法無法變更，讓它指向新的執行個體參考的指標類型，但可以變更它所指向的物件內容傳遞。 大部分的應用程式這就已足夠，並產生您想要的行為。

 如果方法必須傳回不同的執行個體，使用此方法的傳回值來完成這項作業。 請參閱<xref:System.String?displayProperty=fullName>各種不同的方法，處理字串，並傳回字串的新執行個體的類別。 藉由使用此模型，它會保留給呼叫者決定是否要保留原始物件。

 雖然傳回的值很常見，並且大量使用正確的應用程式的`out`和`ref`參數需要中繼的設計和編碼技能。 程式庫架構設計人員負責設計的目標為一般使用者不應預期使用者會熟練地運用`out`或`ref`參數。

> [!NOTE]
> 當您使用大型結構參數時，會複製這些結構所需的其他資源可能會造成效能上的影響時傳值方式傳遞。 在這些情況下，您可以考慮使用`ref`或`out`參數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此起因於實值類型的規則的違規情形，讓方法傳回的物件做為其傳回的值。 如果此方法必須傳回多個值，請將它傳回保存值物件的單一執行個體重新設計。

 若要修正這項規則是參考型別所導致的違規情形，請確定您想要的行為是要傳回之參考的新執行個體。 如果是，方法應使用它的傳回值，若要這樣做。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全地隱藏的警告，這項規則;不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
 下列的程式庫會顯示兩個實作的類別，會產生對使用者的意見反應。 首次實作 (`BadRefAndOut`) 會強制程式庫使用者管理三個傳回的值。 第二個的實作 (`RedesignedRefAndOut`) 傳回的容器類別的執行個體，藉以簡化使用者經驗 (`ReplyData`) 可管理的資料當做單一單位。

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>範例
 下列應用程式說明使用者的體驗。 重新設計的程式庫的呼叫 (`UseTheSimplifiedClass`方法) 是更簡單，並輕鬆地管理方法所傳回的資訊。 這兩個方法的輸出完全相同。

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>範例
 下列範例程式庫將說明如何`ref`參考型別參數使用，並示範更好的方式來實作這項功能。

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>範例
 下列應用程式會呼叫每個方法，以示範行為的文件庫中。

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]

這個範例會產生下列輸出：

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="related-rules"></a>相關的規則
 [CA1021:避免使用 out 參數](../code-quality/ca1021-avoid-out-parameters.md)
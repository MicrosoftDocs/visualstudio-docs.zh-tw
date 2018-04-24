---
title: CA1061：不要隱藏基底類別方法
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fc3be40a81d29da27e9a44d72cca4e78b37abbf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061：不要隱藏基底類別方法
|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 衍生的型別宣告具有相同名稱和相同數量的參數做為其基底的方法; 其中一個方法一或多個參數是基底類型的基底的方法; 中的對應參數而且任何剩餘的參數具有相同基底方法中的對應參數的類型。

## <a name="rule-description"></a>規則描述
 當在衍生方法的參數簽章與只由是弱衍生比基底方法參數簽章中的對應類型的型別衍生類型中相同具名方法所隱藏基底類型中的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除或重新命名方法，或變更的參數簽章，使方法不會隱藏基底方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的方法。

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]
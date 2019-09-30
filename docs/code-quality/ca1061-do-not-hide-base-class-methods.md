---
title: CA1061:不要隱藏基底類別方法
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eacd20dee0758ff481b259807ba52bb78b26f5d2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235393"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061:不要隱藏基底類別方法

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|分類|Microsoft.Design|
|重大變更|中斷|

## <a name="cause"></a>原因
衍生型別會宣告具有相同名稱的方法，並使用與它的其中一個基底方法相同的參數數目;一或多個參數是基底方法中對應參數的基底類型;而且任何剩餘的參數都有與基底方法中對應參數相同的類型。

## <a name="rule-description"></a>規則描述
當衍生方法的參數簽章不同于基底方法的參數簽章中的對應類型較弱的類型時，基底類型中的方法會由衍生類型中的相同名稱方法隱藏。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請移除或重新命名方法，或變更參數簽章，讓方法不會隱藏基底方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反規則的方法。

[!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]
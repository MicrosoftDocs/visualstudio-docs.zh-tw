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
ms.openlocfilehash: faa225178a50be080f92a728998e914025c17168
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947597"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061:不要隱藏基底類別方法

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 衍生的型別宣告具有相同名稱和相同數目的參數做為其基底方法，其中一個方法一或多個參數是在基底方法; 中的對應參數的基底類型而且任何剩餘的參數具有相同基底方法中的對應參數的類型。

## <a name="rule-description"></a>規則描述
 在衍生方法的參數簽章只有不同的類型還要弱衍生比基底方法的參數簽章中對應的類型時所衍生的型別中的相同具名方法隱藏基底類型中的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除或重新命名方法，或變更的參數簽章，使方法不會隱藏基底方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會示範違反規則的方法。

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]
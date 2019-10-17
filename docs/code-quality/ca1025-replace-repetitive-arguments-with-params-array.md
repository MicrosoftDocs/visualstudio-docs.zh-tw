---
title: CA1025：必須以參數陣列取代重複的引數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6b6c45a8a56cab3927355fc4f03c541bcffc1cf
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446680"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025：必須以參數陣列取代重複的引數

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|分類|Microsoft. Design|
|重大變更|不中斷|

## <a name="cause"></a>原因
公用類型中的公用或受保護方法具有三個以上的參數，且其最後三個參數的類型相同。

## <a name="rule-description"></a>規則描述
當引數的確切數目未知，且變數引數是相同的類型，或可以當做相同類型傳遞時，請使用參數陣列，而不是重複的引數。 例如，<xref:System.Console.WriteLine%2A> 方法提供一般用途的多載，其使用參數陣列接受任意數目的 @no__t 1 引數。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請以參數陣列取代重複的引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請一律放心地隱藏此規則的警告;不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
下列範例顯示違反此規則的類型。

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]

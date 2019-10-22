---
title: CA1025 必須：以 params 陣列取代重複的引數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 21d13611a3c4dd11eb691c746f8746347fb9a83b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661974"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025：必須以參數陣列取代重複的引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 公用類型中的公用或受保護方法具有三個以上的參數，且其最後三個參數的類型相同。

## <a name="rule-description"></a>規則描述
 當引數的確切數目未知，且變數引數是相同的類型，或可以當做相同類型傳遞時，請使用參數陣列，而不是重複的引數。 例如，<xref:System.Console.WriteLine%2A> 方法會提供一般用途的多載，其使用參數陣列接受任意數目的 <xref:System.Object> 引數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請以參數陣列取代重複的引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請一律放心地隱藏此規則的警告;不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型。

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]

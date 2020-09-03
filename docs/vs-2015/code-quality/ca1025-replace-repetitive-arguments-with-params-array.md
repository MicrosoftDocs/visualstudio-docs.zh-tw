---
title: CA1025 必須：使用 params 陣列來取代重複的引數 |Microsoft Docs
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
ms.openlocfilehash: 84809341d7898aeb3defe0447f2a2f1142eb460a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546623"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025:以參數陣列取代重複的引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用類型中的公用或受保護方法有三個以上的參數，而最後三個參數的類型相同。

## <a name="rule-description"></a>規則描述
 當引數的確切數目未知，而且變數引數的類型相同，或者可以傳遞為相同的類型時，請使用參數陣列，而不是重複的引數。 例如， <xref:System.Console.WriteLine%2A> 方法會提供一般用途的多載，以使用參數陣列接受任意數目的 <xref:System.Object> 引數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請以參數陣列取代重複的引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告一律是安全的;不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型。

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]

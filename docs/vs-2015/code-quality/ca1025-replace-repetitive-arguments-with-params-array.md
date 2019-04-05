---
title: CA1025:以參數陣列取代重複的引數 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83d36f1f5cd31b1ad1833dd805f4386ac71a3ed1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945979"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025:以參數陣列取代重複的引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 公用類型中的公用或受保護的方法有三個以上的參數和其最後三個參數都是相同類型。

## <a name="rule-description"></a>規則描述
 當引數確切數目未知，而且變數引數都是相同的類型，或可以傳遞做為相同的類型時，請使用參數陣列而不是重複的引數。 例如，<xref:System.Console.WriteLine%2A>方法會提供一般用途的多載接受任意數目的使用參數陣列<xref:System.Object>引數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請以參數陣列取代重複的引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它一律可安全地隱藏這項規則; 一個警告不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別。

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]

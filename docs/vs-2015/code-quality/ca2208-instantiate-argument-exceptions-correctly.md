---
title: Ca2208： 必須正確執行個體化引數例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ba99cddfe42e1b6699dba4fa665302581aa68cdc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588397"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208：請正確執行個體化引數例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2208： 具現化引數例外狀況正確](https://docs.microsoft.com/visualstudio/code-quality/ca2208-instantiate-argument-exceptions-correctly)。

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 可能的原因包括下列情況：

-   例外狀況類型，或衍生自 [System.ArgumentException] 預設 （無參數） 建構函式進行呼叫 (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->)。

-   不正確的字串引數傳遞至參數化建構函式的例外狀況型別，或衍生自 [System.ArgumentException。](<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>規則描述
 而不是呼叫預設建構函式，呼叫其中一個建構函式多載，可讓提供更有意義的例外狀況訊息。 例外狀況訊息應該為目標的開發人員，並清楚地說明錯誤狀況，以及如何修正或避免此例外狀況。

 一個和兩個字串的建構函式的簽章<xref:System.ArgumentException>和其衍生的類型不一致，相對於`message`和`paramName`參數。 請確定正確的字串引數來呼叫這些建構函式。 簽章如下所示：

 <xref:System.ArgumentException>(字串`message`)

 <xref:System.ArgumentException>(字串`message`，字串`paramName`)

 <xref:System.ArgumentNullException>(字串`paramName`)

 <xref:System.ArgumentNullException>(字串`paramName`，字串`message`)

 <xref:System.ArgumentOutOfRangeException>(字串`paramName`)

 <xref:System.ArgumentOutOfRangeException>(字串`paramName`，字串`message`)

 <xref:System.DuplicateWaitObjectException>(字串`parameterName`)

 <xref:System.DuplicateWaitObjectException>(字串`parameterName`，字串`message`)

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，呼叫的建構函式的訊息、 參數名稱，或兩者，並請確定引數類型的適當<xref:System.ArgumentException>所呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全地隱藏此規則的警告，只有當參數化建構函式以正確的字串引數呼叫。

## <a name="example"></a>範例
 下列範例顯示不正確地具現化 ArgumentNullException 型別的執行個體的建構函式。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>範例
 下列範例會修正上述的違規情形，藉由切換的建構函式引數。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]




---
title: CA2208：正確地具現化引數例外狀況 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a63ebb7f3946926864c4dd882c281b5dcd7c6c5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535833"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208:必須正確執行個體化引數例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 可能的原因包括下列情況：

- 針對例外狀況類型（也就是衍生自 [ArgumentException]）的預設（無參數）的函式呼叫進行呼叫（<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

- 不正確的字串引數會傳遞給例外狀況類型（也就是衍生自 [ArgumentException]）的參數化構造函式。(<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>規則描述
 請呼叫其中一個可提供更有意義的例外狀況訊息的其中一個函式多載，而不是呼叫預設的函式。 例外狀況訊息應以開發人員為目標，並清楚說明錯誤情況，以及如何更正或避免例外狀況。

 和其衍生類型的一個和兩個字串構造函式的簽章， <xref:System.ArgumentException> 與 `message` 和參數不一致 `paramName` 。 請確定使用正確的字串引數呼叫這些函式。 簽章如下所示：

 <xref:System.ArgumentException>（字串 `message` ）

 <xref:System.ArgumentException>（字串 `message` ，字串 `paramName` ）

 <xref:System.ArgumentNullException>（字串 `paramName` ）

 <xref:System.ArgumentNullException>（字串 `paramName` ，字串 `message` ）

 <xref:System.ArgumentOutOfRangeException>（字串 `paramName` ）

 <xref:System.ArgumentOutOfRangeException>（字串 `paramName` ，字串 `message` ）

 <xref:System.DuplicateWaitObjectException>（字串 `parameterName` ）

 <xref:System.DuplicateWaitObjectException>（字串 `parameterName` ，字串 `message` ）

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請呼叫接受訊息、參數名稱或兩者的函式，並確定引數對於所呼叫的類型而言是正確的 <xref:System.ArgumentException> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有使用正確的字串引數呼叫參數化的函式時，才可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示不正確具現化 System.argumentnullexception 類型實例的函式。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>範例
 下列範例會切換函式引數，藉以修正上述違規。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]

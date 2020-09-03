---
title: CA1061：不要隱藏基類方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c884eb569d5682326d2dc667363f991467171386
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533350"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061:不要隱藏基底類別方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 衍生型別會宣告具有相同名稱的方法，並使用與它的其中一個基底方法相同的參數數目;一個或多個參數是基底方法中對應參數的基底類型;其餘的任何參數都具有與基底方法中對應參數相同的類型。

## <a name="rule-description"></a>規則描述
 當衍生方法的參數簽章與基底方法的參數簽章中的對應型別不同時，基底型別中的相同命名方法會隱藏基底類型中的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除或重新命名方法，或變更參數簽章，讓方法不會隱藏基底方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的方法。

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]

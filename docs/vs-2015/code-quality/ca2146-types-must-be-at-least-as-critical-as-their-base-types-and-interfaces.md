---
title: CA2146：類型至少必須與基底類型和介面一樣重要 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ab621ade120a257508eddbf9527f674b5fda8748
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610180"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146：類型至少必須和基底類型與介面一樣關鍵
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明類型衍生自標記為 <xref:System.Security.SecuritySafeCriticalAttribute> 或 <xref:System.Security.SecurityCriticalAttribute> 的類型，或標記為 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性的類型是衍生自標記為 <xref:System.Security.SecurityCriticalAttribute> 屬性的類型。

## <a name="rule-description"></a>規則描述
 當衍生類型有安全性透明屬性，且該屬性的重要性不如基底類型或已實作之介面時，就會引發這個規則。 只有關鍵類型可以衍生自關鍵基底類型或實作關鍵介面，而且只有關鍵或安全關鍵類型可以衍生自安全關鍵基底類型或實作安全關鍵介面。 違反層級2透明度中的這項規則會導致衍生類型的 <xref:System.TypeLoadException>。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正這個違規，請使用與基底類型或介面至少一樣重要的透明度屬性來標記衍生或實類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]

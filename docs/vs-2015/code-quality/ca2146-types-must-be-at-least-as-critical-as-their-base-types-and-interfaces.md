---
title: CA2146：類型至少必須和基底類型和介面一樣重要 |Microsoft Docs
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
ms.openlocfilehash: 2316d6e555fa091d26392aee71b774489c81a379
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546389"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146:類型至少必須和基底類型與介面一樣關鍵
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明型別衍生自標示為 <xref:System.Security.SecuritySafeCriticalAttribute> 或的型別 <xref:System.Security.SecurityCriticalAttribute> ，或以屬性標示的型別 <xref:System.Security.SecuritySafeCriticalAttribute> 衍生自標示為屬性（attribute）的型別 <xref:System.Security.SecurityCriticalAttribute> 。

## <a name="rule-description"></a>規則描述
 當衍生類型有安全性透明屬性，且該屬性的重要性不如基底類型或已實作之介面時，就會引發這個規則。 只有關鍵類型可以衍生自關鍵基底類型或實作關鍵介面，而且只有關鍵或安全關鍵類型可以衍生自安全關鍵基底類型或實作安全關鍵介面。 在層級2透明度中違規此規則會導致 <xref:System.TypeLoadException> 衍生類型的。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規，請使用與基底類型或介面至少相同的透明度屬性來標記衍生或實型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]

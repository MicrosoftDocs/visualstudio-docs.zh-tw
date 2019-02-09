---
title: CA2146:類型至少必須和基底類型與介面一樣關鍵
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01a8a5609394f0dd428066e32fb425a2abb486c4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926862"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146:類型至少必須和基底類型與介面一樣關鍵

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明的類型衍生自標記為類型<xref:System.Security.SecuritySafeCriticalAttribute>或<xref:System.Security.SecurityCriticalAttribute>，或標示為類型<xref:System.Security.SecuritySafeCriticalAttribute>屬性衍生自類型標記為<xref:System.Security.SecurityCriticalAttribute>屬性。

## <a name="rule-description"></a>規則描述
 當衍生類型有安全性透明屬性，且該屬性的重要性不如基底類型或已實作之介面時，就會引發這個規則。 只有關鍵類型可以衍生自關鍵基底類型或實作關鍵介面，而且只有關鍵或安全關鍵類型可以衍生自安全關鍵基底類型或實作安全關鍵介面。 此層級 2 透明度規則的違規會導致<xref:System.TypeLoadException>衍生的類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規，標示為至少和基底類型或介面一樣關鍵的透明度屬性的衍生或實作類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]
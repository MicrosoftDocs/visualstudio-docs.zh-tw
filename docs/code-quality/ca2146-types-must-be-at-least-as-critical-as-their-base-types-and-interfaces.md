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
ms.openlocfilehash: a70e999505bd900a7b3d89693ef4f6a1cef9de7d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920416"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146:類型至少必須和基底類型與介面一樣關鍵

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
透明型<xref:System.Security.SecuritySafeCriticalAttribute>別衍生自以<xref:System.Security.SecurityCriticalAttribute>或標記的類型, 或以<xref:System.Security.SecuritySafeCriticalAttribute>屬性標記的類型衍生<xref:System.Security.SecurityCriticalAttribute>自以屬性標記的類型時。

## <a name="rule-description"></a>規則描述
當衍生類型有安全性透明屬性，且該屬性的重要性不如基底類型或已實作之介面時，就會引發這個規則。 只有關鍵類型可以衍生自關鍵基底類型或實作關鍵介面，而且只有關鍵或安全關鍵類型可以衍生自安全關鍵基底類型或實作安全關鍵介面。 在層級2透明度中違反這項規則會<xref:System.TypeLoadException>導致衍生類型的。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正這個違規, 請使用與基底類型或介面至少一樣重要的透明度屬性來標記衍生或實類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
[!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]
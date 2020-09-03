---
title: CA2133：委派必須系結至具有一致透明度的方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 12132622900d5698a6b78a1914c687a369d7dc03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547728"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133:委派必須繫結至具有一致透明度的方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|類別|Microsoft.Security|
|中斷變更|中斷|

> [!NOTE]
> 這個警告只適用于執行 CoreCLR 的程式碼 () Silverlight Web 應用程式專用的 CLR 版本。

## <a name="cause"></a>原因
 這個警告會在系結標示為之委派的方法上引發，這個方法會將標示為 <xref:System.Security.SecurityCriticalAttribute> 透明或以標記的方法 <xref:System.Security.SecuritySafeCriticalAttribute> 。 此警告也會引發將透明或安全關鍵性的委派繫結至關鍵方法的方法。

## <a name="rule-description"></a>規則描述
 委派類型與其系結的方法必須具有一致的透明度。 透明和安全關鍵的委派只能系結至其他透明或安全關鍵的方法。 同樣地，關鍵委派可能只會系結至重要方法。 這些系結規則會確保只能透過委派叫用方法的程式碼，也可以直接叫用相同的方法。 例如，系結規則會防止透明程式碼直接透過透明的委派呼叫重要程式碼。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此警告的違規情形，請變更委派的透明度或它所系結之方法的透明度，讓兩者的透明度相等。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]

---
title: CA2131：安全性關鍵類型可能未參與類型等價 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ccd556a5929e56597de678ad4ad8ea6c101b7c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535885"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131:安全性關鍵類型可能未參與類型等價
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型會參與類型等價，而類型本身或型別的成員或欄位會以 <xref:System.Security.SecurityCriticalAttribute> 屬性標記。

## <a name="rule-description"></a>規則描述
 此規則會引發任何關鍵的類型或包含參與類型等價之關鍵方法或欄位的類型。 當 CLR 偵測到這類型別時，就無法 <xref:System.TypeLoadException> 在執行時間載入它。 通常，只有在使用者手動實作類型等價，而不是依賴 tlbimp 和編譯器進行類型等價時，就會引發這項規則。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除 SecurityCritical 屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範介面、方法，以及會引發此規則的欄位。

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2131.criticaltypesmustnotparticipateintypeequivalence/cs/ca2131 - criticaltypesmustnotparticipateintypeequivalence.cs#1)]

## <a name="see-also"></a>另請參閱
 [安全性透明的程式碼，層級 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)

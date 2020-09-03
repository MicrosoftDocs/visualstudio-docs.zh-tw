---
title: CA1048：不要在密封類型中宣告虛擬成員 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19ae3a4fdc620343f18aa0845c33e1d73529adfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546792"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048:不要在密封類型中宣告 virtual 成員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用類型是密封的，且宣告的方法 `virtual` `Overridable` 在 Visual Basic) 中 (，而不是 final。 此規則不會報告委派類型的違規，必須遵循此模式。

## <a name="rule-description"></a>規則描述
 類型會將方法宣告為 virtual，讓繼承類型可以覆寫 virtual 方法的實作。 根據定義，您無法繼承自密封類型，使密封型別上的虛擬方法沒有意義。

 Visual Basic 的 .NET 和 c # 編譯器不允許類型違反此規則。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將方法設為非虛擬或使類型成為可繼承。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 將類型保留在目前的狀態可能會造成維護問題，而不會提供任何好處。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型。

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]

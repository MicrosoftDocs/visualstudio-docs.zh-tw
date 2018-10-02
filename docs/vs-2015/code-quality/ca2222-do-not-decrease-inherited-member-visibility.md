---
title: CA2222： 不要降低繼承的成員的可視性 |Microsoft Docs
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
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9e631fc55a85e1d1a0383949d7e7592c6a5da44d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588331"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222：請勿降低繼承成員的可視性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2222： 不要降低繼承的成員的可視性](https://docs.microsoft.com/visualstudio/code-quality/ca2222-do-not-decrease-inherited-member-visibility)。

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 非密封類型中的私用方法具有相同的基底類型中宣告的公用方法的簽章。 私用的方法不是最終的。

## <a name="rule-description"></a>規則描述
 您不得變更繼承成員的存取修飾詞 (Modifier)。 將繼承成員變更為私用不會防止呼叫端存取方法的基底類別 (Base Class) 實作。 如果成員設為私用，而且未密封的型別，則繼承的類型可以呼叫繼承階層架構中的最後一個公用方法的實作。 如果您必須變更存取修飾詞，這個方法標記為 final，或其類型應該為密封，以避免方法遭到覆寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，會變更為非私用存取。 或者，如果您的程式語言支援，您可以進行方法最後一個。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別。

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]




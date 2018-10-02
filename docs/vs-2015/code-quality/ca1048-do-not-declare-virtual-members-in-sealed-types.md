---
title: CA1048： 不要宣告在密封類型中的虛擬成員 |Microsoft Docs
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
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3ff0bb128c72f5483c9169a98c6fc41ec3057e54
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588325"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048：不要在密封類型中宣告 virtual 成員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1048： 不要宣告在密封類型中的虛擬成員](https://docs.microsoft.com/visualstudio/code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types)。

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用型別密封格式，並宣告的方法，同時`virtual`(`Overridable` Visual Basic 中) 不是最後一個。 此規則不會報告違規的委派類型，必須遵循這個模式。

## <a name="rule-description"></a>規則描述
 類型會將方法宣告為 virtual，讓繼承類型可以覆寫 virtual 方法的實作。 根據定義，您無法繼承自密封型別，讓密封類型上的虛擬方法沒有任何意義。

 在 Visual Basic.NET 和 C# 編譯器不允許違反此規則的類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將方法設為非虛擬，或讓類型成為可繼承。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 類型在目前的狀態可能會造成維護問題並不提供任何好處。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別。

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]




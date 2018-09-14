---
title: CA1048：不要在密封類型中宣告 virtual 成員
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59a1bd75ce2e9f437661fa2b2034f8e31f729ef9
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546716"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048：不要在密封類型中宣告 virtual 成員
|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|類別|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用型別密封格式，並宣告的方法，同時`virtual`(`Overridable` Visual Basic 中) 不是最後一個。 此規則不會報告違規的委派類型，必須遵循這個模式。

## <a name="rule-description"></a>規則描述
 類型會將方法宣告為 virtual，讓繼承類型可以覆寫 virtual 方法的實作。 根據定義，您無法繼承自密封型別，讓密封類型上的虛擬方法沒有任何意義。

 Visual Basic 和 C# 編譯器不允許違反此規則的類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將方法設為非虛擬，或讓類型成為可繼承。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 類型在目前的狀態可能會造成維護問題並不提供任何好處。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別。

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]
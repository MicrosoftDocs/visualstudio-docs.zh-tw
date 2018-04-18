---
title: CA1048： 不要宣告在密封類型中的虛擬成員 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: ad16335502394d46eade760ba365b6dcf7ed529c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048：不要在密封類型中宣告 virtual 成員
|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用型別密封格式，並宣告的方法，同時為`virtual`(`Overridable`在 Visual Basic 中) 不是最後一個。 此規則不會報告必須遵循此模式的委派類型的違規。  
  
## <a name="rule-description"></a>規則描述  
 類型會將方法宣告為 virtual，讓繼承類型可以覆寫 virtual 方法的實作。 根據定義，您無法繼承自密封類型，讓密封類型上的虛擬方法沒有任何意義。  
  
 Visual Basic 和 C# 編譯器不允許違反此規則的型別。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，讓非虛擬方法，或讓繼承類型。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 類型在目前的狀態可能會造成維護問題並不提供任何優勢。  
  
## <a name="example"></a>範例  
 下列範例顯示違反此規則的類型。  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]
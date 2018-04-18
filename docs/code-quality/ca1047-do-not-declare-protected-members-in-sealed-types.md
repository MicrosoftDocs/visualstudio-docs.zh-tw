---
title: CA1047： 不要宣告在密封類型中的受保護的成員 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b4a8ec92b79fb7df72ebd1984fc49f3cf4396cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047：不要在密封類型中宣告 protected 成員
|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 公用型別是`sealed`(`NotInheritable`在 Visual basic 中)，並宣告 protected 的成員或受保護的巢狀的類型。 此規則不會報告的違規<xref:System.Object.Finalize%2A>必須遵循此模式的方法。  
  
## <a name="rule-description"></a>規則描述  
 類型會宣告 protected 成員，如此繼承的類型即可存取或覆寫成員。 根據定義，您無法繼承自密封的型別，也就是說，受保護的方法，密封類型上的無法呼叫。  
  
 C# 編譯器會發出這項錯誤的警告。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，該成員的存取層級變更為 私用，或是將類型繼承。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 類型在目前的狀態可能會造成維護問題並不提供任何優勢。  
  
## <a name="example"></a>範例  
 下列範例顯示違反此規則的類型。  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]
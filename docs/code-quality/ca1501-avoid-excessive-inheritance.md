---
title: "CA1501： 避免過度繼承 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 05d54c668ee6e21932d766272044bd3a7e0aa0e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501：避免過度繼承
|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|分類|Microsoft.Maintainability|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。  
  
## <a name="rule-description"></a>規則描述  
 太深的巢狀類型階層架構可能會難以依循、了解和維護。 此規則會限制在相同模組中的階層來分析。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，衍生自繼承階層架構中較深的基底類型的型別，或排除部分中繼的基底類型。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告。 不過，程式碼可能更難以維護。 請注意，根據基底類型的可見性，解決違反此規則可能會產生重大變更。 例如，移除公用基底型別是一項重大變更。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的類型。  
  
 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]
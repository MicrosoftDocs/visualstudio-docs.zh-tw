---
title: "CA1806： 不要忽略方法的結果 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58da9a40f8cbbf8a506feb35dcba8a8e9f405899
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806：不要忽略方法的結果
|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 有數個可能的原因，這項警告：  
  
-   已建立但從未使用新的物件。  
  
-   呼叫的方法，建立並傳回新字串，而新字串從未使用過。  
  
-   COM 或 P/Invoke 方法傳回從未使用過的 HRESULT 或錯誤碼程式碼。 規則描述  
  
 建立不必要的物件以及未使用的物件相關聯的記憶體回收集合會降低效能。  
  
 字串是不變，例如 String.ToUpper 方法會傳回字串而非修改呼叫的方法中的字串執行個體的新執行個體。  
  
 忽略 HRESULT 或錯誤碼可能會導致非預期的行為，在錯誤狀況，或資源不足的狀況。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 如果方法 A 建立的新執行個體 B 物件從未使用過的將執行個體做為引數傳遞給另一個方法，或指派給變數的執行個體。 如果不需要建立的物件，將它移除。-或-  
  
 如果方法 A 呼叫 B，方法，但未使用，方法 B 會傳回新字串執行個體。 將執行個體做為引數傳遞給另一個方法，將執行個體指派給變數。 或如果不需要移除的呼叫。  
  
 -或-  
  
 如果方法 A 呼叫 B，方法，但不會使用 HRESULT 或錯誤碼，方法會傳回。 使用中的條件陳述式的結果、 將結果指派給變數，或將它做為引數傳遞給另一個方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告，除非建立物件的某些用途。  
  
## <a name="example"></a>範例  
 下列範例會略過呼叫 String.Trim 結果的類別。  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## <a name="example"></a>範例  
 下列範例會將上述的違規修正 String.Trim 的結果指派給變數呼叫。  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## <a name="example"></a>範例  
 下列範例不會使用它所建立物件的方法。  
  
> [!NOTE]
>  無法在 Visual Basic 中重現此違規。  

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]   
  
## <a name="example"></a>範例  
 下列範例會藉由移除不必要的物件建立修正上述違規。  

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)] 

<!-- Examples don't exist for the below... -->
<!--
## Example  
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.  
  
## Example  
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.  
-->
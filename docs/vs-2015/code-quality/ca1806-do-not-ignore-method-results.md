---
title: CA1806： 不要忽略方法的結果 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d28ca688bbad0054f7522034bfe309dcb1fe698
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250103"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806：不要忽略方法的結果
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 有數個可能的原因，這個警告：  
  
-   已建立新的物件，但從未使用過。  
  
-   呼叫的方法，建立並傳回新字串，以及新字串從未使用過。  
  
-   COM 或 P/Invoke 方法會傳回 HRESULT 或錯誤碼的程式碼，不會用到。 規則描述  
  
 建立不必要的物件和未使用的物件相關聯的記憶體回收集合會降低效能。  
  
 字串是不變，例如 String.ToUpper 方法會傳回字串而非修改字串呼叫方法中的執行個體的新執行個體。  
  
 忽略 HRESULT 或錯誤碼可能會導致非預期的行為，在錯誤條件或資源不足狀況。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 如果方法的建立從未使用過的 B 物件的新執行個體，將執行個體做為引數傳遞給另一個方法，或指派給變數的執行個體。 如果不需要建立的物件，將它移除。-或-  
  
 如果方法 A 呼叫 B，; 方法，但未使用 B 則方法會傳回新字串執行個體。 將執行個體做為引數傳遞給另一個方法，將執行個體指派給變數。 或如果不需要移除的呼叫。  
  
 -或-  
  
 如果方法的呼叫方法，B，但不會使用 HRESULT 或錯誤碼，這個方法傳回。 使用中的條件陳述式的結果、 將結果指派給變數，或將它做為引數傳遞給另一個方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告，除非建立物件的動作有一些用途。  
  
## <a name="example"></a>範例  
 下列範例顯示的類別，會忽略呼叫 String.Trim 的結果。  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>範例  
 下列範例會將前述的違規修正 String.Trim 的結果指派給所呼叫的變數。  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>範例  
 下列範例會示範不會使用它所建立物件的方法。  
  
> [!NOTE]
>  無法在 Visual Basic 中重現此違規。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>範例  
 下列範例會將先前的違規修正藉由移除不必要建立物件。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>範例  
 下列範例會示範會忽略原生方法 GetShortPathName 傳回的錯誤程式碼的方法。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>範例  
 下列範例會藉由檢查錯誤程式碼，並擲回例外狀況，呼叫失敗時修正上述的違規。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]
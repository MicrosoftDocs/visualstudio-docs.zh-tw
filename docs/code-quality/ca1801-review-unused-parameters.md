---
title: "Ca1801： 必須檢閱未使用的參數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1bb8c38d1436ca687664f92bfe0ba6db1ccf68ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1801-review-unused-parameters"></a>CA1801：必須檢閱未使用的參數
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷-成員不是組件，不論您所進行的變更外部可見。<br /><br /> 非中斷-如果您變更要使用此參數在其主體中的成員。<br /><br /> 中斷-如果您移除參數，它會在組件外部顯示。|  
  
## <a name="cause"></a>原因  
 方法簽章包括不用於方法主體中的參數； 此規則不會檢查下列方法：  
  
-   委派所參考的方法。  
  
-   做為事件處理常式的方法。  
  
-   方法宣告與`abstract`(`MustOverride`在 Visual Basic 中) 修飾詞。  
  
-   方法宣告與`virtual`(`Overridable`在 Visual Basic 中) 修飾詞。  
  
-   方法宣告與`override`(`Overrides`在 Visual Basic 中) 修飾詞。  
  
-   方法宣告與`extern`(`Declare`陳述式在 Visual Basic 中的) 修飾詞。  
  
## <a name="rule-description"></a>規則描述  
 檢閱中不會在方法主體中，確定它們存取失敗的不正確性存在的非虛擬方法的參數。 未使用的參數會產生維護與效能成本。  
  
 有時違反此規則可指向方法中實作錯誤。 例如，參數應該已經用於方法主體。 如果參數有因為回溯相容性而存在，則隱藏此規則的警告。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請移除未使用的參數 （重大變更） 或使用參數在方法主體中 （非中斷變更）。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏先前提供之程式碼修正程式將會是一項重大變更這項規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會示範兩種方法。 一種方法違反此規則和其他方法會滿足規則。  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1811：避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812：避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)
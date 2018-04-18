---
title: CA2119： 密封方法以滿足私用介面 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f54b6c58e30145759881a8a612ad6f7edfd044d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119：密封方法以滿足私用介面的要求
|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 可繼承的公用類型提供的可覆寫方法實作`internal`(`Friend`在 Visual Basic 中) 介面。  
  
## <a name="rule-description"></a>規則描述  
 介面方法具有公用存取範圍，無法變更所實作的型別。 內部介面會建立不是定義介面的組件外部實作的合約。 實作內部介面使用的方法的公用類型`virtual`(`Overridable`在 Visual Basic 中) 修飾詞可讓衍生類型在組件外部是由覆寫方法。 如果定義的組件中的第二個型別呼叫方法，並預期僅供內部使用的合約，而是執行外部組件中覆寫的方法時，可能會受到危害的行為。 這會產生安全性弱點。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，避免方法遭到覆寫外部組件使用下列其中一項：  
  
-   請宣告的型別`sealed`(`NotInheritable`在 Visual Basic 中)。  
  
-   以宣告型別的存取範圍變更`internal`(`Friend`在 Visual Basic 中)。  
  
-   移除宣告的型別中的所有公用建構函式。  
  
-   實作的方法，而不使用`virtual`修飾詞。  
  
-   明確實作的方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 安全地隱藏這個警告規則詳細檢閱之後，沒有安全性問題存在，可能會處於易遭利用，如果組件外覆寫此方法。  
  
## <a name="example"></a>範例  
 下列範例顯示型別， `BaseImplementation`，違反此規則。  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會利用先前範例中的虛擬方法實作。  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [介面](/dotnet/csharp/programming-guide/interfaces/index)   
 [介面](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)
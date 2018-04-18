---
title: CA1011： 建議將基底類型當做參數傳遞 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51271f3d6b2ced6fdf0229c18ac2a19ee06de36c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011：建議將基底類型當做參數傳遞
|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 方法宣告包含衍生的型別，在型式參數和方法呼叫參數的基底類型的成員。  
  
## <a name="rule-description"></a>規則描述  
 當方法宣告將基底類型指定為參數，則從此基底類型衍生的任何類型都可以當做對應引數傳遞給方法。 引數之方法主體內使用時，所執行的特定方法，取決於引數的型別。 如果不需要額外的功能所提供的衍生型別，則使用基底型別可讓更廣泛地運用此方法。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請變更參數的型別與其基底類型。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 安全地隱藏此規則的警告  
  
-   如果此方法需要的特定功能所提供的衍生型別  
  
     \-或-  
  
-   若要強制執行只衍生的類型，或是衍生程度較大的類型，傳遞給方法。  
  
 在這些情況下，程式碼將更穩固因為強式型別檢查編譯器和執行階段所提供。  
  
## <a name="example"></a>範例  
 下列範例會示範一種方法， `ManipulateFileStream`，其可用只能搭配<xref:System.IO.FileStream>違反此規則的物件。 第二種方法， `ManipulateAnyStream`，來取代符合規則<xref:System.IO.FileStream>參數使用<xref:System.IO.Stream>。  
  
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1059：成員不應該公開特定的具象類型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
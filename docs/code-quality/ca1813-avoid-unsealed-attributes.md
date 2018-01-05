---
title: "CA1813： 避免非密封的屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9ad548bd51985484ebcb39cb6022e994a5e0534a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813：避免使用非密封屬性
|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用類型會繼承自<xref:System.Attribute?displayProperty=fullName>、 不是抽象的而且不密封 (`NotInheritable`在 Visual Basic 中)。  
  
## <a name="rule-description"></a>規則描述  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Class Library 會提供擷取自訂屬性的方法。 根據預設，這些方法會搜尋屬性繼承階層架構。例如<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>搜尋指定的屬性類型或任何擴充指定的屬性類型的屬性類型。 密封屬性會減少對整個繼承階層架構中，搜尋，並可改善效能。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，密封屬性類型，或將它設為抽象。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告。 如果您正在定義的屬性階層和無法密封屬性或不將它設為抽象，您應該這麼做。  
  
## <a name="example"></a>範例  
 下列範例會顯示符合此規則的自訂屬性。  
  
 [!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1019：必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018：必須以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## <a name="see-also"></a>請參閱  
 [屬性](/dotnet/standard/design-guidelines/attributes)
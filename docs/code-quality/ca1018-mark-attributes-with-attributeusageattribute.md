---
title: "CA1018： 以 AttributeUsageAttribute 標記屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e9218d3908872871ff5dab13529e8b1cbcec0c8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018：以 AttributeUsageAttribute 標記屬性
|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 <xref:System.AttributeUsageAttribute?displayProperty=fullName>屬性不存在於自訂屬性。  
  
## <a name="rule-description"></a>規則描述  
 當您定義自訂屬性時，它使用標記<xref:System.AttributeUsageAttribute>指出在原始程式碼中可以套用自訂屬性的位置。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。 例如，您可以定義的屬性，識別誰負責維護和增強中程式庫中，每種類型和類型層級，永遠指派責任的人員。 在此情況下，編譯器應該啟用類別、 列舉和介面上的屬性，但應該在方法、 事件或屬性上啟用。 組織的原則和程序會指示該屬性是否應該啟用組件。  
  
 <xref:System.AttributeTargets?displayProperty=fullName>列舉會定義您可以指定自訂屬性的目標。 如果您省略<xref:System.AttributeUsageAttribute>，所定義，您的自訂屬性將會適用於所有目標，`All`值<xref:System.AttributeTargets>列舉型別。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請指定目標屬性使用<xref:System.AttributeUsageAttribute>。 請參閱下列範例。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 您應該修正而不是訊息但不包括此規則的違規情形。 即使屬性繼承<xref:System.AttributeUsageAttribute>，屬性應該會出現以簡化程式碼維護。  
  
## <a name="example"></a>範例  
 下列範例會定義兩個屬性。 `BadCodeMaintainerAttribute`不正確地省略<xref:System.AttributeUsageAttribute>陳述式，和`GoodCodeMaintainerAttribute`正確實作本節稍早描述之屬性。 請注意，屬性`DeveloperName`設計規則所需[ca1019 必須： 定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)和隨附的完整性。  
  
 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1019：必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813：避免使用非密封屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>另請參閱  
 [屬性](/dotnet/standard/design-guidelines/attributes)
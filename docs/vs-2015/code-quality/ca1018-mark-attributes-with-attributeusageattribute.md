---
title: CA1018：使用 AttributeUsageAttribute 標記屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 256fc281b27c483f1dda0317f7d2695fa36c47f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535053"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018:必須以 AttributeUsageAttribute 標記屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 <xref:System.AttributeUsageAttribute?displayProperty=fullName>屬性不存在於自訂屬性上。

## <a name="rule-description"></a>規則描述
 當您定義自訂屬性時，請使用將它標示 <xref:System.AttributeUsageAttribute> 為，指出原始程式碼中可以套用自訂屬性的位置。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。 例如，您可以定義一個屬性來識別負責維護和增強文件庫中每個類型的人員，而且一律會在類型層級指派該責任。 在此情況下，編譯器應該啟用類別、列舉和介面上的屬性，但不應該在方法、事件或屬性上啟用它。 組織原則和程式會決定是否應該在元件上啟用屬性。

 <xref:System.AttributeTargets?displayProperty=fullName>列舉會定義您可以為自訂屬性指定的目標。 如果您省略 <xref:System.AttributeUsageAttribute> ，自訂屬性將對所有目標有效，如列舉值所定義 `All` <xref:System.AttributeTargets> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用來指定屬性的目標 <xref:System.AttributeUsageAttribute> 。 請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您應該修正此規則的違規，而不是排除訊息。 即使屬性繼承 <xref:System.AttributeUsageAttribute> ，屬性也應該存在，以簡化程式碼維護。

## <a name="example"></a>範例
 下列範例會定義兩個屬性。 `BadCodeMaintainerAttribute` 不正確地省略 <xref:System.AttributeUsageAttribute> 語句，並正確地執行本節稍 `GoodCodeMaintainerAttribute` 早所述的屬性。 請注意，此屬性 `DeveloperName` 是設計規則 ca1019 必須的必要屬性 [：定義屬性引數的存取](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) 子，而且包含在完整性中。

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1019:定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813:避免使用非密封屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>另請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)

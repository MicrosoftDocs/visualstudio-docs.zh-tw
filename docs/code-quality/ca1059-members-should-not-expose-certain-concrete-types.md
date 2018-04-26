---
title: CA1059：成員不應該公開特定的具象類型
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c872685445dddaf55efc8c5880b053c865ff2351
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059：成員不應該公開特定的具象類型
|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見成員是特定具象型別或公開特定的具象類型，透過的其中一個參數或傳回值。 目前，此規則會回報下列的具象類型的風險：

-   型別衍生自<xref:System.Xml.XmlNode?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 具象類型就是具有完整實作 (Implementation) 且因此能加以具現化 (Instantiated) 的類型。 若要允許的成員能廣泛使用，請使用建議的介面取代具象型別。 這可讓成員接受任何實作介面的型別，或是使用所實作之介面的型別。

 下表列出的目標的具象類型，以及其建議的取代項目。

|具象型別|Replacement|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> 使用介面，以減少從 XML 資料來源的特定實作的成員。|

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更至建議的介面的具象型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的訊息是否需要提供具象類型的特定功能。

## <a name="related-rules"></a>相關的規則
 [CA1011：建議將基底類型當做參數傳遞](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
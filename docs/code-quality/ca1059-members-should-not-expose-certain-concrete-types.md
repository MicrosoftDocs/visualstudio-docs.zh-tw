---
title: CA1059:成員不應該公開特定的具象類型
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f24881d04599677c5d45c93fc940286f115d593
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922518"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059:成員不應該公開特定的具象類型

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
外部可見成員是特定的具象類型, 或透過其中一個參數或傳回值來公開特定的具象類型。 目前, 此規則會報告下列實體類型的公開:

- 衍生自<xref:System.Xml.XmlNode?displayProperty=fullName>的類型。

## <a name="rule-description"></a>規則描述
具象類型就是具有完整實作 (Implementation) 且因此能加以具現化 (Instantiated) 的類型。 若要允許廣泛使用成員, 請使用建議的介面來取代具體類型。 這可讓成員接受任何可實作為介面的型別, 或在需要實介面型別的地方使用。

下表列出目標的具象類型和其建議的替代專案。

|具體類型|Replacement|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> 使用介面會將成員與 XML 資料來源的特定執行分隔。|

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形, 請將具體類型變更為建議的介面。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果需要具象類型所提供的特定功能, 則可放心地隱藏此規則中的訊息。

## <a name="related-rules"></a>相關規則
[CA1011考慮以參數的形式傳遞基底類型](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
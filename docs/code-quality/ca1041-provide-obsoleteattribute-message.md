---
title: CA1041:必須提供 ObsoleteAttribute 訊息
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 354d1d2fe99fa55bba7f8a00bf3e9f760ff1dbaf
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842179"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041:必須提供 ObsoleteAttribute 訊息

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因

使用標示的型別或成員<xref:System.ObsoleteAttribute?displayProperty=fullName>屬性，並沒有其<xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>指定的屬性。

根據預設，此規則只會查看外部可見的類型和成員，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

<xref:System.ObsoleteAttribute> 用來標記已被取代的程式庫類型和成員。 程式庫取用者應該避免使用任何類型或已標記為過時的成員。 這是因為它可能不支援，且最後會移除來自較新版本的程式庫。 使用標記的型別或成員的時<xref:System.ObsoleteAttribute>編譯時，<xref:System.ObsoleteAttribute.Message%2A>顯示屬性的屬性。 以便提供使用者有關過時類型或成員的資訊。 這項資訊通常包括多少時間的過時類型或成員會支援程式庫設計人員，並將慣用的取代項目。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，加入`message`參數來<xref:System.ObsoleteAttribute>建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告，因為<xref:System.ObsoleteAttribute.Message%2A>屬性會提供過時的型別或成員的重要資訊。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示過時的成員具有正確宣告<xref:System.ObsoleteAttribute>。

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>另請參閱

- <xref:System.ObsoleteAttribute?displayProperty=fullName>
---
title: CA1058:類型不應該擴充特定基底類型
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44aaead9e00a1fb279666dfc55d4e9496e21139e
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842097"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058:類型不應該擴充特定基底類型

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

型別會擴充基底類型的其中一個：

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

根據預設，此規則只會查看外部可見的類型，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

適用於.NET Framework 第 1 版中，會建議衍生新的例外狀況，從<xref:System.ApplicationException>。 建議變更和新的例外狀況應該衍生自<xref:System.Exception?displayProperty=fullName>或其中一個子類別中<xref:System>命名空間。

請勿建立的子類別<xref:System.Xml.XmlDocument>如果您想要建立基礎物件模型或資料來源的 XML 檢視。

### <a name="non-generic-collections"></a>非泛型集合

使用及/或擴充盡可能的泛型集合。 除非您先前隨附未延伸您的程式碼中的非泛型集合。

**不正確的使用方式的範例**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

**正確使用方式的範例**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請從不同的基底類型或泛型集合衍生型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這項規則違規警告有關<xref:System.ApplicationException>。 安全地隱藏這項規則違規警告有關<xref:System.Xml.XmlDocument>。 它可安全地隱藏非泛型集合有關的警告，如果先前發行的程式碼。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1058.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。
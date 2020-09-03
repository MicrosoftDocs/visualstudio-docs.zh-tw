---
title: CA1058：類型不應該擴充特定基底類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d8e267b1e6203759efc91936a3b13059368a3862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545388"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058:類型不應該擴充特定基底類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的類型會延伸某些基底類型 (Base Type)。 目前，此規則會報告衍生自下列類型的類型：

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>規則描述
 針對 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 第1版，建議從衍生新的例外狀況 <xref:System.ApplicationException> 。 建議已變更，而新的例外狀況應衍生自 <xref:System.Exception?displayProperty=fullName> 或其命名空間中的其中一個子類別 <xref:System> 。

 <xref:System.Xml.XmlDocument>如果您想要建立基礎物件模型或資料來源的 XML 視圖，請不要建立的子類別。

### <a name="non-generic-collections"></a>非泛型集合
 盡可能使用和（或）擴充泛型集合。 除非您先前已寄出，否則請勿在您的程式碼中擴充非泛型集合。

 **不正確使用方式的範例**

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
 若要修正此規則的違規情形，請從不同的基底型別或泛型集合衍生型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告，以避免發生衝突 <xref:System.ApplicationException> 。 您可以放心地隱藏此規則的警告，以避免發生衝突 <xref:System.Xml.XmlDocument> 。 如果先前已發行程式碼，則隱藏非泛型集合的警告是安全的。

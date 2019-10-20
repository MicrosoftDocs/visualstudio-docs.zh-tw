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
ms.openlocfilehash: 9a4663fe3bc09b27bad9eeec05e325f07a3de6f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603059"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058：類型不應該擴充特定的基底類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Category|Microsoft. Design|
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
 針對 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本1，建議從 <xref:System.ApplicationException> 衍生新的例外狀況。 建議已變更，而新的例外狀況應該衍生自 <xref:System> 命名空間中的 <xref:System.Exception?displayProperty=fullName> 或其中一個子類別。

 如果您想要建立基礎物件模型或資料來源的 XML 視圖，請勿建立 <xref:System.Xml.XmlDocument> 的子類別。

### <a name="non-generic-collections"></a>非泛型集合
 盡可能使用和（或）延伸泛型集合。 請勿擴充程式碼中的非泛型集合，除非您先前已寄出。

 **不正確的使用方式範例**

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
 若要修正此規則的違規，請從不同的基底類型或泛型集合衍生類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則中有關 <xref:System.ApplicationException> 違規的警告。 請放心隱藏此規則中有關 <xref:System.Xml.XmlDocument> 違規的警告。 如果先前已發行程式碼，就可以放心地隱藏非泛型集合的相關警告。

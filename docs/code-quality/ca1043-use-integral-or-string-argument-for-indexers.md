---
title: CA1043:必須針對索引子使用整數或字串引數
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ca381d88524535ad042b5bd3efda25f8cc350fa4
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842130"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043:必須針對索引子使用整數或字串引數

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

類型包含使用索引類型以外的其他索引子<xref:System.Int32?displayProperty=fullName>， <xref:System.Int64?displayProperty=fullName>， <xref:System.Object?displayProperty=fullName>，或<xref:System.String?displayProperty=fullName>。

根據預設，此規則只會查看公用和受保護的類型，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

索引子，也就是索引的屬性，應該使用整數或字串類型索引。 這些類型通常會用於編製索引的資料結構，而且增加程式庫的可用性。 使用<xref:System.Object>類型應該限制為這種情況下，在設計階段無法指定特定的整數或字串類型。 如果設計需要其他類型的索引，請重新考慮類型是否表示的邏輯資料存放區。 如果它不代表邏輯資料存放區，使用方法。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將索引變更為整數或字串類型，或使用的方法，而不是索引子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

隱藏這項規則只有在仔細地考量需要非標準的索引子之後的警告。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1043.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例示範使用索引子<xref:System.Int32>索引。

[!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
[!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
[!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>相關的規則

- [CA1023:索引子不應該使用多維](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)
- [CA1024:在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)
---
title: CA1028:列舉儲存區應該是 Int32
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: eee81a96e6841aa77e2056a95bd18979724b62e5
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842400"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028:列舉儲存區應該是 Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

列舉型別的基礎型別不是<xref:System.Int32?displayProperty=fullName>。

根據預設，此規則只會查看公用列舉型別，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 根據預設，<xref:System.Int32?displayProperty=fullName>資料型別用來儲存常數值。 即使您可以變更這個基礎類型，它不是必要或建議大部分的情況下。 沒有顯著的效能改善之後，即可使用資料類型比小<xref:System.Int32>。 如果您無法使用的預設資料類型，您應該使用其中一個的 Common Language 系統 (CLS)-標準的整數類資料類型， <xref:System.Byte>， <xref:System.Int16>， <xref:System.Int32>，或<xref:System.Int64>藉此確定，將以表示列舉型別的所有值符合 CLS 標準的程式設計語言。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正這項規則的違規情形，除非有大小或相容性問題，請使用<xref:System.Int32>。 情況下所在<xref:System.Int32>不夠大，要保存的值，請使用<xref:System.Int64>。 如果回溯相容性需要較小的資料類型，請使用<xref:System.Byte>或<xref:System.Int16>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

回溯相容性問題需要它才，則隱藏此規則的警告。 在應用程式無法遵守此規則通常不會不會造成問題。 在程式庫，其中語言互通性是必要的無法遵守此規則可能會影響您的使用者。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example-of-a-violation"></a>發生違規的範例

下列範例顯示兩個未使用建議的基礎資料類型的列舉。

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>如何修正問題的範例

下列範例會藉由變更基礎資料類型來修正上述違規<xref:System.Int32>。

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>相關的規則

- [CA1008:列舉應該使用零值](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027:以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217:不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700:未命名的列舉值 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712:不要使用型別名稱的列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>
---
title: CA1714:旗標列舉應該使用複數名稱
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24a412161d9f91830486378d4e8228386cfd3fb7
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841906"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714:旗標列舉應該使用複數名稱

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因

列舉型別有<xref:System.FlagsAttribute?displayProperty=fullName>和其名稱結尾不 in'。

根據預設，此規則只會查看外部可見的列舉型別，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

類型標記為<xref:System.FlagsAttribute>是複數，因為此屬性會指出，可以指定多個值的名稱。 比方說，定義一周天數列舉可能被適用於應用程式中，您可以指定多天。 這個列舉型別應該有<xref:System.FlagsAttribute>而且無法在 '天' 呼叫。 類似的列舉型別，允許只指定一天不會有屬性，並可能是 ' day '。

命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

## <a name="how-to-fix-violations"></a>如何修正違規

複數的單字，讓列舉型別的名稱，或移除<xref:System.FlagsAttribute>屬性如果不能同時指定多個列舉值。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏違規情形，如果名稱是複數的字，但不結束中的 '。 比方說，如果先前所述的數日列舉型別已命名為 'DaysOfTheWeek'，這會違反此規則，但不是其意圖的邏輯。 應該隱藏此違規情況。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1714.api_surface = private, internal
```

此類別 （命名） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="related-rules"></a>相關的規則

- [CA1027:以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217:不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [列舉設計](/dotnet/standard/design-guidelines/enum)
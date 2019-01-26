---
title: CA1714:旗標列舉應該使用複數名稱
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: eb6bcfb7684c27104801ec54839b3fc6598cc850
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971347"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714:旗標列舉應該使用複數名稱

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用列舉型別有<xref:System.FlagsAttribute?displayProperty=fullName>和其名稱結尾不 in'。

## <a name="rule-description"></a>規則描述
 類型標記為<xref:System.FlagsAttribute>是複數，因為此屬性會指出，可以指定多個值的名稱。 比方說，定義一周天數列舉可能被適用於應用程式中，您可以指定多天。 這個列舉型別應該有<xref:System.FlagsAttribute>而且無法在 '天' 呼叫。 類似的列舉型別，允許只指定一天不會有屬性，並可能是 ' day '。

 命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 複數的單字，讓列舉型別的名稱，或移除<xref:System.FlagsAttribute>屬性如果不能同時指定多個列舉值。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏違規情形，如果名稱是複數的字，但不結束中的 '。 比方說，如果先前所述的數日列舉型別已命名為 'DaysOfTheWeek'，這會違反此規則，但不是其意圖的邏輯。 應該隱藏此違規情況。

## <a name="related-rules"></a>相關的規則
 [CA1027:以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [列舉設計](/dotnet/standard/design-guidelines/enum)
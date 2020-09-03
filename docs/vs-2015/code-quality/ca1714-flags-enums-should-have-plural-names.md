---
title: CA1714：旗標列舉應該有複數名稱 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 74e93a9644f365120117bd247d2ea8b9d43608cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548183"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714:旗標列舉應該使用複數名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|類別|Microsoft。命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用列舉具有 <xref:System.FlagsAttribute?displayProperty=fullName> ，且其名稱結尾不是 ' '。

## <a name="rule-description"></a>規則描述
 標記具有複數的型別， <xref:System.FlagsAttribute> 因為屬性指出可以指定一個以上的值。 例如，定義星期幾的列舉可能會在您可以指定多天的應用程式中使用。 這個列舉應該有 <xref:System.FlagsAttribute> ，而且可以稱為「Days」。 只允許指定一天的類似列舉不會有屬性，而且可以稱為「日」。

 命名慣例可針對以 common language runtime 為目標的程式庫提供常見的外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶的信賴度，以開發受管理程式碼的專業知識的人員來開發該程式庫。

## <a name="how-to-fix-violations"></a>如何修正違規
 將列舉的名稱設為複數文字， <xref:System.FlagsAttribute> 如果不應該同時指定多個列舉值，請移除屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果名稱是複數文字，但結尾不是 '，則可以放心隱藏違規。 例如，如果先前所述的多天列舉名為 ' DaysOfTheWeek '，這會違反規則邏輯，但不會違反其意圖。 這類違規應 suppressd。

## <a name="related-rules"></a>相關規則
 [CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.FlagsAttribute?displayProperty=fullName>[列舉設計](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)

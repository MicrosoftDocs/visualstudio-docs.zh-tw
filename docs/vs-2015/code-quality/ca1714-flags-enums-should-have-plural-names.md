---
title: CA1714：旗標列舉應該要有複數名稱 |Microsoft Docs
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
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548183"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714:旗標列舉應該使用複數名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|類別|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用列舉具有 <xref:System.FlagsAttribute?displayProperty=fullName> ，且其名稱結尾不是 ' '。

## <a name="rule-description"></a>規則描述
 標記為的類型 <xref:System.FlagsAttribute> 具有複數名稱，因為屬性工作表示可以指定一個以上的值。 例如，定義一周天數的列舉可能會用於可指定多天的應用程式中。 此列舉應該具有 <xref:System.FlagsAttribute> ，而且可以稱為「天」。 只允許指定一天的類似列舉不會有屬性，而且可以稱為「天」。

 命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 <xref:System.FlagsAttribute>如果不應同時指定多個列舉值，請將列舉的名稱設為複數單字，或移除屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果名稱是複數單字，但結尾不是 ' '，則隱藏違規是安全的。 例如，如果先前所述的多天列舉名為 ' DaysOfTheWeek '，這會違反規則的邏輯，而不是其意圖。 這類違規應為 suppressd。

## <a name="related-rules"></a>相關規則
 [CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.FlagsAttribute?displayProperty=fullName>[列舉設計](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)

---
title: CA1717：只有 FlagsAttribute 列舉應該有複數名稱 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c58c218991226a954185853097dc81da36c69ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543685"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717:只有 FlagsAttribute 列舉應該使用複數名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|類別|Microsoft。命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見列舉的名稱會以複數單字結尾，且列舉不會以 <xref:System.FlagsAttribute?displayProperty=fullName> 屬性標記。

## <a name="rule-description"></a>規則描述
 命名慣例規定列舉的複數名稱表示可以同時指定一個以上的列舉值。 會 <xref:System.FlagsAttribute> 告知編譯器應該將列舉視為位欄位，以啟用列舉上的位運算。

 如果一次只能指定一個列舉值，則列舉的名稱應該是單數的單字。 例如，定義星期幾的列舉可能會在您可以指定多天的應用程式中使用。 這個列舉應該有 <xref:System.FlagsAttribute> ，而且可以稱為「Days」。 只允許指定一天的類似列舉不會有屬性，而且可以稱為「日」。

 命名慣例可針對以 common language runtime 為目標的程式庫提供常見的外觀。 這可減少學習新軟體程式庫所需的時間，並提高客戶的信賴度，以開發受管理程式碼的專業知識的人員來開發該程式庫。

## <a name="how-to-fix-violations"></a>如何修正違規
 將列舉的名稱設為單數位或加入 <xref:System.FlagsAttribute> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果名稱以單數位結尾，則可以安全地隱藏規則中的警告。

## <a name="related-rules"></a>相關規則
 [CA1714:旗標列舉應該使用複數名稱](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.FlagsAttribute?displayProperty=fullName>[列舉設計](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)

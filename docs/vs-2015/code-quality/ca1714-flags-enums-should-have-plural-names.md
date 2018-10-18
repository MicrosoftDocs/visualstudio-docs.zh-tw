---
title: ： 旗標列舉應該 ca1714 複數名稱 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cbc6019b3ead7d65ad4b9cdb7e389cd4d22d75e1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235140"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714：旗標列舉應該使用複數名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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
 它可安全地隱藏違規情形，如果名稱是複數的字，但不結束中的 '。 比方說，如果先前所述的數日列舉型別已命名為 'DaysOfTheWeek'，這會違反此規則，但不是其意圖的邏輯。 這類違規應該才能隱藏。

## <a name="related-rules"></a>相關的規則
 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.FlagsAttribute?displayProperty=fullName> [列舉設計](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)




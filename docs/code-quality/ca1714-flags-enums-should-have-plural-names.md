---
title: ': Ca1714 旗標列舉應該使用複數名稱 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5dc35718a20743ce6ed1502dbd1d9ed3c8a626e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714：旗標列舉應該使用複數名稱
|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用列舉型別的<xref:System.FlagsAttribute?displayProperty=fullName>其名稱結尾不是和中的 '。  
  
## <a name="rule-description"></a>規則描述  
 與標記的型別<xref:System.FlagsAttribute>為複數，因為此屬性會指出，可以指定多個值的名稱。 例如，定義一周天數的列舉可能被適用於應用程式中您可以在此指定多天。 這個列舉型別應該具有<xref:System.FlagsAttribute>和天' 呼叫。 類似的列舉型別，可讓某一天指定沒有屬性，且可能 ' day '。  
  
 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 讓列舉型別的名稱複數單字，或移除<xref:System.FlagsAttribute>屬性如果不能同時指定多個列舉值。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它是以隱藏違規情形，如果名稱為複數的字，但結尾不是安全的 '。 比方說，如果先前已詳述於多天列舉已命名為 'DaysOfTheWeek'，這會違反此規則，但不是其對應方式的邏輯。 這類違規應該計數器。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [列舉設計](/dotnet/standard/design-guidelines/enum)
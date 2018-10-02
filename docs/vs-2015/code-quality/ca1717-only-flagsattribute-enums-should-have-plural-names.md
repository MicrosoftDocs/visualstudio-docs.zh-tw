---
title: ： 只有 FlagsAttribute 列舉應該 ca1717 複數名稱 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5fbaa220d39f72900dbf03d238a45fc988b65e6b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588489"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717：只有 FlagsAttribute 列舉應該使用複數名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1717： 只有 FlagsAttribute 列舉應該使用複數名稱](https://docs.microsoft.com/visualstudio/code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names)。

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的列舉型別名稱結尾的複數的單字和列舉型別未標示為<xref:System.FlagsAttribute?displayProperty=fullName>屬性。

## <a name="rule-description"></a>規則描述
 命名慣例指定列舉的複數名稱表示可以同時指定多個列舉值。 <xref:System.FlagsAttribute>會告知編譯器應該列舉型別視為位元欄位，可讓列舉的位元運算。

 如果只有一個值的列舉型別，可以指定一次，列舉型別的名稱應該是單數的單字。 比方說，定義一周天數列舉可能被適用於應用程式中，您可以指定多天。 這個列舉型別應該有<xref:System.FlagsAttribute>而且無法在 '天' 呼叫。 類似的列舉型別，允許只指定一天不會有屬性，並可能是 ' day '。

 命名慣例提供了通用程式庫 common language runtime 為目標。 這可減少的時間，才能了解新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 讓列舉型別名稱的單數的單字，或新增<xref:System.FlagsAttribute>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏規則的警告，如果名稱結尾的單數的單字。

## <a name="related-rules"></a>相關的規則
 [CA1714：旗標列舉應該使用複數名稱](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.FlagsAttribute?displayProperty=fullName> [列舉設計](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)




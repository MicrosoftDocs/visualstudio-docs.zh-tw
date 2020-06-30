---
title: CA1702：複合單字的大小寫應正確 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f9dc15cec4012d2b63eb5f21c25bd709961c95c8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544075"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702:複合字應該使用正確的大小寫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱[CA1702：複合字的大小寫應正確](/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly)。

|Item|值|
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|類別|Microsoft. 命名|
|中斷變更|中斷-在元件上引發。<br /><br /> 非中斷-在型別參數上引發時。|

## <a name="cause"></a>原因
 識別碼的名稱包含多個單字，而且至少有一個單字顯示為大小寫不正確的複合字。

## <a name="rule-description"></a>規則描述
 識別碼的名稱會分割成以大小寫為基礎的單字。 Microsoft 拼寫檢查程式庫會檢查每個連續的兩個單字組合。 如果可辨識，識別碼會產生規則違規。 造成違規的複合單字範例包括「總和檢查碼」和「多部分」，分別應該以「總和檢查碼」和「多部分」為大小寫。 由於先前的常見用法，規則中內建了數個例外狀況，而且有數個單字標示為「工具列」和「檔案名」，其大小寫應為兩個不同的字組（在此案例中為「工具列」和「檔案名」）。

 命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 請變更名稱，使其大小寫正確。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果拼寫字典能夠辨識複合單字的兩個部分，而且其目的是要使用兩個字組，則可放心地隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>另請參閱
 [命名方針](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)[大小寫慣例](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)

---
title: CA1701：資源字串複合字應該是正確的大小寫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7610852f6d9fbea2fbd2dd10d478ad2d1a0da899
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669263"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701：資源字串複合字應該使用正確的大小寫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Category|Microsoft. 命名|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 資源字串包含不是以正確的大小寫呈現的複合字。

## <a name="rule-description"></a>規則描述
 資源字串中的每個單字都會分割成以大小寫為基礎的權杖。 連續兩個語彙基元的組合都由 Microsoft 拼字檢查程式庫進行檢查。 如果可以辨識，這個字便會產生規則違規。 造成違規的複合單字範例包括「總和檢查碼」和「多部分」，分別應該以「總和檢查碼」和「多部分」為大小寫。 由於先前的常見用法，規則中內建了數個例外狀況，而且有幾個單字標示為旗標，例如「工具列」和「檔案名」，其大小寫應為兩個不同的字組。 在此範例中，「工具列」和「檔案名」會加上旗標。

 命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 變更單字，使其大小寫正確。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果拼寫字典能夠辨識複合單字的兩個部分，而且其目的是要使用兩個字組，則可放心地隱藏此規則的警告。

 您也可以在拼寫檢查的自訂字典中加入複合字組。 自訂字典中的單字不會造成違規。 如需詳細資訊，請參閱[如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

## <a name="related-rules"></a>相關規則
 [CA1702：複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>請參閱
 [大小寫慣例](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)[命名指導方針](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)

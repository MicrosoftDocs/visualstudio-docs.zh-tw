---
title: CA1701：資源字串複合字應該正確的大小寫 |Microsoft Docs
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
ms.openlocfilehash: 7c1c3b0fd6cf3a25d5db9e3039d4dc5d8364a18e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544101"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701:資源字串複合字應該使用正確的大小寫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|類別|Microsoft。命名|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 資源字串包含的複合字不會正確地以正確的大小寫。

## <a name="rule-description"></a>規則描述
 資源字串中的每個單字都會根據大小寫分割為標記。 連續兩個語彙基元的組合都由 Microsoft 拼字檢查程式庫進行檢查。 如果可以辨識，這個字便會產生規則違規。 造成違規的複合單字範例包括「總和檢查碼」和「多部分」，其應分別以「總和檢查碼」和「多部分」為大寫。 由於先前的常見用法，規則內建了數個例外狀況，且會將數個單字標記為旗標（例如 "Toolbar" 和 "Filename"），並以兩個不同的單字作為大小寫。 在此範例中，會將 "ToolBar" 和 "FileName" 標示為旗標。

 命名慣例可針對以 common language runtime 為目標的程式庫提供常見的外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶的信賴度，以開發受管理程式碼的專業知識的人員來開發該程式庫。

## <a name="how-to-fix-violations"></a>如何修正違規
 變更字組，使其大小寫正確。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果拼寫字典可辨識複合單字的兩個部分，而且意圖是使用兩個字，則可以安全地隱藏此規則的警告。

 您也可以將複合字新增至拼寫檢查的自訂字典。 自訂字典中的單字不會造成違規。 如需詳細資訊，請參閱 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

## <a name="related-rules"></a>相關規則
 [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>另請參閱
 [大小寫慣例](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)[命名方針](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)

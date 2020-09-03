---
title: CA1702：複合字應該正確的大小寫 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544075"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702:複合字應該使用正確的大小寫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱 [CA1702：複合字應該正確的大小寫](/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly)。

|Item|值|
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|類別|Microsoft。命名|
|中斷變更|重大-引發于元件上。<br /><br /> 在類型參數上引發時，不會中斷。|

## <a name="cause"></a>原因
 識別碼的名稱包含多個單字，且至少有一個單字看似不正確的複合字。

## <a name="rule-description"></a>規則描述
 識別碼的名稱會根據大小寫分割為單字。 Microsoft 拼寫檢查庫會檢查每個連續的雙字組組合。 如果可辨識，則識別碼會產生規則違規。 造成違規的複合單字範例包括「總和檢查碼」和「多部分」，其應分別以「總和檢查碼」和「多部分」為大寫。 由於先前的常見用法，規則中內建了數個例外狀況，且會將數個單字標示為標示為兩個不同的單字，例如 "toolbar" 和 "Filename"， (在此案例中為 "ToolBar" 和 "FileName" ) 。

 命名慣例可針對以 common language runtime 為目標的程式庫提供常見的外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶的信賴度，以開發受管理程式碼的專業知識的人員來開發該程式庫。

## <a name="how-to-fix-violations"></a>如何修正違規
 變更名稱，使其大小寫正確。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果拼寫字典可辨識複合單字的兩個部分，而且意圖是使用兩個字，則可以安全地隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>另請參閱
 [命名方針](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)[大小寫慣例](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)

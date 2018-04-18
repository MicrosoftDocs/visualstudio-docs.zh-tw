---
title: CA1709： 識別項應該使用的大小寫正確 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c010019c2ae5d1044d11c02c22428dda4197fcd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709：識別項名稱應該使用正確的大小寫
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|分類|Microsoft.Naming|  
|中斷變更|中斷-產生的組件、 命名空間、 類型、 成員和參數時。<br /><br /> 非中斷-時引發的泛型類型參數。|  
  
## <a name="cause"></a>原因  
 識別項名稱大小寫不正確。  
  
 \-或-  
  
 識別項名稱包含兩個字母縮寫，第二個字母為小寫。  
  
 \-或-  
  
 識別項名稱包含三個或多個大寫字母的縮略字。  
  
## <a name="rule-description"></a>規則描述  
 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。  
  
 依照慣例，參數名稱是使用 camel 命名法的大小寫。命名空間、 類型和成員名稱使用 pascal 命名法的大小寫慣例。 依照 camel 命名法的大小寫慣例的名稱，第一個字母為小寫，而任何其餘的文字，在名稱中的第一個字母為大寫。 依照 camel 命名法的大小寫慣例名稱的範例是"packetSniffer"、"ioFile，"和"fatalErrorCode"。 依照 pascal 命名法的大小寫慣例的名稱，第一個字母也是大寫，而任何其餘的文字，在名稱中的第一個字母為大寫。 使用 Pascal 大小寫名稱的範例是"PacketSniffer"、"IOFile，"和"FatalErrorCode"。  
  
 此規則會將名稱分割為根據大小寫的單字，並檢查任何兩個字母的單字針對常見的兩個字母單字，例如 「 位置 」 或 「 我的 」 的清單。 如果找不到相符項目，這個字會假設為縮略字。 此外，這項規則假設名稱包含一個資料列中的四個大寫字母或在名稱結尾處的資料列中的三個大寫字母時找到的縮寫字。  
  
 依照慣例，兩個字母縮略字會使用全部大寫的字母和三個或多個字元的首字母縮略字使用 pascal 命名法的大小寫慣例。 下列範例會使用此命名慣例: 'DB'、 'CR'、 'Cpa，' 和 'Ecma'。 下列範例違反慣例: 'Io'、 'XML' 和 'DoD'，nonparameter 名稱、 'xp' 及 'cpl'。  
  
 'ID' 是特殊案例會造成這項規則的違規情形。 'Id' 不是縮略字，而是 'identification' 的縮寫。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 變更名稱，是正確的大小寫。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏這個警告，或如果您有自己的命名慣例，如果識別項會表示為正確名稱，例如，公司或技術的名稱。  
  
 您也可以新增特定詞彙、 縮寫和首字母縮略字，程式碼分析自訂字典。 自訂字典中指定的詞彙不會違反此規則。 如需詳細資訊，請參閱[How to： 自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>相關的規則  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
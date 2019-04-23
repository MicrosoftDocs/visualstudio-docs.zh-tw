---
title: CA1709:識別項應該使用正確的大小寫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b447b111cedc30aa23f3aaad0fbc964a5d8a2bd2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669350"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709:識別項名稱應該使用正確的大小寫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新文件，請參閱[CA1709:識別項應該使用正確的大小寫](https://docs.microsoft.com/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly)。  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|分類|Microsoft.Naming|  
|中斷變更|中斷-時產生組件、 命名空間、 類型、 成員和參數。<br /><br /> 非分行-時引發的泛型類型參數。|  
  
## <a name="cause"></a>原因  
 識別項的名稱大小寫不正確。  
  
 \-或-  
  
 識別項的名稱包含兩個字母縮寫，第二個字母是小寫。  
  
 \-或-  
  
 識別項的名稱包含的三個以上的大寫英文字母的縮寫。  
  
## <a name="rule-description"></a>規則描述  
 命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。  
  
 依照慣例，參數名稱使用駝峰式命名法的大小寫;命名空間、 類型和成員名稱使用 pascal 命名法大小寫。 駝峰式大小寫字的名稱，第一個字母是小寫，則所有剩餘的文字，在名稱中的第一個字母為大寫。 使用依照 camel 命名法大小寫名稱的範例是"packetSniffer"、"ioFile 」 和 「 fatalErrorCode"。 Pascal 命名法大小寫的名稱，第一個字母是大寫，，並在名稱中任何剩餘的單字的第一個字母為大寫。 Pascal 命名法大小寫名稱的範例是"PacketSniffer"、"IOFile 」 和 「 FatalErrorCode"。  
  
 此規則會分割成依大小寫的字組的名稱，並檢查任何兩個字母的單字針對常見的兩個字母字詞，例如"In"或"My"的清單。 如果找不到相符項目，word 會假設為縮略字。 此外，這項規則假設名稱包含一個資料列中的四個大寫字母或在名稱結尾處的資料列中的三個大寫字母時找到的縮寫。  
  
 依照慣例，兩個字母縮寫全部使用大寫字母，和縮略字的三個或多個字元使用 pascal 命名法大小寫。 下列範例會使用此命名慣例：'DB'、 'C'、 'Cpa、' 和 'Ecma'。 下列範例會違反慣例：'Io'、 'XML' 和 'DoD'、 以及 nonparameter 名稱、 'xp' 和 'cpl'。  
  
 'ID' 是特殊案例，讓這項規則的違規情形。 'Id' 不是縮略字，而是 'identification' 的縮寫。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 是正確的大小寫，請變更名稱。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它會安全地隱藏這個警告，如果您有自己的命名慣例，或如果識別項表示適當的名稱，例如公司或技術的名稱。  
  
 您也可以新增特定詞彙、 縮寫及縮略字，加入程式碼分析自訂字典。 指定自訂的字典中的詞彙不會造成違反此規則。 如需詳細資訊，請參閱[如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>相關的規則  
 [CA1708:識別項應該不僅為大小寫不同](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

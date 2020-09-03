---
title: CA1709：識別碼的大小寫應該正確 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14c50ed94f05401cc5575af9f8b98472c35b261d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543997"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709:識別項名稱應該使用正確的大小寫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱 [CA1709：識別碼應該正確的大小寫](/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly)。

|Item|值|
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|類別|Microsoft。命名|
|中斷變更|重大-引發于元件、命名空間、類型、成員和參數上。<br /><br /> 在泛型型別參數上引發時，不會中斷。|

## <a name="cause"></a>原因
 識別碼的名稱的大小寫不正確。

 \- 或 -

 識別碼的名稱包含兩個字母的縮寫，而第二個字母是小寫。

 \- 或 -

 識別碼的名稱包含三個或更多大寫字母的縮寫。

## <a name="rule-description"></a>規則描述
 命名慣例可針對以 common language runtime 為目標的程式庫提供常見的外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶的信賴度，以開發受管理程式碼的專業知識的人員來開發該程式庫。

 依照慣例，參數名稱使用 camel 大小寫;命名空間、類型和成員名稱使用 Pascal 大小寫。 在 camel 大寫字母的名稱中，第一個字母是小寫，而名稱中任何其餘單字的第一個字母都是大寫。 Camel 大小寫名稱的範例包括 "packetSniffer"、"ioFile" 和 "fatalErrorCode"。 在 Pascal 大小寫名稱中，第一個字母是大寫，而名稱中任何其餘單字的第一個字母都是大寫。 Pascal 大小寫名稱的範例包括 "PacketSniffer"、"IOFile" 和 "FatalErrorCode"。

 此規則會根據大小寫將名稱分割為單字，並根據常見的兩個字母單字清單（例如「In」或「My」）來檢查任何兩個字母的字組。 如果找不到相符項，則會假設該單字為縮寫。 此外，如果名稱的資料列中有四個大寫字母，或在名稱結尾的資料列中有三個大寫字母，則此規則會假設它已找到縮寫。

 依照慣例，兩個字母的縮寫會使用所有大寫字母，而三個或更多字元的縮寫則使用 Pascal 大小寫。 下列範例使用此命名慣例： ' DB '、' CR '、' Cpa ' 和 ' Ecma '。 下列範例違反慣例： ' Io '、' XML ' 和 ' DoD '，以及 nonparameter 名稱、' xp ' 和 ' cpl '。

 ' ID ' 具有特殊大小寫，導致此規則違規。 'Id' 不是縮略字，而是 'identification' 的縮寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 變更名稱，使其大小寫正確。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您有自己的命名慣例，或如果識別碼代表正確的名稱（例如公司或技術的名稱），就可以安全地隱藏這個警告。

 您也可以將特定詞彙、縮寫和縮寫新增至程式碼分析自訂字典。 自訂字典中指定的詞彙不會造成此規則違規。 如需詳細資訊，請參閱 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>相關規則
 [CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

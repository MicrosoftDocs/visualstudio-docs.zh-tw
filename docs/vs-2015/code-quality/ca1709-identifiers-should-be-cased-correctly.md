---
title: CA1709：識別碼的大小寫應正確 |Microsoft Docs
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
ms.openlocfilehash: c4da0414c9923a8ed7bb01456f38000433641522
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919226"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709：識別項名稱應該使用正確的大小寫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱[CA1709：識別碼的大小寫應正確](/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly)。

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|分類|Microsoft. 命名|
|中斷變更|中斷-在元件、命名空間、類型、成員和參數上引發時。<br /><br /> 非中斷-在泛型型別參數上引發時。|

## <a name="cause"></a>原因
 識別碼的名稱不是正確的大小寫。

 \-或-

 識別碼的名稱包含兩個字母的縮寫，而第二個字母則是小寫。

 \-或-

 識別碼的名稱包含三個或多個大寫字母的縮略字。

## <a name="rule-description"></a>規則描述
 命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

 依照慣例，參數名稱會使用 camel 大小寫;命名空間、類型和成員名稱使用 Pascal 大小寫。 在 camel 大小寫名稱中，第一個字母是小寫，而名稱中任何其餘單字的第一個字母是大寫。 Camel 大小寫名稱的範例包括 "packetSniffer"、"ioFile" 和 "fatalErrorCode"。 在 Pascal 大小寫名稱中，第一個字母是大寫，而名稱中任何其餘單字的第一個字母是大寫。 Pascal 大小寫名稱的範例包括 "PacketSniffer"、"IOFile" 和 "FatalErrorCode"。

 此規則會根據大小寫將名稱分割成單字，並檢查兩個字母的單字是否符合一份共通的兩個字母單字，例如 "In" 或 "My"。 如果找不到相符的文字，則會假設為縮寫。 此外，此規則假設在名稱結尾的資料列中，名稱包含四個大寫字母或三個大寫字母的縮寫時，它就會找到縮略字。

 依照慣例，兩個字母的縮寫會使用全部大寫字母，而三個或更多字元的縮略字會使用 Pascal 大小寫。 下列範例會使用此命名慣例： ' DB '、' CR '、' Cpa ' 和 ' Ecma '。 下列範例違反慣例： ' Io '、' XML ' 和 ' DoD '，以及適用于 nonparameter 名稱、' xp ' 和 ' cpl '。

 ' ID ' 具有特殊大小寫，因而導致此規則違規。 'Id' 不是縮略字，而是 'identification' 的縮寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 請變更名稱，使其大小寫正確。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您有自己的命名慣例，或識別碼代表適當的名稱，例如公司或技術的名稱，則隱藏此警告是安全的。

 您也可以在程式碼分析自訂字典中加入特定詞彙、縮寫和縮略字。 在自訂字典中指定的詞彙不會造成此規則違規。 如需詳細資訊，請參閱[如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>相關規則
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

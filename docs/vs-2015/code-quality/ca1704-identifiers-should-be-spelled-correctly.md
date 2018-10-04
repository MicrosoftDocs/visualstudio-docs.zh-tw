---
title: CA1704： 識別項應該使用正確的拼字 |Microsoft Docs
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
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 90b5085e92be22099fbf6bd8729a62223b1c93aa
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588088"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704：識別項應該使用正確的拼字
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1704： 識別項應該使用正確的拼字](https://docs.microsoft.com/visualstudio/code-quality/ca1704-identifiers-should-be-spelled-correctly)。

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別項的名稱包含一或多個 Microsoft 拼字檢查程式庫無法辨識的字。 不，此規則就不會檢查建構函式或特殊命名的成員，例如 get 和 set 屬性存取子。

## <a name="rule-description"></a>規則描述
 此規則會識別項剖析為語彙基元，並檢查每個語彙基元的拼字。 剖析的演算法會執行下列轉換：

-   大寫字母會啟動新的權杖。 比方說，MyNameIsJoe 會語彙基元化為"My"、"Name"、"Is"、"Joe"。

-   對於多個大寫字母，最後一個大寫的字母會啟動新的權杖。 比方說，GUIEditor 會語彙基元化為"GUI 」，「 編輯器 」。

-   會移除開頭和尾端單引號。 例如，'sender' 會語彙基元化為"sender"。

-   表示權杖結尾底線，且會移除。 比方說，Hello_world 會語彙基元化為"Hello"，"world"。

-   會移除內嵌的連字號。 例如，for&mat 會語彙基元化為 "format"。

 預設情況下，會使用英文 (en) 版本的拼字檢查程式。 目前使用任何其他語言字典不。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，更正這個字的拼字，或將該字加入至名為 CustomDictionary.xml 自訂字典。 將字典中的工具，[專案目錄中，安裝目錄，或使用者的設定檔] 下方的工具相關聯的目錄中 (%USERPROFILE%\Application 資料\\...)。若要了解如何加入自訂字典中的專案[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，請參閱[How to： 自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

-   新增應該不會造成違反 Recognized/單字字典/路徑下的單字。

-   新增應該會造成無法識別字典/文字/路徑下的違規的單字。

-   新增應該標示的文字，為即將淘汰字典/文字/路徑下已過時。 請參閱相關的規則主題[ca1726 建議： 使用慣用的詞彙](../code-quality/ca1726-use-preferred-terms.md)如需詳細資訊。

-   加入至字典/首字母縮略字/CasingExceptions 路徑的首字母縮略字大小寫規則的例外狀況。

 以下是結構的範例中的自訂字典檔案。

```
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告，才有刻意拼錯的文字和一組有限的程式庫適用於 word。 正確拼寫的字會縮短學習曲線所需的新軟體程式庫。

## <a name="related-rules"></a>相關的規則
 [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703：資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707：識別項名稱不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726：建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>另請參閱
 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)




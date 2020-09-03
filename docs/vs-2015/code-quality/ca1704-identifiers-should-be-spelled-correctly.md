---
title: CA1704：識別碼應該正確拼寫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5e078fc1bb7fe247d541e7695e98c2de76c2466
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544062"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704:識別項應該使用正確的拼字
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|類別|Microsoft。命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別碼的名稱包含一或多個 Microsoft 拼寫檢查庫無法辨識的字詞。 此規則不會檢查函式或特殊命名的成員，例如 get 和 set 屬性存取子。

## <a name="rule-description"></a>規則描述
 此規則會將識別碼剖析為權杖，並檢查每個權杖的拼寫。 剖析演算法會執行下列轉換：

- 大寫字母會開始新的權杖。 例如，MyNameIsJoe token 化 to "My"，"Name"，"Name"，"Joe"。

- 針對多個大寫字母，最後一個大寫字母會開始新的權杖。 例如，GUIEditor token 化至 "GUI"、"Editor"。

- 開頭和尾端的單引號會遭到移除。 例如，「寄件者」 token 化至「寄件者」。

- 底線表示權杖的結尾，並被移除。 例如，Hello_world token 化為 "Hello"、"world"。

- 移除內嵌的 & 符號。 例如，針對&token 化] 的 [格式]。

  根據預設，會使用拼寫檢查程式的英文 (en) 版本。 目前沒有其他語言字典可用。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請更正單字的拼寫，或將文字加入名為 CustomDictionary.xml 的自訂字典。 將字典放在工具的安裝目錄、專案目錄中，或是與使用者設定檔（位於 [使用者 (%USERPROFILE%\Application Data ... ) ] 下的工具相關聯的目錄中。 \\若要瞭解如何將自訂字典新增至中的專案 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，請參閱 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- 在字典/單字/無法辨識的路徑下新增不應造成違規的單字。

- 新增在字典/單字/無法辨識的路徑下出現違規的單字。

- 新增在字典/單字/已被取代的路徑下應標示為過時的單字。 如需詳細資訊，請參閱相關的規則主題 [ca1726 建議：使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)。

- 將縮寫大小寫規則的例外狀況新增至字典/縮略字/CasingExceptions 路徑。

  以下是自訂字典檔案的結構範例。

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
 只有當單字刻意拼錯，且該單字適用于一組有限的程式庫時，才會隱藏此規則的警告。 拼寫正確的單字可減少新軟體程式庫所需的學習曲線。

## <a name="related-rules"></a>相關規則
 [CA2204:常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707:識別項名稱不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726:建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>另請參閱
 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

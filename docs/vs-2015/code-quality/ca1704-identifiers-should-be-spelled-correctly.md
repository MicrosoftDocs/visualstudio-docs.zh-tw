---
title: CA1704：識別碼應正確拼寫 |Microsoft Docs
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
ms.openlocfilehash: 56ac5e60964621859c77bf53dc4f6c14480b4a83
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669245"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704：識別項應該使用正確的拼字
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Category|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別碼的名稱包含一或多個 Microsoft 拼寫檢查程式庫無法辨識的文字。 此規則不會檢查函數或特殊命名的成員，例如 get 和 set 屬性存取子。

## <a name="rule-description"></a>規則描述
 此規則會將識別碼剖析為權杖，並檢查每個權杖的拼寫。 剖析演算法會執行下列轉換：

- 大寫字母會開始新的權杖。 例如，MyNameIsJoe token 化 to "My"，"Name"，"Is"，"Joe"。

- 若使用多個大寫字母，則最後一個大寫字母會啟動新的 token。 例如，GUIEditor token 化 to "GUI"，"Editor"。

- 開頭和尾端的撇號會被移除。 例如，「寄件者」 token 化為「寄件者」。

- 底線表示標記的結尾，並已移除。 例如，Hello_world token 化 to "Hello"，"world"。

- 已移除內嵌的符號。 例如，& 的 token 化為「格式」。

  根據預設，會使用拼寫檢查的英文（en）版本。 目前未提供任何其他語言字典。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請更正單字的拼寫，或將此單字加入名為 CustomDictionary 的自訂字典中。 將字典放在工具的安裝目錄、專案目錄或與使用者設定檔（%USERPROFILE%\Application Data \\ ...）下的工具相關聯的目錄中。若要瞭解如何在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中將自訂字典加入至專案，請參閱[如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- 新增不應在字典/單字/已辨識路徑下造成違規的文字。

- 新增在字典/單字/無法辨識的路徑底下應造成違規的文字。

- 新增在字典/單字/已取代路徑底下應標示為過時的文字。 如需詳細資訊，請參閱相關的規則主題[ca1726 建議：使用慣用的字詞](../code-quality/ca1726-use-preferred-terms.md)。

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
 只有在 word 故意拼錯，而且該單字適用于一組有限的程式庫時，才會隱藏此規則的警告。 拼寫正確的文字會減少新軟體程式庫所需的學習曲線。

## <a name="related-rules"></a>相關規則
 [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703：資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707：識別項名稱不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726：建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>請參閱
 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

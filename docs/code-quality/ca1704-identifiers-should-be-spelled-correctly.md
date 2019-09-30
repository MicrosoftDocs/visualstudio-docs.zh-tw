---
title: CA1704:識別項應該使用正確的拼字
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa04ca237134c1947b5c58b921f87f32a1ecfb16
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234298"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704:識別項應該使用正確的拼字

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|分類|Microsoft.Naming|
|重大變更|中斷|

## <a name="cause"></a>原因

識別碼的名稱包含一或多個 Microsoft 拼寫檢查程式庫無法辨識的文字。 此規則不會檢查函數或特殊命名的成員，例如 get 和 set 屬性存取子。

## <a name="rule-description"></a>規則描述

此規則會將識別碼剖析為權杖，並檢查每個權杖的拼寫。 剖析演算法會執行下列轉換：

- 大寫字母會開始新的權杖。 例如，MyNameIsJoe token 化 to "My"，"Name"，"Is"，"Joe"。

- 若使用多個大寫字母，則最後一個大寫字母會啟動新的 token。 例如，GUIEditor token 化 to "GUI"，"Editor"。

- 開頭和尾端的撇號會被移除。 例如，「寄件者」 token 化為「寄件者」。

- 底線表示標記的結尾，並已移除。 例如，Hello_world token 化 to "Hello"，"world"。

- 已移除內嵌的符號。 例如，& 的 token 化為「格式」。

## <a name="language"></a>語言

「拼寫檢查」目前只會針對以英文為基礎的文化特性字典進行檢查。 您可以藉由新增**CodeAnalysisCulture**元素，在專案檔中變更專案的文化特性。

例如：

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> 如果您將文化特性設定為英文文化特性以外的任何專案，則會以無訊息模式停用此程式碼分析規則。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請更正單字的拼寫，或將此單字加入自訂字典。

### <a name="to-add-words-to-a-custom-dictionary"></a>若要將文字加入至自訂字典

將自訂字典 XML 檔案命名為*CustomDictionary*。 將字典放在工具的安裝目錄、專案目錄，或與使用者設定檔（ *\\%USERPROFILE%\Application Data ...* ）下的工具相關聯的目錄中。若要瞭解如何在 Visual Studio 中將自訂字典加入至專案， [請參閱如何：自訂程式碼分析](../code-quality/how-to-customize-the-code-analysis-dictionary.md)字典。

- 新增不應在字典/單字/已辨識路徑下造成違規的文字。

- 新增在字典/單字/無法辨識的路徑底下應造成違規的文字。

- 新增在字典/單字/已取代路徑底下應標示為過時的文字。 請參閱相關的規則[主題 ca1726 建議：如需詳細](../code-quality/ca1726-use-preferred-terms.md)資訊，請使用慣用的字詞。

- 將縮寫大小寫規則的例外狀況新增至字典/縮略字/CasingExceptions 路徑。

以下是自訂字典檔案的結構範例：

```xml
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

- [CA2204常值的拼寫應該正確](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703資源字串的拼寫應該正確](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709識別碼的大小寫應該正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708識別碼應該不同于大小寫](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707識別碼不應包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726 建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>另請參閱

- [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

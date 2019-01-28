---
title: CA1704:識別項應該使用正確的拼字
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: cfb91c830239a61b3f7f7e58364ae41c87152321
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935653"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704:識別項應該使用正確的拼字

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

- 大寫字母會啟動新的權杖。 比方說，MyNameIsJoe 會語彙基元化為"My"、"Name"、"Is"、"Joe"。

- 對於多個大寫字母，最後一個大寫的字母會啟動新的權杖。 比方說，GUIEditor 會語彙基元化為"GUI 」，「 編輯器 」。

- 會移除開頭和尾端單引號。 例如，'sender' 會語彙基元化為"sender"。

- 表示權杖結尾底線，且會移除。 比方說，Hello_world 會語彙基元化為"Hello"，"world"。

- 會移除內嵌的連字號。 例如，for&mat 會語彙基元化為 "format"。

## <a name="language"></a>語言

拼字檢查工具目前會檢查只會針對英文版為基礎的文化特性的字典。 您可以加入，以變更您的專案在專案檔中的文化特性**CodeAnalysisCulture**項目。

例如: 

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> 如果您將文化特性設定為以英文為基礎的文化特性以外的任何項目時，此程式碼分析規則是以無訊息模式停用。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，更正這個字的拼字，或將該字加入至自訂字典。

### <a name="to-add-words-to-a-custom-dictionary"></a>若要將文字加入自訂字典

將檔案命名為自訂字典 XML *CustomDictionary.xml*。 在安裝目錄的工具，[專案目錄中，或使用者的設定檔] 下方的工具相關聯的目錄中放置字典 (*%USERPROFILE%\Application 資料\\...*).若要了解如何在 Visual Studio 中的專案中加入自訂字典，請參閱[How to:自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

- 新增應該不會造成違反 Recognized/單字字典/路徑下的單字。

- 新增應該會造成無法識別字典/文字/路徑下的違規的單字。

- 新增應該標示的文字，為即將淘汰字典/文字/路徑下已過時。 請參閱相關的規則主題[ca1726 建議：使用慣用的詞彙](../code-quality/ca1726-use-preferred-terms.md)如需詳細資訊。

- 加入至字典/首字母縮略字/CasingExceptions 路徑的首字母縮略字大小寫規則的例外狀況。

結構的自訂字典檔案範例如下：

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

隱藏此規則的警告，才有刻意拼錯的文字和一組有限的程式庫適用於 word。 正確拼寫的字會縮短學習曲線所需的新軟體程式庫。

## <a name="related-rules"></a>相關的規則

- [CA2204:常值應該使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708:識別項應該不僅為大小寫不同](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707:識別項不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726： 建議使用慣用的詞彙](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>另請參閱

- [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

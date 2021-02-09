---
title: 如何：自訂程式碼分析字典
ms.date: 11/04/2016
description: 瞭解可識別拼寫和命名慣例錯誤的程式碼分析字典。 瞭解如何建立自訂字典，並將其套用至專案。
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10466acedcd5c7f5fda835d66e654128a556d0a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860096"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>如何：自訂程式碼分析字典

程式碼分析會使用內建的字典來檢查程式碼中的識別碼，以取得拼寫、語法案例和其他 .NET 設計指導方針的命名慣例錯誤。 您可以建立自訂字典 Xml 檔案，以新增、移除或修改內建字典的詞彙、縮寫和縮寫。

例如，假設您的程式碼包含一個名為 **DoorKnokker** 的類別。 程式碼分析會將名稱識別為兩個單字的複合： **門** 和 **knokker**。 然後，它會引發 **knokker** 未正確拼寫的警告。 若要強制程式碼分析辨識拼寫，您可以將「詞彙 **knokker** 」新增至自訂字典。

## <a name="to-create-a-custom-dictionary"></a>若要建立自訂字典

建立名為 **CustomDictionary.xml** 的檔案。

使用下列 XML 結構來定義您的自訂文字：

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>自訂字典元素

您可以修改程式碼分析字典的行為，方法是將詞彙新增為自訂字典中下列元素的內部文字：

- [字典/單字/已辨識/單字](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [字典/單字/無法辨識/單字](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [字典/單字/已淘汰/詞彙 [ @PreferredAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Dictionary/單字/複合/詞彙 [ @CompoundAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [字典/縮寫/CasingExceptions/縮寫](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="dictionarywordsrecognizedword"></a><a name="BKMK_DictionaryWordsRecognizedWord"></a> 字典/單字/已辨識/單字

若要在程式碼分析識別拼寫正確的詞彙清單中包含字詞，請將詞彙加入為字典/單字/可辨識/單字元素的內部文字。 字典/單字/可辨識/單字元素中的詞彙不區分大小寫。

**範例**

```xml
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>
```

字典/單字/可辨識的節點中的詞彙會套用至下列程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702.md)

- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703.md)

- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704.md)

- [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709.md)

- [CA1726:建議使用慣用詞彙](../code-quality/ca1726.md)

- [CA2204:常值必須使用正確的拼字](../code-quality/ca2204.md)

### <a name="dictionarywordsunrecognizedword"></a><a name="BKMK_DictionaryWordsUnrecognizedWord"></a> 字典/單字/無法辨識/單字

若要從程式碼分析識別拼寫正確的詞彙清單中排除字詞，請將詞彙加入為字典/單字/無法辨識/單字元素的內部文字。 字典/單字/無法辨識/單字元素中的詞彙不區分大小寫。

**範例**

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>
```

字典/單字/無法辨識的節點中的詞彙會套用至下列程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702.md)

- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703.md)

- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704.md)

- [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709.md)

- [CA1726:建議使用慣用詞彙](../code-quality/ca1726.md)

- [CA2204:常值必須使用正確的拼字](../code-quality/ca2204.md)

### <a name="dictionarywordsdeprecatedtermpreferredalternate"></a><a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> 字典/單字/已淘汰/詞彙 [ @PreferredAlternate ]

若要在程式碼分析識別為已淘汰的詞彙清單中包含字詞，請將詞彙加入為字典/單字/已淘汰/詞彙元素的內部文字。 被取代的字詞是拼寫正確但不應該使用的單字。

若要在警告中包含建議的替代字詞，請在 [詞彙] 元素的 [PreferredAlternate] 屬性中指定替代字詞。 如果您不想建議替代的屬性值，您可以將屬性值留空。

- Dictionary/Words/已淘汰/Term 元素中被取代的詞彙不區分大小寫。

- PreferredAlternate 屬性值會區分大小寫。 針對複合替代使用 Pascal 大小寫。

**範例**

```xml
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>
```

字典/單字/已淘汰節點中的詞彙會套用至下列程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702.md)

- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703.md)

- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704.md)

- [CA1726:建議使用慣用詞彙](../code-quality/ca1726.md)

### <a name="dictionarywordscompoundtermcompoundalternate"></a><a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary/單字/複合/詞彙 [ @CompoundAlternate ]

內建的字典會將某些詞彙識別為單一、離散詞彙，而不是複合詞匯。 若要在程式碼分析識別為複合字的詞彙清單中包含詞彙，並指定正確的詞彙大小寫，請將詞彙加入為 Dictionary/Words/複合詞/Term 元素的內部文字。 在 Term 專案的 CompoundAlternate 屬性中，將個別單字的第一個字母變成大寫，以指定組成複合詞匯的個別單字 (Pascal 案例) 。 請注意，內部文字中指定的詞彙會自動加入至 Dictionary/Words/DiscreteExceptions 清單。

- Dictionary/Words/複合/Term 元素中的複合詞匯不區分大小寫。

- CompoundAlternate 屬性值會區分大小寫。 針對複合替代使用 Pascal 大小寫。

**範例**

```xml
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>
```

字典/單字/複合節點中的詞彙會套用至下列程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702.md)

- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703.md)

- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704.md)

### <a name="dictionarywordsdiscreteexceptionsterm"></a><a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary/Words/DiscreteExceptions/Term

若要在複合單字的大小寫規則檢查字詞時，將詞彙清單中的字詞排除為單一的離散單字，請將詞彙加入為 Dictionary/Words/DiscreteExceptions/Term 元素的內部文字。 Dictionary/Words/DiscreteExceptions/Term 元素中的詞彙不區分大小寫。

**範例**

```xml
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>
```

Dictionary/Words/DiscreteExceptions 節點中的詞彙會套用至下列程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702.md)

### <a name="dictionaryacronymscasingexceptionsacronym"></a><a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> 字典/縮寫/CasingExceptions/縮寫

若要在程式碼分析識別為正確拼寫的詞彙清單中包含縮寫，並指出複合單字的大小寫規則檢查字詞時的縮寫，請將詞彙新增為字典/縮寫/CasingExceptions/縮寫專案的內部文字。 Dictionary/縮寫/CasingExceptions/縮寫元素中的縮寫會區分大小寫。

**範例**

```xml
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>
```

Dictionary/縮寫/CasingExceptions 節點中的詞彙會套用至下列程式碼分析規則：

- [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709.md)

## <a name="to-apply-a-custom-dictionary-to-a-project"></a><a name="BKMK_ToApplyACustomDictionaryToAProject"></a> 將自訂字典套用至專案

1. 在 **方案總管** 中，請使用下列其中一個程式：

    - 若要將字典加入至單一專案，請以滑鼠右鍵按一下專案名稱，然後按一下 [ **加入現有專案**]。 在 [ **加入現有專案** ] 對話方塊中指定檔案。
  
    - 若要加入在兩個或多個專案之間共用的字典，請在 [ **加入現有專案** ] 對話方塊中找出要共用的檔案，按一下 [ **加入** ] 按鈕上的向下箭號，然後按一下 [ **新增為連結**]。

2. 在 **方案總管** 中，以滑鼠右鍵按一下 **CustomDictionary.xml** 的檔案名，然後按一下 [ **屬性**]。

3. 在 [ **建立動作** ] 清單中，選取 [ **CodeAnalysisDictionary**]。

4. 從 [ **複製到輸出目錄** ] 清單中，選取 [ **不要複製**]。

---
title: HOW TO：自訂程式碼分析字典
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbc2d0f0863ae4b9083c0fb56873eb18b665c7c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081641"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>HOW TO：自訂程式碼分析字典
程式碼分析會使用內建的字典，來檢查拼字、 文法的情況下和其他的.NET Framework 方針的命名慣例中的錯誤程式碼中的識別項。 您可以建立自訂字典的 Xml 檔案，來新增、 移除或修改詞彙、 縮寫，以及內建的字典的縮略字。

 例如，假設您的程式碼包含名為類別**DoorKnokker**。 程式碼分析會視為兩個單字的複合的名稱：**門**並**knokker**。 然後，它就會引發警告， **knokker**拼法不正確。 若要強制可辨識的拼字檢查程式碼分析，您可以新增一詞**knokker**至自訂字典。

## <a name="to-create-a-custom-dictionary"></a>若要建立自訂字典
 建立檔案，稱為**CustomDictionary.xml**。

 使用下列 XML 結構，以定義您的自訂字組：

```
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

## <a name="custom-dictionary-elements"></a>自訂字典的項目
 您可以修改程式碼分析字典的行為將詞彙新增為自訂字典中的下列元素的內部文字：

- [字典/文字/辨識/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [字典/文字/無法辨識的/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Dictionary/Words/Deprecated/Term[@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Dictionary/Words/Compound/Term[@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Dictionary/Acronyms/CasingExceptions/Acronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="BKMK_DictionaryWordsRecognizedWord"></a> 字典/文字/辨識/Word
 若要併入的程式碼分析識別正確拼寫的詞彙之清單中的詞彙，請新增一詞做為字典/文字/Recognized/文字項目的內部文字。 字典/文字/Recognized/文字項目中的詞彙不區分大小寫。

 **範例**

```
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

 Recognized/字典/文字節點中的條款適用於下列的程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726： 建議使用慣用的詞彙](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204:常值應該使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> 字典/文字/無法辨識的/Word
 若要排除的程式碼分析識別正確拼寫的詞彙之清單中的詞彙，新增要做為字典/文字/無法識別/文字項目的內部文字中排除的字詞。 字典/文字/無法識別/文字項目中的詞彙不區分大小寫。

 **範例**

```
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

 無法識別字典/文字節點中的條款適用於下列的程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726： 建議使用慣用的詞彙](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204:常值應該使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionary/Words/Deprecated/Term[@PreferredAlternate]
 若要併入的程式碼分析會識別為已被取代的詞彙之清單中的詞彙，請新增一詞做為字典/文字/已過時/詞彙項目的內部文字。 已被取代的詞彙是一個字的拼字正確，但不應使用。

 若要包含建議的替代詞彙警告中，替代 PreferredAlternate 在屬性中指定的詞彙項目。 如果您不想建議替代，您可以將屬性值保留空白。

- 已被取代的詞彙中的字典/字/已過時/詞彙項目不區分大小寫。

- PreferredAlternate 屬性值會區分大小寫。 複合的替代項目，請使用 Pascal 大小寫。

  **範例**

```
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

 已取代字典/文字節點中的條款適用於下列的程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1726： 建議使用慣用的詞彙](../code-quality/ca1726-use-preferred-terms.md)

### <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary/Words/Compound/Term[@CompoundAlternate]
 內建的字典中識別為單一、 離散的詞彙，而不是複合詞彙的一些術語。 若要納入的複合字識別的程式碼分析的詞彙之清單中的詞彙，並指定正確的大小寫的詞彙，加入詞彙做為字典/文字/複合/詞彙項目的內部文字。 中的詞彙項目 CompoundAlternate 屬性，指定單字的大寫單字 （依照 pascal 命名法大小寫） 的第一個字母組成的複合詞彙。 請注意，內部文字中指定的詞彙會自動新增至字典/文字/DiscreteExceptions 清單。

- 已被取代的詞彙中的字典/字/已過時/詞彙項目不區分大小寫。

- PreferredAlternate 屬性值會區分大小寫。 複合的替代項目，請使用 Pascal 大小寫。

  **範例**

```
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

 字典/文字/化合物節點中的條款適用於下列的程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> 字典/文字/DiscreteExceptions/詞彙
 若要排除的程式碼分析會識別為單一的詞彙之清單中的詞彙，離散 word 一詞是若有選取時的大小寫規則的複合字，會加入詞彙做為字典/文字/DiscreteExceptions/詞彙項目的內部文字。 字典/文字/DiscreteExceptions/詞彙項目中的詞彙不區分大小寫。

 **範例**

```
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

 DiscreteExceptions/字典/文字節點中的條款適用於下列的程式碼分析規則：

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

### <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionary/Acronyms/CasingExceptions/Acronym
 包含的程式碼分析會識別為拼寫正確的詞彙清單中的縮寫，以及指出如何縮寫一詞是若有選取時的大小寫規則的複合字，則將詞彙新增為字典/首字母縮略字/CasingExceptions 的內部文字 /縮寫的項目。 字典/首字母縮略字/CasingExceptions/縮寫的項目中的縮寫是區分大小寫。

 **範例**

```
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

 字典/首字母縮略字/CasingExceptions 節點中的條款適用於下列的程式碼分析規則：

- [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

## <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> 若要套用至專案的自訂字典

1. 在 [**方案總管] 中**，使用下列程序的其中一個：

2. 將字典新增至單一專案，以滑鼠右鍵按一下專案名稱，然後按一下**加入現有項目**。 指定的檔案中**加入現有項目** 對話方塊。

3. 若要加入字典，其中兩個或多個專案之間共用，找出的檔案共用**加入現有項目**對話方塊方塊中，按一下向下箭號**新增**按鈕，然後按一下**加入做為連結**.

4. 在 **方案總管**，以滑鼠右鍵按一下**CustomDictionary.xml**檔案名稱，然後按一下**屬性**。

5. 從**建置動作**清單中，選取**CodeAnalysisDictionary**。

6. 從**複製到輸出目錄**清單中，選取**不會複製**。
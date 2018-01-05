---
title: "如何： 自訂程式碼分析字典 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7fa5f88a3578998fca325500a3815b909b6ce4a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>如何：自訂程式碼分析字典
程式碼分析會使用內建的字典來檢查是否有錯誤的拼字、 文法的情況下和其他的命名慣例的程式碼中的識別項[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]指導方針。 您可以建立自訂字典 Xml 檔案來新增、 移除或修改詞彙、 縮寫，以及首字母縮略字內建的字典。  
  
 例如，假設您的程式碼包含名為類別**DoorKnokker**。 程式碼分析會為兩個單字的複合識別的名稱：**門**和**knokker**。 然後，它就會引發警告， **knokker**拼法不正確。 若要強制辨識拼字檢查程式碼分析，您可以加入詞彙**knokker**自訂字典。  
  
## <a name="to-create-a-custom-dictionary"></a>若要建立自訂字典  
 建立名為檔案**CustomDictionary.xml**。  
  
 使用下列 XML 結構，以定義您的自訂文字：  
  
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
 您可以修改程式碼分析字典的行為方式將詞彙新增自訂字典中的下列元素的內部文字為：  
  
-   [字典/單字/辨識/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [字典/單字/無法辨認的/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [字典/單字/已被取代/詞彙 [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [字典/單字/複合/詞彙 [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [字典/單字/DiscreteExceptions/詞彙](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [字典/首字母縮略字/CasingExceptions/縮略字](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a>字典/單字/辨識/Word  
 若要識別程式碼分析拼字為正確的詞彙的清單中包含的詞彙，加入做為字典/單字/Recognized/Word 元素的內部文字的詞彙。 字典/單字/Recognized/Word 項目中的詞彙不區分大小寫。  
  
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
  
 字典/單字/Recognized 節點中的條款適用於下列的程式碼分析規則：  
  
-   [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703：資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726：建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>字典/單字/無法辨認的/Word  
 若要排除之識別程式碼分析拼字為正確的詞彙清單中的詞彙，新增將字典/單字/無法辨識/Word 元素的內部文字排除詞彙。 字典/單字/無法辨識/Word 項目中的詞彙不區分大小寫。  
  
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
  
 無法辨識字典/文字節點中的條款適用於下列的程式碼分析規則：  
  
-   [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703：資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726：建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>字典/單字/已被取代/詞彙 [@PreferredAlternate]  
 詞彙清單中要包含的程式碼分析會識別為已被取代的詞彙，加入做為內部的字典/單字/Deprecated/詞彙項目文字的詞彙。 已被取代的詞彙是指拼寫正確，但不是應使用的單字。  
  
 若要在警告中包含建議的替代詞彙，替代在屬性中指定 PreferredAlternate 詞彙項目。 如果您不想建議替代，您可以將屬性值留空。  
  
-   字典/字組中已被取代的詞彙/Deprecated/詞彙項目不區分大小寫。  
  
-   PreferredAlternate 屬性值會區分大小寫。 使用 Pascal 大小寫的複合的替代項目。  
  
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
  
 已過時字典/文字節點中的條款適用於下列的程式碼分析規則：  
  
-   [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703：資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726：建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>字典/單字/複合/詞彙 [@CompoundAlternate]  
 內建字典識別為單一、 離散的詞彙，而不是複合詞彙的一些辭彙。 若要包含的程式碼分析以複合字所識別的詞彙清單中的詞彙，並指定正確的大小寫的詞彙，加入詞彙做為字典/單字/複合/詞彙項目的內部文字。 在詞彙項目的 CompoundAlternate 屬性，指定的個別字大寫的單字 （依照 pascal 命名法的情況） 的第一個字母所組成的複合詞彙。 請注意內部文字中指定的詞彙會自動加入至字典/單字/DiscreteExceptions 清單。  
  
-   字典/字組中已被取代的詞彙/Deprecated/詞彙項目不區分大小寫。  
  
-   PreferredAlternate 屬性值會區分大小寫。 使用 Pascal 大小寫的複合的替代項目。  
  
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
  
 下列程式碼分析規則適用於複合/字典/文字節點中的條款：  
  
-   [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703：資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>字典/單字/DiscreteExceptions/詞彙  
 若要排除之程式碼分析會顯示為單一詞彙的清單中的詞彙，離散文字大小寫規則的複合字，核取一詞時加入以詞彙為字典/單字/DiscreteExceptions/詞彙項目的內部文字。 字典/單字/DiscreteExceptions/詞彙項目中的詞彙不區分大小寫。  
  
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
  
 字典/單字/DiscreteExceptions 節點中的條款適用於下列的程式碼分析規則：  
  
-   [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702：複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>字典/首字母縮略字/CasingExceptions/縮略字  
 包含的程式碼分析會識別為拼寫的詞彙清單中的縮寫，以及指出縮寫時一詞會檢查其大小寫規則的複合字的方式，加入詞彙做為內部文字的字典/首字母縮略字/CasingExceptions /Acronym 元素。 字典/首字母縮略字/CasingExceptions/Acronym 元素中的縮寫是區分大小寫。  
  
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
  
-   [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>若要套用至專案的自訂字典  
  
1.  在**方案總管 中**，使用下列程序的其中一個：  
  
2.  若要加入至單一專案的字典，以滑鼠右鍵按一下專案名稱，然後按一下 **加入現有項目**。 指定的檔案中**加入現有項目** 對話方塊。  
  
3.  若要加入字典，其中兩個或多個專案之間共用，找出的檔案共用中**加入現有項目**對話方塊方塊中，按一下向下箭號上**新增**按鈕，然後按一下**加入做為連結**.  
  
4.  在**方案總管 中**，以滑鼠右鍵按一下**CustomDictionary.xml**檔案名稱，然後按一下**屬性**。  
  
5.  從**建置動作**清單中，選取**CodeAnalysisDictionary**。  
  
6.  從**複製到輸出目錄**清單中，選取**不要複製**。
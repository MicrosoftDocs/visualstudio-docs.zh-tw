---
title: 文字範本控制區塊
description: 深入瞭解文字模板控制區塊，以及控制項區塊如何讓您在文字模板中撰寫程式碼，以因應不同的輸出。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90a4efea7d37b83d3d5ff7a085abcf3439d99263
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388720"
---
# <a name="text-template-control-blocks"></a>文字範本控制區塊
控制區塊可讓您在文字範本撰寫程式碼，以便產生不同的輸出。 有三種類型的控制區塊，是使用左括號來區別：

- `<# Standard control blocks #>` 可以包含陳述式。

- `<#= Expression control blocks #>` 可以包含運算式。

- `<#+ Class feature control blocks #>` 可以包含方法、欄位和屬性。

## <a name="standard-control-block"></a>標準控制區塊
 標準控制區塊包含陳述式。 例如，下列標準區塊會取得 XML 文件中所有屬性的名稱：

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 您也可以在複合陳述式中內嵌純文字，例如 `if` 或 `for`。 例如，此片段會在每個迴圈反覆項目產生輸出行：

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
> 一律使用 {...} 分隔包含內嵌純文字的內嵌語句。 下列範例可能無法正常運作：
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> 相反地，您應該包括 {大括號}，如下所示：

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>
```

## <a name="expression-control-block"></a>運算式控制區塊
 運算式控制區塊是用來提供要寫入至輸出檔之字串的程式碼。 例如，利用以上範例，您可以如下所示修改程式碼區塊，將屬性的名稱列印至輸出檔：

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>類別功能控制區塊
 您可以使用類別功能控制區塊將方法、屬性、欄位或甚至是巢狀類別加入至文字範本。 類別功能區塊的常見用法是在文字範本其他部分的程式碼中提供 helper 函式。 例如，下列類別功能區塊會將屬性名稱的第一個字母轉換成大寫字母 (或者，如果名稱包含空格，則會將每個字的第一個字母轉換成大寫字母)：

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
> 類別功能控制區塊後面不得接著相同的範本檔案中的標準控制區塊。 不過，這項限制不適用於使用 `<#@include#>` 指示詞的結果。 每個包含的檔案的類別功能區塊後可以有標準區塊。

 您可以建立函式，其會透過在類別功能控制區塊內內嵌文字和運算式區塊來產生輸出。 例如：

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 您可以從標準區塊或從另一個類別的功能區塊呼叫此函式：

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>如何使用控制區塊
 在單一範本 (包括包含的範本中的所有程式碼) 中的所有標準和運算式控制區塊中的所有程式碼會結合，以形成所產生程式碼的 `TransformText()` 方法。  (如需有關使用指示詞來包含其他文字模板的詳細資訊 `include` ，請參閱 [T4 文字模板](../modeling/t4-text-template-directives.md)指示詞。 ) 

 使用控制區塊時，您應該記住下列考量：

- **語言。** 您可以在文字範本中使用 C# 或 Visual Basic 程式碼。 預設語言是 C# 中，但是您可以使用 `template` 指示詞的 `language` 參數指定 Visual Basic。  (如需指示詞的詳細資訊 `template` ，請參閱 [T4 文字模板](../modeling/t4-text-template-directives.md)指示詞。 ) 

     您在控制區塊中使用的語言，與您在文字範本中產生的文字的語言或格式無關。 您可以使用 Visual Basic 程式碼產生 C#，反之亦然。

     您僅可以在指定的文字範本中使用一種語言，包括使用 `include` 指示詞併入的所有文字範本。

- **區域變數。** 由於文字範本中標準和運算式控制區塊中的所有程式碼，會產生為單一方法，您應該確定沒有與區域變數名稱的衝突。 如果還要包含其他文字範本，您必須確定變數名稱在所有內含的範本之間是唯一的。 確保這點的一個方式就是在宣告所的位置，在對識別文字範本的每個區域變數名稱加入一個字串。

     在宣告變數時以合理的值初始化您的區域變數，也是不錯的主意，尤其是在包含多個文字範本時。

- **控制區塊的巢狀結構。** 控制區塊不能在彼此間形成巢狀結構。 開啟另一個之前，您永遠必須終止特定的控制區塊。 例如，以下顯示如何在運算式區塊中列印某些文字做為標準控制區塊的一部分。

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **重 構。** 為了讓您的文字範本保持簡潔和易於了解，強烈建議您避免重複的程式碼，方法是將可重複使用的程式碼重構到類別功能區塊中的 helper 函式，或建立繼承自 Microsoft.VisualStudio.TextTemplating.TextTransformation 類別的自己的文字範本類別。

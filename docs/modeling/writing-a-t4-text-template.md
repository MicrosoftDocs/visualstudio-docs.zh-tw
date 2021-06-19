---
title: 撰寫 T4 文字範本
description: 瞭解 T4 文字模板以及如何撰寫包含指示詞、文字區塊和控制區塊的文字模板。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8034e0d1df6410c842f7d93a4ee3023957904744
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388083"
---
# <a name="writing-a-t4-text-template"></a>撰寫 T4 文字範本
文字範本包含將透過它產生的文字。 例如，建立網頁的範本將會包含 " \<html> ..."以及 HTML 網頁的所有其他標準部分。 插入範本中的 *控制項區塊* 是程式碼的片段。 控制區塊提供不同的值，並允許文字的各部分成為條件式和重複。

 此結構讓範本容易開發，因為您可以從所產生檔案的原型開始，並以累加方式插入讓結果不同的控制區塊。

 文字範本是由下列部分組成：

- 指示詞-控制範本處理 **方式的元素**。

- **文字區塊** -直接複製到輸出的內容。

- **控制區塊** -將變數值插入文字中的程式碼，並控制文字的條件式或重複的部分。

若要嘗試本主題中的範例，請將它們複製到範本檔案中，如 [使用 T4 文字模板在設計階段產生程式碼時](../modeling/design-time-code-generation-by-using-t4-text-templates.md)所述。 編輯範本檔之後，請儲存它，然後檢查輸出 **.txt** 檔。

## <a name="directives"></a>指示詞
 文字範本指示詞提供有關如何產生轉換程式碼和輸出檔案之文字範本引擎的一般指示。

 例如，下列指示詞指定輸出檔案的副檔名應該為 .txt：

```
<#@ output extension=".txt" #>
```

 如需指示詞的詳細資訊，請參閱 [T4 文字模板](../modeling/t4-text-template-directives.md)指示詞。

## <a name="text-blocks"></a>文字區塊
 文字區塊會將文字直接插入至輸出檔案。 文字區塊沒有特殊格式。 例如，下列文字範本將會產生含有 "Hello" 這個字的文字檔：

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>控制區塊
 控制區塊是用來轉換範本的程式碼區段。 預設語言是 C#，但是，若要使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，您可以在檔案開頭撰寫此指示詞：

```
<#@ template language="VB" #>
```

 您用來在控制區塊中撰寫程式碼的語言，與所產生文字的語言無關。

### <a name="standard-control-blocks"></a>標準控制區塊
 標準控制區塊是產生輸出檔案部分的程式碼區段。

 您可以在範本檔中混合使用任意數目的文字區塊和標準控制區塊。 不過，您不可以將某個控制區塊放入另一個控制區塊內。 每個標準控制區塊都是使用符號 `<# ... #>` 隔開。

 例如，下列控制區塊和文字區塊都會讓輸出檔案包含 "0, 1, 2, 3, 4 Hello!" 這行：

```
<#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 您可以交錯使用文字和程式碼，而不要使用明確 `Write()` 陳述式。 下列範例會列印 "Hello！" 四次：

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 只要程式碼中允許 `Write();` 陳述式的位置，就可以插入文字區塊。

> [!NOTE]
> 當您在複合陳述式（如迴圈或條件）中內嵌文字區塊時，請一律使用大括弧 {...} 包含文字區塊。

### <a name="expression-control-blocks"></a>運算式控制區塊
 運算式控制區塊會評估運算式，並將它轉換為字串。 這會插入至輸出檔案。

 運算式控制區塊是使用符號 `<#= ... #>` 隔開。

 例如，下列控制區塊會讓輸出檔案包含 "5"：

```
<#= 2 + 3 #>
```

 請注意，開頭符號有三個字元 "< # ="。

 運算式可以包括範圍內的任何變數。 例如，此區塊會列印含有數字的行：

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>類別功能控制區塊
 類別功能控制區塊定義屬性、方法，或不應該併入主要轉換的任何其他程式碼。 類別功能區塊經常用於協助程式函式。  一般情況下，類別功能區塊會放在不同的檔案中，讓多個文字模板都能 [包含](#Include) 它們。

 類別功能控制區塊是使用符號 `<#+ ... #>` 隔開。

 例如，下列範本檔會宣告和使用方法：

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 類別功能必須放在於其中寫入它們的檔案結尾。 不過，即使 `<#@include#>` 指示詞後面有標準區塊和文字，您還是可以併入 (`include`) 含有類別功能的檔案。

 如需控制區塊的詳細資訊，請參閱 [文字模板控制區塊](../modeling/text-template-control-blocks.md)。

### <a name="class-feature-blocks-can-contain-text-blocks"></a>類別功能區塊可以包含文字區塊。
 您可以撰寫可產生文字的方法。 例如：

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 特別適用於將產生文字的方法放在多個範本可併入的不同檔案中。

## <a name="using-external-definitions"></a>使用外部定義

### <a name="assemblies"></a>組件
 您範本的程式碼區塊可以使用最常用 .NET 組件 (如 System.dll) 中所定義的類型。 此外，您還可以參考其他 .NET 組件或您專屬的組件。 您可以提供路徑名稱，或組件的強式名稱：

```
<#@ assembly name="System.Xml" #>
```

 您應該使用絕對路徑名稱，或在路徑名稱中使用標準巨集名稱。 例如：

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 Assembly 指示詞在前置處理過的 [文字模板](../modeling/run-time-text-generation-with-t4-text-templates.md)中不會有任何作用。

 如需詳細資訊，請參閱 [T4 元件](../modeling/t4-assembly-directive.md)指示詞。

### <a name="namespaces"></a>命名空間
 import 指示詞與 C# 中的 `using` 子句或 Visual Basic 中的 `imports` 子句相同。 它可讓您參考您程式碼中的類型，而不需要使用完整名稱：

```
<#@ import namespace="System.Xml" #>
```

 您可以使用所想要數目的 `assembly` 和 `import` 指示詞。 您必須將它們放在文字和控制區塊的前面。

 如需詳細資訊，請參閱 [T4 匯入](../modeling/t4-import-directive.md)指示詞。

### <a name="including-code-and-text"></a><a name="Include"></a> 包含程式碼和文字
 `include` 指示詞會插入另一個範本檔中的文字。 例如，此指示詞會插入 `test.txt` 的內容。

```
<#@ include file="c:\test.txt" #>
```

 處理所加入的內容時，幾乎可以將此內容當做是進行加入之文字範本的一部分來處理。 不過，即使 include 指示詞後面有一般文字和標準控制區塊，您還是可以包括含有類別功能區塊 `<#+...#>` 的檔案。

 如需詳細資訊，請參閱 [T4 Include](../modeling/t4-include-directive.md)指示詞。

### <a name="utility-methods"></a>公用程式方法
 在控制區塊中，您一律可以使用數種方法 (如 `Write()`)。 它們包括的方法可以協助您縮排輸出，以及報告錯誤。

 您也可以撰寫一組專屬公用程式方法。

 如需詳細資訊，請參閱 [文字模板公用程式方法](../modeling/text-template-utility-methods.md)。

## <a name="transforming-data-and-models"></a>轉換資料和模型
 文字範本的最有用應用是根據來源內容 (如模型、資料庫或資料檔案) 來產生資料。 您的範本會擷取和重新格式化資料。 範本集合可以將這類來源轉換為多個檔案。

 有數種方式可以讀取原始程式檔。

 **讀取文字模板中的** 檔案。 這是取得資料以放入範本的最簡單方式：

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **將檔案載入為可導覽的模型**。 功能較強大的方法是將資料讀取為您文字範本程式碼可以巡覽的模型。 例如，您可以載入 XML 檔案，並使用 XPath 運算式對其進行巡覽。 您也可以使用 [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) 來建立一組可供您用來讀取 XML 資料的類別。

 **編輯圖表或表單中的模型檔案。** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 提供的工具可讓您以圖表或 Windows form 形式來編輯模型。 這樣可以更輕鬆地與所產生應用程式的使用者討論此模型。 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 也會建立一組強型別類別，以反映模型的結構。 如需詳細資訊，請參閱 [從 Domain-Specific 語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

### <a name="relative-file-paths-in-design-time-templates"></a>設計階段範本中的相對檔案路徑
 在 [設計階段文字模板](../modeling/design-time-code-generation-by-using-t4-text-templates.md)中，如果您想要參考與文字模板相對之位置中的檔案，請使用 `this.Host.ResolvePath()` 。 您也必須在 `hostspecific="true"` 指示詞中設定 `template`：

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>
```

您也可以取得主機所提供的其他服務。 如需詳細資訊，請參閱 [從範本存取 Visual Studio 或其他主機](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))。

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>設計階段文字範本是在不同的 AppDomain 中執行

 您應該要注意的是， [設計階段文字模板](../modeling/design-time-code-generation-by-using-t4-text-templates.md) 是在與主要應用程式不同的 AppDomain 中執行。 在大多數情況下，這並不重要，但是，您可能會發現特定複雜情況下的限制。 例如，如果您想要使用不同的服務，將資料傳入或傳出範本，則服務必須提供可序列化的 API 

  (這對 [執行時間文字模板](../modeling/run-time-text-generation-with-t4-text-templates.md)而言並不正確，它會提供與程式碼其餘部分一起編譯的程式碼。 ) 

## <a name="editing-templates"></a>編輯範本
 您可以從「擴充管理員線上圖庫」下載特殊化文字範本編輯器。 按一下 [ **工具** ] 功能表上的 [ **擴充管理員**]。 按一下 [ **線上元件庫**]，然後使用搜尋工具。

## <a name="related-topics"></a>相關主題

|Task|主題|
|-|-|
|撰寫範本。|[撰寫 T4 文字範本的方針](../modeling/guidelines-for-writing-t4-text-templates.md)|
|使用程式碼來產生文字。|[文字模板結構](../modeling/writing-a-t4-text-template.md)|
|在 Visual Studio 解決方案中產生檔案。|[使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|在 Visual Studio 外部執行文字產生。|[使用 TextTransform 公用程式產生檔案](../modeling/generating-files-with-the-texttransform-utility.md)|
|以網域特定領域語言形式，轉換您的資料。|[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)|
|撰寫指示詞處理器，以轉換您專屬的資料來源。|[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)|

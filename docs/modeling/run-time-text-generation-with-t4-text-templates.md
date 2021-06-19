---
title: 使用 T4 文字範本在執行階段產生文字
description: 瞭解如何在執行時間使用 Visual Studio 執行時間文字模板，在應用程式中產生文字字串。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96d37bc586f9e8d6134377244c3181a52ec11a84
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387550"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>使用 T4 文字範本在執行階段產生文字

您可以在執行時間使用 Visual Studio 執行時間文字模板，在應用程式中產生文字字串。 應用程式執行所在的電腦不一定要有 Visual Studio。 執行時間範本有時稱為「前置處理過的文字模板」，因為在編譯時期，範本會產生在執行時間執行的程式碼。

每個範本都會混合文字，因為它會出現在產生的字串中，以及程式碼的片段。 程式片段會提供字串變數部分的值，也會控制條件式和重複的部分。

例如，下列範本可用於建立 HTML 報表的應用程式。

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

請注意，此範本是 HTML 網頁，其中的變數部分已取代為程式碼。 您可以藉由撰寫 HTML 網頁的靜態原型來開始設計這類頁面。 然後，您可以將資料表和其他變數元件取代為程式碼，該程式碼會產生從一次到下一個情況不同的內容。

在您的應用程式中使用範本，可讓您更輕鬆地查看輸出的最終形式，而不是您在中的輸出形式，例如，一系列的寫入語句。 對輸出的形式進行變更更為簡單且更可靠。

## <a name="creating-a-run-time-text-template-in-any-application"></a>在任何應用程式中建立 Run-Time 文字模板

### <a name="to-create-a-run-time-text-template"></a>若要建立執行時間文字模板

1. 在方案總管中，在專案的快捷方式功能表上，選擇 [**加入**  >  **新專案**]。

2. 在 [ **加入新專案** ] 對話方塊中，選取 [ **執行時間文字模板**]。 Visual Basic 中的 (查看  >  **一般** 專案。 ) 

3. 輸入範本檔案的名稱。

    > [!NOTE]
    > 範本檔案名將用來作為產生的程式碼中的類別名稱。 因此，它不應該有空格或標點符號。

4. 選擇 [新增]  。

    建立的新檔案副檔名為 **tt**。 其 **自訂工具** 屬性會設定為 **TextTemplatingFilePreprocessor**。 它包含下列幾行：

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>將現有檔案轉換為 Run-Time 範本

建立範本的好方法是轉換現有的輸出範例。 例如，如果您的應用程式將產生 HTML 檔案，您可以從建立純 HTML 檔案開始。 請確定它能正常運作，而且其外觀正確。 然後將它包含在您的 Visual Studio 專案中，並將其轉換為範本。

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>將現有的文字檔轉換成執行時間範本

1. 將檔案包含在您的 Visual Studio 專案中。 在方案總管中，在專案的快捷方式功能表上，選擇 [**加入**  >  **現有專案**]。

2. 將檔案的 [ **自訂工具** ] 屬性設定為 [ **TextTemplatingFilePreprocessor**]。 在方案總管中，在檔案的快捷方式功能表上，選擇 [ **屬性**]。

    > [!NOTE]
    > 如果屬性已設定，請確定它是 **TextTemplatingFilePreprocessor** 且未 **TextTemplatingFileGenerator**。 如果您包含副檔名為 **tt** 的檔案，就會發生這種情況。

3. 將副檔名變更為 **tt**。 雖然這個步驟是選擇性的，但它可協助您避免在不正確的編輯器中開啟檔案。

4. 從檔案名的主要部分移除任何空格或標點符號。 例如，「我的 Web Page.tt」會是不正確的，但 "MyWebPage.tt" 是正確的。 檔案名將用來作為產生的程式碼中的類別名稱。

5. 在檔案的開頭插入下面這一行。 如果您是在 Visual Basic 專案中工作，請將 "c #" 取代為 "VB"。

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Run-Time 範本的內容

### <a name="template-directive"></a>Template 指示詞

在您建立檔案時，保留範本的第一行：

`<#@ template language="C#" #>`

Language 參數將取決於您專案的語言。

### <a name="plain-content"></a>純文字內容

編輯 **tt** 檔，以包含您想要應用程式產生的文字。 例如：

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>內嵌程式碼

您可以在和之間插入程式碼 `<#` `#>` 。 例如：

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

請注意，在和運算式之間插入的語句會 `<# ... #>` 插入 `<#= ... #>` 。 如需詳細資訊，請參閱 [撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md)。

## <a name="using-the-template"></a>使用範本

### <a name="the-code-built-from-the-template"></a>從範本建立的程式碼

當您儲存 **tt** 檔案時，會產生一個 **.cs** 或 **.vb** 檔案。 若要在 **方案總管** 中查看這個檔案，請展開 [ **tt** 檔] 節點。 在 Visual Basic 專案中，請先選擇 [**方案總管**] 工具列中的 [**顯示所有** 檔案]。

請注意，子公司檔案包含部分類別，其中包含名為的方法 `TransformText()` 。 您可以從應用程式呼叫這個方法。

### <a name="generating-text-at-run-time"></a>在執行時間產生文字

在您的應用程式程式碼中，您可以使用如下的呼叫來產生範本的內容：

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

若要將產生的類別放在特定的命名空間中，請設定文字模板檔案的 **自訂工具命名空間** 屬性。

### <a name="debugging-runtime-text-templates"></a>調試執行時間文字模板

以與一般程式碼相同的方式，來進行 Debug 和 test runtime 文字模板。

您可以在文字模板中設定中斷點。 如果您從 Visual Studio 在偵測模式中啟動應用程式，您可以逐步執行程式碼，並以一般方式評估監看式運算式。

### <a name="passing-parameters-in-the-constructor"></a>在函式中傳遞參數

範本通常必須從應用程式的其他部分匯入一些資料。 為了簡化這項工作，範本所建立的程式碼是部分類別。 您可以在專案的另一個檔案中，建立相同類別的另一個部分。 該檔案可以包含具有參數、屬性和函式的函式，該函式可由範本中內嵌的程式碼以及應用程式的其餘部分存取。

例如，您可以建立個別的 **MyWebPageCode** 檔案：

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

在您的範本檔案 **MyWebPage.tt** 中，您可以撰寫：

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

若要在應用程式中使用此範本：

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Visual Basic 中的函式參數

在 Visual Basic 中，個別的 **MyWebPageCode** 檔案包含：

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

範本檔案可能包含：

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

您可以藉由在函式中傳遞參數來叫用範本：

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>在範本屬性中傳遞資料

將資料傳遞至範本的另一種方式是將公用屬性加入至部分類別定義中的範本類別。 在叫用之前，您的應用程式可以設定屬性 `TransformText()` 。

您也可以在部分定義中，將欄位加入至範本類別。 這可讓您在後續的範本執行之間傳遞資料。

### <a name="use-partial-classes-for-code"></a>針對程式碼使用部分類別

許多開發人員都想要避免在範本中撰寫大型的程式碼主體。 相反地，您可以在與範本檔案同名的部分類別中定義方法。 從範本呼叫這些方法。 如此一來，範本會更清楚地顯示目標輸出字串的樣子。 有關結果外觀的討論可以與建立所顯示資料的邏輯分開。

### <a name="assemblies-and-references"></a>元件和參考

如果您想要讓範本程式碼參考 .NET 或其他元件（例如 **System.Xml.dll**），請以一般方式將它新增至專案的 **參考** 。

如果您想要以語句的相同方式匯入命名空間 `using` ，您可以使用指示詞來執行此動作 `import` ：

```
<#@ import namespace="System.Xml" #>
```

這些指示詞必須放在檔案的開頭，緊接在指示詞之後 `<#@template` 。

### <a name="shared-content"></a>共用的內容

如果您有數個範本之間共用的文字，您可以將它放在個別的檔案中，並將它包含在應出現的每個檔案中：

```
<#@include file="CommonHeader.txt" #>
```

包含的內容可以包含程式碼和純文字的任何混合，也可以包含其他 include 指示詞和其他指示詞。

Include 指示詞可以在範本檔案的文字或包含的檔案中的任何位置使用。

### <a name="inheritance-between-run-time-text-templates"></a>Run-Time 文字模板之間的繼承

您可以撰寫可為抽象的基類範本，以在執行時間範本間共用內容。 使用指示詞的 `inherits` 參數 `<@#template#>` 參考另一個執行時間範本類別。

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>繼承模式：基底方法中的片段

在接下來的範例所使用的模式中，請注意下列幾點：

- 基類會 `SharedFragments` 定義類別功能區塊內的方法 `<#+ ... #>` 。

- 基類不包含任何可用文字。 相反地，其所有的文字區塊都會出現在類別功能方法內。

- 衍生類別會叫用中定義的方法 `SharedFragments` 。

- 應用程式會呼叫 `TextTransform()` 衍生類別的方法，但不會轉換基類 `SharedFragments` 。

- 基底和衍生類別都是執行時間文字模板;亦即， **自訂工具** 屬性會設定為 **TextTemplatingFilePreprocessor**。

**SharedFragments.tt：**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt：**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**Myprogram.exe .cs：**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**產生的輸出：**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>繼承模式：基底主體中的文字

在使用範本繼承的這個替代方法中，大部分的文字都是在基底範本中定義。 衍生的範本會提供適合基底內容的資料和文字片段。

**AbstractBaseTemplate1.tt：**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt：**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**應用程式程式碼：**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**產生的輸出：**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>[相關主題]

設計階段範本：如果您想要使用範本來產生會成為應用程式一部分的程式碼，請參閱 [使用 T4 文字模板產生設計階段程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

執行時間範本可以在任何應用程式中使用，其中範本和其內容會在編譯時期決定。 但是，如果您想要撰寫 Visual Studio 的延伸模組，以便在執行時間變更的範本產生文字，請參閱 [在 VS 延伸模組中叫用文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。

## <a name="see-also"></a>另請參閱

- [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)
- [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)
- [T4 工具箱](http://olegsych.com/T4Toolbox/)

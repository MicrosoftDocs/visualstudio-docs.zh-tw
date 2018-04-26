---
title: 使用 T4 文字範本在執行階段產生文字
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5b39437dc5f81b17c0bcfe27dbb7b8d99bebbc87
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>使用 T4 文字範本在執行階段產生文字

您可以使用 Visual Studio 執行階段文字範本，在執行階段應用程式中產生的文字字串。 應用程式執行所在的電腦沒有安裝 Visual Studio。 執行階段範本有時也稱為 「 前置處理過的文字範本 」 因為在編譯時期，範本會產生在執行階段執行的程式碼。

每個範本是混合的文字，因為它會出現在產生的字串，以及程式碼片段。 程式碼片段提供值的字串變數的組件，而且也控制條件式和重複的組件。

例如，下列範本無法用於建立 HTML 報表的應用程式。

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

請注意，範本中變數的組件已取代為程式碼的 HTML 網頁。 藉由撰寫靜態的 HTML 網頁的原型，您就可以開始這類頁面設計。 然後，您無法取代資料表和其他變數的組件與程式的程式碼，並產生一個場合至下一個可改變內容。

使用範本，在您的應用程式很容易看到的最終格式的輸出，比在中，例如一長串的寫入陳述式。 對輸出的表單中的變更會更方便且更可靠。

## <a name="creating-a-run-time-text-template-in-any-application"></a>在任何應用程式中建立執行階段文字範本

### <a name="to-create-a-run-time-text-template"></a>若要建立執行階段文字範本

1. 在 [方案總管] 中，您的專案的捷徑功能表上選擇**新增**，**新項目**。

2. 在**加入新項目**對話方塊中，選取**執行階段文字範本**。 (在 Visual Basic 中查看 **一般項目** > **一般**。)

3. 輸入您的範本檔案的名稱。

    > [!NOTE]
    > 範本檔案名稱將用於產生的程式碼中的類別名稱。 因此，它不應該有空格或標點符號。

4. 選擇 [新增]。

    建立新檔案具有副檔名 **.tt**。 其**自訂工具**屬性設定為**TextTemplatingFilePreprocessor**。 它包含下列幾行：

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>將現有檔案轉換為執行階段範本

若要建立範本的好方法是輸出的將轉換現有範例。 例如，如果您的應用程式會產生 HTML 檔案，您就可以藉由建立純文字的 HTML 檔啟動。 請確定它是否運作正常，而且它的外觀正確。 然後併入您的 Visual Studio 專案，並將它轉換為範本。

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>若要將現有的文字檔轉換為執行階段範本

1. 將該檔案包含 Visual Studio 專案。 在 方案總管 中，專案的捷徑功能表上選擇 **新增** > **現有項目**。

2. 設定檔案的**自訂工具**屬性**TextTemplatingFilePreprocessor**。 在方案總管] 中，檔案的捷徑功能表上選擇 [**屬性**。

    > [!NOTE]
    > 如果已設定屬性，請確定它是**TextTemplatingFilePreprocessor**而非**TextTemplatingFileGenerator**。 這種情況包括已有延伸模組檔案 **.tt**。

3. 變更的檔案名稱副檔名 **.tt**。 雖然這個步驟是選擇性的它可協助您避免在不正確的編輯器中開啟檔案。

4. 從檔案名稱的主要部分中移除任何空格或標點符號。 例如 「 我的 Web Page.tt"會不正確，但是"MyWebPage.tt"正確無誤。 檔案名稱將用於產生的程式碼中的類別名稱。

5. 在檔案開頭，插入下列這行。 如果您使用 Visual Basic 專案中，取代 」 搭配使用 C#""VB"。

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>執行階段範本內容

### <a name="template-directive"></a>範本指示詞

建立檔案時，請保留範本的第一行：

`<#@ template language="C#" #>`

Language 參數將取決於您專案的語言。

### <a name="plain-content"></a>一般內容

編輯 **.tt**檔案以包含您希望應用程式產生的文字。 例如: 

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>內嵌的程式碼

您可以插入程式碼之間`<#`和`#>`。 例如: 

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

請注意，插入陳述式是之間`<# ... #>`和運算式之間會插入`<#= ... #>`。 如需詳細資訊，請參閱[撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。

## <a name="using-the-template"></a>使用範本

### <a name="the-code-built-from-the-template"></a>從範本建立程式碼

當您儲存 **.tt**檔案，分公司 **.cs**或 **.vb**檔案產生。 若要查看此檔案在 [方案總管] 中的，展開 **.tt**檔案節點。 在 Visual Basic 專案中，首先選擇**顯示所有檔案**[方案總管] 工具列。

請注意附帶檔案包含的部分類別，其中包含呼叫的方法`TransformText()`。 您可以從您的應用程式呼叫此方法。

### <a name="generating-text-at-run-time"></a>在執行階段產生文字

在您的應用程式程式碼，您可以產生使用像這樣呼叫範本的內容：

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

若要將產生的類別放在特定的命名空間，設定**自訂工具命名空間**文字範本檔案的屬性。

### <a name="debugging-runtime-text-templates"></a>偵錯執行階段文字範本

偵錯和測試執行階段文字範本為一般程式碼相同的方式。

您可以在文字範本中設定中斷點。 如果您從 Visual Studio 偵錯模式中啟動應用程式，您可以逐步執行程式碼，並以一般方式評估監看式運算式。

### <a name="passing-parameters-in-the-constructor"></a>建構函式中傳遞參數

通常是範本必須從應用程式的其他組件匯入某些資料。 為了方便，範本所建立的程式碼是部分類別。 您可以在專案中的另一個檔案中建立相同類別的另一個組件。 該檔案可以包含參數、 屬性和函式可以內嵌在範本中的程式碼和其餘的應用程式存取的建構函式。

例如，您可以建立個別的檔案**MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

在範本檔**MyWebPage.tt**，您可以撰寫：

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

#### <a name="constructor-parameters-in-visual-basic"></a>在 Visual Basic 中的建構函式參數

在 Visual Basic 中的個別檔案**MyWebPageCode.vb**包含：

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

範本可以叫用建構函式中傳遞參數：

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>範本內容中傳遞資料

另一種將資料傳遞至範本是範本類別中的部分類別定義中加入公用屬性。 您的應用程式可以設定屬性，再叫用`TransformText()`。

您也可以將欄位加入至您的範本類別中的部分定義。 這可讓您後續執行範本之間傳遞資料。

### <a name="use-partial-classes-for-code"></a>程式碼中使用部分類別

許多開發人員想要避免撰寫範本中的大型主體的程式碼。 相反地，您可以為範本檔案具有相同名稱的部分類別中定義方法。 從範本來呼叫這些方法。 如此一來，多個範本顯示清楚哪些目標輸出字串看起來類似。 討論結果的外觀可以分開建立它會顯示資料的邏輯。

### <a name="assemblies-and-references"></a>組件和參考

如果您想要這類參考.NET 或其他組件範本程式碼**System.Xml.dll**，將它加入至您的專案**參考**一般方式。

如果您想要匯入命名空間，做為相同的方式`using`陳述式中，您可以使用`import`指示詞：

```
<#@ import namespace="System.Xml" #>
```

這些指示詞必須放置在檔案開頭之後立即`<#@template`指示詞。

### <a name="shared-content"></a>共用的內容

如果您有數個範本之間共用的文字，可以將它放在個別的檔案，並將它包含在應顯示每個檔案：

```
<#@include file="CommonHeader.txt" #>
```

包含的內容可以包含任何的程式碼和純文字的混合，而且它可以包含了其他 include 指示詞和其他指示詞。

Include 指示詞可用於任何位置的文字範本檔案或包含的檔案。

### <a name="inheritance-between-run-time-text-templates"></a>執行階段文字範本之間的繼承

您可以共用執行階段範本，藉由撰寫可為抽象的基底類別範本之間的內容。 使用`inherits`參數`<@#template#>`指示詞可參考另一個執行階段範本類別。

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>繼承的模式： 基底方法中的片段

在接下來的範例中所使用的模式，請注意下列幾點：

- 基底類別`SharedFragments`定義類別功能區塊內的方法`<#+ ... #>`。

- 基底類別未包含可用文字。 相反地，所有的文字區塊內部的類別特徵方法進行。

- 在衍生的類別叫用中定義的方法`SharedFragments`。

- 應用程式會呼叫`TextTransform()`方法在衍生類別中，但不會轉換的基底類別`SharedFragments`。

- 基底和衍生的類別是執行階段文字範本。也就是說，**自訂工具**屬性設定為**TextTemplatingFilePreprocessor**。

**SharedFragments.tt:**

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

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

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

#### <a name="inheritance-pattern-text-in-base-body"></a>繼承的模式： 基底的主體中的文字

使用範本繼承此替代方法，在文字的大量被定義在基底範本中。 在衍生的範本會提供資料和文字片段放入基底內容之。

**AbstractBaseTemplate1.tt:**

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

**DerivedTemplate1.tt:**

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

## <a name="related-topics"></a>相關主題

設計階段範本： 如果您想要使用範本來產生程式碼會變成應用程式的一部分，請參閱[設計階段透過使用 T4 文字範本的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

執行階段範本可在任何應用程式範本和其內容在編譯時期決定其中。 如果您想要撰寫產生的文字範本，可變更執行階段從 Visual Studio 擴充功能，但請參閱[叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。

## <a name="see-also"></a>另請參閱

- [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)
- [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)
- [T4 工具箱](http://olegsych.com/T4Toolbox/)
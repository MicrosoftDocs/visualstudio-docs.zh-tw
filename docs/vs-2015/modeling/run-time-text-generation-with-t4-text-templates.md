---
title: 使用 T4 文字範本產生執行階段文字 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 75da17b32d3997121777f398a6663932c7d7143d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920127"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>使用 T4 文字範本在執行階段產生文字
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您也可以使用在您的應用程式在執行階段產生文字字串[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]執行階段文字範本。 執行應用程式的電腦不必具有[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 執行階段範本有時稱為 「 前置處理過的文字範本 」 因為在編譯時期，範本會產生在執行階段執行的程式碼。  
  
 每個範本是文字的混合，因為它會出現在產生的字串，以及的程式碼片段。 程式片段提供值的字串，變動的組件，並控制條件式和重複的組件。  
  
 例如，下列範本可用的應用程式，會建立一份 HTML 報告。  
  
```  
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
  
 請注意，範本中變數的組件已取代為程式碼的 HTML 網頁。 藉由撰寫靜態 HTML 網頁的原型，您就可以開始這類頁面的設計。 您無法取代的資料表和其他變動的組件從一個的情況下產生不同的內容，到下一個程式碼。  
  
 在您的應用程式會使用範本很容易比，比方說，長序列中寫入陳述式，請參閱輸出的最後格式。 對輸出的表單中的變更會更方便且更可靠。  
  
## <a name="creating-a-run-time-text-template-in-any-application"></a>在任何應用程式中建立執行階段文字範本  
  
#### <a name="to-create-a-run-time-text-template"></a>若要建立執行階段文字範本  
  
1.  在 [方案總管] 中，您的專案的捷徑功能表上選擇**新增**，**新項目**。  
  
2.  在 **加入新項目**對話方塊中，選取**執行階段文字範本**。 (在[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]查看底下**常見 Items\General**。)  
  
3.  輸入您的範本檔案的名稱。  
  
    > [!NOTE]
    >  範本檔案名稱將用於做為產生的程式碼中的類別名稱。 因此，它應該沒有空格或標點符號。  
  
4.  選擇 [新增]。  
  
     會建立新的檔案副檔名 **.tt**。 其**自訂工具**屬性設定為**TextTemplatingFilePreprocessor**。 它包含下列幾行：  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## <a name="converting-an-existing-file-to-a-run-time-template"></a>將現有的檔案轉換成執行階段範本  
 若要建立範本的好方法是輸出的將轉換現有範例。 比方說，如果您的應用程式會在產生的 HTML 檔案，您可以開始建立簡單的 HTML 檔案。 請確定它是否運作正常，而且它的外觀正確。 然後將其併入您[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案，然後將它轉換成範本。  
  
#### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>若要將現有的文字檔轉換成執行階段範本  
  
1.  包含檔案到您[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案。 在 [方案總管] 中，在專案的捷徑功能表上選擇**新增**，**現有項目**。  
  
2.  設定檔案的**自訂工具**屬性設**TextTemplatingFilePreprocessor**。 在 [方案總管] 中，檔案的捷徑功能表上選擇**屬性**。  
  
    > [!NOTE]
    >  如果已設定的屬性，請確定它是**TextTemplatingFilePreprocessor**而非**TextTemplatingFileGenerator**。 如果包含檔案已擴充此情形 **.tt**。  
  
3.  變更的檔案名稱副檔名 **.tt**。 雖然這個步驟是選擇性的它可協助您避免在不正確的編輯器中開啟檔案。  
  
4.  移除檔案名稱的主要部分的任何空格或標點符號。 比方說 「 我的 Web Page.tt"是不正確，但是 「 MyWebPage.tt"正確無誤。 檔案名稱將用於做為產生的程式碼中的類別名稱。  
  
5.  在檔案開頭插入下面這一行。 如果您使用 Visual Basic 專案中，會取代 「 C#"與"VB"。  
  
     `<#@ template language="C#" #>`  
  
## <a name="the-content-of-the-run-time-template"></a>執行階段範本內容  
  
### <a name="template-directive"></a>範本指示詞  
 建立檔案時，請讓範本的第一行：  
  
 `<#@ template language="C#" #>`  
  
 語言參數將取決於您專案的語言。  
  
### <a name="plain-content"></a>純文字內容  
 編輯 **.tt**檔案，以包含您想要您的應用程式產生的文字。 例如:   
  
```  
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
  
 請注意，插入的陳述式是之間`<# ... #>`之間會插入運算式和`<#= ... #>`。 如需詳細資訊，請參閱 <<c0> [ 撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。  
  
## <a name="using-the-template"></a>使用範本  
  
### <a name="the-code-built-from-the-template"></a>從範本建置的程式碼  
 每當您儲存 **.tt**檔案，分公司 **.cs**或是 **.vb**會產生檔案。 若要查看此檔案在方案總管 中的，展開 **.tt**檔案節點。 在 Visual Basic 專案中，您將能夠展開節點，在您按下後**顯示所有檔案**在 [方案總管] 工具列中。  
  
 請注意此附帶檔案包含部分類別，其中包含呼叫的方法`TransformText()`。 您可以從您的應用程式來呼叫這個方法。  
  
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
  
 若要將產生的類別放在特定的命名空間中，設定**自訂工具命名空間**文字範本檔案的屬性。  
  
### <a name="debugging-runtime-text-templates"></a>偵錯執行階段文字範本  
 偵錯和測試執行階段文字範本為一般程式碼相同的方式。  
  
 您可以在文字範本中設定中斷點。 如果您從 Visual Studio 的偵錯模式中啟動應用程式，您可以逐步執行程式碼，並以一般方式評估監看式運算式。  
  
### <a name="passing-parameters-in-the-constructor"></a>在建構函式內傳遞參數  
 通常是範本必須從應用程式的其他組件匯入一些資料。 為了方便，範本所建置的程式碼會是部分類別。 您可以建立另一個檔案中的相同類別的另一個組件，在您的專案。 該檔案可以包含參數、 屬性和函式可以存取由內嵌在範本中，程式碼和應用程式的其餘部分的建構函式。  
  
 例如，您可以在其中建立個別的檔案**MyWebPageCode.cs**:  
  
```csharp  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 在您的範本檔案中**MyWebPage.tt**，您可以撰寫：  
  
```csharp  
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
  
 若要使用此範本的應用程式中：  
  
```csharp  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### <a name="constructor-parameters-in-visual-basic"></a>在 Visual Basic 中的建構函式參數  
 在  [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]，個別的檔案**MyWebPageCode.vb**包含：  
  
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
  
 無法包含範本檔案：  
  
```vb  
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
  
 會叫用範本，將參數傳遞的建構函式：  
  
```vb  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### <a name="passing-data-in-template-properties"></a>在範本內容中傳遞資料  
 將資料傳遞至範本的替代方法是加入的部分類別定義範本類別的公用屬性。 您的應用程式可以設定屬性，然後再叫用`TransformText()`。  
  
 您也可以將欄位加入至您的範本類別中的部分定義。 這可讓您可以連續執行的範本之間傳遞資料。  
  
### <a name="use-partial-classes-for-code"></a>程式碼會使用部分類別  
 許多開發人員想要避免在範本中撰寫大型程式碼主體。 相反地，定義為範本檔案具有相同名稱的部分類別中的方法。 從範本呼叫這些方法。 如此一來，範本會顯示更清楚地哪些目標輸出字串看起來像。 討論結果的外觀可以分開建立它所顯示的資料的邏輯。  
  
### <a name="assemblies-and-references"></a>組件和參考  
 如果您想要您的範本程式碼，這類參考.NET 或其他組件**System.Xml.dll**，您應該將它新增至您的專案**參考**平常的方式。  
  
 如果您想要在相同的方式匯入的命名空間`using`陳述式中，您可以使用`import`指示詞：  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 這些指示詞必須置於檔案開頭，後面`<#@template`指示詞。  
  
### <a name="shared-content"></a>共用的內容  
 如果您有數個範本之間共用的文字時，您可以將它放在不同的檔案，並將它包含在應顯示每個檔案：  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 包含的內容可以包含任何混合程式碼和純文字，而且可以包含其他 include 指示詞和其他指示詞。  
  
 Include 指示詞可以使用文字範本檔案或包含的檔案中的任何位置。  
  
### <a name="inheritance-between-run-time-text-templates"></a>執行階段文字範本之間的繼承  
 您可以共用執行階段範本，藉由撰寫一個可為抽象的基底類別範本之間的內容。 使用`inherits`參數`<@#template#>`指示詞可參考另一個執行階段範本類別。  
  
#### <a name="inheritance-pattern-fragments-in-base-methods"></a>繼承模式： 基底方法中的片段  
 在接下來的範例所使用的模式，請注意下列幾點：  
  
- 基底類別`SharedFragments`定義類別功能區塊內的方法`<#+ ... #>`。  
  
- 基底類別會包含任何任意的文字。 相反地，其所有的文字區塊的類別特徵方法內發生。  
  
- 在衍生的類別叫用中定義的方法`SharedFragments`。  
  
- 應用程式會呼叫`TextTransform()`方法的衍生類別中，但不會轉換的基底類別`SharedFragments`。  
  
- 基底和衍生的類別是執行階段文字範本： 亦即**自訂工具**屬性設定為**TextTemplatingFilePreprocessor**。  
  
  **SharedFragments.tt:**  
  
```csharp  
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
  
```csharp  
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
  
#### <a name="inheritance-pattern-text-in-base-body"></a>基底的主體中的繼承模式： 文字  
 使用範本繼承此替代方法，在大量的文字是基底範本中定義。 在衍生的範本會提供資料和文字片段放入基底的內容。  
  
 **AbstractBaseTemplate1.tt:**  
  
```csharp  
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
  
```csharp  
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
 設計階段範本： 如果您想要使用範本來產生程式碼會變成您的應用程式的一部分，請參閱 <<c0> [ 使用 T4 文字範本在設計階段的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
 執行階段範本可用在任何應用程式範本和其內容在編譯時期決定位置。 但是，如果您想要撰寫[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]延伸模組，可產生文字範本在執行階段變更，請參閱[叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
## <a name="see-also"></a>另請參閱  
 [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)   
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)   
 [Oleg Sych 了解 T4： 前置處理過的文字範本](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)




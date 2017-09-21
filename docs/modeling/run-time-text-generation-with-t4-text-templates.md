---
title: "使用 T4 文字範本在執行階段產生文字 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "前置處理過的文字範本專案項目"
  - "文字範本, 在執行階段產生檔案"
  - "文字範本, TransformText() 方法"
  - "TextTemplatingFilePreprocessor 自訂工具"
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 22
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 22
---
# 使用 T4 文字範本在執行階段產生文字
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您也可以使用應用程式在執行階段中產生的文字字串[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]執行階段文字範本。  應用程式執行所在的電腦不需要有 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  執行階段的範本有時稱為 「 前置處理文字範本"因為在編譯時期，範本會產生執行階段執行程式碼。  
  
 每個範本都混合了會出現在產生之字串中的文字，與程式碼的片段。  程式碼片段提供值用於字串的可變部分，而且也控制條件及重複的部分。  
  
 例如，下列範本可用於會建立 HTML 報表的應用程式。  
  
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
  
 請注意，這個範本是 HTML 網頁，其可變部分已被程式碼取代。  您可以撰寫 HTML 網頁的靜態原型來開始設計這種網頁，  然後以程式碼取代表格及其他可變部分，此程式碼會產生因不同場合而變化的內容。  
  
 在應用程式中使用範本查看輸出的最終形式，會比您在例如一長串撰寫的陳述式中檢視來得容易。  變更輸出形式會更輕鬆，也更可靠。  
  
## 在任何應用程式中建立執行階段文字範本  
  
#### 若要建立執行階段文字範本  
  
1.  在 \[方案總管\] 中，在您的專案的快顯功能表上選擇**新增**， **新的項目**。  
  
2.  在**加入新項目** 對話方塊中，選取 **執行階段文字範本**。  \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中，請於 \[**一般項目\\一般**\] 底下查看\)  
  
3.  輸入範本檔的名稱。  
  
    > [!NOTE]
    >  範本檔的名稱將會用來當做產生之程式碼中的類別名稱。  因此，其中不可包含空格或標點符號。  
  
4.  選擇**新增**。  
  
     副檔名為 **.tt** 的新檔案隨即建立。  其 \[**自訂工具**\] 屬性會設定為 **TextTemplatingFilePreprocessor**。  它包含下列幾行：  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## 將現有檔案轉換為執行階段範本  
 有一個建立範本的好方法，就是轉換現有的輸出範例。  例如，如果應用程式將會產生 HTML 檔，您可以從建立純 HTML 檔來著手進行。  請確定它可以正常運作而且外觀正確，  然後將它包含在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案中，再轉換為範本。  
  
#### 若要將現有文字檔轉換為執行階段範本  
  
1.  將檔案包含在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案中。  在 \[方案總管的專案時，快顯功能表上選擇 \[ **新增**， **現有項目**。  
  
2.  將檔案的 \[**自訂工具**\] 屬性設定為 **TextTemplatingFilePreprocessor**。  在 \[方案總管\] 中，在快顯功能表的檔案，請選擇 **屬性**。  
  
    > [!NOTE]
    >  如果已經設定屬性，請確定是設為 **TextTemplatingFilePreprocessor** 而不是 **TextTemplatingFileGenerator**。  如果您加入已經有副檔名 **.tt** 的檔案，可能就要進行這項確認。  
  
3.  將副檔名變更為 **.tt**。  雖然這個步驟可省略，但是它有助於避免在不正確的編輯器中開啟檔案。  
  
4.  從檔案名稱的主檔名移除空格和標點符號。  例如，"My Web Page.tt" 不正確，但 "MyWebPage.tt" 則正確。  檔案名稱將會用來當做產生之程式碼中的類別名稱。  
  
5.  在檔案開頭插入下列程式碼。  如果是處理 Visual Basic 專案，請以 "VB" 取代 "C\#"。  
  
     `<#@ template language="C#" #>`  
  
## 執行階段範本的內容  
  
### 範本指示詞  
 建立檔案時，請原封不動地保留範本的第一行：  
  
 `<#@ template language="C#" #>`  
  
 語言參數將視專案的語言而定。  
  
### 一般內容  
 編輯 **.tt** 檔案以包含您希望應用程式產生的文字。  例如：  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### 內嵌的程式碼  
 您可以在 `<#` 和 `#>` 之間插入程式碼。  例如：  
  
```c#  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb#  
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
  
 請注意，陳述式的插入位置是在 `<# ... #>` 之間，而運算式則是在 `<#= ... #>` 之間。  如需詳細資訊，請參閱[撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。  
  
## 使用範本  
  
### 從範本建置的程式碼  
 每當您儲存 **.tt** 檔案時，都會產生附屬的 **.cs** 或 **.vb** 檔案。  若要在 \[方案總管\] 中查看此檔案，請展開 **.tt** 檔案節點。  在 Visual Basic 專案中，您要按一下 \[方案總管\] 工具列中的 \[**顯示所有檔案**\] 才能展開節點。  
  
 請注意，這個附屬檔案會包含具有 `TransformText()` 方法的部分類別。  您可以從應用程式中呼叫這個方法。  
  
### 在執行階段產生文字  
 在應用程式的程式碼中，您可以使用如下所示的呼叫來產生範本的內容：  
  
```c#  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb#  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 若要在特定的命名空間中放置產生的類別，請設定文字範本檔的 \[**自訂工具命名空間**\] 屬性。  
  
### 偵錯執行階段文字範本  
 偵錯和測試執行階段文字範本的相同方式與一般的程式碼。  
  
 您可以在文字範本中設定中斷點。  如果您是從 Visual Studio 的偵錯模式中啟動應用程式，可以逐步執行程式碼，並依平常的方式評估監看運算式。  
  
### 將參數傳入建構函式  
 範本通常必須從應用程式的其他部分匯入一些資料。  為使這項工作易於進行，範本所建置的程式碼將會是部分類別。  您可以在專案的其他檔案中建立上述類別的另一個部分。  這個檔案可以包含具有參數、屬性及函式的建構函式，同時供內嵌於範本的程式碼以及應用程式的其餘部分存取。  
  
 例如，您可以建立不同的檔案 **MyWebPageCode.cs**：  
  
```c#  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 在範本檔 **MyWebPage.tt** 中，您可以撰寫下列內容：  
  
```c#  
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
  
 若要在應用程式中使用這個範本，則如下：  
  
```c#  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### Visual Basic 中的建構函式參數  
 在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中，個別的 **MyWebPageCode.vb** 檔案包含：  
  
```vb#  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 範本檔可包含：  
  
```vb#  
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
  
 而且藉由將參數傳入建構函式來叫用範本：  
  
```vb#  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### 將資料傳入範本屬性  
 另一個將資料傳入範本的方法就是在部分類別定義中將公用屬性加入至範本類別。  應用程式可以在叫用 `TransformText()` 之前設定屬性。  
  
 您也可以在部分定義中將欄位加入至範本類別。  如此，您之後接續執行範本時，都可以將資料傳遞下來。  
  
### 使用程式碼的部分類別  
 許多開發人員都傾向於避免在範本中撰寫大型的程式碼主體。  而是在與範本檔同名的部分類別中定義方法，  再從範本中呼叫那些方法。  如此一來，您在範本中可更容易看出目標輸出字串的外觀。  結果的外觀也可以和建立範本所顯示之資料的邏輯分開來討論。  
  
### 組件和參考  
 如果您想要讓範本程式碼參考 .NET 或其他像 **System.Xml.dll** 之類的組件，必須按照平常的方式將它加入至專案的 \[**參考**\]。  
  
 如果您想要以如同 `using` 陳述式的方式匯入命名空間，則可以使用 `import` 指示詞來達到目的：  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 這些指示詞必須放在檔案開頭、緊接 `<#@template` 指示詞後面的位置。  
  
### 共用控制項  
 如果有和數個範本共用的文字，您可以將它放在不同的檔案中，然後於每個檔案中納入，如下所示：  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 加入的內容可以混合程式碼與純文字，也可以包含其他 include 指示詞和其他指示詞。  
  
 您可以在範本檔案或被納入的檔案中的任何位置使用 include 指示詞。  
  
### 執行階段文字範本之間的繼承  
 您可以撰寫基底類別範本 \(可以是抽象\)，在執行階段範本之間共用內容。  使用`inherits`參數的`<@#template#>`指示詞以參考另一個執行階段樣板類別。  
  
#### 繼承模式：基底方法中的片段  
 在範例採用的模式中，請注意以下各點：  
  
-   `SharedFragments` 基底類別會在 `<#+ ... #>` 類別功能區塊中定義方法。  
  
-   基底類別不包含任意文字，  但其所有的文字區塊都在類別功能方法內。  
  
-   衍生類別會叫用 `SharedFragments` 中定義的方法。  
  
-   應用程式會呼叫衍生類別的 `TextTransform()` 方法，但不轉換 `SharedFragments` 基底類別。  
  
-   基底和衍生類別的執行階段文字範本： 也就是**自訂工具** 屬性設定為 \[  **TextTemplatingFilePreprocessor**。  
  
 **SharedFragments.tt：**  
  
```c#  
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
  
```c#  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs：**  
  
```c#  
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
  
#### 繼承模式：基底主體中的文字  
 在這個使用範本繼承的替代方法中，會在基底範本中定義大量的文字。  衍生的範本會提供放入基底內容的資料和文字片段。  
  
 **AbstractBaseTemplate1.tt：**  
  
```c#  
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
  
```c#  
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
  
```c#  
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
  
## 相關主題  
 設計階段範本：如果您想要使用範本來產生會成為應用程式之一部分的程式碼，請參閱[使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
 執行階段範本可用於任何應用程式樣板和其內容在編譯時期決定位置。  然而如果您想要撰寫的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 擴充功能會從範本產生文字，但是此範本會在執行階段變更，請參閱[叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
## 請參閱  
 [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)   
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)   
 [了解 T4： 預先處理完之後文字範本，藉由 Oleg Sych](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)
---
title: 使用 T4 文字範本在設計階段產生程式碼
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: abb606712365108c869ee0cfe705359ad6064228
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860403"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>使用 T4 文字範本在設計階段產生程式碼
設計階段 T4 文字範本可讓您在 Visual Studio 專案中產生程式碼和其他檔案。 通常，您會撰寫範本，讓他們變更其根據從資料產生的程式碼*模型*。 模型是檔案或資料庫，其中包含您的應用程式需求的重要資訊。

 例如，您的模型可以將工作流程定義為表格或圖表。 您可以透過模型產生執行工作流程的軟體。 當您的使用者需求變更時，很容易與使用者討論新的工作流程。 透過工作流程重新產生程式碼，會比手動更新程式碼更為可靠。

> [!NOTE]
>  A*模型*是描述應用程式的特定層面的資料來源。 它可以是任何形式、任何類型的檔案或資料庫。 它不需要是任何特定形式 (如 UML 模型或「網域指定的語言」模型)。 一般模型的格式是表格或 XML 檔案。

 您可能已熟悉如何產生程式碼。 當您定義中的資源 **.resx**檔案在 Visual Studio 方案中，一組類別和方法會自動產生。 編輯資源檔案中的資源，會比編輯類別和方法更為簡單也較可靠。 運用文字範本，您可以使用相同的方式透過您專屬設計的原始檔產生程式碼。

 文字範本混合了您想要產生的文字以及產生文字變動部分的程式碼。 程式碼可讓您重複或有條件地省略所產生文字的某些部分。 所產生的文字本身可以是形成您應用程式一部分的程式碼。

## <a name="creating-a-design-time-t4-text-template"></a>建立設計階段 T4 文字範本

#### <a name="to-create-a-design-time-t4-template-in-visual-studio"></a>在 Visual Studio 中建立設計階段 T4 範本

1.  建立 Visual Studio 專案，或開啟現有實驗。

     例如，在**檔案**功能表上，選擇**新增** > **專案**。

2.  將文字範本檔案新增至您的專案，並為它命名副檔名 **.tt**。

     若要這樣做，請在**方案總管**，在您的專案的捷徑功能表，選擇**新增** > **新項目**。 在 [**加入新項目**] 對話方塊中選取**文字範本**從中間的窗格。

     請注意，**自訂工具**檔案的屬性是**TextTemplatingFileGenerator**。

3.  開啟檔案。 它已包含下列指示詞：

    ```
    <#@ template hostspecific="false" language="C#" #>
    <#@ output extension=".txt" #>
    ```

     如果您已將該範本加入至 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案，則語言屬性會是 "`VB`"。

4.  在檔案結尾加入一些文字。 例如：

    ```
    Hello, world!
    ```

5.  儲存檔案。

     您可能會看到**安全性警告**會要求您確認您想要執行範本的訊息方塊。 按一下 [確定 **Deploying Office Solutions**]。

6.  在 **方案總管**，展開範本檔節點，然後您會發現副檔名的檔案 **.txt**。 此檔案包含從範本產生的文字。

    > [!NOTE]
    >  如果您的專案是 Visual Basic 專案，您必須按一下**顯示所有檔案**才能看到輸出檔案。

### <a name="regenerating-the-code"></a>重新產生程式碼
 在下列任何情況下，將會執行範本，並產生附帶檔案：

-   編輯範本，然後將焦點變更至不同的 Visual Studio 視窗。

-   儲存範本。

-   按一下 **轉換所有範本**中**建置**功能表。 這會將轉換的 Visual Studio 方案中的所有範本。

-   在 **方案總管**，在快顯功能表的任何檔案，選擇**執行自訂工具**。 使用此方法可以轉換所選取的範本子集。

 您也可以設定 Visual Studio 專案，因此它們所讀取的資料檔案變更時，範本會執行的。 如需詳細資訊，請參閱 <<c0> [ 自動重新產生程式碼](#Regenerating)。

## <a name="generating-variable-text"></a>產生變數文字
 文字範本可讓您使用程式碼，讓所產生檔案的內容不同。

#### <a name="to-generate-text-by-using-program-code"></a>使用程式碼來產生文字

1.  變更 `.tt` 檔案的內容：

    ```csharp
    <#@ template hostspecific="false" language="C#" #>
    <#@ output extension=".txt" #>
    <#int top = 10;

    for (int i = 0; i<=top; i++)
    { #>
       The square of <#= i #> is <#= i*i #>
    <# } #>
    ```

    ```vb
    <#@ template hostspecific="false" language="VB" #>
    <#@ output extension=".txt" #>
    <#Dim top As Integer = 10

    For i As Integer = 0 To top
    #>
        The square of <#= i #> is <#= i*i #>
    <#
    Next
    #>

    ```

2.  儲存 .tt 檔案，並重新檢查產生的 .txt 檔案。 它會列出 0 到 10 之數字的平方。

 請注意，陳述式會用 `<#...#>` 括住，單一運算式則用 `<#=...#>` 括住。 如需詳細資訊，請參閱 <<c0> [ 撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。

 如果您使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 撰寫產生的程式碼，則 `template` 指示詞應該包含 `language="VB"`。 `"C#"` 是預設值。

## <a name="debugging-a-design-time-t4-text-template"></a>偵錯設計階段 T4 文字範本
 偵錯文字範本：

-   將 `debug="true"` 插入至 `template` 指示詞。 例如：

     `<#@ template debug="true" hostspecific="false" language="C#" #>`

-   在範本中設定中斷點，方法與您對一般程式碼設定中斷點一樣。

-   選擇**偵錯 T4 範本**從文字範本檔案，在 [方案總管] 的捷徑功能表。

 範本將會執行並停止於中斷點。 您可以檢查變數，並照常逐步執行程式碼。

> [!TIP]
>  `debug="true"` 會將更多行號指示詞插入至產生的程式碼，以讓產生的程式碼更精確地對應至文字範本。 如果您遺漏它，則中斷點可能會以錯誤的狀態停止執行作業。
>
>  但是，您可以將此子句留在範本指示詞中，即使未進行偵錯也是一樣。 這樣只會導致效能稍微降低。

## <a name="generating-code-or-resources-for-your-solution"></a>產生您方案的程式碼或資源
 您可以產生不同的程式檔案 (視模型而定)。 模型是一個輸入 (例如資料庫、組態檔、UML 模型、DSL 模型或其他來源)。 您通常會產生數個來自相同模型的程式檔案。 若要達到這樣的效果，請為每個產生的程式檔案建立範本檔，並且讓所有範本讀取相同的模型。

#### <a name="to-generate-program-code-or-resources"></a>產生程式碼或資源

1.  變更輸出指示詞，以產生適當類型的檔案 (如 .cs、.vb、.resx 或 .xml)。

2.  插入將產生您所需方案程式碼的程式碼。 例如，如果您想要在類別中產生三個整數欄位宣：

    ```csharp

              <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3.  儲存檔案，並檢查產生的檔案，該檔案現在會包含下列程式碼：

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>產生程式碼和產生的文字
 當您產生程式碼時，最重要的是避免混淆在範本中執行的產生程式碼與所產生的產生的程式碼 (為方案的一部分)。 兩種語言不需要相同。

 上述範例有兩個版本。 在其中一個版本中，產生程式碼的格式為 C#。 在另一個版本中，產生程式碼的格式為 Visual Basic。 但是兩者所產生的文字會相同，而且是 C# 類別。

 透過相同的方式，您也可以使用 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 範本來產生任何語言的程式碼。 產生的文字不需要是任何特定語言，也不需要是程式碼。

### <a name="structuring-text-templates"></a>建構文字範本
 我們傾向最好將範本程式碼分成兩個部分：

-   組態或資料收集部分：會在變數中設定值，但不包含文字區塊。 在上述範例中，這部分是 `properties` 的初始化。

     這有時稱為「模型」區段，因為它會建構庫存模型，而且通常會讀取模型檔案。

-   文字產生部分 (在此範例中，是 `foreach(...){...}`)：使用變數的值。

 這不是必要的分隔，而是減少含文字部分的複雜性，讓範本的讀取更為容易的樣式。

## <a name="reading-files-or-other-sources"></a>讀取檔案或其他來源
 若要存取模型檔案或資料庫，您的範本程式碼可以使用 System.XML 這類組件。 若要存取這些組件，您必須插入下列這類指示詞：

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

 `assembly`指示詞可指定的組件提供您的範本程式碼，在 Visual Studio 專案的 [參考] 區段的相同方式。 您不需要包括自動參考之 System.dll 的參考。 `import` 指示詞可讓您使用未使用其完整名稱的類型，方式與一般程式檔案中的 `using` 指示詞相同。

 例如，在匯入之後，才能**System.IO**，您可以撰寫：

```csharp

      <# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>

```

### <a name="opening-a-file-with-a-relative-pathname"></a>使用相對路徑名稱來開啟檔案
 若要從與文字範本相對的位置載入檔案，您可以使用 `this.Host.ResolvePath()`。 若要使用 this.Host，您必須在 `hostspecific="true"` 中設定 `template`：

```
<#@ template debug="false" hostspecific="true" language="C#" #>

```

 然後，您可以撰寫，例如：

```csharp
<# string fileName = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...

```

```vb
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>

```

 您也可以使用 `this.Host.TemplateFile`，以識別目前範本檔的名稱。

 `this.Host` (在 VB 中，為 `Me.Host`) 的類型是 `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`。

### <a name="getting-data-from-visual-studio"></a>從 Visual Studio 中取得資料
 若要使用 Visual Studio 中提供的服務，將`hostSpecific`屬性，並載入`EnvDTE`組件。 然後，您可以使用 IServiceProvider.GetCOMService() 來存取 DTE 和其他服務。 例如：

```scr
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>

```

> [!TIP]
>  文字範本是在其專屬應用程式網域中執行，而服務是透過封送處理進行存取。 在此情況下，GetCOMService() 比 GetService() 還要可靠。

## <a name="Regenerating"></a> 自動重新產生程式碼
 一般而言，Visual Studio 方案中的數個檔案會產生使用一個輸入模型。 每個檔案都是透過其專屬範本所產生，但是範本都參考相同的模型。

 如果來源模型變更，則您應該重新執行方案中的所有範本。 若要這樣做以手動方式，請選擇**轉換所有範本**上**建置**功能表。

 如果您已安裝 Visual Studio Modeling SDK，您可以在執行組建時自動轉換所有範本。 若要這麼做，請在文字編輯器中編輯您的專案檔 (.csproj 或 .vbproj)，並在接近檔案結尾處，任何其他 `<import>` 陳述式的後面加入下列各行：

> [!NOTE]
> 在 Visual Studio 2017 中，文字範本轉換 SDK 和 Visual Studio Modeling SDK 會自動安裝時安裝 Visual Studio 的特定功能。 如需詳細資訊，請參閱 <<c0> [ 此部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/12/12/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)。

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

 如需詳細資訊，請參閱 <<c0> [ 建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)。

## <a name="error-reporting"></a>錯誤報告
 若要將錯誤和警告訊息放在 Visual Studio 錯誤視窗中，您可以使用這些方法：

```
Error("An error message");
Warning("A warning message");
```

## <a name="Converting"></a> 將現有的檔案轉換成範本
 範本的有用功能是它們看起來很像它們所產生的檔案和一些插入的程式碼。 這會建議建立範本的有用方法。 第一次建立一般檔案為原型，例如[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]檔案，然後逐漸引進不同所產生的檔案產生程式碼。

#### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>將現有檔案轉換為設計階段範本

1.  加入 Visual Studio 專案，將您想要產生，例如類型的檔案`.cs`， `.vb`，或`.resx`檔案。

2.  測試新的檔案，確定其運作。

3.  在 [方案總管] 中，變更的檔案名稱副檔名 **.tt**。

4.  請確認下列屬性的 **.tt**檔案：

    |||
    |-|-|
    |**自訂工具 =**|**TextTemplatingFileGenerator**|
    |**建置動作 =**|**無**|

5.  在檔案開頭，插入下列各行：

    ```
    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    ```

     如果您想要在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中撰寫範本的產生程式碼，請將 `language` 屬性設定為 `"VB"`，而非 `"C#"`。

     將 `extension` 屬性設定為您要產生之檔案類型的副檔名 (例如 `.cs`、`.resx` 或 `.xml`)。

6.  儲存檔案。

     即會建立具有所指定副檔名的附帶檔案。 其屬性對檔案類型而言正確。 例如，**建置動作**.cs 檔案的屬性會是**編譯**。

     請確認產生的檔案包含與原始檔案相同的內容。

7.  識別您要使其不同的檔案部分。 例如，只在特定狀況下出現的部分、重複的部分，或特定值不同的部分。 插入產生程式碼。 儲存檔案，並確認已正確地產生附帶檔案。 重複此步驟。

## <a name="guidelines-for-code-generation"></a>產生程式碼的指導方針
 請參閱[撰寫 T4 文字範本的指導方針](../modeling/guidelines-for-writing-t4-text-templates.md)。

## <a name="next-steps"></a>後續步驟

|後續步驟|主題|
|---------------|-----------|
|撰寫並偵錯更進階的文字範本 (內含使用輔助函式、包含的檔案和外部資料的程式碼)。|[撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)|
|在執行階段，透過範本產生文件。|[使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|執行 Visual Studio 外部產生的文字。|[使用 TextTransform 公用程式產生檔案](../modeling/generating-files-with-the-texttransform-utility.md)|
|以網域特定領域語言形式，轉換您的資料。|[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)|
|撰寫指示詞處理器，以轉換您專屬的資料來源。|[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>另請參閱

- [撰寫 T4 文字範本的方針](../modeling/guidelines-for-writing-t4-text-templates.md)

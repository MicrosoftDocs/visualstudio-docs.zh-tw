---
title: "從文字範本存取模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字範本, 存取模型"
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 33
---
# 從文字範本存取模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

藉由使用文字範本，您可以建立報表檔案、 原始程式碼檔和其他網域特定語言模型為基礎的文字檔。  基本文字範本的詳細資訊，請參閱[程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。  文字範本時您正在偵錯您的 DSL 會使用實驗性質的模式，也能夠在已部署的 DSL 的電腦上。  
  
> [!NOTE]
>  當您建立一個 DSL 方案，範例文字範本**\*.tt**檔案產生在偵錯的專案。  當您變更的網域類別名稱時，這些範本將不再有效。  不過，它們包含需要的基本指示詞，並提供一些範例，您可以更新以符合您的 DSL。  
  
 若要存取模型，從某文字範本：  
  
-   將繼承的屬性設定範本指示詞，以便在<xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>。  這會提供存取存放區。  
  
-   指定您想要存取 DSL 指示詞處理器。  這會載入您的 DSL 的組件，讓您可以在文字範本的程式碼中使用其網域類別、 屬性和關聯性。  它也會載入您指定的模型檔案。  
  
 A `.tt`類似下列的範例檔案會建立偵錯的專案中，當您建立新的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DSL 最少的語言範本中的方案。  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 請注意下列幾點關於此範本：  
  
-   網域類別、 屬性和在 DSL 定義中所定義的關聯性，可以使用的範本。  
  
-   將範本載入模型檔中所指定`requires`屬性。  
  
-   屬性在`this`包含根項目。  在這裡，您的程式碼可以瀏覽模型的其他項目。  屬性的名稱通常是與您的 DSL 的根網域類別相同。  在本例中，它是`this.ExampleModel`。  
  
-   雖然程式碼片段所撰寫的語言是 C\#，您可以產生任何種類的文字。  您也可以撰寫程式碼[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]藉由加入屬性`language="VB"`到`template`指示詞。  
  
-   若要偵錯的範本，將`debug="true"`到`template`指示詞。  在另一個執行個體中，會開啟範本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]如果發生例外狀況。  如果您要中斷偵錯程式碼中的某一點時，插入的陳述式`System.Diagnostics.Debugger.Break();`  
  
     如需詳細資訊，請參閱 [偵錯 T4 文字範本](../modeling/debugging-a-t4-text-template.md)。  
  
## 關於 DSL 指示詞處理器  
 範本可以使用在您的 DSL 定義中所定義的網域類別。  這是帶動通常會出現靠近起始點的範本指示詞。  在上例中，它是下列項目。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 指示詞的名稱 \( `MyLanguage`，在本例中\) 衍生自您的 DSL 的名稱。  它會叫用*指示詞處理器* ，會產生您的 DSL 的一部分。  您可以將原始? 式碼中的找出**Dsl\\GeneratedCode\\DirectiveProcessor.cs**。  
  
 DSL 指示詞處理器會執行兩項主要工作：  
  
-   它可以有效地插入組件 」 和 「 匯入指示詞會參考您的 DSL 的範本中。  這可讓您在您網域中使用類別樣板程式碼。  
  
-   載入檔案中所指定`requires`參數，設定中的屬性，並`this`所指的是已載入的模型的根項目。  
  
## 執行範本之前，先驗證模型  
 您可能會造成要驗證之前執行的範本的模型。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 請注意：  
  
1.  `filename`和`validation`參數會以";"且沒有其他分隔符號或空格。  
  
2.  驗證類別目錄清單會決定將執行何種驗證方法。  應該以分隔多個類別"&#124;"且沒有其他分隔符號或空格。  
  
 如果找到錯誤，它會報告錯誤\] 視窗中，在而且結果檔案會包含錯誤訊息。  
  
##  <a name="Multiple"></a> 存取多個模型，從某文字範本  
  
> [!NOTE]
>  這個方法可讓您讀取相同的範本中的多個模型，但不支援 ModelBus 的參考。  若要讀取 interlinked 的 ModelBus 參考的模型，請參閱[使用文字範本中的 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。  
  
 如果您想要存取一個以上的模型，從相同的文字範本，您必須呼叫產生的指示詞處理器一次針對每個模型。  您必須指定每個模型中的檔案名稱`requires`參數。  您必須指定您想要使用在根網域類別名稱`provides`參數。  您必須指定不同的值，如`provides`中每個指示詞的呼叫的參數。  比方說，假設您有三個模型檔名 Library.xyz、 School.xyz 和 Work.xyz。  若要存取這些屬性從相同的文字範本，您必須撰寫類似下列的三個指示詞呼叫。  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  這個範例程式碼是一種以最少的語言的 \[方案\] 範本為基礎的語言。  
  
 若要存取您的文字範本中的模型，現在您可以撰寫類似的程式碼程式碼，如下例所示。  
  
```c#  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb#  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## 以動態方式載入模型  
 如果您想要在執行階段決定載入哪一個模型，您可以在您的程式碼，而非使用特定 DSL 的指示詞中以動態方式載入模型檔案。  
  
 不過，其中一個特定 DSL 的指示詞的函式是匯入 DSL 的命名空間，以便將樣板程式碼可以使用該 DSL 所述的網域類別。  因為您沒有使用這個指示詞，您必須將**\<assembly\>**和**\<import\>**指示詞，您可能會載入的所有模型。  這是很容易，如果不同的模型，您可能會載入所有的 「 相同 」 DSL 的執行個體。  
  
 若要載入檔案，最有效的方法是使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus。  在典型的案例中，文字範本會使用特定 DSL 的指示詞，以一般方式載入第一個模型。  該模型會包含 ModelBus 參考另一個模型。  您可以使用 ModelBus 來開啟參考的模型，並存取特定的項目。  如需詳細資訊，請參閱 [使用文字範本中的 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。  
  
 在較不常見的案例中，可能會想要開啟模型檔案，您必須只能是檔名，而且它可能不是在目前[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。  在此情況下，您可以使用開啟檔案所述的技巧[如何：在程式碼中開啟檔案的模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)。  
  
## 從範本產生多個檔案  
 如果您想要產生數個檔案中 – 比方說，以產生不同的檔案，每個項目在模型中，有幾個可能的方法。  預設情況下，只能有一個檔案不會產生每個範本檔案。  
  
### 分割長的檔案  
 這種方法中，您可以使用範本來產生一個檔案，並以分隔符號分隔。  然後您將檔案分割成各個部份。  有兩個範本，以產生單一的檔案，而去分割它的其中一個。  
  
 **LoopTemplate.t4**會產生很長的單一檔案。  請注意其副檔名為".t4"，因為它應該不會處理直接當您按下**轉換所有的範本**。  此範本會指定用來區隔的區段分隔符號字串的參數：  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt`叫用`LoopTemplate.t4`，然後再將產生的檔案分割及其區段。  請注意此範本沒有模組化樣板，因為它不能閱讀的模型。  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```
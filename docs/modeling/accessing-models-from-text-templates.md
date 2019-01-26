---
title: 從文字範本存取模型
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 513ab6f1a953a2992b744aa3680cd453f677f5bb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966799"
---
# <a name="accessing-models-from-text-templates"></a>從文字範本存取模型
使用文字範本，您可以建立報表檔案、 原始程式碼檔案和其他以特定領域語言模型為基礎的文字檔。 如需文字範本的基本資訊，請參閱[程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。 文字範本進行偵錯時您的 DSL 中，以實驗模式運作，並已部署的 DSL 所在的電腦上也能運作。

> [!NOTE]
>  當您建立的 DSL 方案，範例文字範本 **\*.tt**偵錯的專案中產生檔案。 當您變更網域類別的名稱時，這些範本就無法再運作。 不過，它們包含在需要時，基本指示詞，並提供範例，您可以更新以符合您的 DSL。

 若要從文字範本存取模型：

- 將繼承屬性的範本指示詞，以設定<xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>。 此存放區提供存取。

- 指定您想要存取的 dsl 的指示詞處理器。 這會載入 DSL 的組件，好讓您可以在文字範本的程式碼中使用其網域類別、 屬性和關聯性。 它也會載入您指定的模型檔案。

  A`.tt`時從 DSL 最小語言範本建立新的 Visual Studio 方案，建立類似下列的範例檔案中的偵錯專案。

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

 請注意此範本有關的下列重點：

- 網域類別、 屬性和您在 DSL 定義中定義的關聯性，可以使用範本。

- 在範本載入您在中指定的模型檔案`requires`屬性。

- 中的屬性`this`包含根項目。 從該處，您的程式碼可以巡覽至模型的其他項目。 屬性的名稱通常是與您的 DSL 的根網域類別相同。 在此範例中，它是 `this.ExampleModel`。

- 雖然寫入程式碼片段的語言是 C#，您可以產生任何類型的文字。 您也可以撰寫程式碼[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]藉由將屬性加入`language="VB"`到`template`指示詞。

- 若要偵錯範本，請新增`debug="true"`至`template`指示詞。 如果發生例外狀況，將會開啟的 Visual Studio 的另一個執行個體範本。 如果您想要中斷偵錯程式碼中的特定點時，insert 陳述式 `System.Diagnostics.Debugger.Break();`

   如需詳細資訊，請參閱 <<c0> [ 偵錯 T4 文字範本](../modeling/debugging-a-t4-text-template.md)。

## <a name="about-the-dsl-directive-processor"></a>關於 DSL 的指示詞處理器
 範本可以使用您在 DSL 定義中定義的網域類別。 這會帶來所通常會出現在接近範本開頭指示詞。 在上述範例中，它是下列項目。

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 指示詞的名稱 ( `MyLanguage`，在此範例中) 衍生自您的 DSL 的名稱。 它會叫用*指示詞處理器*產生做為您的 DSL 的一部分。 您可以找到其原始程式碼**Dsl\GeneratedCode\DirectiveProcessor.cs**。

 DSL 的指示詞處理器會執行兩項主要工作：

-   它有效地插入範本以參考您的 DSL 組件和匯入指示詞。 這可讓您在範本程式碼中使用您的網域類別。

-   它會載入您在中指定的檔案`requires`參數，並設定中的屬性`this`載入模型的根項目參考。

## <a name="validating-the-model-before-running-the-template"></a>執行範本之前先驗證模型
 您可能會導致要通過驗證，才能在執行範本的模型。

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 請注意：

1. `filename`和`validation`參數會以 「; 」，一定要有任何其他分隔符號或空格。

2. 驗證類別目錄的清單會決定將執行哪些驗證方法。 應該以分隔多個類別"&#124;「 而且必須是沒有其他分隔符號或空格。

   如果發現錯誤，它會回報 [錯誤] 視窗中，結果檔案將包含錯誤訊息。

## <a name="Multiple"></a> 從文字範本存取多個模型

> [!NOTE]
>  這個方法可讓您讀取相同的範本中的多個模型，但不支援 ModelBus 參考。 ModelBus 參考會 shape 的模型，請參閱[文字範本中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。

 如果您想要從相同的文字範本存取多個模型，您必須呼叫產生的指示詞處理器一次針對每個模型。 您必須指定每個模型中的檔案名稱`requires`參數。 您必須指定您想要用於根網域類別中的名稱`provides`參數。 您必須指定不同的值，如`provides`中每個指示詞呼叫的參數。 例如，假設您有三個分別稱為 Library.xyz、 School.xyz 及 Work.xyz 的模型檔案。 若要從相同的文字範本中存取它們，您必須撰寫類似下列的三個指示詞呼叫。

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
>  此程式碼範例是針對最小語言方案範本為基礎的語言。

 若要存取您的文字範本中的模型，您現在可以在下列範例中撰寫程式碼類似的程式碼。

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>以動態方式載入模型
 如果您想要判斷在執行階段来載入哪一個模型，您可以在您的程式碼，而不是使用 DSL 特定指示詞中以動態方式載入模型檔案。

 不過，其中一個 DSL 特定指示詞的函式是匯入 DSL 的命名空間，好讓範本程式碼可以使用中的 DSL 定義的網域類別。 因為您不使用指示詞，您必須新增**\<組件 >** 並**\<匯入 >** 指示詞，您可能會載入的所有模型。 這是簡單如果不同的模型，您可能會載入相同的 DSL 的所有執行個體。

 若要載入檔案，最有效的方法是使用 Visual Studio ModelBus。 在典型的案例中，文字範本會以一般方式載入的第一個模型使用 DSL 特定指示詞。 該模型會包含對另一個模型的 ModelBus 參考。 您可以使用 ModelBus 開啟參考的模型，並存取特定的項目。 如需詳細資訊，請參閱 <<c0> [ 文字範本中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。

 在較不一般的案例中，您可能想要開啟模型檔就只是檔名，且其中可能無法在目前的 Visual Studio 專案。 在此情況下，您可以使用開啟檔案中所述的技巧[How to:從程式碼中的檔案中開啟模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)。

## <a name="generating-multiple-files-from-a-template"></a>從範本產生多個檔案
 如果您想要產生的數個檔案-例如，來產生個別的檔案，每個項目在模型中，有數種可行方法。 根據預設，只有一個檔案會產生從每個範本檔案。

### <a name="splitting-a-long-file"></a>分割長時間的檔案
 在此方法中，您可以使用範本來產生單一檔案，並以分隔符號分隔。 然後您將檔案分割成其各部分。 有兩個範本，一個用來產生單一檔案中，而另一個則將它分割。

 **LoopTemplate.t4**會產生完整的單一檔案。 請注意，其副檔名".t4"，因為它不應處理當您按一下 直接**轉換所有範本**。 此範本會採用參數，而指定的分隔符號字串分隔的區段：

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

 `LoopSplitter.tt` 叫用`LoopTemplate.t4`，，然後將產生的檔案分割成其區段。 請注意，此範本不一定要模型化範本時，因為它不會讀取模型。

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
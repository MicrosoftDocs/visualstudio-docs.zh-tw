---
title: 從文字範本存取模型
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61f69163e4458c62b9f114eca72c954a2317076b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652372"
---
# <a name="access-models-from-text-templates"></a>從文字模板存取模型

藉由使用文字模板，您可以建立以特定領域語言模型為基礎的報表檔案、原始程式碼檔案和其他文字檔。 如需文字模板的基本資訊，請參閱程式[代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)。 當您要對 DSL 進行偵錯工具時，文字模板會在實驗模式下工作，而且也會在您已部署 DSL 的電腦上工作。

> [!NOTE]
> 當您建立 DSL 方案時，會在調試專案中產生範例文字模板 **\* tt**檔案。 當您變更網域類別的名稱時，這些範本將無法再使用。 不過，它們包含您所需的基本指示詞，並提供可更新以符合 DSL 的範例。

 若要從文字模板存取模型：

- 將樣板指示詞的 inherit 屬性設定為[VisualStudio. TextTemplating. .vshost.exe. ModelingTextTransformation](/previous-versions/bb893209(v=vs.140))。 這會提供存放區的存取權。

- 針對您想要存取的 DSL 指定指示詞處理器。 這會載入您的 DSL 元件，讓您可以在文字模板的程式碼中使用其網域類別、屬性和關聯性。 它也會載入您指定的模型檔案。

  當您從 [DSL 最小語言] 範本建立新的 Visual Studio 方案時，會在調試專案中建立類似下列範例的 `.tt` 檔案。

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

 請注意下列關於此範本的要點：

- 範本可以使用您在 DSL 定義中定義的網域類別、屬性和關聯性。

- 範本會載入您在 `requires` 屬性中指定的模型檔案。

- 中的屬性（property） `this` 包含根項目。 您的程式碼可以從該處流覽至模型的其他元素。 屬性的名稱通常與 DSL 的根域類別相同。 在此範例中，它是 `this.ExampleModel`。

- 雖然撰寫程式碼片段的語言是C#，但是您可以產生任何種類的文字。 或者，您也可以藉由將屬性 `language="VB"` 新增至 `template` 指示詞，在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中撰寫程式碼。

- 若要對範本進行 debug，請將 `debug="true"` 新增至 `template` 指示詞。 如果發生例外狀況，此範本會在 Visual Studio 的另一個實例中開啟。 如果您想要在程式碼中的特定點中斷偵錯工具，請插入語句 `System.Diagnostics.Debugger.Break();`

   如需詳細資訊，請參閱對[T4 文字模板進行調試](../modeling/debugging-a-t4-text-template.md)程式。

## <a name="about-the-dsl-directive-processor"></a>關於 DSL 指示詞處理器
 範本可以使用您在 DSL 定義中定義的網域類別。 這會透過通常出現在範本開頭附近的指示詞來呈現。 在上述範例中，如下所示。

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 指示詞的名稱（在此範例中為 `MyLanguage`）是從您的 DSL 名稱衍生而來。 它會叫用在您的 DSL 中產生的指示詞*處理器*。 您可以在**Dsl\GeneratedCode\DirectiveProcessor.cs**中找到其原始程式碼。

 DSL 指示詞處理器會執行兩個主要工作：

- 它會有效地將元件和匯入指示詞插入參考您 DSL 的範本中。 這可讓您在範本程式碼中使用您的網域類別。

- 它會載入您在 `requires` 參數中指定的檔案，並在 `this` 中設定參考已載入模型之根項目的屬性。

## <a name="validating-the-model-before-running-the-template"></a>執行範本之前驗證模型
 在執行範本之前，您可能會先驗證模型。

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 請注意：

1. @No__t_0 和 `validation` 參數是以 ";" 分隔，而且不能有任何其他分隔符號或空格。

2. 驗證分類清單會決定要執行的驗證方法。 多個類別應以 "&#124;" 分隔，而且不能有其他分隔符號或空格。

   如果發現錯誤，則會在 [錯誤] 視窗中報告，且結果檔案會包含錯誤訊息。

## <a name="Multiple"></a>從文字模板存取多個模型

> [!NOTE]
> 這個方法可讓您讀取相同範本中的多個模型，但不支援 ModelBus 參考。 若要讀取由 ModelBus 參考所 interlinked 的模型，請參閱[在文字模板中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。

 如果您想要從相同的文字模板存取多個模型，則必須針對每個模型呼叫所產生的指示詞處理器一次。 您必須在 `requires` 參數中指定每一個模型的檔案名。 您必須在 `provides` 參數中指定要用於根域類別的名稱。 您必須為每個指示詞呼叫中的 `provides` 參數指定不同的值。 例如，假設您有三個稱為程式庫的模型檔案： xyz、School 和 Work. xyz。 若要從相同的文字模板存取它們，您必須撰寫與下列類似的三個指示詞呼叫。

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> 這個範例程式碼適用于以「最小語言解決方案」範本為基礎的語言。

 若要存取文字模板中的模型，您現在可以撰寫類似下列範例中程式碼的程式碼。

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

## <a name="loading-models-dynamically"></a>動態載入模型
 如果您想要在執行時間決定要載入的模型，您可以在程式碼中以動態方式載入模型檔案，而不是使用 DSL 特定的指示詞。

 不過，DSL 特定指示詞的其中一個功能是匯入 DSL 命名空間，讓範本程式碼可以使用該 DSL 中定義的網域類別。 因為您不使用指示詞，所以您必須為所有可能載入的模型加入 **\<assembly >** 和 **\<import >** 指示詞。 如果您可能載入的不同模型都是相同 DSL 的所有實例，這就很簡單。

 若要載入檔案，最有效的方法是使用 Visual Studio ModelBus。 在典型的案例中，您的文字模板會使用 DSL 特定的指示詞，以一般方式載入第一個模型。 該模型會包含另一個模型的 ModelBus 參考。 您可以使用 ModelBus 來開啟參考的模型，並存取特定的元素。 如需詳細資訊，請參閱[在文字模板中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。

 在較不常見的情況下，您可能會想要開啟只有一個檔案名，而且可能不在目前 Visual Studio 專案中的模型檔案。 在此情況下，您可以使用[如何：在程式碼中從檔案開啟模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)中所述的技術來開啟檔案。

## <a name="generating-multiple-files-from-a-template"></a>從範本產生多個檔案
 如果您想要產生數個檔案（例如，針對模型中的每個元素產生個別的檔案），有幾種可能的方法。 根據預設，每個範本檔案只會產生一個檔案。

### <a name="splitting-a-long-file"></a>分割長檔案
 在此方法中，您可以使用範本來產生單一檔案，並以分隔符號分隔。 然後將檔案分割成其元件。 有兩個範本，一個用來產生單一檔案，另一個用來分割。

 **LoopTemplate**會產生長的單一檔案。 請注意，其副檔名為 "t4"，因為當您按一下 [**轉換所有範本**] 時，不應直接處理它。 此範本會使用參數來指定分隔區段的分隔符號字串：

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

 `LoopSplitter.tt` 會叫用 `LoopTemplate.t4`，然後將產生的檔案分割成其區段。 請注意，此範本不一定是模型化範本，因為它不會讀取模型。

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
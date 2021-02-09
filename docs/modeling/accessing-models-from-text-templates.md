---
title: 從文字範本存取模型
description: 瞭解如何使用文字模板來建立報表檔案、原始程式碼檔，以及其他以定義域特定語言模型為基礎的文字檔。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 13cae79908e3a760c37ac590ca61f43001d384d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908924"
---
# <a name="access-models-from-text-templates"></a>從文字模板存取模型

藉由使用文字模板，您可以建立報表檔案、原始程式碼檔，以及其他以特定領域語言模型為基礎的文字檔。 如需文字模板的基本資訊，請參閱程式 [代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)。 當您正在進行 DSL 的偵錯工具時，文字模板將可在實驗模式下運作，而且也可以在已部署 DSL 的電腦上運作。

> [!NOTE]
> 當您建立 DSL 方案時，會在調試專案中產生範例文字模板 **\* tt** 檔。 當您變更網域類別的名稱時，這些範本將無法再運作。 不過，它們包含您所需的基本指示詞，並提供可讓您更新以符合 DSL 的範例。

 若要從文字模板存取模型：

- 將範本指示詞的 inherit 屬性設定為 [VisualStudio. TextTemplating. vshost.exe. ModelingTextTransformation](/previous-versions/bb893209(v=vs.140))。 這可提供存放區的存取權。

- 針對您想要存取的 DSL 指定指示詞處理器。 這會載入您 DSL 的元件，讓您可以在文字模板的程式碼中使用其網域類別、屬性和關聯性。 它也會載入您指定的模型檔案。

  `.tt`當您從 DSL 最基礎語言範本建立新的 Visual Studio 方案時，會在偵錯工具專案中建立類似下列範例的檔案。

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

 請注意下列有關此範本的重點：

- 範本可以使用您在 DSL 定義中定義的網域類別、屬性和關聯性。

- 範本會載入您在屬性中指定的模型檔案 `requires` 。

- 中的屬性 `this` 包含根項目。 從該處，您的程式碼可以流覽至模型的其他元素。 屬性的名稱通常與 DSL 的根域類別相同。 在此範例中為 `this.ExampleModel`。

- 雖然撰寫程式碼片段的語言是 c #，但您可以產生任何種類的文字。 您也可以 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 將屬性加入至指示詞，以撰寫中的程式碼 `language="VB"` `template` 。

- 若要對範本進行 debug，請加入至指示詞 `debug="true"` `template` 。 如果發生例外狀況，就會在 Visual Studio 的另一個實例中開啟範本。 如果您想要在程式碼中的特定點中斷偵錯工具，請插入語句 `System.Diagnostics.Debugger.Break();`

   如需詳細資訊，請參閱 [將 T4 文字模板的調試](../modeling/debugging-a-t4-text-template.md)程式。

## <a name="about-the-dsl-directive-processor"></a>關於 DSL 指示詞處理器
 範本可以使用您在 DSL 定義中定義的網域類別。 這會透過通常出現在範本開頭附近的指示詞來進行。 在上述範例中，其如下所示。

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 指示詞 ( 的名稱 `MyLanguage` ，在此範例中) 衍生自 DSL 的名稱。 它會叫用作為 DSL 一部分產生的指示詞 *處理器* 。 您可以在 **Dsl\GeneratedCode\DirectiveProcessor.cs** 中找到其原始程式碼。

 DSL 指示詞處理器會執行兩個主要工作：

- 它會有效地將元件和匯入指示詞插入參考 DSL 的範本中。 這可讓您在範本程式碼中使用您的網域類別。

- 它會載入您在參數中指定的檔案 `requires` ，並在中設定屬性， `this` 該屬性會參考已載入模型的根項目。

## <a name="validating-the-model-before-running-the-template"></a>執行範本之前先驗證模型
 您可能會在執行範本之前，先驗證模型。

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 請注意：

1. `filename`和 `validation` 參數會以 ";" 分隔，而且不能有其他分隔符號或空格。

2. 驗證類別清單會決定將執行哪些驗證方法。 多個類別應以 "&#124;" 分隔，而且不能有其他分隔符號或空格。

   如果發現錯誤，則會在錯誤視窗中報告，且結果檔將包含錯誤訊息。

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> 從文字模板存取多個模型

> [!NOTE]
> 這個方法可讓您讀取相同範本中的多個模型，但不支援 ModelBus 參考。 若要讀取由 ModelBus 參考 interlinked 的模型，請參閱 [使用文字模板中的 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。

 如果您想要從相同的文字模板存取一個以上的模型，您必須為每個模型呼叫產生的指示詞處理器一次。 您必須在參數中指定每個模型的檔案名 `requires` 。 您必須在參數中指定要用於根域類別的名稱 `provides` 。 您必須為每個指示詞呼叫中的參數指定不同的值 `provides` 。 例如，假設您有三個稱為 Library 的模型檔案： xyz、School 和 Work。 若要從相同的文字模板存取它們，您必須撰寫與下列類似的三個指示詞呼叫。

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> 此範例程式碼適用于以最基礎語言方案範本為基礎的語言。

 若要存取文字模板中的模型，您現在可以撰寫類似下列範例程式碼的程式碼。

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
 如果您想要在執行時間判斷要載入的模型，您可以在程式碼中以動態方式載入模型檔案，而不是使用 DSL 特定的指示詞。

 不過，DSL 特定指示詞的其中一個函式是匯入 DSL 命名空間，讓範本程式碼可以使用該 DSL 中定義的網域類別。 因為您未使用指示詞，所以您必須 **\<assembly>** **\<import>** 為您可能載入的所有模型加入和指示詞。 如果您可能載入的不同模型都是相同 DSL 的所有實例，這就很簡單。

 若要載入檔案，最有效的方法是使用 Visual Studio ModelBus。 在一般案例中，您的文字模板將使用 DSL 特定的指示詞，以一般方式載入第一個模型。 該模型包含另一個模型的 ModelBus 參考。 您可以使用 ModelBus 來開啟參考的模型，並存取特定的元素。 如需詳細資訊，請參閱 [使用文字模板中的 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。

 在較不平常的案例中，您可能會想要開啟只有檔案名，而且可能不在目前 Visual Studio 專案中的模型檔案。 在此情況下，您可以使用 [如何：在程式碼中從檔案開啟模型（可能為程式碼中的檔案開啟模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)）中所述的技術來開啟檔案。

## <a name="generating-multiple-files-from-a-template"></a>從範本產生多個檔案
 如果您想要產生多個檔案（例如，為模型中的每個元素產生個別的檔案），有幾種可能的方法。 根據預設，每個範本檔案只會產生一個檔案。

### <a name="splitting-a-long-file"></a>分割長檔案
 在此方法中，您可以使用範本來產生單一檔案（以分隔符號分隔）。 然後將檔案分割成元件。 有兩個範本，一個用來產生單一檔案，另一個則用於分割。

 **LoopTemplate** 會產生長的單一檔案。 請注意，其副檔名為 "t4"，因為當您按一下 [ **轉換所有範本**] 時，不應該直接處理它。 此範本會使用參數，以指定分隔區段的分隔符號字串：

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

 `LoopSplitter.tt` 叫用 `LoopTemplate.t4` ，然後將產生的檔案分割成其區段。 請注意，此範本不需要是模型化範本，因為它不會讀取模型。

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

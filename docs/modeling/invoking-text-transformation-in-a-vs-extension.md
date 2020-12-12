---
title: 叫用 VS 擴充功能中的文字轉換
description: 瞭解如何使用文字模板化服務來轉換文字模板。 同時瞭解如何取得 STextTemplating 服務，並將其轉換成 ITextTemplating。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40e781e08bba5e01b5e453e4545b5dd19e5a4d16
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360867"
---
# <a name="invoke-text-transformation-in-a-visual-studio-extension"></a>叫用 Visual Studio 延伸模組中的文字轉換

如果您要撰寫 Visual Studio 的延伸模組（例如功能表命令或 [特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)），您可以使用文字模板化服務來轉換文字模板。 取得 [STextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) 服務，並將其轉換成 [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110))。

## <a name="get-the-text-templating-service"></a>取得文字模板化服務

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));
```

## <a name="pass-parameters-to-the-template"></a>將參數傳遞給範本

 您可以將參數傳遞給範本。 在範本中，您可以使用 `<#@parameter#>` 指示詞取得參數值。

 針對參數的類型，您必須使用可序列化或可封送處理的類型。 也就是說，類型必須使用 <xref:System.SerializableAttribute> 宣告或類型必須衍生自 <xref:System.MarshalByRefObject>。 這是必要的限制，因為文字範本會在不同的 AppDomain 中執行。 所有內建類型（如 **system.string** **和 system.string）都** 是可序列化的。

 為了傳遞參數值，呼叫的程式碼可以在 `Session` 字典或 <xref:System.Runtime.Remoting.Messaging.CallContext> 中放入值。

 下列範例會使用兩個方法轉換簡短的測試範本：

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42
```

## <a name="error-reporting-and-the-output-directive"></a>錯誤報表和輸出指示詞

在處理期間發生的任何錯誤都會顯示在 [Visual Studio 錯誤] 視窗中。 此外，您可以藉由指定執行 [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110))的回呼來通知您錯誤。

如果要將結果字串寫入檔案中，您可能會想要知道範本的 `<#@output#>` 指示詞中指定的副檔名和編碼。 此資訊也會傳遞至回呼。 如需詳細資訊，請參閱 [T4 Output](../modeling/t4-output-directive.md)指示詞。

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}
```

可使用範本檔測試的程式碼看起來和下列類似：

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

編譯器警告會出現在 Visual Studio 錯誤視窗中，而且也會產生的呼叫 `ErrorCallback` 。

## <a name="reference-parameters"></a>傳址參數

您可以使用衍生自 <xref:System.MarshalByRefObject> 的參數類別，將值傳出文字範本。

## <a name="related-articles"></a>相關文章

若要從前置處理過的文字模板產生文字：呼叫 `TransformText()` 所產生類別的方法。 如需詳細資訊，請參閱 [使用 T4 文字模板的執行時間文字產生](../modeling/run-time-text-generation-with-t4-text-templates.md)。

若要在 Visual Studio 擴充功能以外產生文字：定義自訂主機。 如需詳細資訊，請參閱 [使用自訂主機處理文字模板](../modeling/processing-text-templates-by-using-a-custom-host.md)。

若要產生稍後可以編譯並執行的原始程式碼：呼叫[ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110))的[PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110))方法。

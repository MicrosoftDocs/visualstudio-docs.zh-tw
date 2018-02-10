---
title: "叫用 VS 擴充功能中的文字轉換 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ae354bafe55a6d5b23caf244f7ff119a107a9b2e
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>叫用 VS 擴充功能中的文字轉換
如果您要撰寫 Visual Studio 擴充功能，例如功能表命令或[網域特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)，您可以使用文字範本化服務來轉換文字範本。 取得 <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> 服務並將它轉換成  <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>。  
  
## <a name="getting-the-text-templating-service"></a>取得文字範本化服務  
  
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
  
## <a name="passing-parameters-to-the-template"></a>將參數傳遞給範本  
 您可以將參數傳遞給範本。 在範本中，您可以使用 `<#@parameter#>` 指示詞取得參數值。  
  
 針對參數的類型，您必須使用可序列化或可封送處理的類型。 也就是說，類型必須使用 <xref:System.SerializableAttribute> 宣告或類型必須衍生自 <xref:System.MarshalByRefObject>。 這是必要的限制，因為文字範本會在不同的 AppDomain 中執行。 所有的內建類型，例如**System.String**和**System.Int32**都是可序列化。  
  
 為了傳遞參數值，呼叫的程式碼可以在 `Session` 字典或 <xref:System.Runtime.Remoting.Messaging.CallContext> 中放入值。  
  
 下列範例會使用兩個方法轉換簡短的測試範本：  
  
```  
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
  
## <a name="error-reporting-and-the-output-directive"></a>錯誤報告和輸出指示詞  
 處理期間所發生的任何錯誤都會顯示在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 錯誤視窗中。 此外，指定實作 <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback> 的回呼，也可以發出錯誤通知。  
  
 如果要將結果字串寫入檔案中，您可能會想要知道範本的 `<#@output#>` 指示詞中指定的副檔名和編碼。 此資訊也會傳遞至回呼。 如需詳細資訊，請參閱[T4 輸出指示詞](../modeling/t4-output-directive.md)。  
  
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
  
 編譯器警告會出現在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 錯誤視窗中，而且也會產生 `ErrorCallback` 的呼叫。  
  
## <a name="reference-parameters"></a>傳址參數  
 您可以使用衍生自 <xref:System.MarshalByRefObject> 的參數類別，將值傳出文字範本。  
  
## <a name="related-topics"></a>相關主題  
 若要從前置處理過的文字範本產生文字：  
 呼叫產生的類別其 `TransformText()` 方法。 如需詳細資訊，請參閱[執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
 若要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 擴充功能外部產生文字：  
 定義自訂主應用程式。 如需詳細資訊，請參閱[使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)。  
  
 若要產生可在之後編譯及執行的原始程式碼：  
 呼叫 `t4.PreprocessTemplate()` 的 <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating> 方法。

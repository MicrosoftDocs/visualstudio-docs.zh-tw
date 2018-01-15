---
title: "T4 參數指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dbb5e31085f4bc7a405722b581c8e424db5b80ca
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="t4-parameter-directive"></a>T4 參數指示詞
在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文字範本`parameter`指示詞會宣告樣板程式碼中初始化自從外部內容傳入值的屬性。 如果您撰寫程式碼會叫用文字轉換，您可以設定這些值。  
  
## <a name="using-the-parameter-directive"></a>使用參數指示詞  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 `parameter`指示詞會宣告樣板程式碼中初始化自從外部內容傳入值的屬性。 如果您撰寫程式碼會叫用文字轉換，您可以設定這些值。 值可以傳遞處於`Session`字典，或在<xref:System.Runtime.Remoting.Messaging.CallContext>。  
  
 您可以宣告任何遠端使用型別參數。 也就是說，必須與宣告的型別<xref:System.SerializableAttribute>，或必須衍生自<xref:System.MarshalByRefObject>。 這可讓的 AppDomain 處理範本時要傳入的參數值。  
  
 例如，您可以撰寫文字範本具有下列內容：  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>將參數值傳遞至範本  
 如果您要撰寫[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]擴充功能，例如功能表命令或事件處理常式，您可以使用文字範本化服務處理的範本：  
  
```csharp  
// Get a service provider - how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## <a name="passing-values-in-the-call-context"></a>傳入呼叫內容的值  
 您可以另外傳遞值中的邏輯資料<xref:System.Runtime.Remoting.Messaging.CallContext>。  
  
 下列範例會使用這兩種方法來傳遞值：  
  
```csharp  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>將值傳遞到執行階段 （前置處理過） 文字範本  
 它通常不需要使用`<#@parameter#>`與執行階段 （前置處理過的） 文字範本指示詞。 相反地，您可以定義其他建構函式或產生之程式碼，您用來傳遞參數值可設定的屬性。 如需詳細資訊，請參閱[執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
 不過，如果您想要使用`<#@parameter>`在執行階段範本中，您可以傳遞值至它所使用的工作階段的字典。 例如，假設您已經建立的檔案做為前置處理過的範本，呼叫`PreTextTemplate1`。 您可以使用下列程式碼叫用範本在程式中。  
  
```csharp  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## <a name="obtaining-arguments-from-texttemplateexe"></a>從 TextTemplate.exe 取得引數  
  
> [!IMPORTANT]
>  `parameter`指示詞不會擷取中設定的值`-a`參數`TextTransform.exe`公用程式。 若要取得這些值，設定`hostSpecific="true"`中`template`指示詞，以及使用`this.Host.ResolveParameterValue("","","argName")`。
---
title: "T4 參數指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# T4 參數指示詞
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 文字範本中，`parameter` 指示詞會在範本程式碼中宣告從外部內容傳入之值初始化的屬性。  如果您撰寫叫用文字轉換的程式碼，就可以設定這些值。  
  
## 使用參數指示詞  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 `parameter` 指示詞會在範本程式碼中宣告從外部內容傳入之值初始化的屬性。  如果您撰寫叫用文字轉換的程式碼，就可以設定這些值。  這些值可以透過 `Session` 字典或 <xref:System.Runtime.Remoting.Messaging.CallContext> 加以傳遞。  
  
 您可以宣告任何可遠端處理之型別的參數。  也就是說，型別必須使用 <xref:System.SerializableAttribute> 宣告或型別必須衍生自 <xref:System.MarshalByRefObject>。  這樣參數值就能被傳入處理範本的 AppDomain。  
  
 例如，您可以撰寫具有下列內容的文字範本：  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## 將參數值傳遞給範本  
 如果撰寫功能表命令或事件處理常式這類 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 擴充功能，可以使用文字範本化服務來處理範本：  
  
```c#  
// Get a service provider – how you do this depends on the context:  
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
  
## 透過呼叫內容傳遞值  
 您也可以透過 <xref:System.Runtime.Remoting.Messaging.CallContext> 將值當做邏輯資料傳遞。  
  
 下列範例會使用兩個方法傳遞值：  
  
```c#  
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
  
## 將值傳遞給執行階段 \(前置處理過的\) 文字範本  
 通常不需要搭配執行階段 \(前置處理過的\) 文字範本使用 `<#@parameter#>` 指示詞。  反之，只要為產生的程式碼定義額外的建構函式或可設定的屬性，透過這兩種方式即可傳遞參數值。  如需詳細資訊，請參閱[使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
 但是，如果要在執行階段範本中使用 `<#@parameter>`，可以使用 Session 字典將值傳遞給該範本。  例如，假設您建立一個檔案做為前置處理過的範本，叫做 `PreTextTemplate1`。  您可以使用下列程式碼，在程式中叫用這個範本。  
  
```c#  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## 從 TextTemplate.exe 取得引數  
  
> [!IMPORTANT]
>  `parameter` 指示詞並不會擷取 `TextTransform.exe` 公用程式之 `–a` 參數中設定的值。  若要取得那些值，請在 `template` 指示詞中設定`hostSpecific="true"`，並使用 `this.Host.ResolveParameterValue("","","argName")`。
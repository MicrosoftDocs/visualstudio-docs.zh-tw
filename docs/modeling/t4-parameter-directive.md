---
title: T4 參數指示詞
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4a9ea9d3c1f80c669ec52936969ae38342e6343
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606188"
---
# <a name="t4-parameter-directive"></a>T4 參數指示詞

在 Visual Studio 文字模板中，`parameter` 指示詞會在範本程式碼中宣告從外部內容傳入的值初始化的屬性。 如果您撰寫的程式碼會叫用文字轉換，您可以設定這些值。

## <a name="using-the-parameter-directive"></a>使用參數指示詞

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 @No__t_0 指示詞會在範本程式碼中宣告從外部內容傳入的值初始化的屬性。 如果您撰寫的程式碼會叫用文字轉換，您可以設定這些值。 可以在 `Session` 字典中，或在 <xref:System.Runtime.Remoting.Messaging.CallContext> 中傳遞值。

 您可以宣告任何可遠端處理類型的參數。 也就是說，類型必須使用 <xref:System.SerializableAttribute> 宣告，或者必須衍生自 <xref:System.MarshalByRefObject>。 這可讓參數值傳遞至處理範本的 AppDomain 中。

 例如，您可以撰寫具有下列內容的文字模板：

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>將參數值傳遞至範本
 如果您要撰寫 Visual Studio 擴充功能（例如功能表命令或事件處理常式），可以使用文字模板化服務來處理範本：

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

## <a name="passing-values-in-the-call-context"></a>傳遞呼叫內容中的值
 您也可以在 <xref:System.Runtime.Remoting.Messaging.CallContext> 中，將值當做邏輯資料傳遞。

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>將值傳遞至執行時間（前置處理過的）文字模板
 通常不需要使用 `<#@parameter#>` 指示詞搭配執行時間（前置處理過的）文字模板。 相反地，您可以為所產生的程式碼定義額外的函式或可設定的屬性，藉此傳遞參數值。 如需詳細資訊，請參閱[使用 T4 文字模板產生執行時間文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。

 不過，如果您想要在執行時間範本中使用 `<#@parameter>`，您可以使用會話字典，將值傳遞給它。 例如，假設您已將檔案建立為前置處理過的範本，稱為 `PreTextTemplate1`。 您可以使用下列程式碼來叫用程式中的範本。

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>從 TextTemplate 取得引數

> [!IMPORTANT]
> @No__t_0 指示詞不會抓取 `TextTransform.exe` 公用程式之 `-a` 參數中設定的值。 若要取得這些值，請在 `template` 指示詞中設定 `hostSpecific="true"`，並使用 `this.Host.ResolveParameterValue("","","argName")`。
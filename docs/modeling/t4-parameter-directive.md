---
title: T4 參數指示詞
description: 瞭解 Visual Studio 中的參數指示詞會宣告範本程式碼中的屬性，這些屬性是從外部內容傳入的值初始化。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ef80179d43996669b9d883fd2ca9163208d18d7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386094"
---
# <a name="t4-parameter-directive"></a>T4 參數指示詞

在 Visual Studio 文字模板中， `parameter` 指示詞會宣告範本程式碼中的屬性，這些屬性是從外部內容傳入的值初始化。 如果您撰寫的程式碼會叫用文字轉換，您可以設定這些值。

## <a name="using-the-parameter-directive"></a>使用參數指示詞

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter`指示詞會宣告範本程式碼中的屬性，這些屬性是從外部內容傳入的值初始化。 如果您撰寫的程式碼會叫用文字轉換，您可以設定這些值。 您可以在 `Session` 字典中或在中傳遞值 <xref:System.Runtime.Remoting.Messaging.CallContext> 。

 您可以宣告任何可遠端處理型別的參數。 也就是說，類型必須使用宣告 <xref:System.SerializableAttribute> ，或必須衍生自 <xref:System.MarshalByRefObject> 。 這可讓參數值傳遞至用來處理範本的 AppDomain。

 例如，您可以使用下列內容來撰寫文字模板：

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>將參數值傳遞至範本
 如果您要撰寫 Visual Studio 的延伸模組（例如功能表命令或事件處理常式），則可以使用文字模板化服務來處理範本：

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

## <a name="passing-values-in-the-call-context"></a>在呼叫內容中傳遞值
 您也可以在中，將值傳遞為的邏輯資料 <xref:System.Runtime.Remoting.Messaging.CallContext> 。

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>傳遞值給 Run-Time (前置處理的) 文字模板
 通常不需要在 `<#@parameter#>` 執行時間 (前置處理的) 文字模板中使用指示詞。 相反地，您可以為產生的程式碼定義其他的函式或可設定的屬性，以傳遞參數值。 如需詳細資訊，請參閱 [使用 T4 文字模板的執行時間文字產生](../modeling/run-time-text-generation-with-t4-text-templates.md)。

 但是，如果您想要 `<#@parameter>` 在執行時間範本中使用，您可以使用會話字典將值傳遞給它。 例如，假設您已將檔案建立為預先處理過的範本，稱為 `PreTextTemplate1` 。 您可以使用下列程式碼，在您的程式中叫用範本。

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
> 指示詞不 `parameter` 會取出 `-a` 公用程式參數中所設定的值 `TextTransform.exe` 。 若要取得這些值，請在指示詞 `hostSpecific="true"` 中設定 `template` ，然後使用 `this.Host.ResolveParameterValue("","","argName")` 。

---
title: 從文字範本存取 Visual Studio 或其他主機
description: 瞭解如何在執行範本的主機所公開的文字模板中使用方法和屬性。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3cde4b2afe6d09c3958bbabe7a5669a13f8de8f2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389120"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>從文字模板存取 Visual Studio 或其他主機

在文字模板中，您可以使用執行範本的主機所公開的方法和屬性。 Visual Studio 是主機的範例。

> [!NOTE]
> 您可以使用一般文字模板中的主控制項方法和屬性，但不能使用前置處理 *過的文字* 範本。

## <a name="obtain-access-to-the-host"></a>取得主機的存取權

若要存取主機，請 `hostspecific="true"` 在指示詞中設定 `template` 。 現在您可以使用 `this.Host` ，其具有類型 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))。 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))型別具有可用來解析檔案名和記錄錯誤的成員，例如。

### <a name="resolve-file-names"></a>解析檔案名

若要尋找相對於文字模板之檔案的完整路徑，請使用 `this.Host.ResolvePath()` 。

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>顯示錯誤訊息

當您轉換範本時，此範例會記錄訊息。 如果主機 Visual Studio，錯誤會新增至 **錯誤清單**。

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>使用 Visual Studio API

如果您要在 Visual Studio 中執行文字模板，您可以使用 `this.Host` 來存取 Visual Studio 所提供的服務，以及任何已載入的封裝或延伸模組。

Set hostspecific = "true" 並轉換 `this.Host` 成 <xref:System.IServiceProvider> 。

此範例會取得作為服務的 Visual Studio API <xref:EnvDTE.DTE> ：

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>搭配使用 hostSpecific 與範本繼承

指定 `hostspecific="trueFromBase"` 是否也要使用 `inherits` 屬性，如果您繼承自指定的範本，則為 `hostspecific="true"` 。 如果沒有，您可能會收到編譯器警告，指出該屬性 `Host` 已宣告兩次。

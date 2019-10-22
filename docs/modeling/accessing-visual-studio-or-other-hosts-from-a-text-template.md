---
title: 從文字範本存取 Visual Studio 或其他主機
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752b9d9e69eee26f267927f03c4b83c68740100b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652367"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>從文字模板存取 Visual Studio 或其他主機

在文字模板中，您可以使用執行範本的主控制項所公開的方法和屬性。 Visual Studio 是主機的範例。

> [!NOTE]
> 您可以在一般文字模板中使用主控制項方法和屬性，但不能在前置處理過*的文字模板*中使用。

## <a name="obtain-access-to-the-host"></a>取得主機的存取權

若要存取主機，請在 `template` 指示詞中設定 `hostspecific="true"`。 現在您可以使用[ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))類型的 `this.Host`。 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))類型具有可供您用來解析檔案名和記錄錯誤的成員，例如。

### <a name="resolve-file-names"></a>解析檔案名

若要尋找相對於文字模板之檔案的完整路徑，請使用 `this.Host.ResolvePath()`。

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

這個範例會在您轉換範本時記錄訊息。 如果 Visual Studio 主機，則會將錯誤新增至**錯誤清單**。

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

設定 hostspecific = "true"，並將 `this.Host` 轉換為 <xref:System.IServiceProvider>。

這個範例會以服務的形式取得 Visual Studio API <xref:EnvDTE.DTE>：

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

## <a name="use-hostspecific-with-template-inheritance"></a>使用 hostSpecific 搭配範本繼承

如果您也使用 `inherits` 屬性，而且如果您繼承自指定 `hostspecific="true"` 的範本，請指定 `hostspecific="trueFromBase"`。 如果沒有，您可能會收到編譯器警告，指出屬性 `Host` 已宣告兩次。
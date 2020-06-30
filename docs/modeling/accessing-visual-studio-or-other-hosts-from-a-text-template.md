---
title: 從文字範本存取 Visual Studio 或其他主機
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 068de3c14240bc7e13be0e2e564c2c4e6034f987
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531413"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>從文字模板存取 Visual Studio 或其他主機

在文字模板中，您可以使用執行範本的主控制項所公開的方法和屬性。 Visual Studio 是主機的範例。

> [!NOTE]
> 您可以在一般文字模板中使用主控制項方法和屬性，但不能在前置處理過*的文字模板*中使用。

## <a name="obtain-access-to-the-host"></a>取得主機的存取權

若要存取主機，請 `hostspecific="true"` 在指示詞中設定 `template` 。 現在您可以使用 `this.Host` ，其型別為[ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))。 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))類型具有可供您用來解析檔案名和記錄錯誤的成員，例如。

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

設定 hostspecific = "true"，並將轉換 `this.Host` 為 <xref:System.IServiceProvider> 。

這個範例會取得 <xref:EnvDTE.DTE> 做為服務的 VISUAL STUDIO API：

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

`hostspecific="trueFromBase"`如果您也使用 `inherits` 屬性，而且如果您繼承自指定的範本，請指定 `hostspecific="true"` 。 如果沒有，您可能會收到編譯器警告，指出屬性已宣告 `Host` 兩次。

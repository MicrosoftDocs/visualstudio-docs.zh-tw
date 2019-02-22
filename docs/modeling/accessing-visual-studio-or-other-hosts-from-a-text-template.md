---
title: 從文字範本存取 Visual Studio 或其他主機
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a75dc86a45c78f6b57d5a326c8c342eca70b26e0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55956801"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>從文字範本存取 Visual Studio 或其他主機

在文字範本中，您可以使用的主控件執行此範本所公開的方法和屬性。 Visual Studio 是主機的範例。

> [!NOTE]
> 您可以使用主機方法和屬性在一般文字範本中，但不是在*前置處理過*文字範本。

## <a name="obtain-access-to-the-host"></a>取得主機的存取權

若要存取主應用程式，設定`hostspecific="true"`在`template`指示詞。 現在您可以使用`this.Host`，其中包含型別<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>。 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>類型具有您可以使用，例如，若要解決檔案名稱，並記錄錯誤的成員。

### <a name="resolve-file-names"></a>解析檔案名稱

若要尋找與文字範本相對之檔案的完整路徑，請使用`this.Host.ResolvePath()`。

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

當您轉換範本時，此範例中會記錄訊息。 如果主機是 Visual Studio，將錯誤加入至**錯誤清單**。

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

如果您在 Visual Studio 中執行文字範本，您可以使用`this.Host`Visual Studio 及任何套件或載入的延伸模組所提供的存取服務。

設定 hostspecific ="true"，且在轉換`this.Host`至<xref:System.IServiceProvider>。

這個範例會取得 Visual Studio API， <xref:EnvDTE.DTE>，做為服務：

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

## <a name="use-hostspecific-with-template-inheritance"></a>HostSpecific 使用範本繼承

指定`hostspecific="trueFromBase"`如果您同時使用`inherits`屬性，而且如果您繼承自指定的範本`hostspecific="true"`。 如果不這麼做，您可能會收到編譯器警告，屬性`Host`已宣告兩次。
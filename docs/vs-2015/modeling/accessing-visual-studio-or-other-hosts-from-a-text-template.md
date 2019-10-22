---
title: 從文字模板存取 Visual Studio 2015 或其他主機 |Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655331"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>從文字範本存取 Visual Studio 或其他主機
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在文字模板中，您可以使用執行範本之主控制項所公開的方法和屬性，例如 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。

 這適用于一般文字模板，而非前置處理過的文字模板。

## <a name="obtaining-access-to-the-host"></a>取得主機的存取權

在 `template` 指示詞中設定 `hostspecific="true"`。 這可讓您使用具有[ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))類型的 `this.Host`。 此類型具有您可以使用的成員，例如，用來解析檔案名和記錄錯誤。

### <a name="resolving-file-names"></a>解析檔案名
 若要尋找相對於文字模板之檔案的完整路徑，請使用這個。ResolvePath （）。

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

### <a name="displaying-error-messages"></a>顯示錯誤訊息
 這個範例會在您轉換範本時記錄訊息。 如果主機是 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的，則會新增至 [錯誤] 視窗。

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

## <a name="using-the-visual-studio-api"></a>使用 Visual Studio API
 如果您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中執行文字模板，則可以使用 `this.Host` 來存取 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 所提供的服務，以及任何已載入的封裝或延伸模組。

 設定 hostspecific = "true"，並將 `this.Host` 轉換為 <xref:System.IServiceProvider>。

 這個範例會以服務的形式取得 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API <xref:EnvDTE.DTE>：

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

## <a name="using-hostspecific-with-template-inheritance"></a>搭配使用 hostSpecific 與範本繼承
 如果您也使用 `inherits` 屬性，而且如果您繼承自指定 `hostspecific="true"` 的範本，請指定 `hostspecific="trueFromBase"`。 這可避免編譯器警告，因為屬性 `Host` 宣告了兩次。

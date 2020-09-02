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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655331"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>從文字範本存取 Visual Studio 或其他主機
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在文字模板中，您可以使用執行範本的主機所公開的方法和屬性，例如 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。

 這適用于一般文字模板，而非前置處理過的文字模板。

## <a name="obtaining-access-to-the-host"></a>取得主機的存取權

在指示詞 `hostspecific="true"` 中設定 `template` 。 這可讓您使用  `this.Host` 具有類型 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))的。 此類型具有您可以使用的成員，例如，用來解析檔案名和記錄錯誤。

### <a name="resolving-file-names"></a>解析檔案名
 若要尋找相對於文字模板之檔案的完整路徑，請使用此檔案。ResolvePath ( # A1。

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
 當您轉換範本時，此範例會記錄訊息。 如果主機為 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，則會將它們新增至錯誤視窗。

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
 如果您要在中執行文字模板 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，您可以使用 `this.Host` 來存取所提供的服務 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，以及任何已載入的封裝或延伸模組。

 Set hostspecific = "true" 並轉換 `this.Host` 成 <xref:System.IServiceProvider> 。

 此範例會 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:EnvDTE.DTE> 以服務的形式取得 API：

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
 指定 `hostspecific="trueFromBase"` 是否也要使用 `inherits` 屬性，如果您繼承自指定的範本，則為 `hostspecific="true"` 。 這可避免編譯器警告，因為屬性 `Host` 已宣告兩次。

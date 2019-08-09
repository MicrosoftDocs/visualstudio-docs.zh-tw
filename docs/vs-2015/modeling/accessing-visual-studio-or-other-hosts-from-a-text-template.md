---
title: 從文字模板存取 Visual Studio 2015 或其他主機 |Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 053e8b09fd2b52683238f1ffe008e5e7d38b3962
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872011"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>從文字範本存取 Visual Studio 或其他主機
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在文字模板中, 您可以使用執行範本之主控制項所公開的方法和屬性, 例如[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。

 這適用于一般文字模板, 而非前置處理過的文字模板。

## <a name="obtaining-access-to-the-host"></a>取得主機的存取權

在指示詞中`hostspecific="true"` 設定。`template` 這可讓您`this.Host`使用, 其型別為[ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))。 此類型具有您可以使用的成員, 例如, 用來解析檔案名和記錄錯誤。

### <a name="resolving-file-names"></a>解析檔案名
 若要尋找相對於文字模板之檔案的完整路徑, 請使用這個。ResolvePath ()。

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
 當您轉換範本時，此範例中會記錄訊息。 如果主機為[!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 則會將它們新增至 [錯誤] 視窗。

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
 如果您要在中[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]執行文字模板, 您可以使用`this.Host`來存取所提供的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]服務, 以及任何已載入的封裝或延伸模組。

 設定 hostspecific ="true"，且在轉換`this.Host`至<xref:System.IServiceProvider>。

 這個範例會以[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]服務形式<xref:EnvDTE.DTE>取得 API:

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
 指定`hostspecific="trueFromBase"`如果您同時使用`inherits`屬性，而且如果您繼承自指定的範本`hostspecific="true"`。 這可避免編譯器警告, 因為屬性`Host`已宣告兩次。

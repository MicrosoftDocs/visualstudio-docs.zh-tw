---
title: 從文字範本存取 Visual Studio 2015 或其他主機 |Microsoft Docs
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
ms.openlocfilehash: d26c168780051d3644d04d209001bf0cc9a551cb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945110"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>從文字範本存取 Visual Studio 或其他主機
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在文字範本中，您可以使用方法和屬性執行範本，例如主機所公開[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。

 這適用於規則的文字範本，而不前置處理過的文字範本。

## <a name="obtaining-access-to-the-host"></a>取得主機的存取權
 設定`hostspecific="true"`在`template`指示詞。 這可讓您使用`this.Host`，其中包含型別<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>。 此類型具有您可以使用，例如，若要解決檔案名稱，並記錄錯誤的成員。

### <a name="resolving-file-names"></a>解析檔案名稱
 若要尋找與文字範本相對之檔案的完整路徑，請使用此。Host.ResolvePath()。

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
 當您轉換範本時，此範例中會記錄訊息。 如果主機是[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，它們會新增至 [錯誤] 視窗。

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
 如果您正在執行中的文字範本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，您可以使用`this.Host`來存取服務所提供[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]以及任何封裝或載入的延伸模組。

 設定 hostspecific ="true"，且在轉換`this.Host`至<xref:System.IServiceProvider>。

 這個範例會取得[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]API， <xref:EnvDTE.DTE>，做為服務：

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

## <a name="using-hostspecific-with-template-inheritance"></a>HostSpecific 使用範本繼承
 指定`hostspecific="trueFromBase"`如果您同時使用`inherits`屬性，而且如果您繼承自指定的範本`hostspecific="true"`。 這可避免編譯器警告的效果，屬性`Host`已宣告兩次。

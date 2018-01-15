---
title: "從文字範本存取 Visual Studio 或其他主機 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fa3f2c0a259afdb09f5565872c9c43c72f38e1c2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>從文字範本存取 Visual Studio 或其他主機
在文字範本中，您可以使用方法和屬性執行範本，例如主機所公開[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 這適用於一般文字範本，而不前置處理過的文字範本。  
  
## <a name="obtaining-access-to-the-host"></a>取得主機的存取權  
 設定`hostspecific="true"`中`template`指示詞。 這可讓您使用`this.Host`，其具有型別<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>。 此類型有一些成員，您可以使用，例如，若要解決檔案名稱，並記錄錯誤。  
  
### <a name="resolving-file-names"></a>解析檔案名稱  
 若要尋找的檔案與文字範本相對的完整路徑，請使用此。Host.ResolvePath()。  
  
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
 轉換範本時，此範例中會記錄訊息。 如果主機是[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，會加入錯誤視窗。  
  
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
  
## <a name="using-the-visual-studio-api"></a>使用 Visual Studio 應用程式開發介面  
 如果您正在執行中的文字範本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，您可以使用`this.Host`來存取服務所提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]以及任何封裝或已載入的延伸模組。  
  
 設定 hostspecific ="true"，並轉換`this.Host`至<xref:System.IServiceProvider>。  
  
 這個範例會取得[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]API， <xref:EnvDTE.DTE>，做為服務：  
  
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
  
## <a name="using-hostspecific-with-template-inheritance"></a>使用範本繼承 hostSpecific  
 指定`hostspecific="trueFromBase"`如果您同時使用`inherits`屬性，而且如果您繼承自指定的範本`hostspecific="true"`。 這可避免編譯器警告的效果，屬性`Host`已兩次宣告。
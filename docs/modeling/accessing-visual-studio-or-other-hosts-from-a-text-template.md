---
title: "從文字範本存取 Visual Studio 或其他主機 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 5
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 5
---
# 從文字範本存取 Visual Studio 或其他主機
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在文字範本中，您可以使用執行範本的主應用程式 \(例如 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\) 所公開的方法和屬性。  
  
 這適用於一般文字範本，不適用於前置處理過的文字範本。  
  
## 取得主機的存取權  
 在 `template` 指示詞中設定 `hostspecific="true"`。  這可讓您使用`this.Host`，它具有型別<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>。  這個型別的成員可用來，例如解析檔案名稱和記錄錯誤。  
  
### 解析檔案名稱  
 若要尋找相對於文字範本的完整檔案路徑，請使用 this.Host.ResolvePath\(\)。  
  
```c#  
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
  
### 顯示錯誤訊息  
 這個範例會在轉換範本時記錄訊息。  如果主應用程式為 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，則會將錯誤訊息加入至錯誤視窗。  
  
```c#  
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
  
## 使用 Visual Studio API  
 如果在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中執行文字範本，您可以使用 `this.Host` 存取 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 所提供的服務，以及任何已載入的封裝或擴充功能。  
  
 設定 hostspecific\="true"，並將 `this.Host` 轉換成 <xref:System.IServiceProvider>。  
  
 這個範例會以服務方式取得 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API，<xref:EnvDTE.DTE>：  
  
```c#  
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
  
## 使用樣板繼承的 hostSpecific  
 指定`hostspecific="trueFromBase"`如果您也使用`inherits`屬性，如果您是繼承自指定的範本，並`hostspecific="true"`。  這可避免編譯器警告的效果，該屬性`Host`已經宣告了兩次。
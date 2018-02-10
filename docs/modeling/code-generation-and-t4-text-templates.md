---
title: "程式碼產生和 T4 文字範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-modeling
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 029b5264d5275458aee1893df0ba4dd4d83d1a91
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="code-generation-and-t4-text-templates"></a>程式碼產生和 T4 文字範本
在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中， *「T4 文字範本」* (T4 text template) 混合了文字區塊及可產生文字檔案的控制邏輯。 控制邏輯是由 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]撰寫的程式碼片段。 在 Visual Studio 2015 Update 2 (含) 以後版本中，您可以在 T4 範本指示詞中使用 C# 6.0 版功能。 產生的檔案可以是任何類型的文字，例如網頁、資源檔或任何語言的原始程式碼。  
  
 T4 文字範本有兩種：  
  
 **執行階段 T4 文字範本** (「前置處理過」的範本) 會在應用程式中執行以產生文字字串，通常作為其輸出的一部分。  
 例如，您可以建立用來定義 HTML 網頁的範本：  
  
```  
<html><body>  
 The date and time now is: <#= DateTime.Now #>  
</body></html>  
```  
  
 請注意，範本與產生的輸出類似。 範本與產生的輸出之間的相似性，可協助您避免在要變更範本時發生錯誤。  
  
 此外，範本也包含程式碼片段。 您可以使用這些片段來重複文字區段、建立條件式區段，以及顯示應用程式的資料。  
  
 為產生輸出，應用程式會呼叫範本所產生的函式。 例如:   
  
```csharp  
string webResponseText = new MyTemplate().TransformText();  
  
```  
  
 應用程式可以在未安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的電腦上執行。  
  
 若要建立執行階段範本，請將 [前置處理過的文字範本]  檔案加入專案中。 此外，您也可以加入純文字檔，並將其 [自訂工具]  屬性設定為 [TextTemplatingFilePreprocessor] 。  
  
 如需詳細資訊，請參閱[執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。 範本的語法的相關資訊，請參閱[撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。  
  
 **設計階段 T4 文字範本** 會在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中執行，以定義原始程式碼的一部分及應用程式的其他資源。  
 您通常會使用幾個範本讀取單一輸入檔案或資料庫中的資料，然後產生部分 `.cs`、 `.vb`或其他原始程式檔。 每個範本都會產生一個檔案， 並且在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]中執行。  
  
 例如，輸入資料可以是組態資料的 XML 檔案。 每當您在開發期間編輯 XML 檔案時，文字範本就會重新產生應用程式程式碼的一部分。 其中一個範本可能類似下列範例：  
  
```  
<#@ output extension=".txt" #>  
<#@ assembly name="System.Xml" #>  
<#  
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.  
#>  
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>  
{  
  ... // More code here.   
}  
  
```  
  
 視 XML 檔案中的值而定，產生的 `.cs` 檔案將與下面類似：  
  
```  
namespace Fabrikam.FirstJob  
{  
  ... // More code here.   
}  
```  
  
 另一個範例是，輸入可以是商務活動中的工作流程圖。 當使用者變更其商務工作流程，或您與工作流程不同的新使用者開始合作時，就可以輕鬆地重新產生符合新模型的程式碼。  
  
 設計階段範本可讓您在需求變更時，更快速且可靠地變更組態。 如工作流程範例所示，輸入通常是依照商務需求定義的。 這可讓您更容易與使用者討論變更。 因此，設計階段範本對敏捷式開發流程來說是很有用的工具。  
  
 若要建立設計階段範本，請將 [文字範本]  檔案加入專案中。 此外，您也可以加入純文字檔，並將其 [自訂工具]  屬性設定為 [TextTemplatingFileGenerator] 。  
  
 如需詳細資訊，請參閱[設計階段透過使用 T4 文字範本的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。 範本的語法的相關資訊，請參閱[撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。  
  
> [!NOTE]
>  *「模型」* (model) 一詞有時可用來描述由一個或多個範本讀取的資料。 模型可以是任何形式、任何類型的檔案或資料庫。 它不需要是 UML 模型或「特定領域語言」模型。 「模型」只表示資料可以依照商務概念定義，而非類似於程式碼。  
  
 文字範本轉換功能的名稱為 *T4*。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 在任何會產生文字檔案的應用程式中，先行編譯的文字範本是簡單而可靠的文字定義方法。 但是，此方法不可用於會在執行階段變更的文字範本。  
  
 [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 從模型產生程式碼和其他資源，可讓您藉由更新模型，來更新您的應用程式。  
  
 [建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)  
 如果您已安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK，即可確保產生的軟體具有模型中的最新變更。  
  
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)  
 文字範本檔案的語法。  
  
 [逐步解說：使用文字範本產生程式碼](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 示範程式碼產生的一種使用方式。  
  
 [偵錯 T4 文字範本](../modeling/debugging-a-t4-text-template.md)  
 如何對文字範本進行偵錯，以及一些常見的文字範本錯誤。  
  
 [使用 TextTransform 公用程式產生檔案](../modeling/generating-files-with-the-texttransform-utility.md)  
 可用以執行文字範本轉換的命令列工具。  
  
 [自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)  
 如何為您自己的資料來源撰寫指示詞處理器和自訂範本化主機。  
  
## <a name="see-also"></a>請參閱  
 [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)
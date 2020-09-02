---
title: 程式碼產生和 T4 文字模板 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f34422dfd47efdce9bf837f923da0e139a13398
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667926"
---
# <a name="code-generation-and-t4-text-templates"></a>程式碼產生和 T4 文字範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中， *「T4 文字範本」* (T4 text template) 混合了文字區塊及可產生文字檔案的控制邏輯。 控制邏輯是由 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]撰寫的程式碼片段。 在 Visual Studio 2015 Update 2 (含) 以後版本中，您可以在 T4 範本指示詞中使用 C# 6.0 版功能。 產生的檔案可以是任何類型的文字，例如網頁、資源檔或任何語言的原始程式碼。

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

 為產生輸出，應用程式會呼叫範本所產生的函式。 例如：

```csharp
string webResponseText = new MyTemplate().TransformText();

```

 應用程式可以在未安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的電腦上執行。

 若要建立執行階段範本，請將 [前置處理過的文字範本] **** 檔案加入專案中。 此外，您也可以加入純文字檔，並將其 [自訂工具] **** 屬性設定為 [TextTemplatingFilePreprocessor] ****。

 如需詳細資訊，請參閱 [使用 T4 文字模板的執行時間文字產生](../modeling/run-time-text-generation-with-t4-text-templates.md)。 如需範本語法的詳細資訊，請參閱 [撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md)。

 **設計階段 T4 文字範本** 會在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中執行，以定義原始程式碼的一部分及應用程式的其他資源。
您通常會使用幾個範本讀取單一輸入檔案或資料庫中的資料，然後產生部分 `.cs`、 `.vb`或其他原始程式檔。 每個範本都會產生一個檔案， 並且在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 或 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]中執行。

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

 若要建立設計階段範本，請將 [文字範本] **** 檔案加入專案中。 此外，您也可以加入純文字檔，並將其 [自訂工具] **** 屬性設定為 [TextTemplatingFileGenerator] ****。

 如需詳細資訊，請參閱 [使用 T4 文字模板的設計階段程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。 如需範本語法的詳細資訊，請參閱 [撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md)。

> [!NOTE]
> *「模型」* (model) 一詞有時可用來描述由一個或多個範本讀取的資料。 模型可以是任何形式、任何類型的檔案或資料庫。 它不需要是 UML 模型或「特定領域語言」模型。 「模型」只表示資料可以依照商務概念定義，而非類似於程式碼。

 文字範本轉換功能的名稱為 *T4*。

## <a name="in-this-section"></a>本節內容
 [使用 T4 文字模板產生執行時間文字](../modeling/run-time-text-generation-with-t4-text-templates.md) 在產生文字檔的任何應用程式中，先行編譯文字模板是定義文字的簡單可靠方法。 但是，此方法不可用於會在執行階段變更的文字範本。

 [使用 T4 文字模板產生設計階段程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md) 從模型產生程式碼和其他資源，可讓您藉由更新模型來更新您的應用程式。

 [在組建流程中產生程式碼](../modeling/code-generation-in-a-build-process.md) 如果您已安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 視覺效果和模型 SDK，您可以確保產生的軟體會隨著模型中的變更保持最新狀態。

 [撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md) 文字模板檔案的語法。

 [逐步解說：使用文字模板產生程式碼](../modeling/walkthrough-generating-code-by-using-text-templates.md) 示範如何使用程式碼產生的一種方式。

 [對 T4 文字模板進行調試](../modeling/debugging-a-t4-text-template.md) 如何調試文字模板，以及一些常見的文字模板錯誤。

 [使用 TextTransform 公用程式產生](../modeling/generating-files-with-the-texttransform-utility.md) 檔案您可以用來執行文字模板轉換的命令列工具。

 [自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md) 如何為您自己的資料來源撰寫指示詞處理器和自訂範本化主機。

## <a name="see-also"></a>另請參閱
 [從 UML 模型產生](../modeling/generate-files-from-a-uml-model.md)檔案從 [特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)

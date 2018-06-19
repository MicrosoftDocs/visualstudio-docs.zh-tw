---
title: 程式碼產生和 T4 文字範本
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f4fed2cbf00717e4eaf9c1353370dbd96037491
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32425497"
---
# <a name="code-generation-and-t4-text-templates"></a>程式碼產生和 T4 文字範本

在 Visual Studio *T4 文字範本*了不同的文字區塊和控制項邏輯，可產生文字檔案。 控制邏輯是由 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]撰寫的程式碼片段。 在 Visual Studio 2015 Update 2 (含) 以後版本中，您可以在 T4 範本指示詞中使用 C# 6.0 版功能。 產生的檔案可以是任何類型的文字，例如網頁、資源檔或任何語言的原始程式碼。

有兩種類型的 T4 文字範本： 執行階段和設計階段。

## <a name="run-time-t4-text-templates"></a>執行階段 T4 文字範本

也稱為 '前置處理過' 的範本，執行階段範本中執行的應用程式來產生文字的字串，通常作為其輸出的一部分。 例如，您可以建立用來定義 HTML 網頁的範本：

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

您的應用程式可以在未安裝 Visual Studio 的電腦上執行。

若要建立執行階段範本，請將 [前置處理過的文字範本]  檔案加入專案中。 此外，您也可以加入純文字檔，並將其 [自訂工具]  屬性設定為 [TextTemplatingFilePreprocessor] 。

如需詳細資訊，請參閱[執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。 範本的語法的相關資訊，請參閱[撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。

## <a name="design-time-t4-text-templates"></a>設計階段 T4 文字範本

設計階段 tempaltes 定義原始程式碼的一部分及應用程式的其他資源。 您通常使用幾個範本讀取單一輸入的檔案或資料庫中的資料，並產生一些您 *.cs*， *.vb*，或其他原始程式檔。 每個範本都會產生一個檔案， 它們會在 Visual Studio 或 MSBuild 內執行。

例如，輸入資料可以是組態資料的 XML 檔案。 每當您在開發期間編輯 XML 檔案，文字範本重新產生應用程式程式碼的一部分。 其中一個範本可能類似下列範例：

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

在 XML 檔案中，所產生的值根據 *.cs*檔案會與下列類似：

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
> *「模型」* (model) 一詞有時可用來描述由一個或多個範本讀取的資料。 模型可以是任何形式、任何類型的檔案或資料庫。 它不需要是 UML 模型或「特定領域語言」模型。 「模型」只表示資料可以依照商務概念定義，而非類似於程式碼。

文字範本轉換功能的名稱為 *T4*。

## <a name="see-also"></a>另請參閱

- [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)